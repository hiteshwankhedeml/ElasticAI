# Configure Network

* You can configure both ingress (incoming) and egress (outgoing) traffic rules using a combination of IP access lists, front-end private connectivity, and network policies.
* Azure Databricks deploys apps on the serverless compute plane, where they receive traffic directly.

1. Initial user requests to an Azure Databricks app initiate OAuth authentication with the control plane to validate the session and authorize access to the app.
2. Upon successful authentication, all subsequent requests are routed directly to the serverless compute plane without traversing the control plane.

