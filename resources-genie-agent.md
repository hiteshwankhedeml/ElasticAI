# Resources - Genie Agent

* Add resource ⇒ Genie Agent.
* Choose the genie agent
* Select the permission level:
  * Can view
  * Can run
  * Can manage
  * Can edit
* Specify the resource key
* Combine Genie Agents with other Databricks Apps resources to create more sophisticated data applications

```yaml
env:
  - name: GENIE_SPACE_ID
    valueFrom: genie-space # Use your custom resource key if different
```

```python
import os
from databricks.sdk import WorkspaceClient

# Access the Genie Agent using the injected environment variable
space_id = os.getenv("GENIE_SPACE_ID")

# Initialize the workspace client
w = WorkspaceClient()

# Start a conversation with a natural language query
response = w.genie.start_conversation_and_wait(
    space_id=space_id,
    content="What were our top-selling products last quarter?"
)

# Process the response (responses contain attachments with text, queries, and so on)
for attachment in response.attachments:
    print(f"Genie response: {attachment.text.content}")

# Continue the conversation with additional questions
follow_up = w.genie.create_message_and_wait(
    space_id=space_id,
    conversation_id=response.conversation_id,
    content="Can you break that down by product category?"
)
```
