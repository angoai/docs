---
description: Overview of data management in Ango Hub
---

# Data in Ango Hub

At its core, Ango Hub is a platform that receives data as input (the data to be labeled) and produces data as output (the annotations).

It is useful to draw the distinction between assets and annotations, the two main data types within Ango Hub:

| Data Type          | Definition                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Asset              | <p>An <strong>asset</strong> is a piece of data that needs to be or has been annotated.</p><p>Examples of assets are:</p><ul><li>An image file</li><li>An audio file</li><li>A text file</li><li>A PDF file</li></ul><p><a href="../../core-concepts/assets.md">More on assets in Ango Hub</a>.</p>                                                                                                       |
| Annotation (label) | <p>Assume labelers need to draw a rectangle (a box) around cars in your pictures. Each rectangle the labeler creates is an individual <strong>annotation</strong> or <strong>label</strong>.</p><p>Examples of annotations are:</p><ul><li>Bounding boxes</li><li>Polygons</li><li>Points</li><li>Classification</li></ul><p><a href="../../labeling/labeling-tools/">More on labels in Ango Hub</a>.</p> |

When dealing with data in Ango Hub, you will first import [assets](../../core-concepts/assets.md). If you have any, you can also import annotations you already have. Once the labeling tasks are done, you will export the labels from Ango Hub.

The following pages explain the process of importing and exporting data to and from Ango Hub:

* [Importing and Exporting Annotations](../importing-and-exporting-annotations/)
* [Importing Assets](../importing-assets/)
