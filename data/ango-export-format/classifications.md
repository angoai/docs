---
description: Classification fields in Ango Annotation Format exports.
---

# Classifications

The [Ango Annotation Format](./) supports the following classifications:

* [Radio](../../labeling/labeling-tools/classification-tools/radio.md)
* [Checkbox](../../labeling/labeling-tools/classification-tools/checkbox.md)
* [Single Dropdown](../../labeling/labeling-tools/classification-tools/single-dropdown.md)
* [Multiple Dropdown](../../labeling/labeling-tools/classification-tools/multiple-dropdown.md)
* [Text](../../labeling/labeling-tools/classification-tools/text.md)

More information on how each classification type is used when annotating can be accessed through the links above.

## Classifications in the Ango Annotation Format

### Fields

* `schemaId` - A unique identifier for the chosen [labeling tool](../../labeling/labeling-tools/).
* `tool` - Internal name of the tool type (e.g. `radio`, `checkbox`).
* `title` - External name of the tool (e.g. `age`, `gender`, `color`).
* `columnField` - Whether the tool was marked to be a column in table labeling.
* `answer` - The actual classification answer(s). The number of answers depends on the type of [classification tool](../../labeling/labeling-tools/classification-tools/) selected.
* `classifications` - Further, nested classifications within the classification.

### Sample Classification Export

```json
"classifications": [
  {
    "schemaId": "b1362e18ee733577da54007",
    "tool": "radio",
    "title": "radioName",
    "columnField": false,
    "answer": "choice1",
    "classifications": []
  },
  {
    "schemaId": "bcab41986fd89a3795e0417",
    "tool": "checkbox",
    "title": "checkboxName",
    "columnField": false,
    "answer": [
      "choiceOne",
      "choiceTwo"
    ],
    "classifications": []
  },
  {
    "schemaId": "6e05ed0ccc6e72f7f572990",
    "tool": "single-dropdown",
    "title": "singleDropdownName",
    "columnField": false,
    "answer": "One",
    "classifications": []
  },
  {
    "schemaId": "18008f37b14fb0106d3d494",
    "tool": "multi-dropdown",
    "title": "multipleDropdownName",
    "columnField": false,
    "answer": [
      "Two",
      "Three"
    ],
    "classifications": []
  },
  {
    "schemaId": "2303b3b4c3436abe45a3422",
    "tool": "text",
    "title": "textName",
    "columnField": false,
    "answer": "Hey!",
    "classifications": []
  }
]
```
