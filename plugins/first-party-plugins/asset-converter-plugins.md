# Asset Converter Plugins

The Asset Converter plugins allow you to convert a folder of files present in a private bucket [you integrated with Ango Hub](../../data/importing-assets/importing-private-cloud-assets-aws.md) from one format to another, and to import the resulting converted assets to a project of your choice.

Usually, such plugins convert files from a format that is not supported by Ango Hub to one that is.

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Appearance of one of the plugins.</p></figcaption></figure>

## Plugin Functionality

Adding the plugin to your organization will allow you to convert files present in a private bucket [you integrated with Ango Hub](../../data/importing-assets/importing-private-cloud-assets-aws.md) from one format to another, and to import the resulting converted assets to a project of your choice.

Currently, we offer the following conversions through plugins:

* NIFTI --> NRRD

After being run, the plugin will:

1. Get the files in the folder you have selected
2. Create a new folder in the folder you have selected, with the new folder name being equal to the name of the format to convert to (e.g. '`nrrd`')
3. Convert them to the format you have selected
4. Upload the converted files to the folder created in Step 2
5. Import the converted files to the project where the plugin is being run.

### NIFTI to NRRD

This plugin accepts the following file extensions as input:

```
.nii
.nii.gz
```

It will convert assets with the above extensions to a file in the NRRD format ending with `.nrrd`.

## Using the Export Converter Plugins

From the Plugin Directory, search for the the name of the converter plugin of your choice and install the plugin to your organization. More information on installing plugins can be found in the [Installing Plugins](../installing-plugins.md) page.

Currently, the names of our Asset Converter plugins are the following:

* \[NIFTI] to \[NRRD] Converter

### Usage

First, ensure you have created an integration between Ango Hub and the private assets where the files you wish to convert and import are being stored. [More information on how to do so can be found here](../../data/importing-assets/importing-private-cloud-assets-aws.md).

Then, navigate to the project where you'd like to import the converted assets.

Enter the _Settings_ tab, then the _Plugins_ section.

Find the converter plugin of your choice, and click on _Open._ A dialog will appear:

<figure><img src="../../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Ensure the dot before the plugin's name is green. The dot indicates the plugin's status, where green signifies the plugin's code is running, and red signifies the plugin's code is not running.

You will not be able to run plugins the code of which isn't running.
{% endhint %}

**Integration**: From this dropdown, select the integration you have created between Ango Hub and the private bucket where the files you wish to convert are stored.

**Bucket Name**: The name of the private bucket where you assets are stored.

**Folder**: After clicking on _Select Folder_, a dialog will open. From this dialog, you will be able to select the folder where the assets you wish to convert are stored.

{% hint style="info" %}
The plugin will attempt to convert all files in the folder. Currently, there is no way to select individual files.
{% endhint %}

**Config JSON**: Leave this field blank.

Once you click on _Run_, the plugin will start converting the plugins. It will then import them to your project.

You may check the progress of the conversion from the _Plugin Sessions_ dialog. More information on checking plugin progress [here](../monitoring-plugin-progress.md).

{% hint style="info" %}
Because the plugin first converts all assets, and only then imports them to Ango Hub, depending on the number and size of the assets, it may take a long time for the assets to appear in your project.
{% endhint %}
