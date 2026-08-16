# Databricks Apps - Steps

**Step 1: Install Dependencies:**

* [https://learn.microsoft.com/en-us/azure/databricks/dev-tools/databricks-apps/configure-env](https://learn.microsoft.com/en-us/azure/databricks/dev-tools/databricks-apps/configure-env)

**Step 2: Create the app:**

* Databricks App ⇒ Create ⇒ Choose Hello World template
* Name the app and create

**Step 3: View the app:**

* It starts automatically and displays a URL that you can use to preview it

**Step 4: Copy the app to local:**

* Navigate to the local folder and run below
* The first command exports three files from your workspace to your local directory
* The second command starts a sync process that watches for local file changes and automatically uploads them to your workspace

```
databricks workspace export-dir /Workspace/Users/my-email@org.com/databricks_apps/gradio-hello-world_2026_02_03-22_34/gradio-hello-world-app .

...
Export complete

gradio-hello-world % databricks sync --watch . /Workspace/Users/my-email@org.com/databricks_apps/gradio-hello-world_2026_02_03-22_34/gradio-hello-world-app

...
Initial Sync Complete
```

**Step 5: Modify and test the app locally:**

* databricks apps run-local --prepare-environment --debug
* This command installs all dependencies and prepares the virtual environment, then starts the app and the debugger on port 5678.

**Step 6: Re-deploy the app to your workspace:**

* Copy the command under Deploy to Databricks Apps on the app overview page

**Step 7: Deploy from a Git repository:**

* For a more scalable workflow, push your app code to a Git repository and deploy from there
* Initialize git
* Configure the git on your app
* For private repositories, add a Git credential for the app's service principal
* Deploy from Git

```
databricks apps create-update gradio-hello-world \
   --json '{"update_mask": "git_repository", "git_repository": {"url":
    "https://github.com/your-org/gradio-hello-world", "provider": "gitHub"}}'
```

```
databricks apps deploy gradio-hello-world \
   --json '{"git_source": {"branch": "main"}}'
```
