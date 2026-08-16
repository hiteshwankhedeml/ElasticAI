# App Development

* App files can't exceed 10 MB. If any file in the app directory exceeds this limit, deployment fails with an error.

**Apps Environment:**

* Ubuntu 22.04 LTS
* Python 3.11
* uv 0.10.2
* By default, each app can use up to 2 virtual CPUs (vCPUs) and 6 GB of memory



* The Databricks Apps runtime automatically sets port and host variables for supported Python frameworks.&#x20;
* You don't need to configure these manually. All port variables are set to the value of `DATABRICKS_APP_PORT`.



