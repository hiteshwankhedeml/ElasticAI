# Resources - Unity Catalog

* Unity Catalog connections manage credentials and authentication details
* Add resource ⇒ UC connection.
* Choose a Unity Catalog connection from the list of available connections
* Grant USE CONNECTION PRIVELEGE (grants your app's [service principal](https://learn.microsoft.com/en-us/azure/databricks/dev-tools/databricks-apps/auth#app-authorization) the `USE CONNECTION` privilege)
* Azure Databricks exposes the connection name through environment variables that you can reference using the `valueFrom` field.

```yaml
env:
  - name: UC_CONNECTION_NAME
    valueFrom: connection # Use your custom resource key if different
```

```python
import os
import requests
from databricks.sdk import WorkspaceClient

# Access the connection name
connection_name = os.getenv("UC_CONNECTION_NAME")

# Initialize workspace client
w = WorkspaceClient()

# Make HTTP request through the connection
response = requests.post(
    f"{w.config.host}/api/2.0/unity-catalog/connections/{connection_name}/proxy/api/v1/resource",
    headers={
        **w.config.authenticate(),
        "Content-Type": "application/json",
        "extra_header_key": "extra_header_value",
    },
    json={"key": "value"},
)

# Process the response
print(response.text)
```
