---
description: Reset labeling tasks and put them back in the labeling or reviewing queue.
---

# Re-queuing

Once a [labeling task](tasks.md) is created, it enters the [labeling queue](labeling-queue.md). This means that it can be assigned to any labeler who clicks on _Submit_ or _Start Labeling_. Once it has been labeled, the same happens for the [reviewing queue](review-queue.md).

Ango Hub provides you with ways to reset your labeling task in such a way that it enters the labeling or reviewing queue anew.

## How to re-queue a task

This section will show you how to open the re-queue dialog. The sections after that will talk about each option in the re-queue dialog.

### Re-queue multiple tasks from the _Tasks_ tab

Enter the _Tasks_ tab (1), then toggle the checkbox (2) next to each task you wish to re-queue. Then, from the _Item_ dropdown click on _Re-queue_ (3). The re-queue dialog will open.

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

### Re-queue a single task from the labeling editor

Enter the labeling editor for the task you wish to re-queue. From the three dots (1) in the top-left corner, click on _Re-queue_ (2). The re-queue dialog will open.

<figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

## Re-queue a task for labeling

You can re-queue a task in such a way that it will be labeled again, either by the same person or by a random annotator.

Open the re-queue dialog as shown in [the previous section](re-queuing.md#how-to-re-queue-a-task).

From the re-queue dialog, choose _Send Back to Label Queue._

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

**Remove Annotations**: Deletes the annotations in the task(s) selected. This operation cannot be reversed.

**Remove Labeler**: Removes the task assignee. If you do not remove the assignee, the task will be re-queued, but it will only be able to be labeled by the assignee. If you do remove it, it will be assigned to the first labeler who comes across it when labeling.

## Re-queue a task for reviewing

You can re-queue a task in such a way that it will be reviewed again, either by the same person or by a random reviewer.

Open the re-queue dialog as shown in [the previous section](re-queuing.md#how-to-re-queue-a-task).

From the re-queue dialog, choose _Send Back to Review Queue._

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

**Remove Reviewer**: Removes the task assignee. If you do not remove the assignee, the task will be re-queued, but it will only be able to be reviewed by the reviewer who has reviewed it earlier. If you do remove it, it will be assigned for review to the first reviewer who comes across it.
