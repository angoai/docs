# Label Validation

You can show errors to labelers when they try to submit annotations that don't fit requirements of your choice, and if you so wish, you can prevent them from submitting their label entirely.

Ango Hub provides a fully customizable and programmatic way to validate annotations, allowing you to create JavaScript functions that hook directly into Ango Hub's code and run when annotators attempt to save or submit their annotations.

{% hint style="info" %}
Label validation is run when the labeler clicks on _Save_ or _Submit_.
{% endhint %}

## Enable Label Validation

Navigate to the project where you'd like to enable label validation, then go to the _Settings_ tab and enter the _Label Validation_ section:

<figure><img src="../.gitbook/assets/image (383).png" alt=""><figcaption></figcaption></figure>

**Enable Custom Validation**: when enabled, validation will be activated for the current project.

**Prevent Submission with Error:** when enabled, annotators will not be allowed to submit or save their annotations when your function returns an error. When disabled, they are shown the error, but can choose to submit the annotation anyway.

In the code area below, you will enter your JavaScript function containing the logic of your label validation. You may click on _Validate Code_ to check for syntax errors and try your code on sample labels.

## Set Up Label Validation

In the code area of the _Label Validation_ section, enter a JavaScript function that takes one parameter (we'll call it _answers,)_ and returns a list of dicts with the errors you'd like to show. The function will be run every time an annotator tries to save or submit annotations.

### Function Parameters

Ango Hub will pass one parameter to your function, a JSON object which contains all objects, relations, and classifications the annotator is trying to submit.

This is a sample 'answers' parameter you'll receive from Ango Hub. In this case, the user created two PDF areas, created a single relation between them, and replied to a classification with two answers:

```json
{
  "tools": [
    {
      "pdf": {
        "position": {
          "boundingRect": {
            "x1": 157,
            "y1": 166.1374969482422,
            "x2": 200,
            "y2": 226.1374969482422,
            "width": 671.001473820641,
            "height": 670.9999999999999
          },
          "rects": [],
          "pageNumber": 1
        },
        "content": {
          "image": "data:image/png;base64="
        }
      },
      "objectId": "7e0bd6f41a01c78c15ae608",
      "classifications": [],
      "metadata": {
        "createdAt": 1674132659608,
        "createdBy": "614348d554e17400149964b1"
      },
      "schemaId": "801a2b8b8079b50d4541789"
    },
    {
      "pdf": {
        "position": {
          "boundingRect": {
            "x1": 106,
            "y1": 271.1374969482422,
            "x2": 135,
            "y2": 332.1374969482422,
            "width": 671.001473820641,
            "height": 670.9999999999999
          },
          "rects": [],
          "pageNumber": 1
        },
        "content": {
          "image": "data:image/png;base64="
        }
      },
      "objectId": "8083daa5d68a090aca6c738",
      "classifications": [],
      "metadata": {
        "createdAt": 1674132663738,
        "createdBy": "614348d554e17400149964b1"
      },
      "schemaId": "801a2b8b8079b50d4541789"
    }
  ],
  "classifications": [
    {
      "schemaId": "fe5af3c7471de99e3868448",
      "answer": [
        "3b935728b7f43b18b1f7553",
        "cb48de7b8c1a10908b2d747"
      ],
      "page": 0,
      "metadata": {
        "createdAt": 1674132625127,
        "createdBy": "614348d554e17400149964b1",
        "updatedAt": 1674132625364,
        "updatedBy": "614348d554e17400149964b1"
      }
    }
  ],
  "relations": [
    {
      "from": "7e0bd6f41a01c78c15ae608",
      "to": "8083daa5d68a090aca6c738",
      "objectId": "5ccee3e5af7eeb84b59a358",
      "schemaId": "c3ec9fbe6c52567a0dfb479",
      "direction": "straight",
      "metadata": {
        "createdAt": 1674132666358,
        "createdBy": "614348d554e17400149964b1"
      }
    }
  ]
}
```

For more on what can be passed in 'answers', we recommend following the steps in the next section. Following that, consulting the page [Ango Annotation Format](../data/ango-export-format/) will also help, as it details the format in which annotations are exported, which is the same as what you'll receive as parameter.

#### Quickly previewing the 'answers' parameter

We developed a fast and efficient way to preview what will be passed to your function based on your needs:

1. Open the labeling editor and perform a test annotation on Hub with the tools and answers you need.
2.  Without having to save or submit the annotation, from the three-dot menu in the top-left corner, click on _Copy Answers:_

    <figure><img src="../.gitbook/assets/image (366).png" alt=""><figcaption></figcaption></figure>

You will have copied exactly what Ango Hub would have passed as parameter in your validation function based on the labels on the screen.

### Function Returns

Your function will need to return a list of dictionaries, containing the ID of the object which is causing the error, as well as an error message string.

This is what a sample return will look like:

```javascript
[
  {
    objectId: "12345678",
    message: "There is a point with an X under 100px."
  },
  {
    objectId: "12345690",
    message: "Maximum 3 answers allowed."
  }
]

```

### Testing and Debugging your Validation Code

From Ango Hub, you can test and debug your function without having to perform labeling and submitting test annotations every time.

1. Obtain a sample of what will be passed into your function by following the steps [in this section](label-validation.md#quickly-previewing-the-answers-parameter).
2. From your project dashboard, enter the _Settings_ tab, then the _Label Validation_ section. In the code area, enter your validation function.
3. To test and debug your code, click on the _Validate Code_ button below the code area:

<figure><img src="../.gitbook/assets/image (368).png" alt=""><figcaption></figcaption></figure>

A dialog will open:

<figure><img src="../.gitbook/assets/image (321).png" alt=""><figcaption></figcaption></figure>

&#x20; 5\. Paste the input parameter you have copied in Step 1, and click on _Run_.

Ango Hub will scan your function for syntax errors, and show them to you if present.

And if your function successfully returned errors based on the annotations JSON you've just passed it as parameter, Ango Hub will show them to you below the code area:

<figure><img src="../.gitbook/assets/image (345).png" alt=""><figcaption></figcaption></figure>

By moving back and forth between writing your function and the validation dialog, you can create a quick build-debug workflow allowing you to create and test your functions quickly.

## Code Examples

Give an error if a point exists with a X under 100:

```javascript
function (answers) {
  let errors = [];

  const points = answers.objects.filter((obj) => obj.tool === "point" && obj["point"][0] < 100);

  points.map((b) => {
    errors.push(
      {
        objectId: b.objectId,
        message: "Point X under 100."
      }
    );
  })

  return errors;
}
```

Give an error if an empty group relation exists:

```javascript
function (answers) {
  let errors = [];

  const groupRelation = answers.relations.find((r) => r.tool === "group");

  if (groupRelation?.group.length > 0) {
    errors.push({
      objectId: groupRelation.objectId,
      message: "Group relation cannot be empty."
    });
  }

  return errors;
}
```

Give an error if a bounding box is narrower than 100px:

```javascript
function (answers) {
  let errors = [];

  const bbs = answers.objects.filter((obj) => obj.tool === "bounding-box" && obj["bounding-box"]["width"] < 100);

  bbs.map((b) => {
    errors.push(
      {
        objectId: b.objectId,
        message: "BB is narrower than 100px."
      }
    );
  })

  return errors;
}
```

Give an error if a group relation you specify contains objects with names different from the ones you specify:

```javascript
function (answers) {
  let errors = [];

  groupRelationToCheck = "TITLE OF GROUP RELATION TO CHECK"

  const acceptableObjectTypes = [
    "TITLE OF ACCEPTABLE OBJECT 1",
    "TITLE OF ACCEPTABLE OBJECT 2"
  ]

  const groupRelations = answers.relations.filter((r) => r.tool === "group" && r.title === groupRelationToCheck);

  groupRelations.forEach(groupRelation => {
    groupRelation.group.forEach(object => {
      if (!acceptableObjectTypes.includes(object.title)) {
        errors.push({
          objectId: groupRelation.objectId,
          message: `A ${groupRelationToCheck} group relation contains a ${object.title} object.`
        })
      }
    })
  })

  return errors;
}
```

Give an error if a group relation you specify contains more than one object from the ones you specify:

```javascript
function (answers) {
  let errors = [];

  groupRelationToCheck = "TITLE OF GROUP RELATION TO CHECK"

  const acceptableObjectTypes = [
    "TITLE OF ACCEPTABLE OBJECT 1",
    "TITLE OF ACCEPTABLE OBJECT 2"
  ]

  const groupRelations = answers.relations.filter((r) => r.tool === "group" && r.title === groupRelationToCheck);

  groupRelations.forEach(groupRelation => {
    acceptableObjectTypes.forEach(objectType => {
      matchingObjects = groupRelation.group.filter(object => object.title === objectType)
      if (matchingObjects.length > 1) {
        errors.push({
          objectId: groupRelation.objectId,
          message: `A group relation contains more than one ${objectType} object.`
        })
      }
    })
  })

  return errors;
}
```
