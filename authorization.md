# Authorization

* We can provide access of warehouse and unity catalog to service principal, but then it won't have the fine grained control, and all the users will have the same access
* Azure automatically inject the service principals credentials

```
import os

client_id = os.getenv('DATABRICKS_CLIENT_ID')
client_secret = os.getenv('DATABRICKS_CLIENT_SECRET')
```

* Below takes the service principal's access

```
from databricks import sql
from databricks.sdk.core import Config

cfg = Config()

conn = sql.connect(
    server_hostname=cfg.host,
    http_path="<your-warehouse-http-path>",
    credentials_provider=lambda: cfg.authenticate,
)

query = "SELECT * FROM main.sandbox.sales_customers LIMIT 1000"

with conn.cursor() as cursor:
    cursor.execute(query)
    df = cursor.fetchall_arrow().to_pandas()
    print(df.head())

conn.close()
```

* Azure Databricks forwards the user’s access token to the app, which uses the token to access resources on the user's behalf.&#x20;
* Azure Databricks enforces all permissions based on the user’s existing [Unity Catalog](https://learn.microsoft.com/en-us/azure/databricks/data-governance/unity-catalog/) policies.
*   Its forwarded in x-forwarded-access-token

    <figure><img src=".gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

```python
import streamlit as st
user_access_token = st.context.headers.get('x-forwarded-access-token')

from databricks import sql
from databricks.sdk.core import Config
from flask import request

cfg = Config()
user_token = request.headers.get("x-forwarded-access-token")

conn = sql.connect(
    server_hostname=cfg.host,
    http_path="<your-warehouse-http-path>",
    access_token=user_token
)

query = "SELECT * FROM main.sandbox.sales_customers LIMIT 1000"

with conn.cursor() as cursor:
    cursor.execute(query)
    df = cursor.fetchall_arrow().to_pandas()
    print(df.head())

conn.close()
```
