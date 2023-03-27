---
description: Ways in which you can import assets (files) in Ango Hub.
---

# Importing Assets

Ango Hub provides two methods to import assets for labeling.

### Methods to Import Assets to Ango Hub

#### Browser Import <a href="#browser-import" id="browser-import"></a>

The Browser Import method is a drag and drop interface, through which files can be imported directly from your system.

If Ango Hub was installed on-premises, assets imported this way will be copied to the `/uploaded-data/` folder within Ango Hub's root. If you are using Ango Hub on the cloud, assets imported this way will be uploaded to Ango's AWS encrypted cloud storage in Germany.

[Click for information on browser import](asset-browser-import.md).

#### Cloud Import <a href="#cloud-import" id="cloud-import"></a>

You may alternatively upload a JSON containing the file paths and their [external IDs](../../core-concepts/assets.md#External-ID). This is what we call Cloud Import. Assets imported this way are not copied over, and are simply fetched as necessary to display them. More details on this method can be found in the pages below:

* [Upload public cloud assets](asset-cloud-import.md)
* Upload private cloud assets
  * [From AWS S3](importing-private-cloud-assets-aws.md)
  * [From GCP](importing-private-cloud-assets-gcp.md)
