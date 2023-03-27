---
description: >-
  Page detailing what General Mode is and why you might want to annotate videos
  using it on Ango Hub.
---

# Labeling Videos in General Mode

General Mode is a way of labeling videos on Ango Hub ideal for classifying the entire video, rather than placing annotations on each frame. Which mode a video is in is determined during asset import.

By default, when importing videos, Hub assumes you wish to label each frame individually. The entire UI is centered on this proposition, and allows you to easily move between frames and place annotations on each. This is determined when, in _Advanced Configs_, the Frame Step value is 1.

<figure><img src="../../../.gitbook/assets/image (325).png" alt=""><figcaption></figcaption></figure>

While this behavior is ideal in most cases, there are times when the entire video, not single frames, need to be classified. We have a special mode dedicated to this use case which we call General Mode.

### How to enable General Mode for videos

During upload, set the Frame Step value to 0 from _Advanced Configs_.

### Properties of General Mode

In General Mode,

* you cannot place annotations on the video itself, such as bounding boxes, points, polygons, etc.
* annotations are limited to asset-level [classifications](../../labeling-tools/classification-tools/)
* since Ango Hub does not have to load each frame individually and prepare it for annotation, videos load significantly faster, and videos can be of nearly limitless size, length, and resolution while maintaining great performance

### General Mode FAQs

#### Is it possible to switch a video's mode after import?

No, a video's mode is determined during import. To change a video's mode, delete it and import it again with the appropriate _Frame Step_ value.

**Is it possible to upload videos using the Cloud Import method in General Mode?**

Yes, simply set the Frame Step value to 0 before uploading your JSON.

**Is it possible to determine each video's Frame Step directly from the JSON itself?**

Not at the moment, but it is in our development pipeline.
