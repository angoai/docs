# Optical Character Recognition

The OCR plugin allows you to run OCR on all image files in your project.

The plugin will draw a bounding box around each OCR token, and add the recognized token text in the metadata of each box.

<figure><img src="../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

## Plugin Functionality

Adding the plugin to your organization will allow you, with one click, to run OCR on all image (.jpg, .png) assets in the project of your choice. The plugin will draw a box around each OCR token, and add the recognized text in the metadata of each box.

{% hint style="info" %}
The OCR plugin will run OCR on all image assets in your project.

Currently, there is no way to only select specific assets as targets for the OCR.
{% endhint %}

## Using the OCR Plugin

From the Plugin Directory, search for the the name of the converter plugin of your choice and install the plugin to your organization. More information on installing plugins can be found in the [Installing Plugins](../installing-plugins.md) page.

The name of the OCR plugin is `Optical Character Recognition`.

### Usage

First, navigate to the project where you'd like to perform the OCR task.

Enter the _Settings_ tab, then the _Plugins_ section.

Find the OCR plugin, and click on _Open._ A dialog will appear:

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Ensure the dot before the plugin's name is green. The dot indicates the plugin's status, where green signifies the plugin's code is running, and red signifies the plugin's code is not running.

You will not be able to run plugins the code of which isn't running.
{% endhint %}

Leave everything empty and click on _Run_. The plugin will start performing OCR on all image assets in the selected project.

You may check the progress of the conversion from the _Plugin Sessions_ dialog. More information on checking plugin progress [here](../monitoring-plugin-progress.md).

{% hint style="info" %}
Because the plugin first performs OCR on all assets, and only then imports the tokens to Ango Hub, depending on the number and size of the assets, it may take a long time for the prelabels to appear in your project.
{% endhint %}
