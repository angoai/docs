---
description: Overview of the Tree Dropdown labeling tool in Ango Hub
---

# Tree Dropdown

The Tree Dropdown labeling tool allows you to ask labelers to pick leaves and trees from complex, nested tree structures.

<img src="../../../.gitbook/assets/image (374).png" alt="" data-size="original">

## The Tree Dropdown Labeling Tool in Ango Hub <a href="#how-to-add-a-multiple-dropdown-tool-to-your-project" id="how-to-add-a-multiple-dropdown-tool-to-your-project"></a>

### How to add a Tree Dropdown tool to your project <a href="#how-to-add-a-multiple-dropdown-tool-to-your-project" id="how-to-add-a-multiple-dropdown-tool-to-your-project"></a>

From the project’s _Settings_ tab, enter the _Label Set_ section.

Click on _Add Category_. From the list that appears, click on _Tree Dropdown_.

A new row will appear named _Tree Dropdown_. Click on it to expand it.

<figure><img src="../../../.gitbook/assets/image (367).png" alt=""><figcaption></figcaption></figure>

### Properties of the Tree Dropdown Tool

* **Schema ID**: A unique ID assigned to all instances of labeling tools on Ango Hub. You can use it when [importing labels for pre-labeling](../../../data/importing-and-exporting-annotations/importing-annotations/).
* **Title**: The title of the labeling tool you are creating. This will show up both in the editor for labelers to see, as well as in the final export.
* **Required**: Toggle this to make is to that labelers have to answer this classification before saving.
* **Frame-specific**: For video assets, determine whether the answer to this classification apply to the whole video or to each individual frame only. Toggling will make it frame-specific.
* **Show Dropdown**: Normally, trees are shown embedded within the classification tool and are immediately, fully visible to annotators. Toggling this option will make it so that to see the tree, annotators will have to click on an area, and as a result of the click the tree will show as a "dropdown". This can especially be useful for larger trees.

Normal "embedded" view:

![](<../../../.gitbook/assets/image (360).png>)

With "Show Dropdown" enabled:

![](<../../../.gitbook/assets/image (357).png>)

#### Adding Branches and Leaves

Click on _Configure_ from the label tool's options:

<figure><img src="../../../.gitbook/assets/image (351).png" alt=""><figcaption></figcaption></figure>

From the dialog that pops up, click on "Add Node" to add a new node stemming from the root:

<figure><img src="../../../.gitbook/assets/image (347).png" alt=""><figcaption></figcaption></figure>

To add a new children node stemming from a parent node, click on the "+" button next to the parent node.

<figure><img src="../../../.gitbook/assets/image (315).png" alt=""><figcaption></figcaption></figure>

You may rename nodes by clicking on the "pencil" button next to the node's name, entering the name, then pressing "Enter".
