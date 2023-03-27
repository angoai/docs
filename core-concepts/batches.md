# Batches

Batches are a way to organize assets in categories.

Each asset can have multiple batches attached to them. Batches are optional to use, and by default, imported assets have no batch.

You can attach batches to assets to quickly find them later, to [assign](task-assignment.md) them all to a certain labeler, to filter performance reports by batch, and much more.

### How To Assign Batches to Assets on Import

When [importing assets](../data/importing-assets/) to Hub, be it [from your local machine](../data/importing-assets/asset-browser-import.md) or from [public](../data/importing-assets/asset-cloud-import.md)/[private cloud assets](../data/importing-assets/importing-private-cloud-assets-gcp.md), you may attach a batch directly during import.

To do so, after clicking on _Add Data_ in the _Assets_ tab, expand the _Advanced Config_ dropdown and add the batches you wish to attach.

If you have existing batches, they will show up here. You may also create new batches from this menu.

<figure><img src="../.gitbook/assets/image (314).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
You may also assign batches during upload when using our SDK. See [upload\_files\_cloud](../sdk/sdk-documentation.md#upload\_files\_cloud-project\_id-assets-integration\_id-batches) for more information.
{% endhint %}

### How to Assign Batches After Import

From the _Assets_ tab, toggle the checkmark next to the assets you wish to batch together (highlighted in green on the screenshot below). It may help to use the filters at the top of the list to narrow down your search.

<figure><img src="../.gitbook/assets/image (390).png" alt=""><figcaption></figcaption></figure>

You may click on the checkmark highlighted in red on the screenshot above to select all tasks in the current page.

{% hint style="warning" %}
Navigating to a different page of assets _will deselect_ the checkmarks you have toggled earlier. Your checkboxes are not kept in memory when navigating between asset pages.

The maximum number of assets you may batch this way at any one time is 1000. This is accomplished by selecting _1000/page_ from the bottom right corner of the page, then clicking on the _Select All_ checkmark highlighted in red on the screenshot above.
{% endhint %}

From the _Item Actions_ dropdown, click on _Set Batches_.

<figure><img src="../.gitbook/assets/image (335).png" alt=""><figcaption></figcaption></figure>

From the dialog that appears, you will be able to select the batches to add to the selected assets from a list of existing project batches.

{% hint style="info" %}
You may also assign batches after upload when using our SDK. See [assign\_batches](../sdk/sdk-documentation.md#assign\_batches-project\_id-asset\_ids-batches) for more information.
{% endhint %}

### Creating and Editing Batches

To create and edit existing batches, navigate to the _Settings_ tab and then to the _Batches_ section.

<figure><img src="../.gitbook/assets/image (339).png" alt=""><figcaption></figcaption></figure>

* To add a new batch, click on _Add new batch_.
* To rename an existing batch, click on the <img src="../.gitbook/assets/image (330).png" alt="" data-size="line">icon next to the name of the batch you wish to rename.
* To delete a batch, click on _Delete_ on the row of the batch to delete.

{% hint style="info" %}
Don't forget to click on _Save_ or your changes will be lost when navigating away from the page.
{% endhint %}

{% hint style="info" %}
You may also create batches after upload by using our SDK. See [create\_batch](../sdk/sdk-documentation.md#create\_batch-project\_id-batch\_name) for more information.
{% endhint %}
