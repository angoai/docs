---
description: Extend the functionality of Ango Hub with custom plugins.
---

# Plugin Developer Documentation

Custom plugins allow you to extend what Ango Hub can do. With custom plugins you can automatically convert outputs, integrate your own models, and more.

This page will cover general information about creating plugins. Visit each plugin's page for more on how to create and run each plugin type.

## Types of Custom Plugins Available

* ****[**Export**](export-plugins.md). Create a script to automatically convert Ango Hub's export to the format of your choice.
* ****[**Model**](batch-model-plugins.md). Integrate your ML model into Ango Hub, pass in assets and pre-label with its results.
* ****[**File Explorer**](file-explorer-plugins.md). Link your cloud storage of choice to Ango Hub and navigate its file structure directly within Hub itself. Then, bulk import assets from a folder with a single click.
* ****[**Markdown Generator**](markdown-generator-plugins.md)**.** Get a Markdown and a .csv file. Process them with a Python script, and upload the results to Hub as a markdown asset.

## Creating a New Plugin

From Hub, click on _Plugins_ on the top navbar, then enter the _Development_ section and click on _Create a Plugin_.

<figure><img src="../../.gitbook/assets/image (348).png" alt=""><figcaption></figcaption></figure>

A dialog will appear:

<figure><img src="../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

* **Name**. The name of your plugin.
* **Description**. A description for your plugin.
* **Banner URL**: A link to a square image which will be used to represent your plugin. Leave blank for default.
* **Type**: The type of your plugin. See [the section above](./#types-of-custom-plugins-available) for the types available.
* **Class Names** (only appears if selecting "Model" as the plugin type.) Add your model's class names, which will then be mapped to Ango Hub category names when being run. More on the page for [Model Plugins](batch-model-plugins.md).
* **Public**: Makes this plugin accessible to the Plugin Directory.
* **Status**: Lists the plugin on the [Directory](../installing-plugins.md). If the plugin is not public, it will be listed for the current organization. If public, it will be listed on the Directory for all Ango Hub users.
* **Default Config**: When running a plugin, users will have the option to input custom JSON in this field. The JSON will be passed to your callback function with other parameters. Here, you can input JSON that will be shown and pre-filled by default to users running the plugin. This is a good way to show users a sample of what you expect from the custom JSON config from users.

Click on _OK_ to create the plugin and add it to your _Development_ list.

## Plugin Info

Once you create a plugin, it will be visible in the _Development_ section of the _Plugins_ page.

<figure><img src="../../.gitbook/assets/image (312).png" alt=""><figcaption></figcaption></figure>

<img src="../../.gitbook/assets/image (385).png" alt="" data-size="line">/<img src="../../.gitbook/assets/image (307).png" alt="" data-size="line">: Whether the plugin has been added to the Directory.

<img src="../../.gitbook/assets/image (338).png" alt="" data-size="line">: Appears when the plugin has been made public.

**ID:** The plugin's unique ID.

**Secret**: The Plugin Secret is what, when necessary, you will use to authenticate with Ango Hub's servers to run your custom script. More information below. Treat this secret as a password and do not share it with anyone else.

**Live**: When your plugin is running, this change will instantly turn green. When you stop execution of your plugin, the light will turn back to red in a couple of minutes.

**Type**: The type of plugin, as mentioned in [this section](./#types-of-custom-plugins-available).



To run the plugin, click on _Open_ and follow the on-screen instructions.

As mentioned above, each plugin type has a different way of being set and run. Please check each plugin's page for more:

## [Export Plugins](export-plugins.md)

## [File Explorer Plugins](file-explorer-plugins.md)

## [Model Plugins](batch-model-plugins.md)

## [Markdown Generator Plugins](markdown-generator-plugins.md)
