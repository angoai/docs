---
description: Overview of the Text data annotation tool in Ango Hub
---

# Text

The text labeling tool allows you to ask labelers open-ended questions.

![](<../../../.gitbook/assets/image (254).png>)

### How to add a Text tool to your project <a href="#how-to-add-a-text-tool-to-your-project" id="how-to-add-a-text-tool-to-your-project"></a>

From the project’s _Settings_ tab, enter the _Label Set_ section.

Click on _Add Category_. From the list that appears, click on _Text_.

A new row will appear named _Text_. Click on it to expand it.

![](<../../../.gitbook/assets/Screen Shot 2022-10-24 at 09.35.17.png>)

### Text Tool Options

**Schema ID**: The unique ID assigned to the tool.

**Title**: The name of your labeling tool.

**Required**: If you enable this toggle, labelers will be required to answer this field before saving.

**Column Field**: If you enable this toggle, a table will appear at the top of the labeling editor and this tool will become the title of one of the columns. For more on table labeling look [here](../relation-tools/table.md).

**Regex Validation**: If you enter a regular expression in this field (without the initial and final `\` slashes), labelers' answers to this field will have to match the regex being input before saving.

**Frame-specific**: If you enable this toggle, the answer to this classification will only be valid for one frame (in videos and multi-frame images/DICOMs) instead of the whole asset.

Once you have selected your options, click on _Save_ at the bottom to save your changes.
