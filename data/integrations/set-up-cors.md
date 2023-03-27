---
description: >-
  Configure your CORS settings so that Ango Hub can safely connect to your
  buckets.
---

# Set up CORS

By default, Ango Hub cannot request resources from your cloud storage and display them in the browser due to CORS policy restrictions. To solve this, Ango Hub's domains need to be included in the CORS headers.

Here's how you can add Ango's domains to your CORS headers.

### AWS S3

1. From your AWS account, go to the S3 Management Console.
2. Click on the bucket you'd like to connect.
3. Go to the permissions tab.
4. In the CORS section, click on Edit.
5. Paste the following text in the field that pops up:

```json
[
    {
        "AllowedHeaders": [
            "*"
        ],
        "AllowedMethods": [
            "GET", "POST", "PUT", "HEAD"
        ],
        "AllowedOrigins": [
            "https://api.ango.ai",
            "https://hub.ango.ai"
        ],
        "ExposeHeaders": []
    }
]
```

&#x20;  6\. Click on Save changes.

For more on setting up CORS on AWS S3, check out these [AWS docs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/enabling-cors-examples.html).

### Google Cloud Platform (GCP)

1. Log in to the GCP console.
2. Click on _Activate Cloud Shell_ in the top-right corner
3. In Cloud Shell, enter the following command:

```
echo '[{"origin": ["https://api.ango.ai","https://hub.ango.ai"],"method": ["GET", "POST", "PUT", "HEAD"],"responseHeader": ["Content-Type","Access-Control-Allow-Origin"]}]' > cors-config.json
```

&#x20; 4\. Apply the CORS configuration to the bucket with the following command:

```
gsutil cors set cors-config.json gs://<bucket-name>
```

&#x20; 5\. Check the CORS configuration with the following command:

```
gsutil cors get gs://<bucket-name>
```
