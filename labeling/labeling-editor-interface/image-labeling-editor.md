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

The following are the labeling tools supported on images:

* [Bounding Box](../labeling-tools/bounding-box.md)
* [Rotated Bounding Box](../labeling-tools/rotated-bounding-box.md)
* [Polygon](../labeling-tools/polygon.md)
* [Polyline](../labeling-tools/polyline.md)
* [Segmentation](../labeling-tools/segmentation.md)
* [Point](../labeling-tools/point.md)
* [Brush](../labeling-tools/brush-bucket.md)

From the _Tools_ panel on the left sidebar, select a supported labeling tool. Then, follow the instructions found on each tool's docs page, linked to above.

If no tools are present in the project, only answer the questions in the _Classifications_ panel.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

#### Nested Questions and Classifications <a href="#nested-questions-and-classifications" id="nested-questions-and-classifications"></a>

If the labels have nested questions, click on a label to select it, then right-click on it and open the the menu item that appears to see and answer the nested questions.

If classification questions are present, you may answer them from the _Classifications_ panel on the left sidebar.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-04 at 10.28.49.png" alt=""><figcaption></figcaption></figure>

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
