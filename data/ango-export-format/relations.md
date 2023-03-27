---
description: Relation fields in Ango Annotation Format exports.
---

# Relations

The [Ango Annotation Format](./) supports the following relation types:

* Single Relation
  * Unidirectional
  * Bidirectional
* Group

## Overview of Relations in the Ango Annotation Format

### Fields

#### Common

* `objectId` - A unique identifier for the relation. (e.g. each new relation has a different objectId.)
* `schemaId` - A unique identifier for the chosen [labeling tool](../../labeling/labeling-tools/). (e.g. all relations of the same category will have the same schemaId.)
* `title` - External name of the tool (e.g. `age`, `gender`, `color`).

#### Single Relation

* `from` - objectID of the first (departure) annotation in the relation.
* `to` - objectID of the last (arrival) annotation in the relation.
* `direction` - Direction of the relation, whether `straight` or `bidirectional`.

#### Group

* `group` - If the relation is a group relation (e.g. is contains more than two members), a list of objectIDs of the objects contained in the group.

### Sample Relation Export

```json
"relations": [
  {
    "objectId": "d64c9411b9e040691f72813",
    "schemaId": "bbe5d081089f774a2fef435",
    "from": "f9b1e50ec081e156c718420",
    "to": "961dc4d7cb430aca8f2f096",
    "direction": "straight",
    "title": "singleRelationName"
  },
  {
    "objectId": "5b7563fe8f76a2fdd1aa889",
    "schemaId": "1c2d75ce36cbf0aea306012",
    "group": [
      "58a07df98f7747a597a8437",
      "2c93005a971933a40831133",
      "065fb5c8738fef22e267333"
    ],
    "title": "groupRelationName"
  }  
]
```
