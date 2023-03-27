---
description: >-
  Attachments are media files like text, images, and videos that can be shown to
  labelers while annotating certain assets.
---

# Attachments

On Ango Hub, you can upload text, images, or videos to be shown to labelers next to specific assets during labeling.

<figure><img src="../.gitbook/assets/image (365).png" alt=""><figcaption><p>An attachment (right) shown next to an asset being labeled.</p></figcaption></figure>

### Properties of Attachments

* Text, image, or video files shown next to specific assets
* Viewable by labelers during labeling
* Unique to each asset, that is, you can show data that belongs to the asset being labeled right next to the asset itself
* Uploadable in bulk with a simple JSON structure
* An asset can have an unlimited number of attachments

### How to View an Attachment

From the labeling editor, navigate to an asset with an attachment.

Click on the "Attachment" tab on the right side of the screen. (1)

The attachment drawer will open. If more than one attachment was uploaded for the asset in question, each attachment is shown in its own tab. (2)

<figure><img src="../.gitbook/assets/image (323).png" alt=""><figcaption></figcaption></figure>

### How to Upload Attachments

From the _Assets_ tab in your project, click on _Import._ A dialogue will pop up.

Enter the _Import Attachment_ tab.

<figure><img src="../.gitbook/assets/image (334).png" alt=""><figcaption></figcaption></figure>

From here, you'll upload a JSON containing your attachments. Here's what a sample JSON looks like:

```json
[
  {
    "externalId": "image-sample.jpg",
    "attachments": [
      {
        "type": "IMAGE",
        "value": "https://sample-image.jpg"
      },
      {
        "type": "TEXT",
        "value": "Some sample text."
      }
    ]
  },
  {
    "externalId": "image-sample.jpg",
    "attachments": [
      {
        "type": "VIDEO",
        "value": "http://sample-video.mp4"
      }
    ]
  }
]
```

{% hint style="info" %}
Only text, images, and videos are supported.
{% endhint %}

If attachment upload is successful, a notification will pop up on the screen notifying you of how many assets were given an attachment.

### Uploading Attachments from Private Buckets

If you have created an integration between Ango Hub and your private bucket, either on AWS S3 or on GCP, you can upload attachments that link to files in your private bucket. The file will never be copied or moved anywhere, and will only be shown to labelers when they open the _Attachments_ drawer.

First, create an integration from the _Integration_ tab of your [Organization page](https://hub.ango.ai/organization). [You can read how to do so here](../data/importing-assets/importing-private-cloud-assets-aws.md).

Then, from the same page, copy the integration ID of your newly created integration, by clicking on the "Copy" button next to the ID:

<figure><img src="../.gitbook/assets/image (423).png" alt=""><figcaption></figcaption></figure>

Prepare a JSON in the same format as the one prepared [in the previous section](attachments.md#how-to-upload-attachments), but with the addition of integration IDs in the URLs. For example:

```json
[
  {
    "externalId": "image-sample.jpg",
    "attachments": [
      {
        "type": "IMAGE",
        "value": "https://sample-image.jpg?integrationId=1234567890"
      },
      {
        "type": "TEXT",
        "value": "Some sample text."
      }
    ]
  },
  {
    "externalId": "image-sample.jpg",
    "attachments": [
      {
        "type": "VIDEO",
        "value": "http://sample-video.mp4?integrationId=1234567890"
      }
    ]
  }
]
```

## Importing Attachments during Asset Import

Hub allows you to import attachments together with assets, at the same time.

To do so, you will have to use the _Cloud Import JSON_ method for importing assets, as explained below:

1. In your project, go to the _Assets_ tab and click on the _Add Data_ button.
2. From the dialog that appears, enter the _Upload Data URL_ tab.
3. Prepare a JSON formatted like the following. It is an array of objects, with each object representing an asset. Each object, then, in its `attachments` property, will have a list of attachments, like so:

```json
[
    {
        "externalId":"my_external_id",
        "data":"https://url-to.asset/video.mp4",
        "attachments":[
            {"type":"IMAGE","value":"https://angohub-public-assets.s3.amazonaws.com/uploaded-data-6cbc3c56-58f9-4430-990d-863bd5a1a755.jpg"},
            {"type":"TEXT","value":"This is a text attachment."}
        ]
    }
]
```

4. Drag and drop the JSON you've just created on the _Upload Data URL_ file box:

<figure><img src="../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

5. Your assets with attachments will appear in the _Assets_ tab.
