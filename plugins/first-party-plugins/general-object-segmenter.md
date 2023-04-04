# General Object Segmenter

The General Object Segmenter plugin allows you to detect a variety of objects on all image files in your project.

The plugin will either draw a bounding box, a polygon, or a segmentation around each object type you specify, using a labeling tool of your choice.

## Plugin Functionality

Adding the plugin to your organization will allow you, with one click, to detect a variety of objects on all image (.jpg, .png) assets in the project of your choice. The plugin will either draw a bounding box, a polygon, or a segmentation around each object belonging to the categories you've selected.

{% hint style="info" %}
The plugin will run object detection on all image assets in your project.

Currently, there is no way to only select specific assets as targets for the object detection.
{% endhint %}

Currently, the following object classes can be automatically detected:

**Traffic**

| person        | bicycle      | car       |
| ------------- | ------------ | --------- |
| motorcycle    | airplane     | bus       |
| truck         | train        | boat      |
| traffic light | fire hydrant | stop sign |
| parking meter | bench        |           |

**Animals**

| zebra | elephant | bird    |
| ----- | -------- | ------- |
| cat   | dog      | horse   |
| sheep | cow      | giraffe |

**Clothes/Accessories**

| backpack | umbrella | handbag |
| -------- | -------- | ------- |
| tie      | suitcase |         |

**Sports**

| frisbee        | skis       | snowboard    |
| -------------- | ---------- | ------------ |
| sports ball    | kite       | baseball bat |
| baseball glove | skateboard | surfboard    |
| tennis racket  |            |              |

**Kitchen**

| wine glass | cup   | fork |
| ---------- | ----- | ---- |
| knife      | spoon | bowl |

**Food**

| banana  | apple    | sandwich |
| ------- | -------- | -------- |
| orange  | broccoli | carrot   |
| hot dog | pizza    | donut    |
| cake    |          |          |

**Home**

| chair      | couch        | potted plant |
| ---------- | ------------ | ------------ |
| bed        | dining table | toilet       |
| tv         | microwave    | oven         |
| toaster    | sink         | refrigerator |
| book       | clock        | vase         |
| scissors   | teddy bear   | hair drier   |
| toothbrush |              |              |

**Electronics**

| laptop   | mouse      | remote |
| -------- | ---------- | ------ |
| keyboard | cell phone |        |

## Using the General Object Segmenter Plugin

From the Plugin Directory, search for _General Object Detector_ and install the plugin to your organization. More information on installing plugins can be found in the [Installing Plugins](../installing-plugins.md) page.

The name of the plugin is `General Object Segmenter`.

### Usage

First, ensure you have created at least one [Bounding Box](../../labeling/labeling-tools/bounding-box.md), [Polygon](../../labeling/labeling-tools/polygon.md), or [Segmentation](../../labeling/labeling-tools/segmentation.md) tool in your project for each of the object classes you wish to detect.

Then, navigate to the project where you'd like to perform the object detection task.

Enter the _Settings_ tab, then the _Plugins_ section.

Find the plugin, and click on _Open._ A dialog will appear:

<figure><img src="../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Ensure the dot before the plugin's name is green. The dot indicates the plugin's status, where green signifies the plugin's code is running, and red signifies the plugin's code is not running.

You will not be able to run plugins the code of which isn't running.
{% endhint %}

In the _Class Mapping_ field, do the following:

1. Open the left dropdown, and pick from one of the 80 classes the plugin can detect.
2. Open the right dropdown, and pick from one of the Bounding Box, Segmentation, or Polygon tools you have created in your project.
3. Click on the "plus" button to finalize the pairing. Now the object class and your tool are linked. The plugin will use the selected tool to label the selected category.
4. Starting again from Step 1, link as many tools to categories as needed.

Click on _Run_. The plugin will start detecting the selected object classes in all images in your project.

You may check the progress of the conversion from the _Plugin Sessions_ dialog. More information on checking plugin progress [here](../monitoring-plugin-progress.md).

{% hint style="info" %}
Because the plugin first performs detection on all assets, and only then imports the tokens to Ango Hub, depending on the number and size of the assets, it may take a long time for the prelabels to appear in your project.
{% endhint %}
