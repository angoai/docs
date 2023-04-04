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

The following are the labeling tools supported on DICOMs:

* [Bounding Box](../labeling-tools/bounding-box.md)
* [Rotated Bounding Box](../labeling-tools/rotated-bounding-box.md)
* [Polygon](../labeling-tools/polygon.md)
* [Polyline](../labeling-tools/polyline.md)
* [Segmentation](../labeling-tools/segmentation.md)
* [Point](../labeling-tools/point.md)
* [Brush](../labeling-tools/brush-bucket.md)

From the _Tools_ panel on the left sidebar, select a supported labeling tool. Then, follow the instructions found on each tool's docs page, linked to above.

If no tools are present in the project, only answer the questions in the _Classifications_ panel.

When done, move forward to the next page and repeat the process until all pages are labeled.

![](<../../.gitbook/assets/Screen Shot 2022-05-10 at 15.19.08.png>)

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
