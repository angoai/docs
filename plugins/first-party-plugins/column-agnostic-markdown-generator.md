# Column-Agnostic Markdown Generator

The Column-Agnostic Markdown Generator is a plugin made, published, and officially supported by Ango AI that allows you to create Markdown assets from a CSV table.

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

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

After feeding the CSV file to the plugin, it will create three assets in the selected project (one for each row of the CSV), each looking like the following:

![](<../../.gitbook/assets/image (457).png>)

A number of parameters, such as text height, whether to have more than one column, and more, can be tweaked when running the plugin from the Config JSON. More on Config JSON for this plugin in the [section on configuring plugin settings](column-agnostic-markdown-generator.md#using-the-column-agnostic-markdown-generator).

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

If you do not wish to use the default names for the batch column, you may specify the name of an already existing column, of any name, in the configuration JSON you pass to the plugin when you run it. More information on using the configuration JSON in the [section on configuring plugin settings](column-agnostic-markdown-generator.md#using-the-column-agnostic-markdown-generator).

### Assigning External IDs to Assets

When running the plugin, you may select a column to be the provider of external IDs for each asset. For example, if you select the column "id" for the following table:

<table><thead><tr><th width="77">id</th><th>name</th><th>surname</th><th width="148">age</th></tr></thead><tbody><tr><td>1</td><td>Thomas</td><td>Haverford</td><td>28</td></tr><tr><td>2</td><td>Leslie</td><td>Knope</td><td>32</td></tr><tr><td>3</td><td>Ronald</td><td>Swanson</td><td>48</td></tr></tbody></table>

The assets created with this table will have, as external ID, "1", "2", and "3".

More on selecting an external ID column in the [section on configuring plugin settings](column-agnostic-markdown-generator.md#using-the-column-agnostic-markdown-generator).

### Pre-Labeling Text Classifications

When running the plugin, you may select a column to be the source for pre-labels for a [text classification tool](../../labeling/labeling-tools/classification-tools/text.md) you have previously added to your project.

For each row, Ango Hub will take the content of the column you've chosen, and use it to prelabel the asset, in a text classification tool of your choice.

More on how to select the column for pre-labeling in the [section on configuring plugin settings](column-agnostic-markdown-generator.md#using-the-column-agnostic-markdown-generator).

### Two-Column Mode

By default, the plugin will create a Markdown table with a row for each column of your CSV, all in the same column:

<figure><img src="../../.gitbook/assets/image (457).png" alt=""><figcaption></figcaption></figure>

If you have a large number of CSV columns, this may cause the asset to be taller than the screen, requiring annotators to scroll down and potentially increase labeling time.

If, in the plugin configuration, you set the `two_columns` property to `true`, the rows will be spread, by default, 50/50 across two columns.

{% hint style="info" %}
For example, if your CSV table has 10 columns, normally, each asset would have a single column with 10 rows. When enabling `two_columns`, the plugin will instead create two columns, each with 5 rows.
{% endhint %}

By changing the value in `two_columns_ratio`, between 0 and 1, you may change how many rows will be shown in the first column as opposed to the second.

{% hint style="info" %}
For example, if you have an asset that would normally be 10 rows long, by enabling `two_columns` and setting `two_columns_ratio` to `0.7`, the plugin will place 70% of the rows in the first column (7) and the remainder (3) in the second.
{% endhint %}

More on configuring plugins in the [section on configuring plugin settings](column-agnostic-markdown-generator.md#using-the-column-agnostic-markdown-generator).

### Paired Columns (Comparison Mode)

If you have data you'd like to place in two different columns in the final asset, for example for comparison purposes, the plugin offers a _Paired Columns_ mode.

Format your .csv to have column names starting with two different prefixes of your choice. In our example, we will use "`to`" and "`from`", but they can be anything you want. The final asset shown on Hub will have three columns:

1. The name of the CSV column
2. The respective data in the `to` field
3. The respective data in the `from` field

For example, imagine you have the following comma-separated CSV:

| to\_name   | to\_surname | from\_name | from\_surname |
| ---------- | ----------- | ---------- | ------------- |
| Mario      | Rossi       | Maria      | Rossa         |
| Matteo     | Bianchi     | Mattia     | Bianca        |
| Alessandro | Verdi       | Alessandra | Verde         |

If, in the Config JSON, you set the `paired_columns` parameter to `true` and the `paired_prefixes` parameter to `["to", "from"]`, the final asset will look like this (asset from the first row):

<figure><img src="../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
There must be an underscore between the column prefix and the column name itself, as shown in the example CSV.
{% endhint %}

{% hint style="warning" %}
All columns starting with the same prefix need to be grouped together.

For example, providing a CSV with the following columns, in this order will cause the plugin to not work:

`to_name, from_name, to_surname, from_surname`

Instead, they can be:

`to_name, to_surname, from_name, from_surname`

or:

`from_name, from_surname, to_name, to_surname.`

The order of the columns in the final asset will be determined by the order of the column prefixes in your CSV.
{% endhint %}

{% hint style="warning" %}
You must provide a CSV column for each of the two prefixes you provide.

For example, if you provide a `to_name`, you must provide a `from_name` column. Failure to do so will result in the plugin not working.
{% endhint %}

{% hint style="warning" %}
The two column groups, in your CSV, need to be ordered the same way.

For example, this will not work:

`to_name, to_surname, from_surname, from_name`

because in the `from` columns, the order of name and surname was swapped.

Both prefix groups columns need to be ordered identically, or the plugin will not work.
{% endhint %}

## Using the Column-Agnostic Markdown Generator

From the Plugin Directory, search for _Column-Agnostic Markdown Generator_ and install the plugin to your organization. More information on installing plugins can be found in the [Installing Plugins](../installing-plugins.md) page.

### Files Necessary

As shown in the example above:

* A comma-separated CSV

{% hint style="warning" %}
Ensure the CSV you are using is comma-separated.

By default, Excel and Numbers export CSVs with columns separated by semicolons. You will need to replace semicolons with commas.
{% endhint %}

### Usage

Navigate to the project where you'd like to create the assets.

Enter the _Settings_ tab, then the _Plugins_ section.

Find the _Column-Agnostic Markdown Generator_, and click on _Open._ A dialog will appear:

<figure><img src="../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

Click on _Upload CSV_ to open your OS file picker and select the CSV file.

In the Config JSON area, you can tweak a number of settings. By default, they are:

```json
{
  "batch_name_column": "AUTO_DETECT",
  "external_id_columns": [],
  "upload_batch_size": 100,
  "title_spacing": 15,
  "iframe_columns": [],
  "ignore_columns": [],
  "prelabel_columns": [],
  "prelabel_schema_ids": [],
  "two_columns": false,
  "two_columns_ratio": 0.5,
  "paired_columns": false,
  "paired_prefixes": []
}
```

* `batch_name_column`: Input here the title of the column you wish to use to assign assets to batches, as explained [in this section](column-agnostic-markdown-generator.md#assigning-rows-assets-to-batches-on-upload). Leaving it on `"AUTO_DETECT"` will make it so that _`batch, batch_name, batch-name, batchname`_ will be used to detect batch columns.
  * Example: `"batch_name_column": "my_batch"`
* `external_id_columns`: Specify here the column(s) to be used as external IDs. If you specify more than one column, the resulting external ID for each asset will be `FIRSTCOLUMNID_SECONDCOLUMN` and so forth, separated with an underscore.
  * Example: `"external_id_columns": ["id", "phone"]`
* `upload_batch_size`: The MD plugin processes lines and creates/imports MD files in batches. You may select here how many assets will be processed at one time. The default, 100, should be sufficient and ideal for most scenarios.
* `title_spacing`: The space, in pixels, between titles (e.g., lines starting with a `#`sign in Markdown) and the following line.
* `iframe_columns`: If any columns of your CSV contain iframes, specify them here.
  * Example: `"iframe_columns": ["id", "phone"]`
* `ignore_columns`: Any columns you specify here will not be inserted in the markdown assets.
  * Example: `"ignore_columns": ["id", "phone"]`
* `prelabel_columns`: You may use the content of a column to pre-label a [text labeling tool](../../labeling/labeling-tools/classification-tools/text.md), as mentioned in [this section](column-agnostic-markdown-generator.md#pre-labeling-text-classifications). Specify here the columns to use for pre-labeling. One column for one Text tool.
  * Example: `"prelabel_columns": ["id", "phone"]`
* `prelabel_schema_ids`: For the columns you have specified in the parameter above, select the schema IDs of the Text labeling tools you'd like to wish to prepopulate with the data in the column(s). In our example, the content of the column "`id`" will be inserted in the text tool with schema ID `1d17c9480973a1c8e0f6708`.
  * Example: `"prelabel_schema_ids": ["1d17c9480973a1c8e0f6708", "ab2af7ff5d1de45fd964377"]`
* `two_columns`: Whether the final Markdown asset should have two columns or only one.
* `two_columns_ratio`: Whether the columns should have equal height or not.
  * For example, assume that each row of your CSV has 20 columns. This will result in 20 fields (rows) being added to your Markdown file. If you have selected `two_columns: true` and 0.5 here, each column will show 10 rows. If you select 0.7, 70% of the rows will be in the first column, and 30% in the second.
* `paired_columns`: Toggle this to `true` if you wish to use the _Paired Columns_ mode explained in [its own section](column-agnostic-markdown-generator.md#paired-columns-comparison-mode).
* `paired_prefixes`: Pass here the prefixes you used in your CSV for _Paired Columns_ mode, without the trailing underscore.
  * Example: `paired_prefixes: ["to", "from"]`

Click on _Run._ The assets will be added to your project.

You may check the progress of the conversion from the _Plugin Sessions_ dialog. More information on checking plugin progress [here](../monitoring-plugin-progress.md).

{% hint style="info" %}
If the assets do not appear, it might be because you have reached your organization's asset limit. Make sure to check the _Usage_ tab of your [Organization page](https://hub.ango.ai/organization).
{% endhint %}

{% hint style="info" %}
Depending on the number and size of the assets, it may take a long time for the assets to appear in your project. You may check the progress from the [_Plugin Sessions_](../monitoring-plugin-progress.md) dialog.
{% endhint %}
