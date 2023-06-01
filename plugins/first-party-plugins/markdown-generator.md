# Markdown Generator

The Markdown Generator is a plugin made, published, and officially supported by Ango AI that allows you to create Markdown assets starting from a Markdown skeleton and a CSV table containing the data to fill in the skeleton.

<figure><img src="../../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

## Plugin Functionality

Assume you have a CSV-formatted table, like the following:

| name   | surname   | age |
| ------ | --------- | --- |
| Thomas | Haverford | 28  |
| Leslie | Knope     | 32  |
| Ronald | Swanson   | 48  |

{% file src="../../.gitbook/assets/markdown-plugin-sample.csv" %}
Download the sample CSV file here
{% endfile %}

And that you have a Markdown-formatted skeleton, with the table column names wrapped around pipes (|), like the following:

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
			<div style="width:100px;color:gray">Age</div>: |age|
		</div>
	</div>
</div>
```

(the above Markdown renders in Ango Hub like so:)

![](<../../.gitbook/assets/image (433).png>)

After feeding both the CSV file and the Markdown skeleton to the Markdown Plugin, the plugin will create three assets in the selected project for us (one for each row of the CSV), looking like the Markdown skeleton but with the "|name|", "|surname|", and "|age|" placeholders populated with the data from each CSV row.

As such, the three assets created by the Markdown Plugin, in our example, would look like this on Ango Hub, each with info from a row of the CSV:

![](<../../.gitbook/assets/image (457).png>)

### Assigning Rows/Assets to Batches on Upload

As the plugin creates one asset for each row, you may have Ango Hub assign each row/asset to a specific [batch](../../core-concepts/batches.md) on upload simply by indicating it in your CSV file.

To indicate batch information, add a column named any one of the following, case-insensitive:

_`batch, batch_name, batch-name, batchname`_

The resulting CSV will look something like this:

| name   | surname   | age | batch   |
| ------ | --------- | --- | ------- |
| Thomas | Haverford | 28  | admins  |
| Leslie | Knope     | 32  | admins  |
| Ronald | Swanson   | 48  | players |

On upload, if the batch exists, Ango Hub will assign the row/asset to that batch. If it does not, Hub will create it and assign the row/asset to it.

If you do not wish to use the default names for the batch column, you may specify the name of an already existing column, of any name, in the configuration JSON you pass to the plugin when you run it. More information on using the configuration JSON in the [section below](markdown-generator.md#using-the-markdown-plugin).

### Assigning External IDs to Assets

When running the plugin, you may select a column to be the provider of external IDs for each asset. For example, if you select the column "id" for the following table:

<table><thead><tr><th width="77">id</th><th>name</th><th>surname</th><th width="148">age</th></tr></thead><tbody><tr><td>1</td><td>Thomas</td><td>Haverford</td><td>28</td></tr><tr><td>2</td><td>Leslie</td><td>Knope</td><td>32</td></tr><tr><td>3</td><td>Ronald</td><td>Swanson</td><td>48</td></tr></tbody></table>

The assets created with this table will have, as external ID, "1", "2", and "3".

More on selecting an external ID column in the [following section](markdown-generator.md#using-the-markdown-plugin).

## Using the Markdown Plugin

From the Plugin Directory, search for _Markdown Plugin_ and install the plugin to your organization. More information on installing plugins can be found in the [Installing Plugins](../installing-plugins.md) page.

### Files Necessary

As shown in the example above:

* A comma-separated CSV
* A Markdown file with placeholders immediately surrounded by pipes (e.g. "|name|") equal to the title of the CSV column from which the data needs to be pulled

{% hint style="info" %}
Ensure the CSV you are using is comma-separated.

By default, Excel and Numbers export CSVs with columns separated by semicolons. You will need to replace semicolons with commas.
{% endhint %}

### Usage

Navigate to the project where you'd like to create the assets.

Enter the _Settings_ tab, then the _Plugins_ section.

Find the _Markdown Plugin_, and click on _Open._ A dialog will appear:

<figure><img src="../../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

Click on _Upload CSV_ to open your OS file picker and select the CSV file. Then, click on _Open Editor_ and paste your Markdown. You will be able to see a preview of the Markdown on the right side of the screen:

<figure><img src="../../.gitbook/assets/image (474).png" alt=""><figcaption></figcaption></figure>

Click on _Set Text_ to save the Markdown.

In the Config JSON area, you can tweak three settings. By default, they are:

```json
{
  "batch_name_column": "AUTO_DETECT",
  "external_id_columns": [],
  "upload_batch_size": 100
}
```

* `batch_name_column`: Input here the title of the column you wish to use to assign assets to batches, as explained [in this section](markdown-generator.md#assigning-rows-assets-to-batches-on-upload). Leaving it on `"AUTO_DETECT"` will make it so that _`batch, batch_name, batch-name, batchname`_ will be used to detect batch columns.
  * Example: `"batch_name_column": "my_batch"`
* `external_id_columns`: Specify here the column(s) to be used as external IDs. If you specify more than one column, the resulting external ID for each asset will be `FIRSTCOLUMNID_SECONDCOLUMN` and so forth, separated with an underscore.
  * Example: `"external_id_columns": ['id', 'phone']`
* `upload_batch_size`: The MD plugin processes lines and creates/imports MD files in batches. You may select here how many assets will be processed at one time. The default, 100, should be sufficient and ideal for most scenarios.

Click on _Run._ The assets will be added to your project.

You may check the progress of the conversion from the _Plugin Sessions_ dialog. More information on checking plugin progress [here](../monitoring-plugin-progress.md).

{% hint style="info" %}
If the assets do not appear, it might be because you have reached your organization's asset limit. Make sure to check the _Usage_ tab of your [Organization page](https://hub.ango.ai/organization).
{% endhint %}

{% hint style="info" %}
Depending on the number and size of the assets, it may take a long time for the assets to appear in your project. You may check the progress from the [_Plugin Sessions_](../monitoring-plugin-progress.md) dialog.
{% endhint %}
