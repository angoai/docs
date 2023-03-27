---
description: Overview of the DICOM Labeling Editor interface on Ango Hub
---

# DICOM Labeling Editor

Ango Hub provides a labeling editor with which single- and multi-page DICOM files can be annotated.

This article will exclusively go over Ango Hub’s DICOM labeling interface. Features common to all labeling editors (audio, image, PDF, and text) are instead [explained here](./).

![](<../../.gitbook/assets/image (322).png>)

## Overview of the DICOM Labeling Editor in Ango Hub <a href="#image-interface-elements" id="image-interface-elements"></a>

### DICOM Interface Elements <a href="#image-interface-elements" id="image-interface-elements"></a>

#### Pages Bar <a href="#zoom-buttons" id="zoom-buttons"></a>

![](<../../.gitbook/assets/Screen Shot 2022-05-10 at 15.13.55.png>)

The back and forward arrows allow you to move backwards and forwards one page at a time. The slider allows you to move quickly between pages by clicking on it dragging it to find the frame you need. If you already know the number of the page you'd like to visualize, enter it in the text box on the right and press Enter to immediately jump to it.

#### Patient and File Information

![](<../../.gitbook/assets/Screen Shot 2022-05-10 at 15.21.40.png>)

If embedded in the DICOM file, patient data such as Patient ID and Patient Name will be shown. If present, the thickness of the slices in the DICOM file is shown.

### How to Annotate DICOM Files <a href="#how-to-annotate-images" id="how-to-annotate-images"></a>

Annotating DICOMs is similar to annotating images and videos since a single-page DICOM is, in essence, an image, and a multi-page DICOM a video. There is, however, additional functionality to consider.

From the _Tools_ panel on the left sidebar, select a _Bounding Box, Rotated Bounding Box, Polygon, Segmentation, or Point_ labeling tool. (If none are present, only answer the questions in the _Questions_ panel below.)

When done, move forward to the next page and repeat the process until all pages are labeled.

![](<../../.gitbook/assets/Screen Shot 2022-05-10 at 15.19.08.png>)

#### Bounding Box <a href="#bounding-box" id="bounding-box"></a>

Click on the image where you’d like the bounding box to start. Release where you’d like the bounding box to end.

After creating the box, you can change its size by dragging on its points. You can drag the entire bounding box by dragging it with the mouse cursor.

#### Rotated Bounding Box

Click on the image where you'd like the top-left corner of the rotated bounding box to be. Release where you'd like the box to end.

You can change the angle of the box by clicking and dragging on the point located just outside the box.

#### Polygon <a href="#polygon" id="polygon"></a>

Click on the image where you’d like the first point of the polygon to be. Click again where you’d like the second point to be, and so on. When you are done, click on the first point again or press on _N_ on your keyboard to close the polygon.

While drawing, you may click anywhere with the right mouse button to delete the last point you have placed. To add a new point after closing the polygon, hold CTRL and click on a point. To delete a point, hold CTRL and right-click on the point you’d like to delete.

#### Segmentation

[More on labeling using the Segmentation tool here](../labeling-tools/segmentation.md).

#### Point <a href="#point" id="point"></a>

Simply click on the image where you’d like the point to be.

You may change the position of the point by clicking and dragging it.

#### Nested Questions and Classifications <a href="#nested-questions-and-classifications" id="nested-questions-and-classifications"></a>

If the labels have nested questions, right-click on each label and click on the menu item that appears to see and answer the nested questions.

If classification questions are present, you may answer them from the _Questions_ panel on the left sidebar.

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
