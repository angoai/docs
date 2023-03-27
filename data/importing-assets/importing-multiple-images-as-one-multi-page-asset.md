# Importing Multiple Images as One Multi-Page Asset

{% hint style="info" %}
This feature is currently only available in our beta build.
{% endhint %}

You may group together images and upload them to Hub as a single multi-page asset, where each page is one of the images uploaded.

At the moment, you may only upload such multi-image assets using the _Cloud Import_ method outlined below.

## Uploading Multi-Image Assets

Prepare a JSON like the following, where each URL points to an image you'd like to include in the asset. The order of the URLs will determine the order in which images will be presented to the annotator as pages.

The following JSON will import two assets of four images each:

```json
[
  {
    "externalId": "my-asset-external-id-1",
    "dataset": [
      "https://url.com/65c18c8b-4513-4a0a-b876-1aeb2e0908ec.png",
      "https://url.com/b0b70590-e4cc-42ef-8537-3ee3f7917fed.jpg",
      "https://url.com/38e11364-1ce0-417a-9e38-436468c555ce.jpg",
      "https://url.com/eff59355-03bd-447f-aa47-46028f90c2e6.jpg"
    ]
  },
  {
    "externalId": "my-asset-external-id-2",
    "dataset": [
      "https://url.com/65c18c8b-4513-4a0a-b876-123456789012.png",
      "https://url.com/b0b70590-e4cc-42ef-8537-234456566787.jpg",
      "https://url.com/38e11364-1ce0-417a-9e38-876345383488.jpg",
      "https://url.com/eff59355-03bd-447f-aa47-319485019239.jpg"
    ]
  }
]
```

From your project dashboard, go to the _Assets_ tab and click on _Add Data_. Then, enter the _Upload Data URL_ section and drag and drop your JSON on the file upload field. Then, press on _Upload_. Your multi-image asset(s) will be uploaded.

<figure><img src="../../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>

Assets uploaded this way will have a slider at the top, allowing annotators to navigate between the images in the dataset.

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>
