---
description: >-
  Overview of the Single Relation relational data classification tool in Ango
  Hub
---

# Single Relation

The Single Relation labeling tool allows you to create a relation between two annotations.

![](<../../../.gitbook/assets/Screen Shot 2021-10-15 at 15.32.51.png>)



## How to add a Single Relation tool to your project <a href="#how-to-add-a-bounding-box-tool-to-your-project" id="how-to-add-a-bounding-box-tool-to-your-project"></a>

From the project’s _Settings_ tab, enter the _Label Set_ section.

Click on _Add Category_. From the list that appears, click on _Single Relation_.

A new row will appear named _Single Relation_. Click on it to expand it.

![](<../../../.gitbook/assets/Screen Shot 2021-10-15 at 15.31.25.png>)

Give your single relation tool a title and description.

Enable the _Required_ toggle if you want to force labelers to create a single relation for each asset. When the toggle is disabled, labelers will be able to save and move to the next asset without creating the single relation.

### How to Draw a Single Relation <a href="#how-to-draw-a-bounding-box" id="how-to-draw-a-bounding-box"></a>

Click on the label where you’d like the single relation to start. Click on the second label where you’d like the relation to end.

![](<../../../.gitbook/assets/Screen Shot 2021-10-15 at 15.32.51.png>)

After creating the relation, you can change its direction by clicking on the <img src="../../../.gitbook/assets/image (257).png" alt="" data-size="line"> small arrow inside the relation's box.

#### Single Relation Directions

<img src="../../../.gitbook/assets/image (218).png" alt="" data-size="line">**Forward**: the first label points at the second label.

<img src="../../../.gitbook/assets/image (452).png" alt="" data-size="line">**Backward**: the second label points at the second label.

<img src="../../../.gitbook/assets/image (116).png" alt="" data-size="line">**Bidirectional**: The labels point at each other.

### Differences between Single Relation and Tables <a href="#differences-between-bounding-box-and-polygon" id="differences-between-bounding-box-and-polygon"></a>

Single Relations are ideal in situations where there is a relatively small number of relations in an asset. This is because after a certain number of single relations have been created, the number of arrows can make it hard to perform further labeling.

For assets with a large number of relations, we recommend using the Tables tool.
