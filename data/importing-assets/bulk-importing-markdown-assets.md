# Bulk Importing Markdown Assets

Ango Hub supports importing Markdown files in bulk using a single JSON file.

## Preparing the JSON

Your JSON file will need to be in the following format:

```json
[
    {
        "externalId":"my_external_id_1",
        "data":"<div style='font-size:13px;font-weight:500;display:flex;'><div style='width:100px;color:gray'>Serial No</div>: 1</div>"
    },
    {
        "externalId":"my_external_id_2",
        "data":"<div style='font-size:13px;font-weight:500;display:flex;'><div style='width:100px;color:gray'>Serial No</div>: 1</div>"
    }
]
```

Your JSON will be a list of objects. Each object will be a single asset in Ango Hub, and will need to contain an `externalId` property and a `data` property. The `externalId` will be used by Ango Hub to identify your asset. The `data` is the Markdown content itself.

{% hint style="warning" %}
You will need to flatten your markdown to fit a single line, and to convert all double quotes contained within the markdown (") to single quotes (').

Failure to do so will result in the Markdown files not being imported correctly or at all.
{% endhint %}

{% hint style="info" %}
We strongly recommend you ensure `externalID`s are unique, or you may not be able to distinguish between some assets when exporting them, or when using [pre-labels](../importing-and-exporting-annotations/importing-annotations/).

External IDs are one of the two ways used to identify [assets](../../core-concepts/assets.md) on Ango Hub, together with the asset's file path. However, markdowns uploaded this way (embedded) have no file path.

Embedded markdowns are being directly uploaded and stored into Ango Hub's database as strings, where the file path would normally be.

This means that the only way to distinguish between embedded Markdowns is either through their `data` content, or by their `externalId`s. As such, if you upload two embedded markdowns with the same content and the same external ID, you will not be able to distinguish between them when obtaining the export.

You will still be able to distinguish between different labeling [tasks](../../core-concepts/tasks.md), as Ango Hub assigns a unique ID to each task.

Ango Hub will not warn you if you upload more than one asset with the same `externalId`and will continue to work as usual.
{% endhint %}

## Uploading the JSON

### From the UI

From your project's dashboard, enter the _Assets_ tab (1), then click on the _Add Data_ button (2). A dialog will appear. Enter the _Upload Data URL_ tab (3) and drag and drop your JSON in the upload box (4).

<figure><img src="../../.gitbook/assets/image (358).png" alt=""><figcaption></figcaption></figure>

Click on _Upload_ to upload your markdown assets.

### From the SDK

Using the [`upload_files_cloud`](../../sdk/sdk-documentation.md#upload\_files\_cloud-project\_id-assets-integrationid-batches)`()`function, you may upload bulk Markdowns like so:

```python
direct_json = [
   {
      "externalId": "1",
      "data": "<MARKDOWN CONTENTS HERE>"
   },
   {
      "externalId": "2",
      "data": "<MARKDOWN CONTENTS HERE>"
   }
]

res = ango_sdk.upload_files_cloud(
   project_id='<YOUR_PROJECT_ID>',
   assets=direct_json
)
```
