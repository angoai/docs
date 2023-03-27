---
description: Hub supports IAM delegated access integration for our cloud users.
---

# Integrations

Ango Hub supports connecting your cloud data storage through IAM delegated access.

![Click on the "Organization" link at the top, then enter the "Integrations" tab.](<../../.gitbook/assets/image (379).png>)

With Delegated Access, you can securely host your unlabeled assets in your cloud storage provider, while being able to view them and label them on Hub, giving Hub the minimal access necessary to work with them.

### Supported Cloud Providers

<table><thead><tr><th>Provider</th><th>Setup Instructions</th><th data-hidden></th></tr></thead><tbody><tr><td>Amazon S3</td><td><a href="https://docs.ango.ai/data/importing-assets/importing-private-cloud-assets-aws">Here</a></td><td></td></tr><tr><td>Google Cloud Platform</td><td><a href="https://docs.ango.ai/data/importing-assets/importing-private-cloud-assets-gcp">Here</a></td><td></td></tr></tbody></table>

### Supported Data Types

<table><thead><tr><th>Data Type</th><th data-type="checkbox">Supported</th></tr></thead><tbody><tr><td>Images</td><td>true</td></tr><tr><td>Video</td><td>true</td></tr><tr><td>Text</td><td>true</td></tr><tr><td>Audio</td><td>true</td></tr><tr><td>DICOM</td><td>true</td></tr><tr><td>PDF</td><td>true</td></tr></tbody></table>

### How does Delegated Access work?

You will need to set up an IAM role in your cloud provider's dashboard, and allow Ango Hub to take upon the IAM role. You will then define the policies determining what the Hub IAM account will be able to access and do. This way, Hub can access your stored data securely and only within the bounds of what you allow.

![](../../.gitbook/assets/ango-iam.png)

Delegated Access is the preferred way to connect cloud data to Hub because of its adaptability. You can set policies allowing Hub access granularly. For example, you can allow access to all buckets, only one bucket, or only one asset in one bucket. You can set up multiple IAM integrations for different projects with different permissions, and so on.

### How does Ango Hub access your data?

#### Asset

Ango Hub will only access your data when it is necessary to display it within Hub, for example, during labeling.

To display an asset, Hub requests a temporary signed URL from the Ango backend. The backend will assume the role you have configured and generate a signed URL for the asset. The backend then passes that URL to the frontend, which then displays the asset using that temporary, expiring, signed URL.

#### Metadata

Hub will occasionally also need asset metadata, such as image dimensions, video length, etc. To do so, Hub will generate a temporary, expiring, signed URL the same way, download the asset, extract the metadata it needs (also known as processing), then instantly delete it.

All asset processing is done in Germany-based datacenters.

### IAM Delegated Access - Frequently Asked Questions

#### Does setting up an IAM integration change the way labels are stored?

No, annotations are stored in Ango's own storage even when the asset comes from an IAM integration. The only exception to this is if Hub was installed on-premises.

#### Does Ango Hub cache assets?

No. Ango Hub does not cache assets coming from IAM delegated access connections.

#### Can I quickly invalidate all live signed URLs?

Yes. Remove the "GetObject" permission from your permission policy for the role, and all live signed URLs will become invalid.
