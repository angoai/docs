# Batch Model Plugins

With the Batch Model custom plugin, you can add a quick way for users to run your model on their project assets.

When users click to run your plugin, you will get their assets, feed them to your model, and return the model's results as pre-annotations to their assets.

## Creating a Batch Model Plugin

Following the steps outlined [in this section](./#creating-a-new-plugin), create a new plugin from the UI, choosing "Batch Model" as the plugin type.

<figure><img src="../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

For more information on what all of the fields do, you may check the Plugin Developer Documentation's [main page](./).

In the "Class Names" section, enter the names of the classes used by your model. For example, if it detects cars, bikes, and trains using three different labeling tools, enter the three class names here.

In the "Default Config" section, enter JSON which will be shown to users by default in their _Config JSON_ field when running the plugin. Users can input any freeform JSON in this field, and it will be passed to your callback function in the code as parameter.

Then, create and run a Python script using the `BatchModelPlugin` class you can find in our `ango` Python package under `ango.plugins`.

You will need to add the `ango` package to your Python environment by running

```
pip install ango
```

Here is the class's documentation, and an example:

#### BatchModelPlugin

Parameters:

* **id:** _string_
  * The plugin's ID. You may obtain this ID from the plugin's information box in the _Development_ section of the _Plugin_ page.
* **secret:** _string_
  * The plugin's secret. You can think of this as a private key you'll need to be able to connect your script to the plugin. You may obtain this secret from the plugin's information box in the _Development_ section of the _Plugin_ page.
* **callback:** _Callable\[\[str, dict], Tuple\[str, BytesIO]]_
  * The callback function. This function will be run whenever a user asks for your model to be run using this plugin. More on the callback function below.

**Callback Function**

Parameters:

*   **\*\*data**: _dict_

    * **projectId:** _string_
      * The ID of the project for which the plugin was run.
    *   **categorySchema:** _dict_

        * The label categories that have been passed to this plugin when the plugin is being run.
        * For example, when creating the plugin, if in the "Class Names" section you had input the classes "Vehicle" and "Person", and when running, if they were both mapped to existing labeling tools, this is what you would get as input here:

        ```
        [{'schemaId': '797ea755f5693c0dc902558', 'modelClass': 'Vehicle'}, {'schemaId': '797ea755f5693c0dc902558', 'modelClass': 'Person'}]
        ```
    * **apiKey**: _str_
    * **orgId**: _str_
    * **runBy:** _str_
      * The user ID of the user running the plugin.
    * **session:** _str_
    * **logger:** _PluginLogger_
    * **batches**: _List\[str]_
    * **configJSON**: _str_
      * The config JSON your users will pass to you through the _Config JSON_ text field when running the plugin. Warning: the JSON will be passed as a string so you will have to destringify it. Example code to obtain the original JSON as a Python object:

    ```python
    def sample_callback(**data):
        config_str = data.get('configJSON')
        config = json.loads(config_str)
    ```

Returns:

* **message:** _string_
  * A message to show users when the plugin finishes running.

#### Sample Python Script

In this script, we get the first 10 assets of the project. Then, for the sake of brevity, instead of running them through a model, we add a bounding box to each as pre-label, "simulating" the model's results. We then upload these annotations to the user's assets with a "To-Do" status as prelabels using the [SDK](../../sdk/sdk-documentation.md).

```python
from ango.sdk import SDK
from ango.plugins import BatchModelPlugin, run
import json

HOST = '<YOUR HOST>'
PLUGIN_ID = '<YOUR PLUGIN ID>'
PLUGIN_SECRET = '<YOUR PLUGIN SECRET>'


def run_model(**data):
    # Extract input parameters
    project_id = data.get('projectId')
    category_schema = data.get('categorySchema')
    logger = data.get('logger')
    api_key = data.get('apiKey')
    config_str = data.get('configJSON')
    config = json.loads(config_str)

    logger.info("Plugin session is started!")

    # Check whether class mapping is done or not
    if category_schema is None:
        logger.warning("Please complete class mapping!")
        logger.info("Plugin session is ended!")
        return "Please complete class mapping!"

    sdk = SDK(api_key=api_key, host=HOST)

    # Get assets of the project
    # get_assets(project_id) returns only 10 assets. For more information check Ango SDK Documentation:
    # https://docs.ango.ai/sdk/sdk-documentation#get_assets-project_id-asset_id-external_id-page-limit
    get_assets_response = sdk.get_assets(project_id)
    asset_list = get_assets_response['data']['assets']

    # Add a dummy bounding-box to every asset
    schema_id = category_schema[0]['schemaId']  # Get schema_id of the first class
    annotation_json_list = []
    for asset in asset_list:
        # model
        external_id = asset['externalId']
        annotation_json = {"externalId": external_id,
                           "objects": [{"schemaId": schema_id,
                                        "bounding-box": config["dummy-bounding-box"]}]}
        annotation_json_list.append(annotation_json)

    # Import labels via SDK
    sdk.import_labels(project_id, annotation_json_list)
    logger.info("Plugin session is ended!")
    return "All annotations are imported!"


if __name__ == "__main__":
    plugin = BatchModelPlugin(id=PLUGIN_ID,
                              secret=PLUGIN_SECRET,
                              callback=run_model)

    run(plugin, host=HOST)
```

For this example, we use the following default Config JSON:

```json
{
  "dummy-bounding-box": {
    "x": 20, 
    "y": 30, 
    "width": 50, 
    "height": 60
  }
}
```

Find an always up-to-date code sample at the following link:

{% embed url="https://github.com/angoai/plugin-samples/blob/main/batch_model_plugin.py" %}

## Running a Model using the Plugin

{% hint style="info" %}
Your Python script needs to be running for users to be able to run your plugin.
{% endhint %}

Navigate to the project were you'd like to run the model. From the _Settings_ tab, enter the _Plugins_ section. Click _Open_ on the Model plugin of interest.

<figure><img src="../../.gitbook/assets/image (382).png" alt=""><figcaption></figcaption></figure>

From the dialog that pops up, map your classes to the model's classes, then click on _Run_.
