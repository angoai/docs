---
description: Page detailing all API methods to use Ango Hub programmatically.
---

# API Documentation

## List of API Methods

{% swagger method="get" path="/v2/listProjects" baseUrl="https://api.ango.ai" summary="List Projects" %}
{% swagger-description %}
Returns a list of all projects visible to the user.

Example request:

`curl --location --request GET 'https://api.ango.ai/v2/listProjects' --header 'Content-Type: application/json' --header 'apikey: YOUR-API-KEY-HERE'`
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
Response content type. Must be 

`application/json`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="apikey" type="String" required="true" %}
API Key obtained from 

[hub.ango.ai/account](https://hub.ango.ai/account)


{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success" %}
```javascript
{
    "status": "success",
    "data": {
        "projects": [
            {
                "_id": "123123123123123123123123",
                "name": "Project Name",
                "description": "Project Description",
                "organization": "234234234234234234234234",
                "createdAt": "2021-10-14T07:44:46.373Z"
            }
        ],
        "total": 1
    }
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Invalid API key" %}
```javascript
{
    "status": "fail",
    "message": "Invalid API KEY"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/v2/project/{project_id}" baseUrl="https://api.ango.ai" summary="Get Project" %}
{% swagger-description %}
Returns information about a project, including labeling tools, consensus count, assigned users, review configuration, and name and description.

Example request:

`curl --location --request GET 'https://api.ango.ai/v2/project/61602b346ee9eb45e8273fbb' --header 'Content-Type: application/json' --header 'apikey: YOUR-API-KEY-HERE'`
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
Response content type. Must be 

`application/json`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="apikey" type="String" required="true" %}
API Key obtained from 

[hub.ango.ai/account](https://hub.ango.ai/account)


{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success" %}
```javascript
{
    "status": "success",
    "data": {
        "project": {
            "categorySchema": {
                "tools": [
                    {
                        "title": "Vehicle",
                        "tool": "bounding-box",
                        "required": false,
                        "schemaId": "4b8ac18a570747f87b27025",
                        "columnField": false,
                        "classifications": [
                            {
                                "title": "Type",
                                "tool": "radio",
                                "required": false,
                                "schemaId": "ae40cb11c104045c1a31698",
                                "columnField": false,
                                "options": [
                                    {
                                        "value": "Car",
                                        "schemaId": "27504d2d08f05b9944aa713"
                                    },
                                    {
                                        "value": "Truck",
                                        "schemaId": "c734a046cbee0646886a067"
                                    },
                                    {
                                        "value": "Bus",
                                        "schemaId": "41abb6003990d2aa1ce3605"
                                    },
                                    {
                                        "value": "Other",
                                        "schemaId": "32b3611a68df286fe6eb281"
                                    }
                                ]
                            }
                        ],
                        "color": "#9c27b0",
                        "shortcutKey": "h"
                    }
                ],
                "classifications": [],
                "relations": []
            },
            "consensusCount": 1,
            "deleted": false,
            "reviewConf": {
                "filters": []
            },
            "_id": "6167dfee2a810d000e9d313f",
            "name": "Project Name",
            "description": "Project Description",
            "user": {
                "organizationRole": "admin",
                "deleted": false,
                "_id": "614348d554e17400149964b1",
                "name": "Name Surname",
                "email": "name_surname@example.com",
                "organization": "61435781cdb61b0013d05a03",
                "lastActiveAt": "2021-10-14T09:55:54.814Z",
                "apiKey": "API-KEY-HERE"
            },
            "organization": "61435781cdb61b0013d05a03",
            "createdAt": "2021-10-14T07:44:46.373Z",
            "assignedTo": [],
            "__v": 0,
            "role": "Manager"
        }
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Invalid Project" %}
```javascript
{
    "status": "fail",
    "message": "Invalid project: 6167dfee2a810d000e9d313."
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Invalid API key" %}
```javascript
{
    "status": "fail",
    "message": "Invalid API KEY"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/v2/project/{project_id}/tasks" baseUrl="https://api.ango.ai" summary="Get Tasks of Project" %}
{% swagger-description %}
Returns all tasks in a project, with all of their information, including labeling tools, status, etc.

Example request:

`curl --location --request GET 'https://api.ango.ai/v2/project/615ffd3c455fc7000e6c45eb/tasks' --header 'Content-Type: application/json' --header 'apikey: YOUR-API-KEY-HERE'`
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
Response content type. Must be 

`application/json`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="apikey" type="String" required="true" %}
API Key obtained from 

[hub.ango.ai/account](https://hub.ango.ai/account)


{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success" %}
```javascript
{
    "status": "success",
    "data": {
        "tasks": [
            {
                "sample": {
                    "isSample": false,
                    "updatedAt": "2021-10-14T08:20:31.259Z"
                },
                "review": {
                    "status": "Todo"
                },
                "answer": {
                    "tools": [
                        {
                            "schemaId": "258f3a07abdb690af46b879",
                            "classifications": [
                                {
                                    "schemaId": "a20942feeaa72bd14d25150",
                                    "answer": "b8135ff7ae3c7ff38347978"
                                },
                                {
                                    "schemaId": "195857feb959465d20c8215",
                                    "answer": "fb19996138864f54eb61839"
                                },
                                {
                                    "schemaId": "c6403fdb451daad92247100",
                                    "answer": "Ocre"
                                }
                            ],
                            "lock": false,
                            "objectId": "014273c35ff83e2e19c9392",
                            "ner": {
                                "start": 10,
                                "end": 15
                            },
                            "metadata": {
                                "createdAt": 1634199730392,
                                "createdBy": "import"
                            }
                        }
                    ],
                    "classifications": [],
                    "relations": []
                },
                "status": "TODO",
                "isBenchmark": false,
                "deleted": false,
                "issues": [],
                "openIssuesCount": 0,
                "isPreLabeled": true,
                "isFlag": false,
                "isStar": false,
                "_id": "6167e84f2a810d000e9d3186",
                "project": "6167dfee2a810d000e9d313f",
                "asset": {
                    "_id": "6167e84f2a810d000e9d3185",
                    "externalId": "text_file.txt",
                    "data": "https://angohub-public-assets.s3.eu-central-1.amazonaws.com/uploaded-data-d187239d-9fc0-4565-983d-50c7b42b258b.txt"
                },
                "organization": "61435781cdb61b0013d05a03",
                "createdAt": "2021-10-14T08:20:31.259Z"
            },
            {
                "sample": {
                    "isSample": false,
                    "updatedAt": "2021-10-14T07:47:23.457Z"
                },
                "review": {
                    "status": "Todo"
                },
                "answer": {
                    "tools": [
                        {
                            "schemaId": "4b8ac18a570747f87b27025",
                            "classifications": [
                                {
                                    "schemaId": "ae40cb11c104045c1a31698",
                                    "answer": "27504d2d08f05b9944aa713"
                                },
                                {
                                    "schemaId": "2ea7c2a0712af78cd9bb827",
                                    "answer": "ca9e9c4c13caa3f11a3d292"
                                },
                                {
                                    "schemaId": "364dc1e2a7ed4d9f57ce731",
                                    "answer": "Ocre"
                                }
                            ],
                            "lock": false,
                            "objectId": "7719679ed20f149af886359",
                            "bounding-box": {
                                "x": 50.3,
                                "y": 30.4,
                                "width": 120.005,
                                "height": 135.345
                            },
                            "metadata": {
                                "createdAt": 1634199268359,
                                "createdBy": "import"
                            }
                        }
                    ],
                    "classifications": [],
                    "relations": []
                },
                "status": "TODO",
                "isBenchmark": false,
                "deleted": false,
                "issues": [],
                "openIssuesCount": 0,
                "isPreLabeled": true,
                "isFlag": false,
                "isStar": false,
                "_id": "6167e08b2a810d000e9d314d",
                "project": "6167dfee2a810d000e9d313f",
                "asset": {
                    "_id": "6167e08b2a810d000e9d314c",
                    "externalId": "test.jpg",
                    "data": "https://angohub-public-assets.s3.amazonaws.com/uploaded-data-15c12f8e-4b46-4d55-8fd4-776455448810.jpg"
                },
                "organization": "61435781cdb61b0013d05a03",
                "createdAt": "2021-10-14T07:47:23.457Z"
            }
        ],
        "total": 2
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Invalid Project" %}
```javascript
{
    "status": "fail",
    "message": "Invalid project: 6167dfee2a810d000e9d313."
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Invalid API key" %}
```javascript
{
    "status": "fail",
    "message": "Invalid API KEY"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/v2/task/{task_id}" baseUrl="https://api.ango.ai" summary="Get Task" %}
{% swagger-description %}
Returns all information about a task given the task's ID.

Example request:

`curl --location --request GET 'https://api.ango.ai/v2/task/616433306b763c8c0e922b14' --header 'Content-Type: application/json' --header 'apikey: YOUR-API-KEY-HERE'`
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
Response content type. Must be 

`application/json`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="apikey" type="String" required="true" %}
API Key obtained from 

[hub.ango.ai/account](https://hub.ango.ai/account)


{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success" %}
```javascript
{
    "status": "success",
    "data": {
        "task": {
            "sample": {
                "isSample": false,
                "updatedAt": "2021-10-14T07:47:23.457Z"
            },
            "review": {
                "status": "Todo"
            },
            "answer": {
                "tools": [
                    {
                        "schemaId": "4b8ac18a570747f87b27025",
                        "classifications": [
                            {
                                "schemaId": "ae40cb11c104045c1a31698",
                                "answer": "27504d2d08f05b9944aa713"
                            },
                            {
                                "schemaId": "2ea7c2a0712af78cd9bb827",
                                "answer": "ca9e9c4c13caa3f11a3d292"
                            },
                            {
                                "schemaId": "364dc1e2a7ed4d9f57ce731",
                                "answer": "Ocre"
                            }
                        ],
                        "lock": false,
                        "objectId": "7719679ed20f149af886359",
                        "bounding-box": {
                            "x": 50.3,
                            "y": 30.4,
                            "width": 120.005,
                            "height": 135.345
                        },
                        "metadata": {
                            "createdAt": 1634199268359,
                            "createdBy": "import"
                        }
                    },
                    {
                        "schemaId": "4b8ac18a570747f87b27025",
                        "bounding-box": {
                            "x": 179.8469387755102,
                            "y": 311.79138321995464,
                            "height": 123.58276643990929,
                            "width": 112.24489795918367
                        },
                        "objectId": "4e42a539188471304757866",
                        "classifications": [],
                        "metadata": {
                            "createdAt": 1634207308867,
                            "createdBy": "614348d554e17400149964b1"
                        }
                    }
                ],
                "classifications": [],
                "relations": []
            },
            "status": "Completed",
            "isBenchmark": false,
            "deleted": false,
            "issues": [],
            "openIssuesCount": 0,
            "isPreLabeled": true,
            "isFlag": false,
            "isStar": false,
            "_id": "6167e08b2a810d000e9d314d",
            "project": {
                "_id": "6167dfee2a810d000e9d313f"
            },
            "asset": {
                "_id": "6167e08b2a810d000e9d314c",
                "externalId": "test.jpg",
                "data": "https://angohub-public-assets.s3.amazonaws.com/uploaded-data-15c12f8e-4b46-4d55-8fd4-776455448810.jpg"
            },
            "organization": "61435781cdb61b0013d05a03",
            "createdAt": "2021-10-14T07:47:23.457Z",
            "__v": 0,
            "completedAt": "2021-10-14T10:28:30.025Z",
            "completedBy": "614348d554e17400149964b1",
            "duration": 4141,
            "updatedAt": "2021-10-14T10:28:30.025Z",
            "updatedBy": "614348d554e17400149964b1",
            "assignee": "614348d554e17400149964b1"
        }
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Invalid Project" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Invalid API key" %}
```javascript
{
    "status": "fail",
    "message": "Invalid API KEY"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/v2/project/{project_id}/upload" baseUrl="https://api.ango.ai" summary="Upload File" %}
{% swagger-description %}
Upload local files as assets to a project. Multiple files can be uploaded with one request by sending more than one 'files' form.

Example request:

`curl --location --request POST 'https://api.ango.ai/v2/project/615ffd3c455fc7000e6c45eb/upload' --header 'Content-Type: multipart/form-data' --header 'apikey: YOUR-API-KEY-HERE' --form 'files=@"/home/ofk/Pictures/Screenshot from 2021-08-29 12-06-49.png"' --form 'files=@"/home/ofk/Pictures/Screenshot from 2021-08-26 17-16-11.png"'`
{% endswagger-description %}

{% swagger-parameter in="body" name="form" type="String" required="true" %}
`'files=@"/path/to/file.jpg"'`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
Response content type. Must be 

`multipart/form-data`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="apikey" type="String" required="true" %}
API Key obtained from 

[hub.ango.ai/account](https://hub.ango.ai/account)


{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success" %}
```javascript
{
    "status": "success",
    "data": {
        "assets": "Successfully created."
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/v2/project/{project_id}/cloud" baseUrl="https://api.ango.ai" summary="Upload Files from Cloud Storage" %}
{% swagger-description %}
Uploads files from cloud storage to a specified Ango Hub project as assets.

Example request:

`curl --location --request POST 'https://api.ango.ai/v2/project/61602b346ee9eb45e8273fbb/cloud'`\
`--header 'Content-Type: application/json'`\
`--header 'apikey: YOUR-API-KEY-HERE'`\
`--data-raw '{ "assets": [ { "data": "https://angohub.s3.us-east-2.amazonaws.com/1605167545820-0b395d1ef7df81b7558f87eb47a59dda4dbe19bd.jpg", "externalId": "111" }, { "data": "https://angohub.s3.us-east-2.amazonaws.com/1605167545822-0b0b60d298c4afebed824d8ee2f793676c7835bf.jpg", "externalId": "113" } ] }'`
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="String" required="true" %}
Response content type. Must be 

`application/json`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="apikey" type="String" required="true" %}
API Key obtained from 

[hub.ango.ai/account](https://hub.ango.ai/account)


{% endswagger-parameter %}

{% swagger-parameter in="body" name="assets" type="Array" required="true" %}
Array of objects each containing two key-value pairs: 

`"data":"URL"`

and 

`"externalId":"ID"`

. See example above.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Success" %}
```javascript
{
    "status": "success",
    "data": {
        "assets": "Successfully created."
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/issues" baseUrl="https://api.ango.ai/v2" summary="Create Issue" %}
{% swagger-description %}
Creates an issue. If a `position` parameter is sent, the issue will be created at the position requested (on single images, multi-page TIFFs, video, and text only.)

Example request:

`curl --location --request POST 'https://api.ango.ai/v2/issues'`\
`--header 'apikey: YOUR-API-KEY-HERE'`\
`--data-raw '{ "content":"Issue Text Here", "labelTask": "6143498454e17400149964d1", "position": "[50,120]" }'`
{% endswagger-description %}

{% swagger-parameter in="header" name="apikey" required="true" %}
API Key obtained from 

[hub.ango.ai/account](https://hub.ango.ai/account)


{% endswagger-parameter %}

{% swagger-parameter in="body" name="content" required="true" %}
Issue text
{% endswagger-parameter %}

{% swagger-parameter in="body" name="labelTask" required="true" %}
ID of the label task where the issue is to be created.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="position" required="false" %}
For images: stringified array with the X and Y position where the issue is to be created on the asset. Example: "\[50, 120]"

For text: stringified index of the character in the text where the issue will be created. Example: "54".
{% endswagger-parameter %}

{% swagger-parameter in="body" name="page" type="Int" %}
For multi-page TIFFs and videos, the zero-indexed page/frame number where the issue is to be displayed.
{% endswagger-parameter %}
{% endswagger %}

{% swagger method="post" path="/attachments" baseUrl="https://api.ango.ai/v2" summary="Create Attachment" %}
{% swagger-description %}
Adds an attachment to an existing labeling task.

Example request:

`curl --location --request POST 'https://api.ango.ai/v2/attachments'`\
`--header 'apikey: YOUR-API-KEY-HERE'`\
`--data-raw '{`\
&#x20; `"project": "61d444045e299635ed689056",`\
&#x20; `"attachments": [`\
&#x20;   `{`\
&#x20;     `"data": "https://angohub-public-assets.s3.eu-central-1.amazonaws.com/uploaded-data-0a0988b2-d6ca-420e-97e6-577b96417989.png",`\
&#x20;     `"externalId": "uploaded-data-65dfb652-d7c8-4fa5-b6d5-de6bfe2a4365.png",`\
&#x20;     `"attachments": [`\
&#x20;       `{`\
&#x20;         `"type": "IMAGE",`\
&#x20;         `"value": "https://sample-image.jpg"` \
&#x20;       `},`\
&#x20;       `{`\
&#x20;         `"type": "VIDEO",`\
&#x20;         `"value": "http://sample-video.mp4"`\
&#x20;       `},`\
&#x20;       `{`\
&#x20;         `"type": "TEXT",`\
&#x20;         `"value": "Some sample text"`\
&#x20;       `}`\
&#x20;     `]`\
&#x20;   `}`\
&#x20; `]`\
`}'`
{% endswagger-description %}

{% swagger-parameter in="header" name="apikey" type="String" required="true" %}
API Key obtained from 

[hub.ango.ai/account](https://hub.ango.ai/account)


{% endswagger-parameter %}

{% swagger-parameter in="body" name="project" type="String" required="true" %}
ID of the project where the attachment is to be created. Found at the end of the project URL.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="attachments" type="Array" required="true" %}
Array of objects describing task/attachment pairs. See example.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="String" required="true" %}
URL to the asset where the attachment is to be added.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="externalId" type="String" required="true" %}
External ID of the asset. Found in the project under the Assets tab.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="String" required="true" %}
Attachment data type. Available types are IMAGE, VIDEO, and TEXT.



Supported IMAGE file types are .png and .jpg. The supported video type is .mp4, and the supported text type is .txt.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="value" type="String" required="true" %}
In case the type is TEXT, the content of the attachment in plain text.

\




\


In case the type is IMAGE or VIDEO, a URL linking to the image or video.
{% endswagger-parameter %}
{% endswagger %}
