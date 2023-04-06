---
description: Overview of assets as they are used on Ango Hub.
---

# Assets

An asset is a piece of data to be annotated. Usually, an asset will be in the form of a file, for example, a .jpg image, a .mp3 audio, or a .txt text.

During labeling, Ango Hub will show annotators one asset at a time. The labeler will then annotate the asset using the labeling tools determined in the label set.

Ango Hub supports different categories of assets. [See all the supported file types](../data/importing-assets/supported-asset-file-types.md).

[Check out how to import assets into Ango Hub](../data/importing-assets/).

## Asset Attributes <a href="#asset-attributes" id="asset-attributes"></a>

### Path <a href="#path" id="path"></a>

Each asset has a file path associated with it.

To see an asset’s file path, in your project, enter the _Assets_ tab, then hover with your cursor over an asset preview. The asset’s absolute path will be shown.

![](<../.gitbook/assets/image (167).png>)

{% hint style="info" %}
Thumbnail previews are only shown for videos, and for images under 10MB in size.
{% endhint %}

Clicking on the “Copy” symbol at the beginning of the path will copy the path to the clipboard.

### External ID <a href="#external-id" id="external-id"></a>

Each asset is given a non-unique External ID.

This ID is used throughout the Ango Hub interface to identify the asset.

When [importing assets from the browser](../data/importing-assets/asset-browser-import.md), assets are given an External ID equal to their filenames, including the extension. When uploading assets using the [Cloud Import](../data/importing-assets/asset-cloud-import.md) functionality, External IDs are determined by the uploader in the JSON file.

Hovering the mouse cursor over an externalId will show the full external ID of the asset. Clicking on the “Copy” symbol at the beginning of the ID will copy the ID to the clipboard.

### Status <a href="#status" id="status"></a>

An asset’s status shows where the asset is currently located in the labeling pipeline. The status of an asset can be viewed from the _Assets_ tab. An asset can have one of four different statuses:

<img src="../.gitbook/assets/image (465).png" alt="" data-size="line">: An asset is to do when none of its labeling tasks, nor any of the reviewing tasks have been completed.

<img src="../.gitbook/assets/image (213).png" alt="" data-size="line">: An asset is in progress when at least one, but not all of its labeling tasks have been completed.

<img src="../.gitbook/assets/image (148).png" alt="" data-size="line">: An asset is labeled when all of its labeling tasks have been completed. For example, if consensus on the project has been set at 3 labelers, the task will not be considered labeled until all three labelers have annotated the asset.

<img src="../.gitbook/assets/image (199).png" alt="" data-size="line">: An asset is reviewed when its review task has been completed.

### Completed At <a href="#completed-at" id="completed-at"></a>

The _Completed At_ attribute shows the date and time when the last labeling task for the asset has been completed. This attribute is only shown when all labeling tasks have been completed.

### Duration <a href="#duration" id="duration"></a>

The _Duration_ attribute shows how long the asset has been labeled for, cumulatively, by all labelers assigned to it.

### Consensus <a href="#consensus" id="consensus"></a>

If more than one labeling task has been assigned to an asset, and if all labeling tasks of an asset have been completed, the consensus score will be shown in the _Assets_ tab.

Consensus is a score ranging from 0 to 100%, showing how much annotators agreed with one another when labeling the asset. 0% indicating no agreement, and 100% indicating full agreement.

### Labels <a href="#labels" id="labels"></a>

![](<../.gitbook/assets/image (473).png>)

Shown under the _Labels_ attribute are all the tasks associated with the asset. Each task is represented by a circle. Review tasks are to the left of the vertical line, while labeling tasks are to the right of it. The letters in the circle are the initials of the user assigned to the task.

A _green checkmark_ <img src="../.gitbook/assets/image (179).png" alt="" data-size="line"> indicates that the task has been completed.

A _yellow crown_ <img src="../.gitbook/assets/image (292).png" alt="" data-size="line"> indicates that the task has been marked as benchmark. [More on benchmarks here.](benchmarks.md)

A _grey circle_ <img src="../.gitbook/assets/image (229).png" alt="" data-size="line"> indicates that the task has not been completed.

A _blue label_ <img src="../.gitbook/assets/image (256).png" alt="" data-size="line"> indicates that the labels in the task have been imported externally into Ango Hub. [More on importing annotations here.](../data/importing-and-exporting-annotations/importing-annotations/)
