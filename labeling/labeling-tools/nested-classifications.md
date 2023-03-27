---
description: Overview of the Nested Classifications labeling tool in Ango Hub
---

# Nested Classifications

Ango Hub allows annotators to answer multiple, nested questions regarding individual labels.

![](<../../.gitbook/assets/image (471).png>)

In the example above, we ask annotators to draw a polygon. Then, they answer questions related to the polygon they’ve just drawn. Each question’s answer determines which question will be asked next.

Here, if annotators select the “clothing” answer, they will be shown a question asking what type of clothing it is. If then they select “shirt” they will be asked the shirt’s gender, and so on.

## Setting Up Nested Classifications on Ango Hub <a href="#how-to-nest-classifications-in-your-project" id="how-to-nest-classifications-in-your-project"></a>

From the project’s _Settings_ tab, enter the _Label Set_ section.

Click on the label on which you’d like to ask nested questions. In our example, we expand our “Vehicle” bounding box.

![](<../../.gitbook/assets/image (310).png>)

Click on the blue _Add Classification_ button towards the bottom, and select the type of classification you need. ([More on classification in Ango Hub](classification-tools/).) In our case, we will select a Radio.

{% hint style="info" %}
If you are adding a classification to an existing classification tool, you will be asked to pick when this new classification will be shown.
{% endhint %}

{% hint style="info" %}
The _Add Classification_ button will not appear for classifications if no options have been added.
{% endhint %}

![](<../../.gitbook/assets/image (303).png>)

A new labeling tool will appear. Fill up its title and description as before, and add options if available.

![](<../../.gitbook/assets/image (260).png>)

From here, if you click on _Add Classification_ again, you can nest a further question. For example, we can show annotators a free text tool if they answer “Other.”

![](<../../.gitbook/assets/image (240).png>)

As with all other label tools, enable the _Required_ toggle if you want to force labelers to create a bounding box for each asset. When the toggle is disabled, labelers will be able to save and move to the next asset without creating the bounding box.

### How to Answer Nested Questions <a href="#how-to-answer-nested-questions" id="how-to-answer-nested-questions"></a>

In the [labeling editor](../labeling-editor-interface/), right-click on the annotation where you’d like to answer the nested questions. Audio, image, PDF, and Text (NER) all support this functionality.

A contextual menu will appear. Clicking on it will expand the questions if available.

![](<../../.gitbook/assets/image (246).png>)

It is also possible to answer questions from the “Objects” panel in the same way.

![](<../../.gitbook/assets/image (269).png>)
