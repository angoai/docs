# Download DICOM Segmentation Masks

{% hint style="warning" %}
In previous versions, Hub automatically generated and provided links to ready-made segmentation .png masks for DICOMS in the export. This has now been deprecated.

The following workaround, however, will provide the exact same result.
{% endhint %}

{% hint style="info" %}
To obtain masks for annotations created with the Brush tool, simply activate the _Mask URLs_ export field  and click on the _brushDataUrl_ URL in the export.
{% endhint %}

1. After having uploaded and annotated your DICOM files with a [Segmentation labeling tool](../labeling/labeling-tools/segmentation.md), go to the _Export_ tab.
2. In the Export tab, ensure the _Segmentation Points_ toggle in the _Fields_ dropdown is active.
3. Click on _Export_ to get the export, and save the resulting .json file somewhere you'll remember.
4. Download [this .zip archive](https://github.com/angoai/convert-to-single-mask/archive/refs/heads/main.zip) containing our scripts to create masks from polygon or segmentation exports. Extract it, and move your .json file to this folder.
5. With a text editor, open the file `2_segmentation_to_single_mask.py` and replace the placeholder variable contents with your own data.
6. With a terminal, navigate to the folder and run `pip install -r requirements.txt` to install the required packages to run the Python script.
7. Within the terminal, run `python 2_segmentation_to_single_mask.py` to extract a .png mask from your export.
