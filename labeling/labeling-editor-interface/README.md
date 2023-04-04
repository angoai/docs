---
description: Overview of the labeling interface on Ango Hub.
---

# Labeling Editor Interface

Ango Hub has labeling editors for each of the supported formats: audio, image, DICOM video, PDF, and text (NER).

Even though the data types supported by Ango Hub are all different, we designed our labeling editors to be as similar to one another as possible. This way, once an annotator has learned how to use one, they will be able to quickly switch to the other, without having to spend time retraining.

In this article, we will go through the features in common between all editors. At the bottom of this article are links to documentation pages for more details on each of the editors.

The following is an overview of the editor’s interface.

![](<../../.gitbook/assets/image (137).png>)

## Overview of the Labeling Editor on Ango Hub

### Left Sidebar

#### Tools (when available)

At the top of the left sidebar is the list of all labeling tools available in the project. Bounding boxes, polygons, points, and entities, for example, are all labeling tools.

![](<../../.gitbook/assets/image (438).png>)

Tools of different types can be present in the same project. To annotate, the labeler clicks on the tool from this section then clicks on the asset, where the label needs to be placed.

#### Questions (when available)

In the middle of the sidebar are the top-level classification tools for this project.

![](<../../.gitbook/assets/image (89).png>)

If created from the _Label Set_ section of the _Settings_ tab, classifications will be shown here. From this section, annotators can categorize the asset shown, with radio buttons, dropdowns, free text, and more.

#### Objects

Below the classification section is a list of all annotations (objects) placed on the current asset.

![](<../../.gitbook/assets/image (156).png>)

As the annotator adds labels to the asset, they will be shown in this list. The <img src="../../.gitbook/assets/image (295).png" alt="" data-size="line"> “eye” icon next to _Objects_ allows you to hide all labels on the screen.

If the label has a nested question, by clicking on it in the list, you can expand it.

![](<../../.gitbook/assets/image (466).png>)

The <img src="../../.gitbook/assets/image (155).png" alt="" data-size="line"> eye icon allows you to hide the label from the asset. You can also use the shortcut H while hovering over an annotation to hide it. To unhide all annotations, press Shift + H.

The <img src="../../.gitbook/assets/image (224).png" alt="" data-size="line"> trash can deletes it. If present, nested labels will be shown below. In the example above, we ask the labeler what kind of vehicle they have just labeled with the bounding box tool.

Clicking on the <img src="../../.gitbook/assets/image (300).png" alt="" data-size="line"> three dots will open a submenu:

![](<../../.gitbook/assets/image (166).png>)

#### <img src="../../.gitbook/assets/image (157).png" alt="" data-size="line"> Change category

If in your project you have more than one of the same tool, you can quickly change the label’s category from here. If we had another bounding box tool called “tree”, for example, we would be able to change this label’s category from “vehicle” to “tree.”

{% hint style="warning" %}
It is not possible to change an annotation to a label of a different type. (for example, a bounding box into a polygon.)
{% endhint %}

{% hint style="info" %}
Another way to quickly change a label's category is to hover over it with the mouse cursor and pressing Alt + the new category's keyboard shortcut.
{% endhint %}

#### <img src="../../.gitbook/assets/image (237).png" alt="" data-size="line"> Copy Object ID

Each object (annotation) has a unique ID. Clicking this button will copy the annotation's ID to the clipboard.

#### <img src="../../.gitbook/assets/image (239).png" alt="" data-size="line"> Lock

A locked label cannot be edited. The lock function is particularly useful when [importing labels](../../data/importing-and-exporting-annotations/importing-annotations/), if there are labels you'd like the annotators not to change.

#### <img src="../../.gitbook/assets/image (277).png" alt="" data-size="line"> Set Flag

You can flag labels. The flag does not have a particular meaning out-of-the-box. The flag function is particularly useful when performing post-labeling QA checks through our [API](broken-reference).

For example, imagine you have a tool that automatically detects abnormal labels, connected to our platform using our API. You can have this tool flag all abnormal labels for manual review.

#### Quick Object Scrolling

You can quickly move between objects in the editor by hovering over an object such that it is selected, and then by pressing on Shift + Up or Shift + Down to navigate between objects. The selected object will automatically be shown in the middle of the screen and the zoom level will be accommodated to better view the object.

#### Reset and Submit/Save

At the bottom of the sidebar, we find the _Reset_ and _Submit/Save_ buttons.

![](<../../.gitbook/assets/image (139).png>)

_Reset_ undoes all changes made, restoring the state found when the asset was first opened.

_Save_ saves the annotations made on the asset. If the button shows instead the word _Submit_, changes will be saved and you will be brought to the next unlabeled asset.

{% hint style="warning" %}
There is no autosave.

If you try to leave the page without saving, you will be asked to save before exiting.
{% endhint %}

### Top bar

