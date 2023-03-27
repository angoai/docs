---
description: Overview of the Rotated Bounding Box labeling tool in Ango Hub
---

# Rotated Bounding Box

The rotated bounding box labeling tool allows you to draw a box around an object or point of interest in an image, and to then rotate it.

![](<../../.gitbook/assets/Screen Shot 2021-10-15 at 15.18.23.png>)

## The Rotated Bounding Box Tool in Ango Hub <a href="#how-to-add-a-bounding-box-tool-to-your-project" id="how-to-add-a-bounding-box-tool-to-your-project"></a>

### How to add a Rotated Bounding Box tool to your project <a href="#how-to-add-a-bounding-box-tool-to-your-project" id="how-to-add-a-bounding-box-tool-to-your-project"></a>

From the project’s _Settings_ tab, enter the _Label Set_ section.

Click on _Add Category_. From the list that appears, click on _Rotated Bounding Box_.

A new row will appear named _Rotated Bounding Box_. Click on it to expand it.

![](<../../.gitbook/assets/Screen Shot 2021-10-15 at 15.24.45.png>)

Give your rotated bounding box tool a title and description.

Enable the _Required_ toggle if you want to force labelers to create a rotated bounding box for each asset. When the toggle is disabled, labelers will be able to save and move to the next asset without creating the rotated bounding box.

If you would like to ask labelers further questions, for example, if you want to show a further _radio_ after drawing the rotated bounding box, click on _Add Classification_ and add a further question. [More on nested questions here](nested-classifications.md).

### How to Draw a Rotated Bounding Box <a href="#how-to-draw-a-bounding-box" id="how-to-draw-a-bounding-box"></a>

Click on the image where you'd like the top-left corner of the rotated bounding box to be. Click again where you'd like the box to end.

![](<../../.gitbook/assets/Screen Shot 2021-10-15 at 15.18.23.png>)

You can change the angle of the box by clicking and dragging on the point located just outside the box.

### Differences between Rotated Bounding Box and Polygon <a href="#differences-between-bounding-box-and-polygon" id="differences-between-bounding-box-and-polygon"></a>

The Rotated Bounding Box tool allows annotators to create boxes with 4 edges only. This is ideal when we are not interested in the shape of an object but in its position on the asset.

The Polygon tool allows annotators to create polygons with an unlimited number of points. This is ideal to accurately trace around the edges of an object, for example, and is useful when we are interested in annotating the shape of an object.

In most cases, rotated bounding boxes are much faster to create than polygons.
