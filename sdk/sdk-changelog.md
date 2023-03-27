# SDK Changelog

### 0.1.19

Added a _batches_ parameter to `get_tasks`.

Added [`set_task_status`](sdk-documentation.md#set\_task\_status-task\_id-status) to set the status of a task, either TODO or COMPLETED.

### 0.1.17 - 0.1.18

Upgraded the performance of keep-alive connections.

### 0.1.16

#### Features and Improvements

Removed `get_export` timeouts.

Removed the requirement to fetch the API Key for export plugins.

### 0.1.12 - 0.1.15

Fixed a number of bugs occurring when creating plugins.

### 0.1.11

It is now possible to specify batches while uploading directly from within the JSON containing the asset URLs when using [`upload_files_cloud`](sdk-documentation.md#upload\_files\_cloud-project\_id-assets-integration\_id-batches).

### 0.1.10

#### Features and Improvements

Using [`get_batches`](sdk-documentation.md#get\_batches-project\_id) on an invalid project now returns a more descriptive error.

Added the ability to upload configuration JSONs to plugins.

### 0.1.8 - 0.1.9

#### Features and Improvements

You can now add attachments while uploading files with [`upload_files_cloud`](sdk-documentation.md#upload\_files\_cloud-project\_id-assets-integrationid-batches).

Limited the amount of information about users that is obtainable from [`get_project`](sdk-documentation.md#get\_project-project\_id).

Added a verbose error message when trying to upload assets using the wrong integrationId with `upload_files_cloud`.

Changed the error message when trying to obtain batches from nonexisting projects when using [`get_batches`](sdk-documentation.md#get\_batches-project\_id).

### 0.1.6 - 0.1.7

Fixed a bug where plugins would occasionally not run instantly.

### 0.1.5

Added a toggle to activate the Rich Text Editor for Text Classifications when using [create\_label\_set](sdk-documentation.md#create\_label\_set-project\_id-tools-classifications-relations).

### 0.1.3 - 0.1.4

Fixed a bug which occasionally prevented correct exports when using a Tree Dropdown tool created with [create\_label\_set](sdk-documentation.md#create\_label\_set-project\_id-tools-classifications-relations).

### 0.0.35 - 0.1.2

Improvements for the upcoming [Custom Plugin](../plugins/plugin-developer-documentation/) functionality.

### 0.0.34

#### Improvements

`assign_batches`'s `batch_id` parameter has been renamed to `batches` and now accepts both Batch IDs and Batch Names.

### 0.0.33

#### Bug fixes

Bug fixed preventing the setting of more than one Tree Dropdown tool at the same time.

### 0.0.32

#### Bug fixes

Bug fixes related to the upcoming Plugin functionality.

### 0.0.31

#### Improvements

You can now choose to pass the Batch Name instead of the Batch ID in all functions where you used to pass the Batch ID except for `assign_batches`.

"`tag`" parameter in `export` renamed to `batches`.

### 0.0.30

#### Features

Added the ability to [upload local files](sdk-documentation.md#upload\_files-project\_id-file\_paths-integrationid-batches) with a custom external ID.

### 0.0.29

#### Features

Added the ability to nest classifications conditionally when creating project ontologies with `create_label_set`.

Added the ability to create the new Tree Dropdown classification tool when using `create_label_set`.&#x20;

Info on how to do both in [the documentation for `create_label_set`](sdk-documentation.md#create\_label\_set-project\_id-tools-classifications-relations) with examples.

### 0.0.28

#### Features

Added the `create_project(name, description)`method to programmatically create new projects in your organization.

### 0.0.27

#### Bug fixes

Bug fixed on the `assign_batches` function.

### 0.0.26

#### Features

`batches: List[str]`  optional parameter added to `upload_files_cloud` and `upload_files`.

`get_batches(self, project_id: str)` function is added to get batches of specific project.

`assign_batches(self, asset_ids: List[str], batch_ids: List[str])` function is added to assign batches to existing assets.

`create_batch(self, project_id: str, batch_name: str)` function is added to create batches in a project.

### 0.0.25

#### Bug fixes

Fixed a bug in `assign_task`.

### 0.0.24

#### Features

Improved the output of `get_integrations`.

