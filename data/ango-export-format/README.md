---
description: JSON-based universal annotation export format.
---

# Ango Export Format

Ango Hub exports annotations in its own JSON-based format, called the Ango Annotation Format (AAF).

AAF is not a new file type. It is instead a way in which annotation data is recorded and organized within a JSON structure. AAF is not a superset of JSON, as it does not add any new features or syntax.&#x20;

The extension used for exports in the AAF format is `.json`.

## Structure of an Export in the Ango Annotation Format

* [Asset](asset.md)
  * [Asset Metadata](asset.md#asset-object-fields)
  * [Task](task.md)
    * [Task Metadata](task.md#task-object-fields)
    * [Objects](objects.md)
    * [Classifications](classifications.md)
    * [Relations](relations.md)
  * Task
    * ...
* Asset
  * ...

### Sample AAF Export

```json
[
  {
    "asset": "https://asset.url/image-sample.jpg",
    "externalId": "image-sample.jpg",
    "labeledAt": "2021-12-08T12:31:36.043Z"
    "reviewedAt": "2021-12-08T15:31:36.043Z",
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
            "title": "Label Title"
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
]
```

An AAF export is, at its core, an array of assets. Each asset, in turn, contains metadata about itself, plus an array of labeling tasks performed on the asset.

If, for example, two labelers labeled the same asset, the asset will contain an array with two "tasks."

Each task, in turn, other than metadata about the task itself such as its review status, also contains the actual [object annotation data](objects.md), such as X and Y coordinates of a bounding box, answers to classification questions, relations, and more.

AAF was created with the main goal of being easy to convert from. Our philosophy is to provide the user with the most control possible over their annotations.

By design, AAF is a malleable format, built to be easy to parse and understand at a first glance, so that you can get to converting it to whatever format you need as quickly as possible.

### More on the Ango Annotation Format

{% content-ref url="asset.md" %}
[asset.md](asset.md)
{% endcontent-ref %}

{% content-ref url="task.md" %}
[task.md](task.md)
{% endcontent-ref %}

{% content-ref url="objects.md" %}
[objects.md](objects.md)
{% endcontent-ref %}

{% content-ref url="classifications.md" %}
[classifications.md](classifications.md)
{% endcontent-ref %}

{% content-ref url="relations.md" %}
[relations.md](relations.md)
{% endcontent-ref %}
