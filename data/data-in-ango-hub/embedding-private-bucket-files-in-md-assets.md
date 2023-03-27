# Embedding Private Bucket Files in MD Assets

Ango Hub supports uploading assets in the powerful Markdown format, allowing you to create assets styled and structured with HTML and CSS.

You can embed external files with an URL in a Markdown file, for example:

```markdown
# Heading
Subtitle

<div style="display:flex;flex-wrap: wrap;">
  <div style="width:210px;margin:10px">
    <div style="width:210px">
      <a href="https://link.com" target="_blank">
        <img src="https://private-assets.link/20210408-DSC_4015.jpg" width="200" />
      </a>
    </div>
    <div style="font-size:20px;font-weight:500;margin:10px 0 0 0">
      Text Under Image
    </div>
  </div>
</div>
```

The above Markdown file contains a link to an external image. That image will be loaded when the labeler loads the Markdown asset.

It is also possible, if you have [created an integration](../importing-assets/importing-private-cloud-assets-aws.md) between your private bucket on AWS S3 or GCP, to link to files in your private bucket and have them show in your Markdown file.

## How to Embed Private Bucket Files in Markdown Assets

First, create an integration from the _Integration_ tab of your [Organization page](https://hub.ango.ai/organization). [You can read how to do so here](../importing-assets/importing-private-cloud-assets-aws.md).

Then, from the same page, copy the integration ID of your newly created integration, by clicking on the "Copy" button next to the ID:

<figure><img src="../../.gitbook/assets/image (423).png" alt=""><figcaption></figcaption></figure>

In your Markdown file, append `integrationId=1111111`to the end of your private asset URLs, where 111111 is the integration ID you've just copied to your clipboard.

As an example, this is what such a Markdown asset would look like:

```markdown
# Heading
Subtitle

<div style="display:flex;flex-wrap: wrap;">
  <div style="width:210px;margin:10px">
    <div style="width:210px">
      <a href="https://link.com" target="_blank">
        <img src="https://private-assets.link/20210408-DSC_4015.jpg?integrationId=123456789123" width="200" />
      </a>
    </div>
    <div style="font-size:20px;font-weight:500;margin:10px 0 0 0">
      Text Under Image
    </div>
  </div>
</div>
```
