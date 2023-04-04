---
description: Overview of the Bounding Box labeling tool in Ango Hub
---

# Bounding Box

The bounding box labeling tool allows you to draw a box around an object or point of interest in an image. It also allows you to perform OCR on the area marked by the box.

![](<../../.gitbook/assets/image (247).png>)

## How to add a Bounding Box tool to your project <a href="#how-to-add-a-bounding-box-tool-to-your-project" id="how-to-add-a-bounding-box-tool-to-your-project"></a>

From the project’s _Settings_ tab, enter the _Label Set_ section.

Click on _Add Category_. From the list that appears, click on _Bounding Box_.

A new row will appear named _Bounding Box_. Click on it to expand it.

<figure><img src="../../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>

**Schema ID**: A unique ID which identifies this class in your project.

**Title:** The name of your class.

**Required:** Whether or not annotators have to add at least one instance of this class in order to submit their annotation task.

**Targeted OCR**: By enabling this, you will be able to perform OCR and get the OCR results in the exports for the areas highlighted by the bounding boxes belonging to this class.

If you would like to ask labelers further questions, for example, if you want to show a further _radio_ after drawing the bounding box, click on _Add Classification_ and add a further question. [More on nested questions here](nested-classifications.md).

### How to Draw a Bounding Box <a href="#how-to-draw-a-bounding-box" id="how-to-draw-a-bounding-box"></a>

Click on the image where you’d like the bounding box to start. Click again where you’d like the bounding box to end.

![](<../../.gitbook/assets/image (272).png>)

After creating the box, you can change its size by selecting it by clicking it, then dragging on its points. You can drag the entire bounding box by selecting it then dragging it with the mouse cursor.

## Perform OCR on the contents of the bounding box

Hub allows you to perform OCR on the contents of bounding boxes, both single and in bulk.

To do so, when adding your bounding box class to your project, enable the _Targeted OCR_ toggle as mentioned [in this section](bounding-box.md#how-to-add-a-bounding-box-tool-to-your-project).

### On a Single Bounding Box

Once you are in the labeling editor, draw a bounding box over the text you'd like to perform OCR on. Then, right-click on the box and expand the context menu. This is what you should see:

<figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

Click on the![](<../../.gitbook/assets/image (7) (1) (1).png>)button to perform OCR on the area highlighted by the box. The OCR results will appear in the context menu, together with how confident our OCR module is about the OCR results:

<figure><img src="../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

### On Multiple Bounding Boxes <a href="#differences-between-bounding-box-and-polygon" id="differences-between-bounding-box-and-polygon"></a>

In the labeling editor, press _Shift_ and click on the bounding boxes you'd like to perform OCR on. Once you have selected all boxes, right click on any one of them and click on _Run OCR_.

To see the OCR results, right-click on a box and expand the context menu that appears. Alternatively, expand the rows in the _Objects_ section in the lower-left corner of the UI.
