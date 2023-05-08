# Managing the Project Ontology

You can set and manage the ontology of your project by navigating to your project's settings, then to the _Category Schema_ section.

## Managing Classes through the UI

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

### Adding new classes

You can add a new labeling tool (e.g., a new class) to your project by clicking on the _Add Category_ button, then selecting the type of tool you'd like to add.

<figure><img src="../.gitbook/assets/image (7) (1) (2).png" alt=""><figcaption></figcaption></figure>

There is no limit to how many labeling tools you may have in your project.

### Editing existing classes

Once you have added classes to your project, each of your classes will be represented by a row in the _Category Schema_ section of your project.

To edit a class, click on its row and the row will expand to show the class's details:

<figure><img src="../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

All labeling tools share three common properties:

* **Schema ID**: A unique identifier for your class.
* **Title**: What your class should be known as (e.g. `vehicle`, `person`, `lesion`)
* **Required**: Whether or not labelers are required to use this class before submitting their annotations.
  * For classifications, annotators will not be able to submit their labeling task without having answered it.
  * For visual tools (e.g. bounding box, polygon), annotators will not be able to submit their annotations without adding at least one annotation using the class specified.

For all properties of all labeling tools in Ango Hub, please consult the [Labeling Tools](labeling-tools/) page and navigate to the docs page describing the tool of your choice.

### Deleting and changing the order of classes

You may change the order in which classes are shown on the labeling editor by using the "up" and "down" arrows on each class's row.

You may delete a class by clicking on the "rubbish bin" icon in each class's row.

<figure><img src="../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>

## Managing Classes through JSON

You can view and edit the underlying JSON Ango Hub uses to store project ontologies by clicking on the _Show/Hide JSON_ button on the top right of the _Category Schema_ section.

<figure><img src="../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

This allows you to do a number of things. You can:

* Copy the JSON of a project ontology to your clipboard
* Paste an ontology into another project
* Edit the JSON directly

As you update your classes from the UI on the left, you will see the updates change the JSON in real time. This works the other way too – changing the JSON will instantly change what's shown on the UI.

See [here](../how-to/transfer-project-ontologies-between-projects.md) for a quick how-to guide on how to copy an ontology from a project and pasting it into another.
