# Create a 'rerank' inference Endpoint

* `rerank` as the type of inference task.
* `elasticsearch` for the `service`, and the following values for `service_settings`:
  * `"num_allocations": 1`
  * `"num_threads": 1`
  * `"model_id": ".rerank-v1"`

```
PUT _inference/rerank/elastic-rerank
{
    "service": "elasticsearch",
    "service_settings": {
        "num_allocations": 1,
        "num_threads": 1,
        "model_id": ".rerank-v1"
    }
}
```
