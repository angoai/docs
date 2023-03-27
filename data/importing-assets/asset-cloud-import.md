---
description: Overview of importing publicly available assets into Ango Hub
---

# Importing Public Cloud Assets

Administrators and project managers can import assets to Ango Hub without having to move them to another folder.

The main difference between importing data from cloud storage services and using drag-and-drop is the files' location. When [importing assets with drag-and-drop](asset-browser-import.md), the assets get copied to a folder within Ango Hub. This means that, if you are using Hub's cloud version, your assets are uploaded to Ango AI's own cloud storage. When importing assets from your own cloud storage, however, your assets are left in your own storage and are never copied anywhere else.

## Importing Public Assets from the Cloud to Ango Hub

### Preparing the JSON <a href="#preparing-the-csv" id="preparing-the-csv"></a>

Before importing the assets to Ango Hub, we will need to prepare a JSON file containing each asset’s [external ID](../../core-concepts/assets.md#External-ID) as well as the asset's full absolute path, plus optionally the image's width and height if the asset is an image.

{% hint style="info" %}
The width and height fields are only necessary if you plan on exporting polygon annotations as image bitmasks. In most cases, width and height information will not be necessary.
{% endhint %}

{% hint style="warning" %}
Ensure your URLs are percent-encoded in the UTF-8 format.

If your filenames contain spaces, for example, ensure they are encoded as `%20`, and not as pluses (`+`).
{% endhint %}

This is what the JSON should look like:

```json
[
  {
   "data":"https://i.imgur.com/CzXTtJV.jpg",
   "externalId":"cute-cat.jpg"
  },
  {
   "data":"https://i.imgur.com/OB0y6MR.jpg",
   "externalId":"cute-dog.jpg"
  }
]
```

There is no upper bound to the number of assets that can be imported to a project in Ango Hub this way. There is no file size restriction.

For videos the additional `frameRate`property may be passed. If you don't pass a `frameRate` property, Ango Hub will assume your video has a frame rate of 30fps. Example for videos:

```json
[
  {
    "data": "https://your-url.com/asset.mp4",
    "externalId": "YOUR_EXTERNAL_ID",
    "metadata": {
      "frameRate": 25
    }
  }
]
```

### Uploading the JSON to Ango Hub <a href="#uploading-the-csv-to-ango-hub" id="uploading-the-csv-to-ango-hub"></a>

From your project’s dashboard, enter the _Assets_ tab and click on _Add Data_.

![](<../../.gitbook/assets/Screen Shot 2022-02-24 at 20.37.30.png>)

A dialog will pop up. Click on “Upload Data URL” at the top.

![](<../../.gitbook/assets/Screen Shot 2022-02-24 at 20.38.56.png>)

Drag the JSON file you would like to upload to the box in the center. Alternatively, click on the box to open your system’s file explorer and select it from there.

Click on the _Close_ button. Your assets will show up in the _Assets_ tab.

![](<../../.gitbook/assets/Screen Shot 2022-02-24 at 20.40.02.png>)

It is also possible to upload assets through our [API](../../api/api-documentation.md).
