---
description: Overview of labeling tasks in Ango Hub
---

# Tasks

Every labeling project is broken down into [assets](assets.md), then individual tasks.

An asset is each file that gets uploaded to Ango Hub. A task is each time an annotator labels an asset.

### Creating and Deleting Tasks <a href="#creating-and-deleting-tasks" id="creating-and-deleting-tasks"></a>

Tasks are created automatically when assets are added.

Ango Hub by default creates one labeling task for each asset, but this behavior can be changed from the _Quality_ section of the _Settings_ tab.

If a [consensus](consensus.md) of four has been set in the _Quality_ tab, for example, four labeling tasks will be created for each asset imported.

{% hint style="warning" %}
When an asset is deleted, the tasks assigned to the asset are deleted as well. Importing the asset again will not restore the tasks that have been deleted this way.
{% endhint %}

Tasks are shown in their own _Tasks_ tab, and under the _Labels_ column in the _Assets_ tab.

![](<../.gitbook/assets/Screen Shot 2021-11-16 at 14.41.26.png>)

### Creating and Deleting Tasks Manually <a href="#creating-and-deleting-tasks-manually" id="creating-and-deleting-tasks-manually"></a>

Administrators can manually add and remove labeling tasks from individual assets.

To manually add a new labeling task to an asset:

1. Open the _Assets_ tab.
2. On the row of the asset where you wish to add the labeling task, click on the three dots on the right-hand side.
3. Click on “Add Label Task”.

![](<../.gitbook/assets/image (177).png>)

To delete a labeling task, from the _Assets_ tab, right-click on the circle representing the task you wish to delete and click on _Delete_.

{% hint style="warning" %}
Deleting tasks is a destructive and irreversible action.
{% endhint %}

### Release a Task from a Labeler

Once a user has opened a task, the task will be assigned to that user.

What this means is that when others click on _Start Labeling_, they will not be shown this task.

It might occasionally be necessary to release/unassign a labeler from a task. To do so, simply right-click on the task circle and click on "Requeue."

<figure><img src="../.gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>

This will completely reset the task and place it back in the labeling queue.
