# Apps

* Add another [Databricks app](https://learn.microsoft.com/en-us/azure/databricks/dev-tools/databricks-apps/) as a resource for your app so it can communicate with other deployed apps.&#x20;
* This enables app-to-app interactions, such as calling another app's AP
* App ⇒ Add resource ⇒ Add App
* Azure Databricks grants your app's [service principal](https://learn.microsoft.com/en-us/azure/databricks/dev-tools/databricks-apps/auth#app-authorization) the `CAN USE` permission on the target app.
* To get the target app's URL, resolve the name using the Azure Databricks SDK.

```yaml
env:
  - name: MY_OTHER_APP
    valueFrom: app # Use your custom resource key if different
```

```python
import os
from databricks.sdk import WorkspaceClient

# Access the target app name from the environment variable
w = WorkspaceClient()
other_app = w.apps.get(name=os.environ["MY_OTHER_APP"])

# Get the target app's URL
url = other_app.url  # e.g. "https://my-other-app-12345.cloud.databricksapps.com"
```
