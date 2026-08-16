# app.yaml

* Defines how your app runs.&#x20;
* If your app requires a different entry point or environment-specific configuration, you can include this optional file in your project to override the default behavior.

**Streamlit app:**

```yaml
command: ['streamlit', 'run', 'app.py']
env:
  - name: 'DATABRICKS_WAREHOUSE_ID'
    value: 'quoz2bvjy8bl7skl'
  - name: 'STREAMLIT_GATHER_USAGE_STATS'
    value: 'false'
```

**Flask app:**

```yaml
command:
  - gunicorn
  - app:app
  - -w
  - 4
env:
  - name: 'VOLUME_URI'
    value: '/Volumes/catalog-name/schema-name/dir-name'
```
