---
description: Overview of the Video Labeling Editor in Ango Hub
---

# Video Labeling Editor

For a complete video tutorial on labeling videos on Hub, see the following:

{% embed url="https://youtu.be/eYxAiwg4pQg" %}

Ango Hub provides a labeling editor with which video files can be annotated. The video editor will be opened when a user opens an asset with the following file extensions: `.mp4`, `.mov`, `.webm`, `.ogg`.

This article will exclusively go over Ango Hub’s video labeling interface. Features common to all labeling editors are instead [explained here](../).

<figure><img src="../../../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

## Overview of the Video Labeling Editor in Ango Hub <a href="#image-interface-elements" id="image-interface-elements"></a>

### Playback Bar <a href="#zoom-buttons" id="zoom-buttons"></a>

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-16 at 11.32.12.png" alt=""><figcaption></figcaption></figure>

The back and forward arrows allow you to move backwards and forwards one frame at a time. The Play ![](<../../../.gitbook/assets/image (76).png>) button starts and stops playback of the video file. The slider allows you to move between frames by clicking on the playhead and dragging it to find the frame you need.

{% hint style="info" %}
When dragging with the slider, the frame selected will only be loaded when you release the left mouse button.
{% endhint %}

The volume slider (![](<../../../.gitbook/assets/image (30).png>)) allows you to change the volume of the audio when playing the file back.

## How to Annotate Videos <a href="#how-to-annotate-images" id="how-to-annotate-images"></a>

The following are the labeling tools supported on videos:

* [Bounding Box](../../labeling-tools/bounding-box.md)
* [Rotated Bounding Box](../../labeling-tools/rotated-bounding-box.md)
* [Polygon](../../labeling-tools/polygon.md)
* [Polyline](../../labeling-tools/polyline.md)
* [Segmentation](../../labeling-tools/segmentation.md)
* [Point](../../labeling-tools/point.md)
* [Brush](../../labeling-tools/brush-bucket.md)

From the _Tools_ panel on the left sidebar, select a supported labeling tool. Then, follow the instructions found on each tool's docs page, linked to above.

If no tools are present in the project, only answer the questions in the _Classifications_ panel.

### Labeling Properties Specific to Videos

#### Bounding Box Interpolation

Once you have created a bounding box, move forward some frames, then edit the label to its new position on the video. Ango Hub will automatically interpolate the position of the box in the frames where the label was not manually placed.

{% hint style="info" %}
Interpolation is currently only available for the Bounding Box labeling tool.
{% endhint %}

If the object you are following with the label leaves the frame, hover over the label with your mouse cursor and press S or disable the ![](<../../../.gitbook/assets/image (22) (1).png>)toggle next to the annotation from the _Objects_ panel in the lower left of the screen. The label will be hidden from view. To restore it, simply enable its toggle.

#### Frame-Specific Classifications <a href="#nested-questions-and-classifications" id="nested-questions-and-classifications"></a>

When creating classifications such as [radio](../../labeling-tools/classification-tools/radio.md), [dropdown](../../labeling-tools/classification-tools/single-dropdown.md), and others, project managers may choose to make those classifications general (e.g., one response per video) or frame-specific (e.g. one response per frame.)

![](<../../../.gitbook/assets/image (435).png>)

Here's an example on how to classify single frames using frame-specific classifications.

For this example, let's assume I have a video with 506 frames and a radio classification class with the answers "First", "Second", and "Third," and I wish to:

* annotate frames 1 to 10 with "First"
* frames 11 to 20 with "Second", and
* frames 50 to 60 with "Third."

Here's how you would go about doing so:

1. Navigate to frame 1 and click on First. This will enable the "First" answer for all following frames until we tell Hub otherwise.
2. Navigate to frame 11 and click on Second. This will switch the annotation to Second.
3. Navigate to frame 21 and disable the ![](<../../../.gitbook/assets/image (31).png>)toggle next to the classification. This will make it so that from frame 21 onwards included, the classification will not be answered.
4. Navigate to frame 50 and click on Third.
5. Navigate to frame 61 and disable the ![](<../../../.gitbook/assets/image (15).png>)toggle next to the classification.

### Keyboard Shortcuts <a href="#keyboard-shortcuts" id="keyboard-shortcuts"></a>

A full list of keyboard shortcuts is available by clicking on the _Keyboard_ button on the right side of the top bar:

![](<../../../.gitbook/assets/image (394).png>)

### Further reading

{% content-ref url="../audio-labeling-editor.md" %}
[audio-labeling-editor.md](../audio-labeling-editor.md)
{% endcontent-ref %}

{% content-ref url="../" %}
[..](../)
{% endcontent-ref %}
