---
description: How to install and use Ango Hub's Python SDK.
---

# SDK Documentation

We provide a Python SDK to interface programmatically with Ango Hub.

## How to Install the Ango SDK

To use the Ango SDK, you will need the `ango` Python package, [which we publish on PyPI](https://pypi.org/project/ango/).

To download and add the package to your current Python environment, simply run&#x20;

```
pip install ango
```

## How to upgrade the Ango SDK

To upgrade the `ango` package to its latest version in your current Python environment run

```
pip install ango --upgrade
```

## Obtaining your API Key

To use the `ango` package, you will need an API key. To obtain your API key, from your [account page](https://hub.ango.ai/account), enter the _API_ tab. From here, you can create and copy your API key.

<figure><img src="../.gitbook/assets/image (332).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Creating a new API key will revoke the existing one.
{% endhint %}

## Obtaining Project and Task IDs

Each [project](../core-concepts/projects.md) and [task](../core-concepts/tasks.md) in Ango Hub is assigned its own unique ID. You may need to use such IDs in the SDK.

#### Project IDs

To obtain a project's ID, open the project and look at your browser's address bar. The URL will be in the format:

`https://hub.ango.ai/projects/<project_id>`

Copy the project ID from your address bar.

#### Task and Asset IDs

To obtain Task and Asset IDs, from the _Task_ or the _Assets_ tab, open the task you'd like to copy the ID of. Then, open the _Task Info_ (1) panel on the right and copy the ID you need.

You may use one of the _Copy to Clipboard_ buttons (2) to speed up the process.

<figure><img src="../.gitbook/assets/image (319).png" alt=""><figcaption></figcaption></figure>

## SDK Examples

You can find examples for each method below, under each method's heading.

You can also find those examples in [our Colab](https://colab.research.google.com/drive/1HMWQCHWxnNJZvztGPpSqgpWWZ9Y8kHfS?usp=sharing).

## SDK Methods (v0.1.18)

_**ango.sdk.SDK.**_

### assign\_batches(project\_id, asset\_ids, batches)

Assign specific asset(s) to specific batches.

Parameters:

* **project\_id:** string
  * ID of the project where the attachment will be created. Project IDs can be obtained [from the UI](sdk-documentation.md#project-ids) and from [list\_projects](sdk-documentation.md#list\_projects-page-limit).
  * Example: `'0000000aa0a00a0000aaaa0a'`
* **asset\_ids:** List\[str]
  * List of asset IDs to assign to batches. Asset IDs can be obtained [from the UI](sdk-documentation.md#task-and-asset-ids), or from [get\_assets](sdk-documentation.md#get\_assets-project\_id-asset\_id-external\_id-page-limit).
  * Example: `['0000000aa0a00a0000aaaa0a', '0000000aa0a00a0000aaaa0b']`
* **batches:** List\[str]
  * List of batches to which assets will be assigned.&#x20;
  * You can choose to pass either a list of batch names or a list of batch IDs. Batch names and batch IDs can be obtained with [get\_batches](sdk-documentation.md#get\_batches-project\_id).
  * Example:&#x20;
    * `['Batch-1', 'Batch-2']` or
    * `['0000000aa0a00a0000aaaa0a', '0000000aa0a00a0000aaaa0b']`

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'
ango_sdk = SDK(api_key)

asset_ids = ['<YOUR ASSET ID 1>', '<YOUR ASSET ID 2>']
batch_ids = ['<YOUR BATCH ID 1>', '<YOUR BATCH ID 2>']

ango_sdk.assign_batches(project_id, asset_ids, batch_ids)
```

Outputs:

```python
{
  "status": "success",
  "data": {
    "assets": 2
  }
}
```

Where "assets" is the number of assets successfully assigned to the batch(es).

{% hint style="info" %}
**See also**

[create\_batch](sdk-documentation.md#create\_batch-project\_id-batch\_name), [get\_batches](sdk-documentation.md#get\_batches-project\_id)
{% endhint %}

### assign\_task(task\_id, user\_id, email)

Assign a task to a specific user with either user\_id or email.

Parameters:

* **task\_id:** string
  * ID of the task to be assigned. Task IDs can be obtained [from the UI](sdk-documentation.md#task-and-asset-ids), and from [get\_tasks](sdk-documentation.md#get\_tasks-project\_id-page-limit-status).
  * Example: `'0000000aa0a00a0000aaaa0a'`
* **user\_id:** string, _Optional_
  * ID of the user to assign the task to. User IDs can be obtained with [get\_project](sdk-documentation.md#get\_project-project\_id). Not required if _email_ was provided.
  * Example: `'0000000aa0a00a0000aaaa0a'`
* **email:** string, _Optional_
  * Mail address with which the user to be assigned the task to registered. Not required if _user\_id_ was provided.
  * Example: `'lorenzo@example.com'`

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
ango_sdk = SDK(api_key)

task_id = '<YOUR TASK ID>'
email = '<example@example.com>'
ango_sdk.assign_task(task_id, email)
```

{% hint style="info" %}
**See also**

[get\_tasks](sdk-documentation.md#get\_tasks-project\_id-page-limit-status)
{% endhint %}

### create\_attachment(project\_id, attachments)

Add attachments to assets in a project. More on attachments and uploading them [here](../core-concepts/attachments.md).

Parameters:

* **project\_id:** string
  * ID of the project where the attachment will be created. Project IDs can be obtained [from the UI](sdk-documentation.md#project-ids) and from [list\_projects](sdk-documentation.md#list\_projects-page-limit).
  * Example: `'0000000aa0a00a0000aaaa0a'`
* **attachments:** List\[dict]
  * List of attachments to attach to existing assets. Attachments are dictionaries containing information about the asset the attachment will be attached to, the type of attachment, and the content of the attachment.
  * Example attachment parameter with 3 attachments being attached to 2 assets:

```python
attachments = [
    {"externalId": "sample_image_1.png",
     "attachments": [
         {"type": "IMAGE", "value": "https://sample-attachment-image.jpg"},
         {"type": "TEXT", "value": "Some sample text."}
     ]
     },
    {"externalId": "sample_image_2.png",
     "attachments": [
         {"type": "VIDEO", "value": "https://sample-attachment-video.jpg"}
     ]
     }
]
```

{% hint style="info" %}
Attachments can have one of the types "IMAGE", "TEXT", or "VIDEO".

For IMAGE and VIDEO, you will need to provide a link to the resource. JPG, PNG, and MP4 are supported.

For text, you will need to provide the text that will be attached.
{% endhint %}

{% hint style="info" %}
For image and video attachments, you may provide links to assets in private buckets, provided that you've connected them to Ango Hub. More information on how to do so can be found in the [Attachments](../core-concepts/attachments.md#uploading-attachments-from-private-buckets) page.
{% endhint %}

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'
ango_sdk = SDK(api_key)

attachments = [{"externalId": "sample_image_1.png",
                "attachments": [{"type": "IMAGE",
                                 "value": "https://sample-attachment-image.jpg"},
                                {"type": "TEXT",
                                 "value": "Some sample text."}]
               },
               {"externalId": "sample_image_2.png",
                "attachments": [{"type": "VIDEO",
                                 "value": "https://sample-attachment-video.jpg"}]
               }]

ango_sdk.create_attachment(project_id, attachments)
```

### create\_batch(project\_id, batch\_name)

Create batches in a specific project.

Parameters:

* **project\_id:** str
  * ID of the project where the batch will be created. Project IDs can be obtained [from the UI](sdk-documentation.md#project-ids) and from [list\_projects](sdk-documentation.md#list\_projects-page-limit).
  * Example: `'0000000aa0a00a0000aaaa0a'`
* **batch\_name:** str
  * Name of the batch to be created.
  * Example: `'My Batch 1'`

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'
ango_sdk = SDK(api_key)

ango_sdk.create_batch(project_id, "My Batch Name")
```

{% hint style="info" %}
**See also**

[assign\_batches](sdk-documentation.md#assign\_batches-project\_id-asset\_ids-batches), [get\_batches](sdk-documentation.md#get\_batches-project\_id)
{% endhint %}

### create\_issue(task\_id, content, position)

Opens an issue to the specified task, with given content on the given position.

Parameters:

* **task\_id:** string
  * ID of the task to be assigned. Task IDs can be obtained [from the UI](sdk-documentation.md#task-and-asset-ids) and from [get\_tasks](sdk-documentation.md#get\_tasks-project\_id-page-limit-status).
  * Example: `'0000000aa0a00a0000aaaa0a'`
* **content:** string
  * Text content of the issue.
  * Example: `'The bounding box here should reach the edges.'`
* **position:** List\[integer]
  * Position, in pixel, of where the issue should be placed on the image asset.
  * Example: `[25, 15]`

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
ango_sdk = SDK(api_key)

task_id = '<YOUR TASK ID>'
content = 'Hey! Check this annotation.'
position = [25, 15]

ango_sdk.create_issue(task_id, content, position)
```

{% hint style="info" %}
**See also**

[get\_tasks](sdk-documentation.md#get\_tasks-project\_id-page-limit-status)
{% endhint %}

### create\_label\_set(project\_id, tools, classifications, relations)

Create and set the project's ontology.

As this method is more complex than others, we recommend also consulting the examples at the end of this section.

Parameters:

* **project\_id:** string
  * ID of the project where the label set will be created. Project IDs can be obtained [from the UI](sdk-documentation.md#project-ids) and from [list\_projects](sdk-documentation.md#list\_projects-page-limit).
  * Example: `'0000000aa0a00a0000aaaa0a'`
* **tools:** List\[ToolCategory], _optional_
  * List of tools that will be added to the label set.
  * Example: `[ToolCategory(Tool.Segmentation, title="SegmentationTool")]`
* **classifications:** List\[ClassificationCategory], _optional, default None_
  * List of classifications that will be added to the label set.
  * Example: `[ClassificationCategory(Classification.Single_dropdown, title = "Choice", options=[LabelOption("First"), LabelOption("Second")])]`
* **relations:** List\[RelationCategory], _optional, default None_
  * List of relations that will be added to the label set.
  * Example: `[RelationCategory(Relation.Single, title="SingleRelationTool")]`

#### Label Set Classes

_ToolCategory:_ {Segmentation, Polyline, Polygon, Rotated\_bounding\_box, Ner, Point, Pdf}

ToolCategory Parameters:

* **tool:** __ Tool
  * The tool type. ex.: `Tool.Segmentation`
* **title:** __ string, _default ""_
  * The title of the tool.
* **required:** bool, _default None_
  * Whether annotators are required to draw at least one instance of this tool.
* **schemaId:** string, _default None_
  * Sets the tool's schemaId.
* **columnField:** bool, _default False_
  * Whether this tool should be a table column.
* **color:** string, _default ""_
  * The color assigned to this labeling tool, in the format "#FFFFFF"
* **shortcutKey:** string, _default ""_
  * The shortcut to quickly select this tool, "0"-"9", "ctrl+0"-"ctrl+9", "a"-"k"
* **classifications:** List\[ClassificationCategory], _default \[]_
  * List of nested classifications, if any
* **options:** List\[LabelOption], _default \[]_
  * The tool's answers (options.)

_ClassificationCategory_: {Multi\_dropdown, Single\_dropdown Tree\_dropdown, Radio, Checkbox, Text, Instance}

ClassificationCategory Parameters:

* **classification:** __ Classification
  * The classification type. ex.:`Classification.Tree_dropdown`
* **title:** __ string, _default ""_
  * The title of the classification.
* **required:** bool, _default None_
  * Whether annotators have to answer this classification or not.
* **schemaId:** string, _default None_
  * Sets the classification's Schema ID.
* **columnField:** bool, _default False_
  * Whether this classification should be a table column.
* **color:** string, _default ""_
  * The color assigned to this labeling tool, in the format "#FFFFFF"
* **shortcutKey:** string, _default ""_
  * The shortcut to quickly select this tool, "0"-"9", "ctrl+0"-"ctrl+9", "a"-"k"
* **classifications:** List, _default \[ClassificationCategory]_
  * List of nested classifications, if any
* **options:** List\[LabelOption], _default \[]_
  * The classification's answers (options.)
* **treeOptions:** List\[TreeOption], _default \[]_
  * For trees, the tree's leaves/branches.
* **parentOptionId:** string, _default ""_
  * The schema ID of the parent option. That is, the option that the labeler needs to select in order for this classification to appear. Enables conditional nesting.
* **richText**: _bool, default False_
  * &#x20;__ Set to True to enable the Rich Text editor for the selected text classification tool.

_RelationCategory:_ {Single, Group}

RelationCategory Parameters:

* **relation:** __ Relation
  * The classification type. ex.:`Relation.Single`
* **title:** __ string, _default ""_
  * The title of the relation.
* **required:** bool, _default None_
  * Whether annotators have to include at least one such relation in order to submit their annotation.
* **schemaId:** string, _default None_
  * Sets the schemaId of the relation.
* **columnField:** bool, _default False_
  * Whether this relation should be a table column.
* **color:** string, _default ""_
  * The color assigned to this relation, in the format "#FFFFFF"
* **shortcutKey:** string, _default ""_
  * The shortcut to quickly select this relation, "0"-"9", "ctrl+0"-"ctrl+9", "a"-"k"
* **classifications:** List\[ClassificationCategory], _default \[]_
  * List of nested classifications, if any
* **options:** List\[LabelOption], _default \[]_
  * The relation's answers (options.)

LabelOption parameters:

* **value:** string
  * The text of the answer (option.)
* **schemaId:** string, _default None_
  * The schema ID of the option. Necessary for conditional nesting.

Returns:

* **output:** dict

Examples:

Creating an ontology with:

* A [Single Dropdown](../labeling/labeling-tools/classification-tools/single-dropdown.md) classification, with two choices named "First" and "Second":

{% code overflow="wrap" %}
```python
from ango.sdk import SDK
from ango.models.label_category import LabelOption, ClassificationCategory, Classification

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'

ango_sdk = SDK(api_key)

category = ClassificationCategory(Classification.Single_dropdown, 
                                  title = "Choice", 
                                  options=[LabelOption("First"), LabelOption("Second")])

label_set = [category]

response = ango_sdk.create_label_set(project_id=project_id, classifications=label_set)
print(response)
```
{% endcode %}

Creating an ontology with:

* A [Single Dropdown](../labeling/labeling-tools/classification-tools/single-dropdown.md) classification with the classifications "First" and "Second"
* A [Segmentation](../labeling/labeling-tools/segmentation.md) tool called "SegmentationTool"
* A [Single Relation](../labeling/labeling-tools/relation-tools/single-relation.md) called "SingleRelationTool"

```python
from ango.sdk import SDK
from ango.models.label_category import ClassificationCategory, Classification, LabelOption, Tool, ToolCategory, RelationCategory, Relation

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'

ango_sdk = SDK(api_key)

dropdown = ClassificationCategory(Classification.Single_dropdown,
                                  title = "SingleDropdown",
                                  options = [LabelOption('First'), LabelOption('Second')])
classifications = [dropdown]

segmentation = ToolCategory(Tool.Segmentation, title="SegmentationTool")
tools = [segmentation]

relation = RelationCategory(Relation.Single, title="SingleRelationTool")
relations = [relation]

ango_sdk.create_label_set(project_id=project_id,
                          tools=tools,
                          classifications=classifications,
                          relations=relations)
```

Creating an ontology with:

* A Single Dropdown classification called "Entity Type" with the choices "Vehicle" and "Person"
* Another Single Dropdown classification nested inside the first unconditionally (that is, any choice in the first dropdown will open this second) named "Position" with the choices "On Road" and "Off Road".

```python
from ango.sdk import SDK
from ango.models.label_category import ToolCategory, ClassificationCategory, RelationCategory, LabelOption, Classification, Tool, Relation
import json

API_KEY = '<YOUR API KEY>'
PROJECT_ID = '<YOUR PROJECT ID>'
ango_sdk = SDK(API_KEY)

nestedClassInDropdown = ClassificationCategory(Classification.Single_dropdown,
                                               title="Position",
                                               options=[LabelOption('On Road'),
                                                        LabelOption('Off Road')]
                                               )

dropdown = ClassificationCategory(Classification.Single_dropdown,
                                  title="Entity Type",
                                  options=[LabelOption('Vehicle'),
                                           LabelOption('Person')],
                                  classifications=[nestedClassInDropdown],
                                  required=True
                                  )

classifications = [dropdown]

print(ango_sdk.create_label_set(
    project_id=PROJECT_ID,
    classifications=classifications)
)
```

Creating an ontology with:

* A [Tree Dropdown ](../labeling/labeling-tools/classification-tools/tree-dropdown.md)tool with:
  * A root
    * With a "tree0" branch
      * With a "subtree0" leaf
      * With a "subtree1" leaf
    * With a "tree1" leaf

```python
from ango.sdk import SDK
from ango.models.label_category import ClassificationCategory, LabelOption, Classification, Tool, Relation, TreeOption
import json

API_KEY = '<YOUR API KEY>'
PROJECT_ID = '<YOUR PROJECT ID>'
ango_sdk = SDK(API_KEY)

subTree0 = TreeOption(title="subtree0")
subTree1 = TreeOption(title="subtree1")
tree0 = TreeOption(title="tree0", children=[subTree0, subTree1])
tree1 = TreeOption(title="tree1")

treeTool = ClassificationCategory(
    classification=Classification.Tree_dropdown,
    title="Tree One",
    treeOptions=[tree0, tree1]
)

ango_sdk.create_label_set(
    project_id=PROJECT_ID,
    classifications=[treeTool]
)
```

Creating an ontology with:

* A [radio classification tool](../labeling/labeling-tools/classification-tools/radio.md) with two possible answers, "Radio Option 1" and "Radio Option 2"
* A conditionally nested [Text classification tool](../labeling/labeling-tools/classification-tools/text.md) using the rich text editor, which only appears if the labeler clicks on "Radio Option 1" (here, `parentOptionId` links the text tool to the option which reveals it)

```python
from ango.sdk import SDK
from ango.models.label_category import ClassificationCategory, LabelOption, Classification, Tool, Relation, TreeOption
import json

API_KEY = '<YOUR_API_KEY>'
PROJECT_ID = '<YOUR_PROJECT_ID>'
ango_sdk = SDK(API_KEY)

radio1 = LabelOption(
    value="Radio Option 1",
    schemaId="radioOption1SchemaId"
)
radio2 = LabelOption(
    value="Radio Option 2"
)

conditionalText = ClassificationCategory(
    classification=Classification.Text,
    title="Text Tool",
    parentOptionId="radioOption1SchemaId",
    color="#333333",
    richText=True
)

radio = ClassificationCategory(
    classification=Classification.Radio,
    title="Radio Classification",
    options=[radio1, radio2],
    classifications=[conditionalText]
)

res = ango_sdk.create_label_set(
    project_id=CREATE_SCHEMA_PROJECT_ID,
    classifications=[radio]
)
```

Creating an ontology with:

* A [radio classification tool](../labeling/labeling-tools/classification-tools/radio.md) with the possible answers "Radio Answer 1" and "Radio Answer 2"
* A [Tree Dropdown classification tool](../labeling/labeling-tools/classification-tools/tree-dropdown.md) which only appears if the annotator clicks on "Radio Answer 1"
  * The Tree Dropdown has a main root
    * With a branch called "Branch 1"
      * With leaves called "Leaf 1" and "Leaf 2"
    * With a leaf called "Leaf 3"

```python
leaf1 = TreeOption(
    title="Leaf 1"
)

leaf2 = TreeOption(
    title="Leaf 2"
)
branch1 = TreeOption(
    title="Branch 1",
    children=[leaf1, leaf2]
)

leaf3 = TreeOption(
    title="Leaf 3"
)

treeTool = ClassificationCategory(
    classification=Classification.Tree_dropdown,
    title='tree',
    treeOptions=[branch1, leaf3],
    parentOptionId="radioOptionSchemaId"
)

radio1 = LabelOption(
    value="Radio Answer 1",
    schemaId="radioOptionSchemaId"
)

radio2 = LabelOption(
    value="Radio Answer 2"
)

radio = ClassificationCategory(
    classification=Classification.Radio,
    title='radio',
    classifications=[treeTool],
    options=[radio1, radio2]
)

res = ango_sdk.create_label_set(
    project_id="639879404e2aa4e134db0c48",
    classifications=[radio]
)
```

### create\_project(name, description)

Creates a new project.

Parameters:

* **name:** string
  * The name of the project to be created. This field cannot be empty.
  * Example: `'Project One'`
* **description:** string, _optional, default ""_
  * Example: `'Vehicle Classification Project'`

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
ango_sdk = SDK(api_key)

res = ango_sdk.create_project(
    name="Created from SDK",
    description="I created this from the SDK."
)

print(res)
```

Returns:

```
{
  "status": "success",
  "data": {
    "project": {
      "aiAssistance": {
        "cocoRelations": []
      },
      "description": "I created this from the SDK.",
      "categorySchema": {
        "tools": [],
        "classifications": [],
        "relations": []
      },
      "consensusCount": 1,
      "benchmark": false,
      "deleted": false,
      "reviewConf": {
        "filters": []
      },
      "batches": [],
      "_id": "PROJECT ID",
      "name": "Created from SDK",
      "user": "USER ID OF PROJECT CREATOR",
      "organization": "ORGANIZATION ID",
      "createdAt": "2022-12-13T13:28:34.479Z",
      "assignedTo": [],
      "tags": [],
      "__v": 0
    }
  }
}
```

{% hint style="info" %}
**See also**

[list\_projects](sdk-documentation.md#list\_projects-page-limit), [get\_project](sdk-documentation.md#get\_project-project\_id)
{% endhint %}

### create\_webhook(webhook\_url, project\_id, secret, types)

Adds a new webhook to a project of your choice. [More on webhooks in Ango Hub here](../webhooks/integrating-webhooks-with-ango-hub.md).

Parameters:

* **webhook\_url:** str
  * The URL where the webhook will be fired to.
  * Example: `"https://3611-185-218-246-40.eu.ngrok.io/hook"`
* **project\_id:** str
  * Example: `'Vehicle Classification Project'`
* **secret**: str
  * The secret you provided when setting up [the webhook integration](../webhooks/integrating-webhooks-with-ango-hub.md). Can be any string.
* **types**: List\[str]
  * The action triggers for your webhook. For example, adding "UPDATED", will fire a webhook anytime a label is updated.
  * Example: `['ACCEPTED', 'UPDATED', 'COMPLETED']`
  * Accepted webhook types:
    * `ACCEPTED`: Fires any time a reviewer marks a labeling task as being accepted. (e.g. positive rewiew)
    * `COMPLETED`: Fires any time an annotator clicks on "Submit" and completes labeling.
    * `UPDATED`: Fires any time an user clicks on "Save" after updating an already-labeled labeling task.

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
ango_sdk = SDK(api_key)

res = ango_sdk.create_webhook(
    webhook_url='https://webhook.url/hook',
    project_id='<YOUR_PROJECT_ID>',
    secret='<YOUR_SECRET>',
    types=['ACCEPTED']
)

print(res)
```

Returns:

```json
{
  "status": "success",
  "data": { ... all integration data from the project }
}
```

### export(project\_id, assignees, completed\_at, updated\_at, batches)

Export annotated assets together with labels and metadata. Use assignee, completed\_at, updated\_at or batch filters to export specific parts of the dataset.

Parameters:

* **project\_id:** string
  * ID of the project which will be exported. Project IDs can be obtained [from the UI](sdk-documentation.md#project-ids) and from [list\_projects](sdk-documentation.md#list\_projects-page-limit).
  * Example: `'0000000aa0a00a0000aaaa0a'`
* **assignees:** List\[string], _optional_, _default None_
  * You may filter your export by only obtaining tasks completed by certain users. Enter your User IDs here. User IDs can be obtained with [get\_project](sdk-documentation.md#get\_project-project\_id).
  * Example: `['0000000aa0a00a0000aaaa0a', '0000000aa0a00a0000aaaa0b']`
* **completed\_at:** List\[datetime.datetime], _optional_, _default None_
  * You may obtain only tasks completed between two specific dates.
  * Example, to only export tasks completed from December 1st to today: `[datetime.datetime.fromisoformat("2022-12-01"), datetime.datetime.now()]`
* **updated\_at:** List\[datetime.datetime], _optional_, _default None_
  * You may obtain only tasks updated between two specific dates.
  * Example, to only export tasks updated from December 1st to today: `[datetime.datetime.fromisoformat("2022-12-01"), datetime.datetime.now()]`
* **batches:** List\[string], _optional_, _default None_
  * You may choose to only export assets pertaining to one or more specific batches.
  * Example: `['0000000aa0a00a0000aaaa0a']`

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'
ango_sdk = SDK(api_key)

ango_sdk.export(project_id)
```

{% hint style="info" %}
**See also**

[import\_labels](sdk-documentation.md#import\_labels-project\_id-labels)
{% endhint %}

### get\_assets(project\_id, asset\_id, external\_id, page, limit)

Get details of assets from a project.

Parameters:

* **project\_id:** string
  * ID of the project of which the assets will be obtained. Project IDs can be procured [from the UI](sdk-documentation.md#project-ids) and from [list\_projects](sdk-documentation.md#list\_projects-page-limit).
  * Example: `'0000000aa0a00a0000aaaa0a'`
* **asset\_id:** string, _Optional_, _default None_
  * List of asset IDs to assign to batches. (Asset IDs can be obtained [from the UI](sdk-documentation.md#task-and-asset-ids), with [get\_project(project\_id)](sdk-documentation.md#get\_project-project\_id), and with [get\_tasks(project\_id, page, limit, status)](sdk-documentation.md#get\_tasks-project\_id-page-limit-status)
  * Example: `['0000000aa0a00a0000aaaa0a', '0000000aa0a00a0000aaaa0b']`
* **external\_id:** string, _Optional_, _default None_
* **page:** integer, _default 1_
* **limit:** integer, _default 10_

Returns:

* **output:** dict

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'
ango_sdk = SDK(api_key)

sdk_response = ango_sdk.get_assets(project_id)

data_url = sdk_response['data']['assets'][0]['data']
external_id = sdk_response['data']['assets'][0]['externalId']
```

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'
ango_sdk = SDK(api_key)

items_per_page = 100
max_limit = None

assets = []
page = 1
remaining_tasks = 1
while remaining_tasks > 0:
    response =  ango_sdk.get_assets(project_id, page=page, limit=items_per_page)
    assets.extend(response['data']['assets'])
    remaining_tasks = response["data"]["total"] - len(assets)
    page += 1
    if max_limit:
        if len(assets) >= max_limit:
            assets = assets[:max_limit]
            break

print(len(assets))
```

{% hint style="info" %}
**See also**

[get\_task](sdk-documentation.md#get\_task-task\_id), [get\_tasks](sdk-documentation.md#get\_tasks-project\_id-page-limit-status)
{% endhint %}

### get\_batches(project\_id)

Get details of all batches in a project.

Parameters:

* **project\_id:** string
  * ID of the project to download the batches of. Project IDs can be obtained [from the UI](sdk-documentation.md#project-ids) and from [list\_projects](sdk-documentation.md#list\_projects-page-limit).
  * Example: `'0000000aa0a00a0000aaaa0a'`

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'
ango_sdk = SDK(api_key)

output = ango_sdk.get_batches(project_id=project_id)
```

Outputs:

```python
[
  {
    "_id": "<BATCH_ID>",
    "name": "Batch Name 1"
  },
  {
    "_id": "<BATCH_ID>",
    "name": "Batch Name 2"
  }
]
```

{% hint style="info" %}
**See also**

[assign\_batches](sdk-documentation.md#assign\_batches-project\_id-asset\_ids-batches), [create\_batch](sdk-documentation.md#create\_batch-project\_id-batch\_name)
{% endhint %}

### get\_integrations()

Get all integrations of the current organization.

Parameters:

* None

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
ango_sdk = SDK(api_key)

sdk_response = ango_sdk.get_integrations()
integrations_list = sdk_response['data']['integrations']
```

Outputs:

```python
{
  "status": "success",
  "data": {
    "integrations": [
      {
        "id": "<INTEGRATION ID>",
        "name": "<INTEGRATION NAME>",
        "provider": "GCP",
        "createdAt": "2022-11-24T13:48:32.100Z",
        "organization": "<ORGANIZATION ID>"
      }
    ]
  }
}
```

{% hint style="info" %}
**See also**

[upload\_files\_cloud](sdk-documentation.md#upload\_files\_cloud-project\_id-assets-integrationid-batches)
{% endhint %}

### get\_project(project\_id)

Get details of a project.

Objects available within the `response` returned by this function:

`response['data']['project']['<one of the below>']`

`aiAssistance, description, categorySchema, consensusCount, benchmark, deleted, reviewConf, batches, _id, name, user, organization, createdAt, assignedTo, tags, __v, role`

Parameters:

* **project\_id:** string
  * ID of the project to download the details of. Project IDs can be obtained [from the UI](sdk-documentation.md#project-ids) and from [list\_projects](sdk-documentation.md#list\_projects-page-limit).
  * Example: `'0000000aa0a00a0000aaaa0a'`

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'
ango_sdk = SDK(api_key)

sdk_response = ango_sdk.get_project(project_id)

project_name = sdk_response['data']['project']['name']
project_description = sdk_response['data']['project']['description']
project_creation_time = sdk_response['data']['project']['createdAt']
project_ontology = sdk_response['data']['project']['categorySchema']

print(project_name)
print(project_description)
print(project_creation_time)
print(project_ontology)
```

Outputs:

```
<Project Name>
<Project Description>
2000-01-01T00:00:00.000Z
{'tools': [...], 'classifications': [...], 'relations': [...]}
```

{% hint style="info" %}
**See also**

[create\_project](sdk-documentation.md#create\_project-name-description), [list\_projects](sdk-documentation.md#list\_projects-page-limit)
{% endhint %}

### get\_task(task\_id)

Get information on a task

Parameters:

* **task\_id:** string
  * ID of the task the information of which will be downloaded. Task IDs can be obtained [from the UI](sdk-documentation.md#task-and-asset-ids) and from [get\_tasks](sdk-documentation.md#get\_tasks-project\_id-page-limit-status).
  * Example: `'0000000aa0a00a0000aaaa0a'`

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
ango_sdk = SDK(api_key)

sdk_response = ango_sdk.get_task('<YOUR TASK ID>')

data_url = sdk_response['data']['task']['asset']['data']
external_id = sdk_response['data']['task']['asset']['externalId']
```

{% hint style="info" %}
**See also**

[get\_assets](sdk-documentation.md#get\_assets-project\_id-asset\_id-external\_id-page-limit), [get\_tasks](sdk-documentation.md#get\_tasks-project\_id-page-limit-status)
{% endhint %}

### get\_tasks(project\_id, page, limit, status)

Get tasks of a project.

Tasks in projects are paginated. A maximum of 1000 items per page can be obtained. See the code snippets below for an example of how to download all tasks from a project by flipping through the pages.

Parameters:

* **project\_id:** string
  * ID of the project to download the tasks of. Project IDs can be obtained [from the UI](sdk-documentation.md#project-ids) and from [list\_projects](sdk-documentation.md#list\_projects-page-limit).
  * Example: `'0000000aa0a00a0000aaaa0a'`
* **page:** integer, _default 1_
  * Current page.
  * Example: `1`
* **limit:** integer, _default 10_
  * Page size. Default 10, maximum 1000.
  * Example: `100`
* **status:** string, _default None_, {None, "TODO", "Completed", "Reviewed"}
  * Filter tasks by status.
  * Example: `'Completed'`
* **batches**: list\[str], _default None_
  * Filter tasks by batch (e.g., only get tasks belonging to the batch specified)
  * Example `['batch_1', 'batch_2']`

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'
ango_sdk = SDK(api_key)

sdk_response = ango_sdk.get_tasks(project_id, page=1, limit=10, status=None)

data_url = sdk_response['data']['tasks'][0]['asset']['data']
external_id = sdk_response['data']['tasks'][0]['asset']['externalId']
```

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'
ango_sdk = SDK(api_key)

items_per_page = 100
annotation_status = None
max_limit = None

tasks = []
page = 1
remaining_tasks = 1
while remaining_tasks > 0:
    response =  ango_sdk.get_tasks(project_id, page=page, limit=items_per_page, status=annotation_status)
    tasks.extend(response['data']['tasks'])
    remaining_tasks = response["data"]["total"] - len(tasks)
    page += 1
    if max_limit:
        if len(tasks) >= max_limit:
            tasks = tasks[:max_limit]
            break

print(len(tasks))
```

{% hint style="info" %}
**See also**

[get\_assets](sdk-documentation.md#get\_assets-project\_id-asset\_id-external\_id-page-limit), [get\_task](sdk-documentation.md#get\_task-task\_id)
{% endhint %}

### import\_labels(project\_id, labels)

Import labels to the project. More details on importing existing labels to Hub [here](https://docs.ango.ai/data/importing-and-exporting-annotations/importing-annotations/ango-hub-import-format).

Parameters:

* **project\_id:** string
  * ID of the project where to import labels. Project IDs can be obtained [from the UI](sdk-documentation.md#project-ids) and from [list\_projects](sdk-documentation.md#list\_projects-page-limit).
  * Example: `'0000000aa0a00a0000aaaa0a'`
* **labels:** List\[dict]
  * List of labels to import. See more on our label format here: [Ango Annotation Format](../data/importing-and-exporting-annotations/importing-annotations/ango-hub-import-format.md) and learn more about importing labels into Ango Hub [here](../data/importing-and-exporting-annotations/importing-annotations/).
  * Example:

```json
[
  {
    "externalId": "Test Pattern 844x844.png",
    "objects": [
      {
        "schemaId": "8f60cb0209a4d80f9add122",
        "title": "bbb",
        "bounding-box": {
          "width": 86,
          "height": 86,
          "x": 83,
          "y": 83
        }
      },
      {
        "schemaId": "8f60cb0209a4d80f9add122",
        "title": "bbb",
        "bounding-box": {
          "width": 167,
          "height": 167,
          "x": 338,
          "y": 338
        }
      },
      {
        "schemaId": "8f60cb0209a4d80f9add122",
        "title": "bbb",
        "bounding-box": {
          "width": 84,
          "height": 84,
          "x": 675,
          "y": 675
        }
      }
    ]
  }
]
```

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
ango_sdk = SDK(api_key)

schema_id = '<Schema ID of Car Class>'
annotations = [{"externalId": "10001.png",
                "objects": [{"schemaId": schema_id,
                             "title": 'Car',
                             "bounding-box": {"x": 20, "y": 30, "width": 50, "height": 60}}]
               }]

ango_sdk.import_labels(project_id, annotations)
```

{% hint style="info" %}
**See also**

[export](sdk-documentation.md#export-project\_id-assignees-completed\_at-updated\_at-batches)
{% endhint %}

### list\_projects(page, limit)

Lists projects from the current users' organization.

Projects are paginated. A maximum of 1000 projects can be obtained per page. See the second code example for more on how it works.

Parameters:

* **page:** int, _default 1_
  * Current page.
  * Example: `1`
* **limit:** int, _default 10, maximum 1000_
  * Number of projects per page.
  * Example: `100`

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
ango_sdk = SDK(api_key)

sdk_response = ango_sdk.list_projects()
project_list = sdk_response['data']['projects']

project_list[0]
```

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
ango_sdk = SDK(api_key)

items_per_page = 50
max_limit = None

project_list = []
page = 1
remaining_tasks = 1
while remaining_tasks > 0:
    response = ango_sdk.list_projects(page=page, limit=items_per_page)
    project_list.extend(response['data']['projects'])
    remaining_tasks = response["data"]["total"] - len(project_list)
    page += 1
    if max_limit:
        if len(project_list) >= max_limit:
            project_list = project_list[:max_limit]
            break

print(len(project_list))
```

Outputs:

```
{'_id': '000000000000000000000000',
 'name': 'Project Name',
 'description': 'Project Description',
 'organization': ‘000000000000000000000000',
 'createdAt': '2000-01-01T00:00:00.000Z'}
```

{% hint style="info" %}
**See also**

****[create\_project](sdk-documentation.md#create\_project-name-description), [get\_project](sdk-documentation.md#get\_project-project\_id)
{% endhint %}

### set\_asset\_priority(project\_id, priority, external\_id, asset\_id)

Change labeling priority of the asset. Higher priority values provide earlier labeling.

Priority parameter should be between -10.000 and 10.000. Asset’s priority value is equal to 0 by default. One of external\_id or asset\_id must be given.

Parameters:

* **project\_id:** string
  * ID of the project where priority will be set. Project IDs can be obtained [from the UI](sdk-documentation.md#project-ids) and from [list\_projects](sdk-documentation.md#list\_projects-page-limit).
  * Example: `'0000000aa0a00a0000aaaa0a'`
* **priority:** integer \[-10.000, 10.000]
  * The priority of the asset, between -10.000 and 10.000
  * Example: `30`
* **external\_id:** string, _default None_
  * External ID of the asset the priority of which will be set. Either the External ID or the Asset ID (next parameter) must be given.
* **asset\_id:** string, _default None_
  * Asset ID of the asset the priority of which will be set. Either the Asset ID or the External ID (previous parameter) must be given.

Returns:

* **output:** dict

Example:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'
ango_sdk = SDK(api_key)

external_id = '<YOUR EXTERNAL ID>'
priority = 120

ango_sdk.set_asset_priority(project_id, priority, external_id)
```

### set\_task\_status(task\_id, status)

Set the status of a task, either TODO and COMPLETED.

Parameters:

* **task\_id:** string
  * ID of the task to be assigned. Task IDs can be obtained [from the UI](sdk-documentation.md#task-and-asset-ids), and from [get\_tasks](sdk-documentation.md#get\_tasks-project\_id-page-limit-status).
  * Example: `'0000000aa0a00a0000aaaa0a'`
* **status:** TaskStatus.TODO or TaskStatus.COMPLETED
  * The status of the task.

Example:

```python
set_task_status(
    task_id='640828dfd5f1a42cce03e46d',
    status=TaskStatus.COMPLETED
)
```

Returns:

* **output:** dict

### upload\_files(project\_id, file\_paths, integration\_id, batches)

Upload files to Ango Hub. A list of local file paths should be given as an input parameter.

Optionally, a custom externalID for the files may be given from within the `file_paths` parameter. (See examples below)

Parameters:

* **project\_id:** string
  * ID of the project where priority will be set. Project IDs can be obtained [from the UI](sdk-documentation.md#project-ids) and from [list\_projects](sdk-documentation.md#list\_projects-page-limit).
  * Example: `'0000000aa0a00a0000aaaa0a'`
* **file\_paths:** List\[string]
  * List containing absolute paths to files.
  * Example: `["/Users/lorenzo/data/my_image_1.png", "/Users/lorenzo/data/my_image_2.png"]`
* **integration\_id:** string, _Optional_
  * This parameter has no function anymore and will be deprecated in the next version of the SDK.
* **batches**: List\[string], _Optional_
  * You may assign the files you are uploading to one or more batches that exist in your project by providing their IDs here. You may create new batches with [create\_batch](sdk-documentation.md#create\_batch-project\_id-batch\_name) and you can get a list of batches with [get\_batches](sdk-documentation.md#get\_batches-project\_id).
  * Example: `['0000000aa0a00a0000aaaa0a', '0000000aa0a00a0000aaaa0b']`

Returns:

* **output:** dict

Example:

Importing two local files:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'
ango_sdk = SDK(api_key)

file_paths = ["data/my_image_1.png", "data/my_image_2.png"]
ango_sdk.upload_files(project_id, file_paths)
```

Importing a file with a custom external ID:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'
ango_sdk = SDK(api_key)

file_paths = [
    {"data": "/Users/lorenzo/test.jpg", "externalId": "custom!"}
]
ango_sdk.upload_files(project_id, file_paths)
```

{% hint style="info" %}
**See also**

[upload\_files\_cloud](sdk-documentation.md#upload\_files\_cloud-project\_id-assets-integration\_id-batches)
{% endhint %}

### upload\_files\_cloud(project\_id, assets, integration\_id, batches)

Import files in cloud storage to Ango Hub. Check [_Importing Assets_](../data/importing-assets/) for more information.

Parameters:

* **project\_id:** string
  * The ID of the project where you'd like to add files.
  * Example: `'0000000aa0a00a0000aaaa0a'`
* **assets:** List\[string]
  * A list of asset dictionaries in the \[{"data": \<URL>, "externalId": "\<external\_id>"}] format.
  * Assets uploaded with this method can also contain attachments and batches. For example:

```python
public_file = [
    {
        "data": "https://angohub-public-assets.s3.eu-central-1.amazonaws.com/CzXTtJV.jpg",
        "externalId": "aws-public.png",
        "batches": ["Batch 1", "Batch 2"]
        "attachments": [
            {'type': "IMAGE", 'value': "https://angohub-public-assets.s3.eu-central-1.amazonaws.com/CzXTtJV.jpg"},
            {'type': "TEXT", 'value': "An attachment."}]
    }
]
```

{% hint style="info" %}
For image and video attachments, you may provide links to assets in private buckets, provided that you've connected them to Ango Hub. More information on how to do so can be found in the [Attachments](../core-concepts/attachments.md#uploading-attachments-from-private-buckets) page.
{% endhint %}

{% hint style="info" %}
Batches you specify in the _assets_ dictionary will override the batches you specify in the _batches_ parameter of this function.
{% endhint %}

* **integration\_id:** string, _Optional, default None_
  * If importing files from a private bucket [previously integrated with Hub](../data/importing-assets/importing-private-cloud-assets-gcp.md), this parameter is necessary. This is the ID of the bucket's integration, obtainable from [get\_integrations()](sdk-documentation.md#get\_integrations).
* **batches**: List\[string], _Optional_
  * You may add the files being uploaded to one or multiple batches, by passing a list of batch IDs. You may obtain a list of batch IDs available in your project using [get\_batches(project\_id)](sdk-documentation.md#get\_batches-project\_id), or create new ones using [create\_batch(project\_id, batch\_name)](sdk-documentation.md#create\_batch-project\_id-batch\_name).

Returns:

* **output:** dict

Examples:

Importing a file from a public bucket, and assigning it to a batch:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'
batch_id_list = ['<YOUR BATCH ID>']
ango_sdk = SDK(api_key)

public_file = [
    {
        "data": "https://storage.googleapis.com/a-public-bucket/file.png",
        "externalId": "myExternalId.png"
    }
]

ango_sdk.upload_files_cloud(
    project_id=project_id,
    assets=public_file,
    batches=batch_id_list
)
```

Importing a file from a private bucket, and assigning it to multiple batches:

```python
from ango.sdk import SDK

api_key = '<YOUR API KEY>'
project_id = '<YOUR PROJECT ID>'
batch_id_list = ['<BATCH ID 1>', '<BATCH ID 2>']
integration_id = '<YOUR_INTEGRATION_ID>' # Obtain with get_integrations, mandatory when importing files from private buckets
ango_sdk = SDK(api_key)

private_file = [
    {
        "data": "https://storage.googleapis.com/a-private-bucket/file.png",
        "externalId": "myExternalId.png"
    }
]

ango_sdk.upload_files_cloud(
    project_id=project_id,
    assets=public_file,
    batches=batch_id_list,
    integration_id=integration_id
)
```

{% hint style="info" %}
**See also**

[upload\_files](sdk-documentation.md#upload\_files-project\_id-file\_paths-integration\_id-batches), [get\_integrations](sdk-documentation.md#get\_integrations)
{% endhint %}
