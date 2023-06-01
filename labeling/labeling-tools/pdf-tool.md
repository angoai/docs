---
description: Overview of the PDF labeling tool in Ango Hub
---

# PDF Tool

The PDF labeling tool allows you to annotate text and arbitrary rectangular areas on PDF documents.

![](<../../.gitbook/assets/image (112).png>)

## How to add a PDF tool to your project <a href="#how-to-add-a-pdf-tool-to-your-project" id="how-to-add-a-pdf-tool-to-your-project"></a>

From the project’s _Settings_ tab, enter the _Label Set_ section.

Click on _Add Category_. From the list that appears, click on _PDF_.

A new row will appear named _PDF_. Click on it to expand it.

<figure><img src="../../.gitbook/assets/image (1) (3).png" alt=""><figcaption></figcaption></figure>

Give your PDF tool a title and description.

Enable the _Required_ toggle if you want to force labelers to create a PDF label for each asset. When the toggle is disabled, labelers will be able to save and move to the next asset without creating the PDF label.

If you would like to ask labelers further questions, for example, if you want to show a further _radio_ after placing a PDF tool, click on _Add Classification_ and add a further question. [More on nested questions here](nested-classifications.md).

## How to Label with the PDF Tool <a href="#how-to-label-with-the-pdf-tool" id="how-to-label-with-the-pdf-tool"></a>

From the _Tools_ panel on the left sidebar, select a _PDF_ labeling tool, marked with an A enclosed in a square.

![](<../../.gitbook/assets/image (169).png>)

With the _PDF_ tool selected, click and drag where you’d like the bounding box to be placed.

![](<../../.gitbook/assets/image (265).png>)

### OCR

{% hint style="info" %}
By default, targeted OCR only detects English. To change, add, or remove which languages should be detected in your project, head over to _Settings -> Quality_ to do so:

![](<../../.gitbook/assets/image (5).png>)
{% endhint %}

#### Single OCR

To perform OCR on the area you've just drawn, click on the area to select it, then right-click it and click on the ![](<../../.gitbook/assets/image (3) (3).png>)_OCR_ button to perform OCR.

After performing OCR, Hub will display how confident it is that the OCR results are correct.

<figure><img src="../../.gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>

#### Group OCR

To perform OCR on a group of annotations at once, hold _Shift_ then click on each annotation for which you'd like to perform OCR. Right-click on any one of them and click on _OCR._
