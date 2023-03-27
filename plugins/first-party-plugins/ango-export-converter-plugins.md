# Ango Export Converter Plugins

The Ango Export Converter plugins are made, published, and officially supported by Ango AI, allowing you to download your annotations in formats not supported within Ango Hub's core functionality.

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

## Plugin Functionality

Adding the plugin to your organization will allow you to download your annotations in a format other than the [Ango Export Format](../../data/ango-export-format/).

Currently, we offer the following additional export formats through plugins:

* KITTI
* YOLO
* COCO
* NIFTI (In alpha stage, not publicly available yet)

{% hint style="warning" %}
The only way to ensure you get all of the data created with Ango Hub is to download your export in the original [Ango Export Format](../../data/ango-export-format/) (JSON).

As other export formats were created by third parties and with different use cases in mind, they may not contain all data created within Ango Hub.

For example, the COCO and YOLO formats only support certain labeling tools, and only on images. Thus, non-image assets will not be exported, and data points created with labeling tools unsupported by YOLO/COCO will also not be exported.
{% endhint %}

## Using the Export Converter Plugins

From the Plugin Directory, search for the the name of the converter plugin of your choice and install the plugin to your organization. More information on installing plugins can be found in the [Installing Plugins](../installing-plugins.md) page.

Currently, the names of our Export Converter plugins are the following:

* \[Ango] to \[KITTI] Converter
* \[Ango] to \[YOLO] Converter
* \[Ango] to \[COCO] Converter
* NIFTI Export (In alpha stage, not publicly available yet)

### Usage

Navigate to the project where you'd like to get the export.

Enter the _Settings_ tab, then the _Plugins_ section.

Find the converter plugin of your choice, and click on _Open._ A dialog will appear:

<figure><img src="../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Ensure the dot before the plugin's name is green. The dot indicates the plugin's status, where green signifies the plugin's code is running, and red signifies the plugin's code is not running.

You will not be able to run plugins the code of which isn't running.
{% endhint %}

If you wish to receive an email when the export is complete, toggle _Send Email_ on.

You may vary a number of settings related to your export from the _Config JSON_ field. Each option is detailed below:

#### Plugin Configuration

* `export_review_assets`: set this to `true` to get the export of labeling tasks that have been reviewed.
* `export_labeled_assets`: set this to `true` to get the export of labeling tasks that have been labeled. (e.g., by turning this off, you can choose to only get the export for tasks that have been reviewed, or by doing the opposite, only of tasks that have not.)
* `batch_names`: enter a list of batch names here to only export assets belonging to the specified assets.
  * Example: `"batch_names": ["my_batch_1", "my_batch_2"]`
* `verbose`: set this to true to turn on logging for the plugin. [See here](../monitoring-plugin-progress.md) for more on how to see plugin logs.
* `verbose_frequency`: the interval at which a log message will be sent.
  * For example, if you set this to 10, you will get a log message every time 10 assets are processed.

Click on _Run_ to receive your export. You'll get a notification when it's ready. Clicking on the notification will start the download of your export.

#### NIFTI Export (In alpha stage, not publicly available yet)

You can get your export as a NIFTI only for .nrrd assets annotated in the [NRRD Labeling Editor](../../labeling/labeling-editor-interface/new-medical-labeling-editor.md).

The NRRD file will be served to you as a link in the `medicalBrushDataNIFTIUrl`property of each asset in the JSON export.
