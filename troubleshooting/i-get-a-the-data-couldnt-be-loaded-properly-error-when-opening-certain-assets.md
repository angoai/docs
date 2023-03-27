# I get a 'The data couldn't be loaded properly' error when opening certain assets

This is likely to be an issue with how CORS is set up in the bucket where your assets are located.

In order for Hub to display your assets in AWS S3 or GCP, you need to set up CORS following the steps outlined [in this page](../data/integrations/set-up-cors.md). Try to open the assets again after setting up CORS as mentioned in the page.

If you still see the error, please open a ticket through our built-in help system, clicking on the question mark located at the top right of the screen.
