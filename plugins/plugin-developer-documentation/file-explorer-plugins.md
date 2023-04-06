# File Explorer Plugins

File Explorer plugins allow you to import an entire folder of assets at once into the project of your choice, from a private bucket.&#x20;

## Creating a File Explorer Plugin

First, add an integration from Hub to the private bucket you'd like to navigate with the File Explorer. You may find instructions on doing so [here](../../data/importing-assets/importing-private-cloud-assets-aws.md).

Following the steps outlined [in this section](./#creating-a-new-plugin), create a new plugin from the UI, choosing "File Explorer" as the plugin type.

Then, create and run a Python script using the `FileExplorerPlugin` class you can find in our `ango` Python package under `ango.plugins`.

You will need to add the `ango` package to your Python environment by running

```
pip install ango
```

Here is the class's documentation, and an example:

#### FileExplorerPlugin

Parameters:

* **id:** _string_
  * The plugin's ID. You may obtain this ID from the plugin's information box in the _Development_ section of the _Plugin_ page.
* **secret:** _string_
  * The plugin's secret. You can think of this as a private key you'll need to be able to connect your script to the plugin. You may obtain this secret from the plugin's information box in the _Development_ section of the _Plugin_ page.
* **callback:** _Callable\[\[str, dict], Tuple\[str, BytesIO]]_
  * The callback function. This function will be run whenever a user runs this plugin.

**Callback Function**

Parameters:

*   **\*\*data**: _dict_

    * **folder**: _str_
    * **projectId:** _str_
    * **integrationId**: _str_
    * **bucket:** _str_
      * The ID of the project for which the plugin was run.
    * **apiKey**: _str_
    * **orgId**: _str_
    * **runBy:** _str_
      * The user ID of the user running the plugin.
    * **session:** _str_
    * **logger:** _PluginLogger_
    * **batches**: _List\[str]_
    * **files**
    * **upload**
    * **project**
    * **scroll\_token**
    * **configJSON**: _str_
      * The config JSON your users will pass to you through the _Config JSON_ text field when running the plugin. Warning: the JSON will be passed as a string so you will have to destringify it. Example code to obtain the original JSON as a Python object:



    ```python
    def sample_callback(**data):
        config_str = data.get('configJSON')
        config = json.loads(config_str)
    ```

**Sample Python Script**

This script allows your users to navigate the file structure of a private bucket from AWS S3, from Ango Hub's UI, and to them import an entire folder of valid assets into the project of their choice.

```python
import boto3 as boto3
from ango.sdk import SDK
from ango.plugins import FileExplorerPlugin, run


HOST = '<YOUR HOST>'
PLUGIN_ID = '<YOUR PLUGIN ID>'
PLUGIN_SECRET = '<YOUR PLUGIN SECRET>'

PAGE_SIZE = 50


def sample_callback(**data):
    # Extract input parameters
    bucket = data.get("bucket")
    folder = data.get("folder", "")
    files = data.get("files", None)
    upload = data.get("upload", False)
    project_id = data.get("projectId", None)
    integration_id = data.get("integrationId", None)
    scroll_token = data.get("scrollToken", None)
    api_key = data.get("apiKey")
    logger = data.get("logger")

    logger.info("Plugin session is started!")

    sdk = SDK(api_key=api_key, host=HOST)
    integration = sdk.get_integrations(integration_id)

    region = integration.get("region")

    client = boto3.client('s3', region_name=region, aws_access_key_id=integration.get("publicKey"),
                          aws_secret_access_key=integration.get("privateKey"))
    s3paginator = client.get_paginator('list_objects')

    path = folder

    if upload:
        page_iterator = s3paginator.paginate(Bucket=bucket,
                                             Prefix=path,
                                             Delimiter='/',
                                             PaginationConfig={'PageSize': 1000})
        files_to_upload = []
        if files:
            for key in files:
                url = "https://%s.s3.%s.amazonaws.com/%s" % (bucket, region, key)
                files_to_upload.append({"data": url, "externalId": key})
        else:
            for page in page_iterator:
                for content in page.get("Contents", []):
                    key = content["Key"]
                    if key[-1] != "/":
                        url = "https://%s.s3.%s.amazonaws.com/%s" % (bucket, region, key)
                        files_to_upload.append({"data": url, "externalId": key})
        response = sdk.upload_files_cloud(project_id=project_id, assets=files_to_upload, integration_id=integration_id)
        logger.info("Plugin session is ended!")
        if response.get("status", "") == "success":
            return {"status": "success"}
        else:
            return {"status": "fail", "error": response}

    else:
        page_iterator = s3paginator.paginate(Bucket=bucket,
                                             Prefix=path,
                                             Delimiter='/',
                                             PaginationConfig={'PageSize': PAGE_SIZE, 'StartingToken': scroll_token})

        folders = []
        files = []
        page_iter = iter(page_iterator)
        page = next(page_iter)
        new_scroll_token = None
        files_page = page.get("Contents", [])
        folders_page = page.get("CommonPrefixes", [])
        if files_page is not None:
            for content in files_page:
                key = content["Key"]
                if key[-1] != "/":
                    files.append(key)
            if len(files_page) == PAGE_SIZE:
                new_scroll_token = page.get("Contents", [{}])[-1].get("Key", None)

        if folders_page is not None:
            for content in folders_page:
                key = content["Prefix"]
                folders.append(key)

        return {"folders": folders, "files": files, "scrollToken": new_scroll_token, "success": True}


if __name__ == "__main__":
    plugin = FileExplorerPlugin(id=PLUGIN_ID,
                                secret=PLUGIN_SECRET,
                                callback=sample_callback)
    run(plugin, host=HOST)
```

{% embed url="https://github.com/angoai/plugin-samples/blob/main/file_explorer_plugin.py" %}

## Running the File Explorer

If you have added this plugin from the [Directory](../installing-plugins.md), from the dashboard of the project where you'd like to run the script, enter the _Settings_ tab and then the _Plugin_ section. Then click on _Open_ on the File Explorer plugin you need. A dialog will pop up.

If you have created this plugin yourself, from the _Development_ section of the _Plugins_ page, click on _Open_ on the File Explorer plugin you need. A dialog will pop up.

<figure><img src="../../.gitbook/assets/image (355).png" alt=""><figcaption></figcaption></figure>

**Project**: The project in which you wish to import the assets.

**Bucket Name**: The name of the bucket you have integrated with Hub, which contains the assets to be imported. Ensure this is typed correctly.

**Integration**: The integration you set up in the previous step.

**Folder**: Once all other fields are filled, this button will activate. By clicking it, a dialog will pop up. From the dialog, you will be able to select a folder from your bucket, and by clicking on "Import" you will instantly add all valid assets in that folder to the selected project on Hub.