![](<../../.gitbook/assets/Screen Shot 2021-10-07 at 10.45.29.png>)

#### Project Navigation

On the left-hand side are links to navigate between projects and within the current project.

![](<../../.gitbook/assets/image (222).png>)

The <img src="../../.gitbook/assets/image (461).png" alt="" data-size="line"> _Ango Logo_ opens your project list.\
The <img src="../../.gitbook/assets/image (420).png" alt="" data-size="line"> _Home_ opens the current project’s dashboard.\
The <img src="../../.gitbook/assets/image (221).png" alt="" data-size="line"> _Back_ button brings you back one page.

#### Asset Tasks (Reviewer and Project Owner Only)

![](<../../.gitbook/assets/image (280).png>)

The number of circles appearing in the top bar is the number of labeling tasks associated with the asset. In the picture above, for example, the current asset was labeled three times.

Hovering over a circle will show detailed information about each of the labeling tasks. Clicking on a circle will open the task.

A green checkmark <img src="../../.gitbook/assets/image (264).png" alt="" data-size="line"> indicates that the task was completed.

A yellow star <img src="../../.gitbook/assets/image (159).png" alt="" data-size="line"> indicates that the task has been marked as a benchmark. [More on benchmarks here](../../core-concepts/benchmarks.md).

A blue label <img src="../../.gitbook/assets/image (128).png" alt="" data-size="line"> indicates that the labels in the task were created outside of Ango Hub, and have been imported. [More on importing annotations here](../../data/importing-and-exporting-annotations/importing-annotations/).

A grey circle <img src="../../.gitbook/assets/image (422).png" alt="" data-size="line"> indicates that the task has not been completed, thus, it will not appear in the [export](../../data/importing-and-exporting-annotations/exporting-annotations.md).

#### Navigation Arrows

![](<../../.gitbook/assets/image (286).png>)

The arrows allow users to move back to the previous asset, and forward to the next asset.

The navigation arrows are only shown if the current task was opened by following an internal link from within the platform. Directly opening a task from an URL will prevent the arrows from showing.

#### Right-Hand Side

![](<../../.gitbook/assets/image (232).png>)

The <img src="../../.gitbook/assets/image (267).png" alt="" data-size="line"> _Keyboard_ icon opens a panel showing all available keyboard shortcuts.\
The <img src="../../.gitbook/assets/image (111).png" alt="" data-size="line"> _Bell_ icon shows the user’s notifications.\
The <img src="../../.gitbook/assets/image (209).png" alt="" data-size="line">circle allows the user to enter their profile and log out.

### Toolbar

![](<../../.gitbook/assets/Screen Shot 2021-10-07 at 10.47.43.png>)

Starting from the left-hand side,

#### Submenu (Reviewer, Manager, and Project Owner only)

The _three dots_ open a submenu with a number of options:

![](<../../.gitbook/assets/image (204).png>)

__<img src="../../.gitbook/assets/image (108).png" alt="" data-size="line">_Set as benchmark_ sets the current task as benchmark.

__<img src="../../.gitbook/assets/image (233).png" alt="" data-size="line"> _Requeue_ resets the current task and puts it back into the labeling or reviewing queue. (e.g., it will be shown to labelers and reviewers again)

__<img src="../../.gitbook/assets/image (143).png" alt="" data-size="line">_Delete_ deletes the current task.

__<img src="../../.gitbook/assets/image (291).png" alt="" data-size="line">_Change Assignee_ changes the assignee of the current task. Practically, it changes the name of the person who has labeled the task.

#### Left toolbar

![](<../../.gitbook/assets/image (115).png>)

1. <img src="../../.gitbook/assets/image (172).png" alt="" data-size="line"> Export the current task (_coming soon_)
2. <img src="../../.gitbook/assets/image (217).png" alt="" data-size="line"> Delete all annotations in the current task
3. <img src="../../.gitbook/assets/image (195).png" alt="" data-size="line"> Copy all annotations from the current task
4. <img src="../../.gitbook/assets/image (187).png" alt="" data-size="line"> Paste all annotations to the current task
5. <img src="../../.gitbook/assets/image (110).png" alt="" data-size="line"> Plugins.

#### Right toolbar

![](<../../.gitbook/assets/image (150) (1).png>)

1. <img src="../../.gitbook/assets/image (263).png" alt="" data-size="line"> Mark the current task as _Accepted_ (Project Owner, Manager, and Reviewer only)
2. <img src="../../.gitbook/assets/image (304).png" alt="" data-size="line"> Mark the current task as _Fixed_ (Project Owner, Manager, and Reviewer only)
3. <img src="../../.gitbook/assets/image (430).png" alt="" data-size="line"> Mark the current task as _Rejected_ (Project Owner, Manager, and Reviewer only)
4. <img src="../../.gitbook/assets/image (416).png" alt="" data-size="line"> Set the current task as sample (Project Owner, Manager, and Reviewer only)
5. <img src="../../.gitbook/assets/image (153).png" alt="" data-size="line"> Create an Issue on a specific location on the asset (Image, Video, and Text only)
6. <img src="../../.gitbook/assets/image (227).png" alt="" data-size="line"> Flag the current task.
7. <img src="../../.gitbook/assets/image (342).png" alt="" data-size="line"> Star the current task.

