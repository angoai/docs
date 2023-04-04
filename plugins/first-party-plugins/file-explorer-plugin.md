# File Explorer Plugin

The File Explorer Plugin is a plugin made, published, and officially supported by Ango AI that allows you to browse a folder in your AWS S3 bucket and quickly import it into Ango Hub.

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

## Plugin Functionality

The plugin hooks into your AWS S3 private buckets and allows you to bulk import a folder of your choice in the bucket. Optionally, you can assign all assets imported this way to one or more specific batches, it has duplicate prevention, and more.

## Using the File Explorer Plugin

From the Plugin Directory, search for _File Explorer Plugin_ and install the plugin to your organization. More information on installing plugins can be found in the [Installing Plugins](../installing-plugins.md) page.

### Usage

First, ensure you have created an integration between Ango Hub and the private assets where the files you wish to import are being stored. [More information on how to do so can be found here](../../data/importing-assets/importing-private-cloud-assets-aws.md).

Then, navigate to the project where you'd like to import the assets.

Enter the _Settings_ tab, then the _Plugins_ section.

Find the _File Explorer Plugin_ and click on _Open._ A dialog will appear:

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

From the _Integration_ dropdown, pick the integration to the bucket from which you wish to import the assets.

In the _Bucket Name_ area, type in the full name of the bucket you are connecting to. For example, `acme-private-assets`.

Then, click on _Select Folder_. A dialog will pop up, from which you will be able to pick a folder, from within your bucket, to import. Navigate to the folder you'd like to import and press _Select Current Folder._

In _Batch_, you may pick one or more batches to which assets imported in this session will be assigned to.

In the Config JSON area, you can tweak five settings. By default, they are:

```json
{
  "upload_subfolders": false,
  "prevent_duplicates": false,
  "assign_folder_names_as_batch_name": false,
  "accepted_extensions": [],
  "ignored_extensions": []
}
```

* `upload_subfolders`: Enabling this will cause the plugin to import all files, recursively, including those in subfolders.
  * Example: `"upload_subfolders": true`
* `prevent_duplicates`: Enabling this will prevent the plugin from importing an asset, if an asset with the same name already exists in the project.
* `assign_folder_names_as_batch_name`: Enabling this will assign each asset a batch depending on where it was located. For example, if the asset was located in the `plugin-import/nifti` folder, that will be its batch name. You don't need to create the batches in advance -- the plugin will create them for you.
* `accepted_extensions`: Whitelist here the extensions of the files you wish to import. For example, adding ".jpg" or "jpg" will import only files ending with the ".jpg" extension.
* `ignored_extension` works similarly, except it's a file extension blacklist.

Click on _Run._ The assets will be added to your project.

You may check the progress of the conversion from the _Plugin Sessions_ dialog. More information on checking plugin progress [here](../monitoring-plugin-progress.md).

{% hint style="info" %}
If the assets do not appear, it might be because you have reached your organization's asset limit. Make sure to check the _Usage_ tab of your [Organization page](https://hub.ango.ai/organization).
{% endhint %}

{% hint style="info" %}
Depending on the number and size of the assets, it may take a long time for the assets to appear in your project. You may check the progress from the [_Plugin Sessions_](../monitoring-plugin-progress.md) dialog.
{% endhint %}
