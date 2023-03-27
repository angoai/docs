---
description: How assets (files) are represented in the Ango Annotation Format
---

# Asset

_This page is about the `asset` object in Ango Hub's export file. For more information on assets as they are used in Ango Hub, check out the page named_[ _Assets_](../../core-concepts/assets.md)_._

The asset is the main unit in the Ango Annotation Format. When obtaining an export from Ango Hub, you are essentially getting a list of assets.

This page details assets and their available metadata in the export format.

## Assets in the Ango Annotation Format

### Asset Object Fields

* `asset` - the URL to the asset.
* `externalId` - The [external ID](../../core-concepts/assets.md#external-id) assigned to the asset at import time.
* `labeledAt` - The date and time in which the asset was labeled, in the UTC time zone. An asset is considered labeled when all of its labeling tasks have been completed. Check out the [Assets](../../core-concepts/assets.md#completed-at) page for more information.
* `reviewedAt` - The date and time in which the asset was reviewed, in the UTC time zone. An asset is considered reviewed when all of its labeling tasks have been reviewed.
* `status` - The status of the asset. [More on status here](../../core-concepts/assets.md#status).
* `labelDuration` - The time it took, in milliseconds, to label the asset. The timer starts when a user opens the asset and stops when they click on "Submit."
* `consensus` - If consensus was activated (e.g. more than one labeler annotated the same asset), this is the consensus score from 0 (no consensus at all) to 100 (full consensus).
* `metadata` - Metadata on the asset file itself. At the moment, it contains the width and height of the image, if the asset is an image.
* `tasks` - The list of labeling tasks attached to the asset. [More on tasks in exports here](task.md).

### Sample Asset Export

```json
{
    "asset": "https://asset.url/image-sample.jpg",
    "externalId": "image-sample.jpg",
    "labeledAt": "2021-12-08T12:31:36.043Z",
    "reviewedAt": "2021-12-08T15:31:36.043Z",
    "status": "Labeled",
    "labelDuration(ms)": 6429,
    "consensus": 90,
    "metadata": {
      "width": 100,
      "height": 100
    },
    "tasks": [
      {
        "completedBy": "Labeler Name",
        "completedAt": "2021-12-08T12:31:36.043Z",
        "duration(ms)": 6429,
        "isSkipped": false,
        "review": {
          "status": "Fixed",
          "completedBy": "Reviewer Name",
          "completedAt": "2021-12-08T10:46:36.296Z",
          "duration(ms)": 36283
        },
        "status": "Completed",
        "updatedBy": "Labeler Name",
        "updatedAt": "2021-12-08T18:32:38.908Z",
        "isBenchmark": false,
        "benchmark": "60",
        "issues": [],
        "taskId": "taskId123456789",
        "objects": [
          {
            "schemaId": "schemaId12345",
            "bounding-box": {
              "x": 200,
              "y": 200,
              "height": 400,
              "width": 400
            },
            "objectId": "objectId12345",
            "classifications": [],
            "title": "Label Title",
            "metadata": {
              "createdAt": "2021-12-08T12:31:34.418Z",
              "createdBy": "Reviewer Name"
            }
          }
        ],
        "classifications": [
          {
            "schemaId": "schemaId12346",
            "tool": "radio",
            "title": "Radio Title",
            "columnField": false,
            "answer": "Four",
            "classifications": []
          }
        ],
        "relations": [
          {
            "objectId": "objectId123457",
            "schemaId": "schemaId12347",
            "from": "objectId12345",
            "to": "objectId12345",
            "direction": "straight",
            "title": "Relation Title"
          }
        ]
      }
    ]
  }
```
