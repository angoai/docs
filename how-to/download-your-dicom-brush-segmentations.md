# Download your DICOM Brush Segmentations

1. After having uploaded and annotated your DICOM files with a [Brush labeling tool](../labeling/labeling-tools/brush-bucket.md), go to the _Export_ tab.
2. Click on _Export_ to get the export.
3. In the export .json you've just downloaded, you'll find a URL in the `brushDataUrl` field. It'll look something like this: `"brushDataUrl": "https://angohub-public-assets.s3.eu-central-1.amazonaws.com/eca113b2-358a-4645-be26-9d7a52b27b5b.png"`
4. Go to your [account page](https://hub.ango.ai/account) and, from the API tab, retrieve your API key. If you don't have one, you'll be able to create one from the page as well.
5. Send a GET request to the URL you obtained in step 3, adding as header your API key.
   1. For example, using `curl`, you may send the following request to download the PNG of your brush data:

```
curl --location --request GET 'https://api.ango.ai/v2/mask?annotation=24528180ed95ae41e57a881&task=63ff2648f666310012250000' --header 'apikey: 15d3939b-0000-0000-0000-7de7f4f6ad43' --output mask.png
```
