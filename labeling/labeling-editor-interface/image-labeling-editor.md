---
description: Overview of the Image Labeling Editor in Ango Hub
---

# Image Labeling Editor

Ango Hub provides a labeling editor with which image files can be annotated.

This article will exclusively go over Ango Hub’s image labeling interface. Features common to all labeling editors (audio, image, PDF, and text) are instead [explained here](./).

![](<../../.gitbook/assets/image (96).png>)

### Overview of the Image Labeling Editor in Ango Hub <a href="#image-interface-elements" id="image-interface-elements"></a>

#### **Zoom buttons** <a href="#zoom-buttons" id="zoom-buttons"></a>

![](<../../.gitbook/assets/image (266).png>)

The three buttons allow you to zoom in, zoom out, and fit the asset to screen, respectively.

Scrolling with the mouse wheel will zoom in and out of the asset. Double-clicking will zoom in on the zone that’s been double-clicked.

#### Zoom Level Indicator

The zoom level indicator marks the current zoom level of the image. 100% represents the level at which the image fit within the Ango Hub editor canvas when you opened the asset.

<figure><img src="../../.gitbook/assets/Screen Shot 2022-10-24 at 13.46.19.png" alt=""><figcaption></figcaption></figure>

### How to Annotate Images <a href="#how-to-annotate-images" id="how-to-annotate-images"></a>

From the _Tools_ panel on the left sidebar, select a _Bounding Box, Polygon, or Point_ labeling tool. (If none are present, only answer the questions in the _Questions_ panel.)

![](<../../.gitbook/assets/image (242).png>)

#### Bounding Box <a href="#bounding-box" id="bounding-box"></a>

Click on the image where you’d like the bounding box to start. Release where you’d like the bounding box to end.

![](<../../.gitbook/assets/image (274).png>)

After creating the box, you can change its size by dragging on its points. You can drag the entire bounding box by dragging it with the mouse cursor.

#### Rotated Bounding Box

Click on the image where you'd like the top-left corner of the rotated bounding box to be. Release where you'd like the box to end.

![](<../../.gitbook/assets/Screen Shot 2021-10-15 at 15.18.23.png>)

You can change the angle of the box by clicking and dragging on the point located just outside the box.

#### Polygon <a href="#polygon" id="polygon"></a>

Click on the image where you’d like the first point of the polygon to be. Click again where you’d like the second point to be, and so on. When you are done, click on the first point again or press on _N_ on your keyboard to close the polygon.

![](<../../.gitbook/assets/image (419).png>)

While drawing, you may click anywhere with the right mouse button to delete the last point you have placed. To add a new point after closing the polygon, hold CTRL and click on a point. To delete a point, hold CTRL and right-click on the point you’d like to delete.

#### Point <a href="#point" id="point"></a>

Simply click on the image where you’d like the point to be.

![](<../../.gitbook/assets/image (202).png>)

You may change the position of the point by clicking and dragging it.

#### Nested Questions and Classifications <a href="#nested-questions-and-classifications" id="nested-questions-and-classifications"></a>

If the labels have nested questions, right-click on each label and click on the menu item that appears to see and answer the nested questions.

If classification questions are present, you may answer them from the _Questions_ panel on the left sidebar.

![](<../../.gitbook/assets/image (435).png>)

### Quick Settings Menu <a href="#quick-settings-menu" id="quick-settings-menu"></a>

<figure><img src="../../.gitbook/assets/Screen Shot 2022-10-24 at 13.38.34.png" alt=""><figcaption></figcaption></figure>

The following is a list of quick settings unique to Ango Hub's image labeling editor. For an explanation of the settings common to all data types, visit the [_Labeling Editor Interface_](./) docs page.&#x20;

**Hide Unknown Objects**: when enabled, unknown objects (annotations without categorization, for example, annotations created with OCR or Lung Detector) are not shown. They will still appear in the export.

**Image Smoothing Enabled**: when enabled, images will be smoothed out so that individual pixels are not discernible.

**Opacity**: sets the opacity of the annotations.

**Box Border Thickness**: sets the thickness of the borders of bounding boxes.

**Brightness**: sets the image's brightness.

**Contrast**: sets the image's contrast.

### Keyboard Shortcuts <a href="#keyboard-shortcuts" id="keyboard-shortcuts"></a>

A full list of keyboard shortcuts is available by clicking on the _Keyboard_ button on the right side of the top bar:

![](<../../.gitbook/assets/image (394).png>)

### Further reading

{% content-ref url="audio-labeling-editor.md" %}
[audio-labeling-editor.md](audio-labeling-editor.md)
{% endcontent-ref %}

{% content-ref url="./" %}
[.](./)
{% endcontent-ref %}
