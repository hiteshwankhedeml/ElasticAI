# Databricks Apps

* Build and deploy secure data and AI applications
* Apps run on the serverless platform
* Develop apps locally using Python or Node.js, then deploy them to a workspace and move them between workspaces
* Apps are billed per hour of compute time while running, based on provisioned capacity
* Setup - [https://learn.microsoft.com/en-us/azure/databricks/dev-tools/databricks-apps/configure-env](https://learn.microsoft.com/en-us/azure/databricks/dev-tools/databricks-apps/configure-env)
* Runs as a containerized service on the Azure Databricks serverless platform
* Apps belong to a specific workspace, they can access workspace-level resources
* Databricks automatically assigns each app a unique URL when you create it
  * https://\<app\_name>-\<workspace-id>.\<region>databricksapps.com
* An app template is a prebuilt scaffold that helps developers start building apps quickly using a supported framework
* Databricks Apps run in a pre-configured system environment managed by Azure Databricks
* databricks.yml ⇒ Azure Databricks-native services that an app depends on, such as SQL warehouses, model serving endpoints, jobs, secrets, or volumes.
* Two stages of configuring app resources:
  * **Declaration (development):**
    * Declared in databricks.yml
  * **Configuration (deployment):**
    * During deployment, use the Databricks Apps UI to configure the declared resources with actual workspace-specific instances
* **App Status:**
  * Running
  * Stopped
  * Deploying
  * Crashed
* **App Authorization:**
  * Azure Databricks automatically creates a service principal for each app.&#x20;
  * This service principal acts as the app’s identity and is granted permissions by the app developer.&#x20;
  * All users of the app share this identity and have access to the same set of permissions
* **User authorization:**
  * Users must belong to the Azure Databricks account where the app is deployed.&#x20;
  * After signing in through single sign-on (SSO), the app can use the user's credentials to access governed resources like a SQL warehouse.&#x20;
  * This allows the app to respect the fine-grained permissions managed by Unity Catalog without granting those permissions to the app’s service principal.