#### Spot Issues

Clicking on the bubble icon on the right side of the toolbar will turn the cursor into an issue bubble. When in this mode, click on the asset. An issue will be placed at your cursor's position.

![](<../../.gitbook/assets/image (414).png>)

To submit the issue, type into the box and press Enter.

{% hint style="info" %}
Spot issues are not available for all file types. Currently, Image, Video, DICOM, and Text support Spot Issues.
{% endhint %}

### Right Sidebar

![](<../../.gitbook/assets/image (135).png>)

#### Issues

From the right sidebar, open the _Issues_ panel. This will show all issues present in the current task.

![](<../../.gitbook/assets/image (458).png>)

Users can type text in the _+ Create Issue_ field and press Enter to create issues, which will be sent as in-app notifications to task assignees, project owners, and project reviewers.

The user who created the issue, as well as reviewers and project owners, will be able to reply to the issue, resolve it, or delete it from the buttons on the right side of the panel.

#### Instructions

The _Instructions_ button opens a drawer showing labeling instructions for the current project, if present. Project owners can upload instructions as a PDF file from the project’s _Settings_ tab.

![](<../../.gitbook/assets/image (245).png>)

The buttons above the PDF allow the user to reset the zoom, zoom in and out, and to navigate between pages.

[More on instructions here](../../core-concepts/instructions.md).

#### Samples

The _Samples_ button opens a drawer showing all samples set in the project. [More on samples here.](../../core-concepts/samples.md)

![](<../../.gitbook/assets/image (456).png>)

Clicking on a sample in the list will open its related asset and description. Clicking on the _Arrow in box_ button in the sample will open an enlarged view of the sample:

![](<../../.gitbook/assets/image (412).png>)

#### Attachment

Clicking on _Attachment_ will open a drawer showing the attachment linked to the current asset, if available. [More on attachments here](./#attachment).

![](<../../.gitbook/assets/image (459).png>)

#### Task info

Clicking on _Task info_ will show information related to the current task.

![](<../../.gitbook/assets/image (406).png>)

### Assets drawer (Project Owner, Manager, and Reviewer only)

Clicking on the right-facing arrow on the left side of the screen will open the _Assets_ drawer.

![](<../../.gitbook/assets/image (460).png>)

The _assets drawer_ contains a list of all assets in the current project, together with their related information such as their status, consensus score, assignees, and more. Clicking on an item in the list will open the related asset.

From the top, clicking on <img src="../../.gitbook/assets/image (251).png" alt="" data-size="line"> will refresh the asset list. Clicking on _X_ will close the drawer. At the bottom, arrows and page numbers allow you to navigate the asset list.

### Labeling Settings

Clicking on the blue _Settings_ button on the bottom left of the editor will open a panel with a number of quick labeling settings.

Each data type has its own set of settings. This page will only go through those that are common to all data types. For more details on each data type's settings, visit its page, for example, [Image Labeling Editor](image-labeling-editor.md).

![](<../../.gitbook/assets/image (144).png>)

#### Fast Tool Selection

By default, after placing an annotation, the current labeling tool is deselected, and the annotator needs to click on a labeling tool again to place another annotation.

When this toggle is selected, placing annotations will not deselect the currently selected labeling tool, and the annotator can immediately place another one. The annotator can deselect the currently selected labeling tool by pressing _Esc_.

#### Fast Context Menu

When this setting is activated, right-clicking on an asset will automatically open the expanded version of the context menu, instead of opening the collapsed one.

#### Opacity, Brightness, Contrast

The _opacity, brightness, and contrast_ sliders apply to all annotations on screen.

#### Border Thickness

Changes the thickness of bounding boxes.

### Labeling editors in more depth <a href="#labeling-editors-in-more-depth" id="labeling-editors-in-more-depth"></a>

{% content-ref url="audio-labeling-editor.md" %}
[audio-labeling-editor.md](audio-labeling-editor.md)
{% endcontent-ref %}

{% content-ref url="image-labeling-editor.md" %}
[image-labeling-editor.md](image-labeling-editor.md)
{% endcontent-ref %}

{% content-ref url="pdf-labeling-editor.md" %}
[pdf-labeling-editor.md](pdf-labeling-editor.md)
{% endcontent-ref %}

{% content-ref url="text-ner-labeling-editor.md" %}
[text-ner-labeling-editor.md](text-ner-labeling-editor.md)
{% endcontent-ref %}
