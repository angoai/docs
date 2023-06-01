---
description: Overview of exporting annotations from Ango Hub
---

# Exporting Annotations

Administrators and project managers can create and download an export of all annotations performed in a project on Ango Hub.

## Getting your Export

Enter your project's _Export_ tab. The _Export_ button at the bottom will allow you to download your annotations.

You will receive a notification within Ango Hub when the export is ready. You may navigate away from the page while the export is being prepared.

## Export Options

<figure><img src="../../.gitbook/assets/image (384).png" alt=""><figcaption></figcaption></figure>

### Export Format

You can download your export in the JSON, NDJSON, and YOLO formats.

{% hint style="info" %}
If you need to download your export in more, different formats, we recommend you use our [Export Converter Plugins](../../plugins/first-party-plugins/ango-export-to-kitti-coco-yolo-converter-plugins.md).

We have developed the JSON export format to be as easy to parse and convert to other formats as possible. If you need your annotations in a format that is not supported by our plugins and you are a paid customer, contact us and we will provide you a script to convert our JSON export to the format of your choice.
{% endhint %}

### Fields

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

Click on the checkboxes next to the desired fields to include them in the export. Details of each toggle are as follows:

#### Asset Toggles

<table><thead><tr><th width="157">Toggle</th><th width="254">Description</th><th>Format</th></tr></thead><tbody><tr><td>Labeled at</td><td>Date and time in which the asset was labeled.</td><td><pre class="language-json"><code class="lang-json">"labeledAt": "2021-12-08T12:31:36.043Z"
</code></pre></td></tr><tr><td>Reviewed at</td><td>Data and time in which the asset was reviewed.</td><td><pre class="language-json"><code class="lang-json">"reviewedAt": "2021-12-08T15:31:36.043Z"
</code></pre></td></tr><tr><td>Status</td><td>Status of the asset (To-Do, In Progress, Completed, Reviewed)</td><td><pre class="language-json"><code class="lang-json">"status": "Labeled"
</code></pre></td></tr><tr><td>Label duration</td><td>How long it took to label the asset in milliseconds. Calculated from the moment the annotator opened the asset to the moment they clicked on <em>Submit</em>.</td><td><pre class="language-json"><code class="lang-json">"labelDuration(ms)": 6429,
</code></pre></td></tr><tr><td>Consensus</td><td><a href="../../core-concepts/consensus.md">Consensus</a> score of the asset, between 0 and 100.</td><td><pre class="language-json"><code class="lang-json">"consensus": 90
</code></pre></td></tr><tr><td>Batch Name</td><td>Batch(es) the asset belongs to.</td><td><pre class="language-json"><code class="lang-json">"batches": ["Batch 1", "Batch 2"]
</code></pre></td></tr></tbody></table>

#### Label Task Toggles

<table><thead><tr><th width="168">Toggle</th><th width="246">Description</th><th>Format</th></tr></thead><tbody><tr><td>Completion info</td><td>Name and data of who completed the task.</td><td><pre class="language-json"><code class="lang-json">"completedBy": "Labeler Name",
"completedAt": "2021-12-08T12:31:36.043Z"
</code></pre></td></tr><tr><td>Duration</td><td>How long it took to complete the task in milliseconds. Calculated from the moment the annotator opened the asset to the moment they clicked on <em>Submit</em>.</td><td><pre class="language-json"><code class="lang-json">"duration(ms)": 6429
</code></pre></td></tr><tr><td>Skip info</td><td>Whether or not the task was skipped.</td><td><pre class="language-json"><code class="lang-json">"isSkipped": false
</code></pre></td></tr><tr><td>Review</td><td>Information about the task's review step, if it was reviewed, including its status, who reviewed it, when, and how long it took to review.</td><td><pre class="language-json"><code class="lang-json">"review": {
  "status": "Fixed",
  "completedBy": "Reviewer Name",
  "completedAt": "2021-12-08T10:46:36.296Z",
  "duration(ms)": 36283
}
</code></pre></td></tr><tr><td>Status</td><td>Status of the task (To-Do, In Progress, Completed, Reviewed)</td><td><pre class="language-json"><code class="lang-json">"status": "Completed"
</code></pre></td></tr><tr><td>Update Info</td><td>If the task was updated after being labeled initially, information about who updated the task and when.</td><td><pre class="language-json"><code class="lang-json">"updatedBy": "Labeler Name",
"updatedAt": "2021-12-08T18:32:38.908Z"
</code></pre></td></tr><tr><td>Benchmark</td><td>Whether the task was marked as benchmark, and if so, the consensus score between all annotators completing this benchmark.</td><td><pre class="language-json"><code class="lang-json">"isBenchmark": false,
"benchmark": "60"
</code></pre></td></tr><tr><td>Issues</td><td>Data regarding issues opened on the task.</td><td><pre class="language-json"><code class="lang-json">"issues": [
        {
          "_id": "63db6ee989f9a600126e31ea",
          "status": "Open",
          "createdBy": {
            "_id": "614348d554e17400149964b1",
            "name": "Lorenzo Gravina"
          },
          "updatedAt": "2023-02-02T08:06:01.072Z"
        }
      ]
</code></pre></td></tr><tr><td>Annotation Metadata</td><td>Metadata regarding each individual annotation in the task.</td><td><pre class="language-json"><code class="lang-json">"metadata": {
  "createdAt": "2023-02-02T08:06:03.263Z",
  "createdBy": "Lorenzo Gravina",
  "updatedAt": "2023-02-02T08:06:07.276Z",
  "updatedBy": "Lorenzo Gravina"
}
</code></pre></td></tr><tr><td>Mask URLs</td><td>URL to a PNG image containing a segmentation mask for the task, if the Segmentation tool was used.</td><td><pre class="language-json"><code class="lang-json">"masks": [
  "https://apibeta.ango.ai/v2/mask?annotation=a47bbd2d4d8f3f086d25510&#x26;task=63c909a8819a2100129a22b0"
]
</code></pre></td></tr><tr><td>Segmentation Points</td><td>Coordinates of each segmentation point.<br><br>Warning: this adds significant size to the export and is disabled by default.</td><td><pre class="language-json"><code class="lang-json">"segmentation": {
  "zones": [
    {
      "region": [
        [
          266,
          644
        ],
        [
          267,
          643
        ],
        [
          267,
          640
        ]
      ],
      "holes": [
        [
          266,
          644
        ],
        [
          267,
          643
        ],
        [
          267,
          640
        ]
      ]
    }
  ]
}
</code></pre></td></tr><tr><td>B-Box Image Content</td><td>PNG image content, in plain text, of the contents of each PDF area tool.<br><br>Warning: this adds significant size to the export and is disabled by default.</td><td><pre class="language-json"><code class="lang-json">"content": {
  "image": "data:image/png;base64,iVBORw0KGgo / TRUNCATED / AAAANSUhEUgAAAH8AK5CYII="
}
</code></pre></td></tr></tbody></table>

{% hint style="info" %}
By default, segmentation points are not included in the export. Ensure you toggle its checkbox to see your segmentations in the export.
{% endhint %}

#### Send Link as an Email

When this is active, you will receive an email with a link to your export when it is ready.
