# Integrating Webhooks with Ango Hub

Ango Hub can fire webhooks with a JSON of the label contents to a URL of your choice when, in a project of your choice, said label gets created or updated.

### Setting Up Webhooks on Ango Hub

From your organization's _Organization_ page, enter the _Webhooks_ tab.

<figure><img src="../.gitbook/assets/image (372).png" alt=""><figcaption></figcaption></figure>

Click on the _Add Webhook_ button. A dialog will appear.

<figure><img src="../.gitbook/assets/image (336).png" alt=""><figcaption></figcaption></figure>

* **URL**: The URL Ango Hub will send a webhook to.
* **Project**: The project to monitor for changes.
* **Trigger**: When to send the webhook. _Label Completed_ triggers only when an annotator clicks on _Submit_, while _Label Updated_ triggers when an annotator clicks on _Save_.
* **Secret Key**: The secret key you will integrate and check in your endpoint.

Click on _OK_ to save and enable your webhook.

Now, whenever a label is completed, updated, or both (depending on your choice of trigger,) Ango Hub will send a POST request to the URL you provided with the contents of the created/updated label.

### Sample Webhook Server

Here is a sample server set up to receive webhooks from Ango Hub.

```python
import json

from flask import request, Flask
import hmac
import hashlib

secret = b'your_secret_key' # Secret Key you entered while adding the integration
app = Flask(__name__)


@app.route('/hook', methods=['POST'])  # Custom Endpoint
def hook():
    computed_signature = hmac.new(secret, msg=request.data, digestmod=hashlib.sha1).hexdigest()
    if request.headers["X-Hub-Signature"] != computed_signature:
        print("Error")  # Signature Mismatch means the webhook was triggered by a 3rd party.
    else:
        print(json.dumps(request.get_json(), indent=2))  # This is the actual label result
    return "ok"


if __name__ == '__main__':
    app.run(debug=True)
```

As webhooks cannot be sent to a local address, you will need to expose your local address to a public endpoint.
