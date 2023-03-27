# Importing Attachments during Asset Import

Hub allows you to import [attachments](../../core-concepts/attachments.md) together with assets, at the same time.

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

<figure><img src="../../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

5. Your assets with attachments will appear in the _Assets_ tab.

See the pages on [attachments](../../core-concepts/attachments.md) and [cloud import](asset-cloud-import.md) for more on each topic.
