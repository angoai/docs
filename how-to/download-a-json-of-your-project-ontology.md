# Download a JSON of your project ontology

1. [Get your API key](../sdk/sdk-documentation.md#obtaining-your-api-key). Note it somewhere.
2. [Download and install the \`ango\` package from pip](../sdk/sdk-documentation.md#how-to-install-the-ango-sdk).
3. Run the following Python script, substituting the project ID and the API key with your own

```python
import json
from ango.sdk import SDK

API_KEY = "<YOUR API KEY>"
PROJECT_ID = "<YOUR PROJECT ID>"

ango_sdk = SDK(API_KEY)

res = ango_sdk.get_project(PROJECT_ID)

json_object = json.dumps(res, indent=2)
print(json_object)
```

This script will print the category schema for the project.
