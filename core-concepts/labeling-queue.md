---
description: Order in which assets are shown to labelers on Ango Hub.
---

# Labeling Queue

The labeling queue is the list of [tasks](tasks.md) that are distributed to labelers, in order.

## The Labeling Queue in Ango Hub

### Using the Labeling Queue

From the dashboard, click on the _Start Labeling_ button on the top-right:

<figure><img src="../.gitbook/assets/image (129).png" alt=""><figcaption></figcaption></figure>

You will be shown the first labeling task that is available to you from the labeling queue. Once you label it and click on _Submit_, you will be shown the next, and so on.

{% hint style="info" %}
You may choose to label a certain task without following queue order by going to the _Task_ tab and clicking on any task, or by clicking on a circle under the _Labels_ column in the _Assets_ tab.

Doing so does not invoke the labeling queue, and the _Submit_ button will not be available to you. Instead, you will see the _Save_ button. This is because labeling and saving the asset will not move you forward one task. Essentially, you will only edit that one particular task.
{% endhint %}

### Properties of the Labeling Queue

* The task at the top of the queue is the task that will be shown next to labelers in the project.
* Each project has only one labeling queue. When labelers open a new task, they pick from the top of the queue the first task that is unassigned or assigned to them.
* All tasks created with a status of _To-Do_ become automatically part of the queue.
* Tasks get added to the bottom of the queue as they are created. Thus, the queue is ordered by task creation time, first in first out.
* Tasks that have been assigned to user X (for example, X is currently labeling them) will be unavailable to Y. Y will be given the next task in the queue that is unassigned or assigned to him.

Whenever users press on the _Start Labeling_ button on the top-right corner of the dashboard, they are shown the first task in the labeling queue. When they complete labeling and press on _Submit_, they pick another task from the top of the queue, and so on.

{% hint style="info" %}
It is not currently possible to filter or alter the labeling queue like you can with the review queue.
{% endhint %}

### See Also

{% content-ref url="labeling-core-concept.md" %}
[labeling-core-concept.md](labeling-core-concept.md)
{% endcontent-ref %}

{% content-ref url="tasks.md" %}
[tasks.md](tasks.md)
{% endcontent-ref %}
