# Model Plugins

With the Model custom plugin, you can add a quick way for users to run your model on their project assets.

When users click to run your plugin, you will get one of their assets, feed them to your model, and return the model's results as pre-annotations to their assets.

## Creating a Model Plugin

Following the steps outlined [in this section](./#creating-a-new-plugin), create a new plugin from the UI, choosing "Model" as the plugin type.

<figure><img src="../../.gitbook/assets/image (373).png" alt=""><figcaption></figcaption></figure>

In the "Class Names" section, enter the names of the classes used by your model.

For example, assume that your model has three classes it returns, "person," "car," and "light." At a later stage, the user will be able to "link" (map) these classes to their own label categories representing the ideas of "person," "car" etc.

Then, create and run a Python script using the `ModelPlugin` class you can find in our `ango` Python package under `ango.plugins`.

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
    * **dataURL**: _str_
      * The URL of the file to be sent to the model.
      * Example: `https://your-bucket.s3.eu-central-1.amazonaws.com/bb26ccc1-3a9f-4e41-bb01-df285b0c5bd5.jpg`
    * **apiKey**: _str_
      * The API Key of the user running the plugin.
    * **orgId**: _str_
      * The Organization ID of the organization where the plugin is run.
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

* **annotation\_json:** _dict_
  * A message to show users when the plugin finishes running.
  * Example:

```json
{
  "data": "https://angohub-public-assets.s3.eu-central-1.amazonaws.com/bb26ccc1-3a9f-4e41-bb01-df285b0c5bd5.jpg",
  "answer": {
    "objects": [...],
    "classifications": [...],
    "relations": [...]
  }
}
```

#### Sample Python Script

In this script, for the sake of brevity, instead of running the asset through a model, we add a bounding box to it as pre-label, "simulating" the model's results. We then upload these annotations to the user's assets with a "To-Do" status as prelabels using the [SDK](../../sdk/sdk-documentation.md).

```python
import json
from ango.sdk import SDK
from ango.plugins import ModelPlugin, run

HOST = '<YOUR HOST>'
PLUGIN_ID = '<YOUR PLUGIN ID>'
PLUGIN_SECRET = '<YOUR PLUGIN SECRET>'


def run_model(**data):
    # Extract input parameters
    project_id = data.get('projectId')
    data_url = data.get("dataURL")
    category_schema = data.get('categorySchema')
    logger = data.get('logger')
    api_key = data.get('apiKey')
    config_str = data.get('configJSON')
    if config_str is not None:
        config = json.loads(config_str)

    logger.info("Plugin session is started!")

    if category_schema is None:
        bbox_obj = [{"bounding-box": {"x": 20, "y": 30, "width": 50, "height": 60} }]
        annotation_json = {"data": data_url,
                           "answer": {"objects": bbox_obj, "classifications": [], "relations": []}}
    else:
        schema_id = category_schema[0]['schemaId']
        bbox_obj = [{"schemaId": schema_id,
                     "bounding-box": {"x": 20, "y": 30, "width": 50, "height": 60} }]
        annotation_json = {"data": data_url,
                           "answer": {"objects": bbox_obj, "classifications": [], "relations": []}}
    
    logger.info("Plugin session is ended!")
    return annotation_json

if __name__ == "__main__":
    plugin = ModelPlugin(id=PLUGIN_ID,
                         secret=PLUGIN_SECRET,
                         callback=run_model)

    run(plugin, host=HOST)
```

Find the always up-to-date version of this code at the following link:

{% embed url="https://github.com/angoai/plugin-samples/blob/main/v2/model_plugin.py" %}

## Running a Model using the Plugin

{% hint style="info" %}
Your Python script needs to be running for users to be able to run your plugin.
{% endhint %}

Navigate to the asset were you'd like to run the model. Click on the "detectors" icon, then on the name of the model.

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

From the dialog that pops up, map your classes to the model's classes, then click on _Run_. The plugin will pre-label your asset with the model's results.
