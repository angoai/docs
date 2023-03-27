---
description: Overview of the Segmentation labeling tool in Ango Hub
---

# Segmentation

Here is a complete video tutorial with everything you need to know abut segmentation on Ango Hub:

{% embed url="https://youtu.be/zGE5dnfyrBA" %}

The Segmentation labeling tool allows you to segment an image, and provides you with useful utilities to make sure no pixel is left out of your segmentation.

![](<../../.gitbook/assets/image (125).png>)

## How to add a Segmentation tool to your project <a href="#how-to-add-a-bounding-box-tool-to-your-project" id="how-to-add-a-bounding-box-tool-to-your-project"></a>

From the project’s _Settings_ tab, enter the _Label Set_ section.

Click on _Add Category_. From the list that appears, click on _Segmentation_.

A new row will appear named _Segmentation_. Click on it to expand it.

![](<../../.gitbook/assets/Screen Shot 2022-05-10 at 15.32.01.png>)

Give your segmentation tool a title and description.

Enable the _Required_ toggle if you want to force labelers to create a segmentation for each asset. When the toggle is disabled, labelers will be able to save and move to the next asset without creating the segmentation.

If you would like to ask labelers further questions, for example, if you want to show a further _radio_ after drawing the segmentation, click on _Add Classification_ and add a further question. [More on nested questions here](nested-classifications.md).

## How to Segment Images <a href="#how-to-draw-a-bounding-box" id="how-to-draw-a-bounding-box"></a>

### Creating a Segmentation Instance

Click on the image where you’d like the segmentation to start. Keep the left mouse button (LMB) pressed to draw your segmentation. Release the LMB and press it again to create a straight line.

When you are done with your segmentation, press N to finalize it. If you wish to create more segmentations in the same instance, click the LMB on the image to repeat the process. When you are done with the current instance, press Escape on your keyboard.

{% hint style="info" %}
**What's an Instance?**

Segmentations created within the same instance will be shown as a group in the export.

In short, every time you click on a Segmentation tool, you are starting a new instance. When you exit the tool (e.g. by selecting another tool, deselecting the tool, or pressing Esc), you are closing the current instance.
{% endhint %}

### Cutting Out From / Creating a Hole in a Segmentation Instance

After you've opened a new instance and you have created as least one segmentation, click on the Scissors button to switch to the Scissors tool.

![](<../../.gitbook/assets/Screen Shot 2022-05-10 at 15.41.25.png>)

The Scissors tool is the opposite of the Segmentation tool, in that it creates holes and removes segmentations.

To create a hole in an existing segmentation instance, even after having closed it by pressing Escape, click with the LMB on an existing instance and press on the Scissors tool. You'll be able to create holes in the instance.

### Adding to a Segmentation Instance

To add more pixels to an existing instance, when no tools are selected, click on an existing instance on the image. You will be entering "edit mode" for the currently-selected instance.

Draw on the image on the pixels you'd like to add to the current instance.

### Overwrite Segmentations

By default, new segmentation instances do not overlap already existing ones. To make it so that new instances cover the existing ones, after selecting the Segmentation tool or having entered "edit mode" for an instance, enable the _Overwrite_ tool as shown below:

![](<../../.gitbook/assets/Screen Shot 2022-05-10 at 15.44.01.png>)

Now, new instances you create will overwrite existing ones on the image.

### Capturing All Pixels in an Image <a href="#differences-between-bounding-box-and-polygon" id="differences-between-bounding-box-and-polygon"></a>

When the _Overlap_ tool is disabled, no segmentation will ever erase another segmentation instance. This means that you can start a new segmentation from within another instance to ensure there is no gap between the previous instance and the new.

Ulteriorly, you can start a segmentation by clicking outside of the image, and no gap will be left between the segmentation and the image's border.

### Differences between Bounding Box, Polygon, and Segmentation <a href="#differences-between-bounding-box-and-polygon" id="differences-between-bounding-box-and-polygon"></a>

The Bounding Box tool allows annotators to create boxes with 4 edges only. The boxes cannot be rotated. This is ideal when we are not interested in the shape of an object but in its position on the asset.

The Polygon tool allows annotators to create polygons with an unlimited number of points. This is ideal to accurately trace around the edges of an object, for example, and is useful when we are interested in annotating the shape of an object.

The Segmentation tool allows annotators to classify each pixel in the image.&#x20;
