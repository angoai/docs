# Download your Segmentation Masks

{% hint style="info" %}
This feature is currently available for all image and video assets except DICOM.

To download DICOM segmentation masks, please follow the instructions [on this page](download-dicom-segmentation-masks.md).
{% endhint %}

1. After having uploaded and annotated your image files with a [Brush](../labeling/labeling-tools/brush-bucket.md) or [Segmentation](../labeling/labeling-tools/segmentation.md) labeling tool, go to the _Export_ tab.
2. Click on _Export_ to get the export.
3. In the export .json you've just downloaded, you'll find a URL in the `masks` field. It'll look something like this: `"masks": "https://api.ango.ai/v2/mask?annotation=8ff014e7e3c364e550c0303&task=63ff1df98027bc0012ce4c21"`
4. Go to your [account page](https://hub.ango.ai/account) and, from the API tab, retrieve your API key. If you don't have one, you'll be able to create one from the page as well.
5. Send a GET request to the URL you obtained in step 3, adding as header your API key.
   1. For example, using `curl`, you may send the following request to download the PNG of your brush data:

```
curl --location --request GET 'https://api.ango.ai/v2/mask?annotation=8ff014e7e3c364e550c0303&task=63ff1df98027bc0012ce4000' --header 'apikey: 15d3939b-0000-0000-0000-7de7f4f6ad43' --output mask.png
```
