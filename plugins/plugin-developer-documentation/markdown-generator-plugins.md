# Markdown Generator Plugins

The Markdown Generator custom plugin allows you to create a form for your project managers, to which they will upload a Markdown and a CSV file. You will get access to both in your Python script, and you'll be able to manipulate both to then upload assets to a project.

Usually, the Markdown file will be be populated with data from the CSV file and will be imported to your project of choice as an asset, as shown in the example below.

## Creating a Markdown Generator Plugin

Following the steps outlined [in this section](./#creating-a-new-plugin), create a new plugin from the UI, choosing "Markdown Generator" as the plugin type.

Then, create and run a Python script using the `MarkdownPlugin` class you can find in our `ango` Python package under `ango.plugins`.

You will need to add the `ango` package to your Python environment by running

```
pip install ango
```

Here is the class's documentation, and an example:

#### MarkdownPlugin

Parameters:

* **id:** _string_
  * The plugin's ID. You may obtain this ID from the plugin's information box in the _Development_ section of the _Plugin_ page.
* **secret:** _string_
  * The plugin's secret. You can think of this as a private key you'll need to be able to connect your script to the plugin. You may obtain this secret from the plugin's information box in the _Development_ section of the _Plugin_ page.
* **callback:** _Callable\[\[str, dict], Tuple\[str, BytesIO]]_
  * The callback function. This function will be run whenever a user runs this plugin. More on the callback function below.

**Callback Function**

Parameters:

* **\*\*data**: _dict_
  * **projectId:** _str_
    * The ID of the project to which the populated Markdown file needs to be uploaded.
  * **fileList**: _List\[dict]_
  * **inputFile**: _str_
  * **apiKey**: _str_
    * The API key of the user running the plugin.
  * **orgId**: _str_
    * The ID of the organization where the plugin is being run.
  * **runBy**: _str_
    * The ID of the user running the plugin.
  * **session**: _str_
    * The ID of the session created when running the plugin.
  * **batches:** _List\[str]_
    * Batches to which the final text assets will be assigned.
  * **markdownText:** _string_
    * The Markdown text the contents of which will be populated with the CSV.
  * **logger:** _PluginLogger_
    * \[TODO]
  * **configJSON**: _str_
    * The config JSON your users will pass to you through the _Config JSON_ text field when running the plugin. Warning: the JSON will be passed as a string so you will have to destringify it. Example code to obtain the original JSON as a Python object:

```python
def sample_callback(**data):
    config_str = data.get('configJSON')
    config = json.loads(config_str)
```

Returns:

* **message:** _string_
  * Message to show users once the plugin has finished running.

#### Sample Python Script

```python
import os
import math
import json
import pandas as pd
import numpy as np
from io import BytesIO
from ango.sdk import SDK
from html import unescape
from base64 import b64decode
from ango.plugins import MarkdownPlugin, run

HOST = '<YOUR HOST>'
PLUGIN_ID = '<YOUR PLUGIN ID>'
PLUGIN_SECRET = '<YOUR PLUGIN SECRET>'


def check_config(config, column_names):
    batch_name_column = 'AUTO_DETECT'
    if 'batch_name_column' in config:
        if config['batch_name_column'] in column_names:
            batch_name_column = config['batch_name_column']

    external_id_columns = []
    if 'external_id_columns' in config:
        external_id_columns = config['external_id_columns']

    upload_batch_size = 100
    if 'upload_batch_size' in config:
        if isinstance(config['upload_batch_size'], int):
            if config['upload_batch_size'] > 0:
                upload_batch_size = config['upload_batch_size']

    return batch_name_column, external_id_columns, upload_batch_size


def sample_callback_function(**data):
    # Extract input parameters
    file = data.get('inputFile')
    project_id = data.get('projectId')
    api_key = data.get('apiKey')
    batches = data.get('batches', [])
    markdown_text = data.get('markdownText', [])
    integration_id = data.get('integrationId')
    logger = data.get('logger')
    config_str = data.get('configJSON')
    config = json.loads(config_str)

    logger.info("Plugin session is started!")

    sdk = SDK(api_key=api_key, host=HOST)

    # Read CSV file
    file_decoded = BytesIO(b64decode(file))
    data_df = pd.read_csv(file_decoded, dtype=str, keep_default_na=False)
    field_list = list(data_df.columns)

    batch_name_column, external_id_columns, upload_batch_size = check_config(config, field_list)

    # Detect the batch field
    batch_field = ""
    batch_flag = False
    if batch_name_column == "AUTO_DETECT":
        batch_keywords = ['batch', 'batch_name', 'batch-name', 'batchname']
        for field in field_list:
            if field.lower() in batch_keywords:
                batch_field = field
                batch_flag = True
                break
    elif batch_name_column == "IGNORE":
        batch_field = ""
        batch_flag = False
    else:
        batch_field = batch_name_column
        batch_flag = True

    # Get project batches
    project_batch_name_list = []
    if batch_flag:
        batch_response = sdk.get_batches(project_id)
        for index in range(len(batch_response)):
            batch_name = batch_response[index]['name']
            project_batch_name_list.append(batch_name)

    # Create batches
    if batch_flag:
        unique_batch_name_list = list(data_df[batch_field].unique())
        for batch_name in unique_batch_name_list:
            if batch_name not in project_batch_name_list:
                sdk.create_batch(project_id=project_id, batch_name=batch_name)

    # Replace escape characters in HTML code
    markdown_text_raw = unescape(markdown_text)

    batch_size = upload_batch_size
    num_batches = math.ceil(len(data_df) / batch_size)
    logger.info("Files Uploaded: [" + str(len(data_df)) + "/0]")
    for batch_index in range(num_batches):
        start_index = batch_index*batch_size
        end_index = np.min( [(batch_index+1)*batch_size, len(data_df)] )

        file_paths = []
        for index in range(start_index, end_index):
            # Replace placeholders in markdown text with the values on the CSV file
            markdown_text_processed = markdown_text_raw
            for field in field_list:
                search_keyword = '|' + field + '|'
                replace_keyword = data_df.iloc[index][field]
                markdown_text_processed = markdown_text_processed.replace(search_keyword, replace_keyword)

            # Create temporary md file
            if len(external_id_columns) == 0:
                external_id = str(index).zfill(5) + '.md'
            else:
                name_list = []
                for external_id_column in external_id_columns:
                    name_list.append(data_df.iloc[index][external_id_column])
                external_id = '_'.join(name_list)

            if batch_flag:
                batch_name = data_df.iloc[index][batch_field]
                file_paths.append({"data": markdown_text_processed, "externalId": external_id, "batches": [batch_name]})
            else:
                file_paths.append({"data": markdown_text_processed, "externalId": external_id})

        response = sdk.upload_files_cloud(project_id=project_id, assets=file_paths)
        logger.info("Files Uploaded: [" + str(len(data_df)) + "/" + str(end_index) + "]")

    logger.info("Plugin session is ended!")
    if response['status'] == 'success':
        return 'All markdown files are uploaded!'
    else:
        logger.warning(response['message'])
        return response['message']


if __name__ == "__main__":
    plugin = MarkdownPlugin(id=PLUGIN_ID,
                            secret=PLUGIN_SECRET,
                            callback=sample_callback_function)

    run(plugin, host=HOST)
```

Find an always up-to-date version of this sample code at:

{% embed url="https://github.com/angoai/plugin-samples/blob/main/markdown_plugin.py" %}

For this example, we use the following default Config JSON:

```json
{
  "batch_name_column": "AUTO_DETECT",
  "external_id_columns": [],
  "upload_batch_size": 100
}
```

## Creating a Markdown Asset with the Plugin

{% hint style="info" %}
Your Python script needs to be running for users to be able to run your plugin.
{% endhint %}

If you are the creator of the plugin, from the _Plugins_ page, enter the _Development_ section and click on _Open_ on the relevant plugin. A dialog will pop up.

If you have added the plugin from the [Directory](../installing-plugins.md), go to the project where you'd like to use the plugin, and from the _Settings_ tab (1) click on _Plugins_ (2). Then, click on _Open_ (3) on the relevant plugin. A dialog will pop up.

<figure><img src="../../.gitbook/assets/image (382).png" alt=""><figcaption></figcaption></figure>

This is the dialog that will appear when clicking on _Run_ on the Markdown plugin:

<figure><img src="../../.gitbook/assets/image (370).png" alt=""><figcaption></figcaption></figure>

**Project**: The project where you'd like the final assembled asset to be uploaded. If you are running this plugin from a project, the project you're in will be pre-selected.

**File Upload**: Upload the CSV file you'd like to use as base to populate the Markdown file.

**Create Markdown**: Upload or write a Markdown file to use as skeleton. Clicking on _Open Editor_ will open a simple Markdown text editor with built-in preview of what it will look like on Hub.



For example, if you were to use the Python code provided above, you might use the following CSV file:

```csv
id,name,surname,phone,birthday,birthplace,url1,url2,url3,url4,url5
1001,Harry,Potter,1234,31.07.1980,London,https://en.wikipedia.org/wiki/Harry_Potter_(character),https://en.wikipedia.org/wiki/Daniel_Radcliffe,https://www.imdb.com/name/nm0705356/,https://www.rottentomatoes.com/celebrity/daniel_radcliffe,https://www.instagram.com/daniel9340/?hl=en
1002,Hermione,Granger,4567,19.09.1979,London,https://en.wikipedia.org/wiki/Hermione_Granger,https://en.wikipedia.org/wiki/Emma_Watson,https://www.imdb.com/name/nm0914612/,https://www.rottentomatoes.com/celebrity/emma_watson,https://www.instagram.com/emmawatson/?hl=en
1003,Ron,Weasley,1357,01.03.1980,London,https://en.wikipedia.org/wiki/Ron_Weasley,https://en.wikipedia.org/wiki/Rupert_Grint,https://www.imdb.com/name/nm0342488/,https://www.rottentomatoes.com/celebrity/rupert_grint,https://www.instagram.com/rupertgrint/?hl=en
```

And the following Markdown file:

```markdown
<div style="margin:10px;display:flex;">
	<div style="width:50%">
		<div style="font-size:13px;font-weight:500;display:flex;">
			<div style="width:100px;color:gray">Name</div>: |name|
		</div>
		<div style="font-size:13px;font-weight:500;display:flex;">
        	<div style="width:100px;color:gray">Surname</div>: |surname|		
		</div>
		<div style="font-size:13px;font-weight:500;display:flex;">
			<div style="width:100px;color:gray">Phone</div>: |phone|
		</div>
		<div style="font-size:13px;font-weight:500;display:flex;">
        	<div style="width:100px;color:gray">Birthday</div>: |birthday|	
		</div>
		<div style="font-size:13px;font-weight:500;display:flex;">
        	<div style="width:100px;color:gray">Birthplace</div>: |birthplace|
		</div>
	</div>
	<div style="width:50%">
		<div style="font-size:13px;font-weight:500;display:flex;">
        	<div style="width:100px;color:gray">url1</div>: <a href="|url1|" target="_blank">|url1|</a>
		</div>
		<div style="font-size:13px;font-weight:500;display:flex;">
        	<div style="width:100px;color:gray">url2</div>: <a href="|url2|" target="_blank">|url2|</a>
		</div>
		<div style="font-size:13px;font-weight:500;display:flex;">
        	<div style="width:100px;color:gray">url3</div>: <a href="|url3|" target="_blank">|url3|</a>
		</div>
		<div style="font-size:13px;font-weight:500;display:flex;">
        	<div style="width:100px;color:gray">url4</div>: <a href="|url4|" target="_blank">|url4|</a>
		</div>
		<div style="font-size:13px;font-weight:500;display:flex;">
        	<div style="width:100px;color:gray">url5</div>: <a href="|url5|" target="_blank">|url5|</a>
		</div>
	</div>
</div>
```

You would obtain three assets, one from each of the CSV lines, looking like the Markdown but populated in the |name|, |surname|, etc. areas with the data in the CSV.

{% embed url="https://github.com/angoai/plugin-samples/tree/main/files" %}
