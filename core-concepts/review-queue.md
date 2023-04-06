---
description: Order in which assets are shown to labelers on Ango Hub.
---

# Review Queue

The review queue is the list of [tasks](tasks.md) to be shown to reviewers, in order.

## The Review Queue in Ango Hub

### Using the Review Queue

From the dashboard, click on the _Start Reviewing_ button on the top right of the screen:

<figure><img src="../.gitbook/assets/image (331).png" alt=""><figcaption></figcaption></figure>

You will be shown the first task that is available for you to review. No further action is necessary.

Once you have [reviewed the task](reviewing.md), you will be shown the next available review task.

### Properties of the Review Queue

* Reviewers cannot review tasks they have labeled themselves. They will be shown the next available task in the queue.
* Each project has one common review queue. When reviewers open a new task, they pick from the top of the queue the first task that is available to them.
* By default, all tasks that have been labeled become automatically part of the review queue.
* Tasks that have been assigned to review to user X (for example, X is currently reviewing them) will be unavailable to Y. Y will be given the next task in the queue that is available to them.

Whenever users press on the _Start Reviewing_ button on the top-right corner of the dashboard, they are shown the first task in the review queue. When they complete reviewing, they pick another task from the top of the queue, and so on.

### Customizing the Review Queue

You may want your reviewers to only review assets with a consensus score below 80%. Or, to only review tasks labeled by a specific labeler. You can with Review Queue Filters.

To filter your review queue, go to the _Settings_ tab of your project, then to the _Quality_ section and lastly click on _Configure Review:_

<figure><img src="../.gitbook/assets/image (146).png" alt=""><figcaption></figcaption></figure>

You will be shown a dialog from which you can set up a filter. The filtered review queue is shown on screen. Once you are done, click on _Save_ and reviewers in your project will be able to only review tasks in the list you have created.

<figure><img src="../.gitbook/assets/image (109).png" alt=""><figcaption></figcaption></figure>

### Read More

{% content-ref url="reviewing.md" %}
[reviewing.md](reviewing.md)
{% endcontent-ref %}
