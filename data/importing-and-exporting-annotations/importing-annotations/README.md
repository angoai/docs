---
description: Overview of importing pre-labeled annotations into Ango Hub
---

# Importing Annotations

Ango Hub provides a way to import existing annotations to the platform. This can be useful if you are migrating from another tool or if you wish to import existing model outputs.

{% hint style="warning" %}
Your annotations will need to be converted to the Ango Hub Import Format. [More information on the format can be found at this link.](ango-hub-import-format.md)
{% endhint %}

## Importing Labels into Ango Hub <a href="#how-to-import-labels-into-ango-hub" id="how-to-import-labels-into-ango-hub"></a>

### How to Import Labels into Ango Hub <a href="#how-to-import-labels-into-ango-hub" id="how-to-import-labels-into-ango-hub"></a>

{% hint style="info" %}
Ensure all assets that will be pre-labeled have been added to the project.

Ensure all assets that will be pre-labeled have a status of _To Do_. Assets with status other than _To Do_ will not be pre-labeled.
{% endhint %}

First, convert your existing labels to the Ango Hub Import Format. [More information on the format here.](ango-hub-import-format.md)

From the Assets tab, click on the _Import_ button.

![](<../../../.gitbook/assets/Screenshot 2022-10-27 at 15.36.28.png>)

From the dialog that pops up, click on the dashed rectangle in the middle to open your system’s file explorer and pick an import file. Alternatively, drag and drop the import file on the dashed rectangle.

<figure><img src="../../../.gitbook/assets/image (333).png" alt=""><figcaption></figcaption></figure>

If the import was successful, the dialog will close and your assets will gain a blue “label” mark to indicate that they have been pre-labeled.

![](<../../../.gitbook/assets/image (250).png>)

{% hint style="warning" %}
Labeling tasks annotated this way will not immediately have a status of "Completed." They will, therefore, not appear in your export. Only labeling tasks with a status of "Completed" are included in the export.

[More information on tasks here.](../../../core-concepts/tasks.md)
{% endhint %}
