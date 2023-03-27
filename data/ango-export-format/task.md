---
description: Page explaining how tasks are represented in the Ango Annotation Format
---

# Task

_This page is about the `task` object in Ango Hub's export file. For more information on tasks as they are used in Ango Hub, see the page named_ [_Tasks_](../../core-concepts/tasks.md)_._

The task is the main sub-unit of the [_Asset_](asset.md) __ in the Ango Annotation Format. When obtaining an export from Ango Hub, you are essentially getting a list of assets, which contains a list of labeling tasks.

Tasks are what contain the actual labeling data (e.g. points, classifications, relations, etc.)

This page details tasks and their metadata in Ango Annotation Format exports.

## Tasks in Ango Hub

### Task Object Fields

* `completedBy` - Username of the user completing the labeling task.
* `completedAt` - The date and time in which the labeling task was completed, in the UTC time zone.
* `duration(ms)` - The time it took, in milliseconds, to label the asset. The timer starts when a user opens the asset and stops when they click on "Submit."
* `isSkipped` - Whether or not the task was skipped by the assignee (by clicking on "Skip" on the bottom left corner of the labeling editor.)
* `review` - The review status of the task. [More on reviewing here](../../core-concepts/reviewing.md).
* `status` - The status of the task, whether it is still to do, it's being worked on, or if it was completed.
* `updatedBy` - If the task was reopened and modified, this is the username of the user who did.
* `updatedAt` - If the task was reopened and modified, this is the time, in the UTC time zone, when it happened.
* `isBenchmark` - Whether or not the task was marked as benchmark. [More on benchmarks here](../../core-concepts/benchmarks.md).
* `benchmark` - If the task was not marked as benchmark, but another task in the same asset was, the percentage by which the task is similar to the benchmark, with 0 being completely dissimilar and 100 being identical.
* `issues` - Issues opened in the task, if any.
* `taskId` - Unique alphanumeric ID assigned to the labeling task.
* `objects` - List of objects, if any, created within the labeling task. [More on objects as they appear in the AAF here](objects.md).
* `classifications` - List of classifications, if any, created within the labeling task.
* `relations` - List of relations, if any, created within the labeling task.

### Sample Task

```json
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
```
