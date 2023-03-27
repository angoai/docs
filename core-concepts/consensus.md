---
description: >-
  You can have the same asset be labeled by more than one annotator at the same
  time, and have Ango Hub calculate how much they agree with one another.
---

# Consensus

You may choose to have the same [asset](assets.md) be labeled by more than one annotator at the same time.

Ango Hub, then, will calculate how similar their annotations are to one another, and come up with what we call the "consensus score". Assets with a high consensus score are likely to have been labeled correctly.

You can then use this consensus score in your workflows: for example, you can have your reviewers only review assets with a low consensus score, among others.

### Labeling Tools for which Consensus is Available

* Bounding Box
* Polygon
* PDF Area Tool
* Entity
* Top-Level Classifications

{% hint style="warning" %}
Labeling tools for which consensus calculation is not available will not count towards and will not affect the consensus score.

Nested classifications are also not counted, only the first (top-level) classifications are.

For example, if you have a project with both bounding boxes and polylines, the resulting consensus will only be calculated taking bounding boxes into consideration.

Also, if you have a bounding box project in which labelers need to answer questions nested under the bounding boxes (e.g. vehicle type), only the size and position of the boxes will be taken into consideration, as nested classifications do not count towards consensus.
{% endhint %}

### How to Set Up Project-Wide Consensus

When creating a new project, in the _Quality Settings_ step, ensure you toggle _Consensus_ on and pick how many labelers should annotate the same asset.

<figure><img src="../.gitbook/assets/image (318).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
While consensus can be changed later, from the _Quality_ section of the _Settings_ tab, we recommend setting it up from the start.

This is because assets that have already been uploaded to the project before the consensus change will not be affected by it.

For example, if you upload 5 assets with a consensus of 2 and then change it to 3, those first 5 assets will retain their consensus of 2.

It is possible to manually add or remove consensus to assets but it is a manual operation in which assets need to be selected one by one from the UI.
{% endhint %}

If you selected a consensus of 4, for example, from this point on, whenever you upload an asset, four labeling tasks will be created along with it.

What this means is that the asset will be placed on the [labeling queue](labeling-queue.md) four times, however in such a way that the same labeler can never label the same asset twice.

Once you set up consensus, no further action is required from you, as the tasks are automatically assigned first-come-first-serve to labelers.

### Viewing Consensus

#### Project-wide

You can see the general, project-wide consensus distribution right from the project dashboard, in the _Consensus DIstribution_ section:

<figure><img src="../.gitbook/assets/image (387).png" alt=""><figcaption></figcaption></figure>

You can also drill down and only show the consensus distribution for a specific labeling tool by selecting it from this dropdown:

<figure><img src="../.gitbook/assets/image (359).png" alt=""><figcaption></figcaption></figure>

#### For each asset

You can also see each asset's consensus score, and you can examine the annotations of each individual labeler and quickly compare them, to pinpoint exactly what their differences are.

From the _Assets_ tab, you can see each asset's consensus score in the _Consensus_ column. (1)

Under the _Labels_ column, you can see each label created by an annotator. For example, in the screenshot below, each asset has been annotated by 4 labelers. (2) Their initials are shown in each circle, and clicking on a circle will open that labeler's annotations.

{% hint style="info" %}
For more information on each labeling task, hover over a circle to see the labeler's full name and more.
{% endhint %}

<figure><img src="../.gitbook/assets/image (362).png" alt=""><figcaption></figcaption></figure>

Once you click on a circle, you are shown that labeler's annotations. From the top of the screen, click on different circles (1) to see different labelers' annotations.

<figure><img src="../.gitbook/assets/image (324).png" alt=""><figcaption></figcaption></figure>

### Manually Adding Consensus to an Asset

You may only need to check consensus for a limited number of assets, without resorting to project-wide consensus. It is possible to add and remove label tasks to an asset manually.

#### Adding a Label Task to an Asset

From the _Assets_ tab, click on the three dots at the right of the row of the asset for which you wish to add the label task. Then, click on _Add Label Task_.

<figure><img src="../.gitbook/assets/image (326).png" alt=""><figcaption></figcaption></figure>

A new label task will be created. This means that with the exception of the labeler who has already annotated the asset, when a project member clicks on _Start Labeling_, they will be shown this asset.

#### Removing a Label Task from an Asset

Right-click on the circle representing the label task you'd like to remove, and click on _Delete_.

![](<../.gitbook/assets/image (388).png>)



### How Consensus is Calculated

#### Classifications

Let `questionCount` be the total number of classification questions in the project, and `taskCount` the total number of tasks assigned to an asset.

We calculate `x`, the single-question consensus for a single task as `(sameAnswers / (taskCount - 1))`, where `sameAnswers` is the count of answers that are equal to one another, current one excluded.

We repeat the above calculation for all tasks in the asset, to calculate the final result represented as Σ(x) below.

We calculate `y`, the overall consensus on a single question (classification) as `(∑(x) / taskCount)`.

We repeat the above calculation for all questions in the asset, to get to the final result represented as Σ(y) below.

The final consensus score, then, is calculated as `∑(y) / questionCount`.

#### Objects (Bounding Box, Polygon, PDF Area)

We calculate consensus for objects using the Intersection over Union (IoU) method.

We compare objects with one another to generate their IoU scores. If some annotations are completely separate, for example, with not even a pixel in common, their IoU score would be 0. If they overlapped completely, their score would be 100.

We then average the IoU scores of all annotation to calculate the final consensus score.
