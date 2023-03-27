---
description: How to import assets in private buckets on AWS S3 for labeling on Ango Hub
---

# Importing Private Cloud Assets from GCP

Administrators and project managers can import assets to Ango Hub from GCP private buckets.

The main difference between importing data from cloud storage services and using drag-and-drop is the files' location. When [importing assets with drag-and-drop](asset-browser-import.md), the assets get copied to a folder within Ango Hub. This means that, if you are using Hub's cloud version, your assets are uploaded to Ango AI's own cloud storage. When importing assets from your own cloud storage, however, your assets are left in your own storage and are never copied anywhere else.

## Configure CORS

The CORS header below allows Ango Hub to send a request to your cloud storage, and allows your cloud storage to explicitly allow requests from Hub. This is a necessary step to ensure Hub can connect to your private bucket.

[The steps to follow to set up CORS with Ango Hub can be found here.](../integrations/set-up-cors.md#google-cloud-platform-gcp)

## Connect your Cloud Storage <a href="#preparing-the-csv" id="preparing-the-csv"></a>

Once you've set up CORS for your bucket, you will need to create a connection between Hub and the bucket itself.

To link your bucket to Hub, you will need a JSON obtained from the GCP dashboard called _Service Account Key_. [Here are the instructions on how to obtain the necessary Service Account Key JSON from your GCP console](https://cloud.google.com/iam/docs/creating-managing-service-account-keys#creating).

Once you have downloaded the JSON, go to [your organization's page](https://hub.ango.ai/organization), then click on _Integrations_ and _Add Integration._

![](<../../.gitbook/assets/Screen Shot 2022-03-17 at 12.01.42.png>)

From the dialog that pops up, pick GCP as the provider and drag and drop the Service Account Key JSON you've just downloaded.

<figure><img src="../../.gitbook/assets/image (136).png" alt=""><figcaption></figcaption></figure>

After clicking _OK_, your bucket will be linked to Hub, and it will show up in your list of integrations.

{% hint style="info" %}
Integrations belong to your organization, not your user.

If you want to be able to access your non-public cloud data in multiple organizations, you will have to integrate Hub with AWS in every one of them.
{% endhint %}

## Preparing the JSON to Import Assets <a href="#preparing-the-csv" id="preparing-the-csv"></a>

After connecting our bucket, we will need to prepare a JSON file containing each asset’s [external ID](../../core-concepts/assets.md#External-ID) as well as the asset's full absolute path, plus optionally the image's width and height if the asset is an image.

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
   "data":"https://bucket-name.s3.eu-central-1.amazonaws.com/file.jpg",
   "externalId":"cute-cat.jpg",
   "width":603,
   "height":450
  },
  {
   "data":"https://bucket-name.s3.eu-central-1.amazonaws.com/file%202.jpg",
   "externalId":"cute-dog.jpg",
   "width":1800,
   "height":1200
  }
]
```

There is no upper bound to the number of assets that can be imported to a project in Ango Hub this way. There is no file size restriction.

## Uploading the JSON to Ango Hub <a href="#uploading-the-csv-to-ango-hub" id="uploading-the-csv-to-ango-hub"></a>

From your project’s dashboard, enter the _Assets_ tab and click on _Add Data_.

![](<../../.gitbook/assets/Screen Shot 2022-02-24 at 20.37.30.png>)

A dialog will pop up. Click on “Upload Data URL” at the top.

![](<../../.gitbook/assets/Screen Shot 2022-02-24 at 20.38.56.png>)

Click on _Advanced Configs_ and from _Storage Method_, pick the storage integration you created in the previous step.

![](<../../.gitbook/assets/image (113).png>)

Drag the JSON file you would like to upload to the box in the center. Alternatively, click on the box to open your system’s file explorer and select it from there.

Click on the _Close_ button. Your assets will show up in the _Assets_ tab.

![](<../../.gitbook/assets/Screen Shot 2022-02-24 at 20.40.02.png>)

It is also possible to upload assets through our [API](../../api/api-documentation.md).
