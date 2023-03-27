# TPT Export

The TPT Export plugin allows you to download a .csv file with key annotation performance metrics for a project of your choice.

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

## Plugin Functionality

Adding the plugin to your organization will allow you to download a CSV spreadsheet containing the following data for each asset:

* Asset URL
* Asset ID
* Label Duration
* Review Duration
* Number of Annotations

## Using the Plugin

From the Plugin Directory, search for the the name of the plugin and install the plugin to your organization. More information on installing plugins can be found in the [Installing Plugins](../installing-plugins.md) page.

The name of our TPT plugin is `TPT Export Plugin`

### Usage

Navigate to the project where you'd like to get the data.

Enter the _Settings_ tab, then the _Plugins_ section.

Find the plugin, and click on _Open._ A dialog will appear:

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Ensure the dot before the plugin's name is green. The dot indicates the plugin's status, where green signifies the plugin's code is running, and red signifies the plugin's code is not running.

You will not be able to run plugins the code of which isn't running.
{% endhint %}

If you wish to receive an email when the export is complete, toggle _Send Email_ on.

Click on _Run_ to receive your data. You'll get a notification when it's ready. Clicking on the notification will start the download of your data.

You may check the progress of the conversion from the _Plugin Sessions_ dialog. More information on checking plugin progress [here](../monitoring-plugin-progress.md).
