# Export Plugins

With the Export custom plugin, you can add your own export format to Ango Hub with only a few clicks.

The Export custom plugin provides a way for you to obtain the normal Ango JSON Export, manipulate it from within a Python script, and present its manipulated version to users for download.

## Creating an Export Plugin

Following the steps outlined [in this section](./#creating-a-new-plugin), create a new plugin from the UI, choosing "Export" as the plugin type.

Then, create and run a Python script using the `ExportPlugin` class you can find in our `ango` Python package under `ango.plugins`.

In this script, you will get the 'regular' Ango export as input, and you will need to provide a .zip file as well as its name as output. An example is provided below.

You will need to add the `ango` package to your Python environment by running

```
pip install ango
```

Here is the class's documentation, and an example:

#### ExportPlugin

Parameters:

* **id:** _str_
  * The plugin's ID. You may obtain this ID from the plugin's information box in the _Development_ section of the _Plugin_ page.
* **secret:** _str_
  * The plugin's secret. You can think of this as a private key you'll need to be able to connect your script to the plugin. You may obtain this secret from the plugin's information box in the _Development_ section of the _Plugin_ page.
* **callback:** _Callable\[\[str, dict], Tuple\[str, BytesIO]]_
  * The callback function. This function will be run whenever a user asks for the export using this plugin. More on the callback function below.
* **host:** _str, default="https://api.ango.ai"_
  * You do not need to change the host unless you are creating plugins in environments other than our main Cloud instance at hub.ango.ai.

**Callback Function**

Parameters:

* **\*\*data**: _dict_
  * **projectId:** _str_
    * The ID of the project for which the export was wanted.
  * **jsonExport:** _dict_
    * The normal JSON export in Ango Hub Annotation Format. This is the export you would get if you manually requested the export in the "JSON" format.
  * **logger:** _PluginLogger_
    * \[TODO]
  * **apiKey**: _str_
    * The API key of the user running the plugin.
  * **orgId**: _str_
    * The organization ID of the organization where the plugin is run.
  * **runBy**: _str_
    * User ID of the user running the plugin.
  * **session**: _str_
    * ID of the session opened when the plugin is run.
  * **configJSON**: _str_
    * The config JSON your users will pass to you through the _Config JSON_ text field when running the plugin. Warning: the JSON will be passed as a string so you will have to destringify it. Example code to obtain the original JSON as a Python object named _config_:

```python
def sample_callback(**data):
    config_str = data.get('configJSON')
    config = json.loads(config_str)
```

Returns:

* **zip\_file\_name:** _str_
  * When closing your callback, you'll need to return the name of the export .zip file as a string here.
* **zip\_data:** _BytesIO_
  * The final .zip you will provide users with, containing the export.

#### Sample Python Script

```python
import json
import zipfile
from tqdm import tqdm
from io import BytesIO
from ango.plugins import ExportPlugin, run

HOST = '<YOUR HOST>'
PLUGIN_ID = '<YOUR PLUGIN ID>'
PLUGIN_SECRET = '<YOUR PLUGIN SECRET>'


def sample_callback(**data):
    # Extract input parameters
    project_id = data.get('projectId')
    json_export = data.get('jsonExport')
    logger = data.get('logger')
    config_str = data.get('configJSON')
    config = json.loads(config_str)

    logger.info("Plugin session is started!")

    # Check config input
    separator_char = '-'
    if 'separator-character' in config:
        if isinstance(config['separator-character'], str):
            separator_char = config['separator-character']

    # Convert annotation data to intended format
    file_list = []
    for image_index, asset in enumerate(tqdm(json_export)):
        external_id = asset['externalId']
        data_url = asset['asset']
        objects = asset['tasks'][0]['objects']

        object_list = []
        for obj in objects:
            if "bounding-box" in obj:
                class_name = obj['title']
                x, y = int(round(obj["bounding-box"]['x'])), int(round(obj["bounding-box"]['y']))
                w, h = int(round(obj["bounding-box"]['width'])), int(round(obj["bounding-box"]['height']))

                single_object_string = ' '.join([class_name, str(x), str(y), str(w), str(h)])
                object_list.append(single_object_string)
        object_string = separator_char.join(object_list)
        file_list.append({'externalId': external_id, 'URL': data_url, 'Annotations': object_string})

    # Create zip file
    zip_file_name = project_id + '.zip'
    zip_data = BytesIO()
    with zipfile.ZipFile(zip_data, mode="w") as zf:
        zf.writestr(project_id + '.json', json.dumps(file_list, indent=4))

    logger.info("Plugin session is ended!")
    return zip_file_name, zip_data


if __name__ == "__main__":
    plugin = ExportPlugin(id=PLUGIN_ID,
                          secret=PLUGIN_SECRET,
                          callback=sample_callback,
                          host=HOST)

    run(plugin, host=HOST)
```

Find an always up-to-date version of this sample code at:

{% embed url="https://github.com/angoai/plugin-samples/blob/main/v2/export_plugin.py" %}

For this example, we use the following default Config JSON:

```json
{
  "separator-character": "-"
}
```

## Getting an Export using the Plugin

{% hint style="info" %}
Your Python script needs to be running for users to be able to download exports using your format.
{% endhint %}

Navigate to the project you'd like to get the export of. From the _Settings_ tab, enter the _Plugins_ section. Click _Open_ on the Export plugin of interest.

<figure><img src="../../.gitbook/assets/image (382).png" alt=""><figcaption></figcaption></figure>

From the dialog that pops up, click on _Run_. You will get a notification when your export is ready.
