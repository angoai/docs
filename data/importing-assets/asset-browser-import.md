---
description: Overview of importing files for labeling into Ango Hub from the local machine
---

# Importing From Local Machine

Administrators can import [data](../data-in-ango-hub/) to Ango Hub by simply dragging and dropping the [assets](../../core-concepts/assets.md) they’d like to label.

Assets uploaded this way will be stored in the `/uploaded-data/` folder within Ango Hub. These assets will be assigned an [_External ID_](../../core-concepts/assets.md#External-ID) equal to their filename, including the extension.

## How to import assets from the browser <a href="#how-to-import-assets-from-the-browser" id="how-to-import-assets-from-the-browser"></a>

From your project’s dashboard, enter the _Assets_ tab and click on _Add Data_.

<figure><img src="../../.gitbook/assets/Screenshot 2022-10-27 at 16.17.06.png" alt=""><figcaption></figcaption></figure>

A dialog will pop up. Drag the assets you would like to upload to the box in the center. Alternatively, click on the box to open your system’s file explorer.

<figure><img src="../../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
Ango Hub will assume that videos uploaded this way are 30fps.

If your videos have a different frame rate, you will need to upload them using the [Cloud Import function](asset-cloud-import.md#preparing-the-csv).
{% endhint %}

### Import Options

**Batch Name**: If you select one or more [batches](../../core-concepts/batches.md) from this dropdown, the assets you will upload will be assigned to the selected batches.

**Frame Step**: If 1, you will be able to see and label each frame of a video. If 2, you will see and label 1 frame every 2, and so on.

If Frame Step is set to 0, videos will be uploaded in General Mode, which is ideal for tasks where the entire video needs to be classified rather than individual frames. [More info on General Mode here](../../labeling/labeling-editor-interface/video-labeling-editor/labeling-videos-in-general-mode.md).

Click on _Upload_ to import your assets. After uploading, they will appear in the _Assets_ tab.

{% hint style="info" %}
It is also possible to upload assets through our [API](../../api/api-documentation.md) and [SDK](../../sdk/sdk-documentation.md).
{% endhint %}
