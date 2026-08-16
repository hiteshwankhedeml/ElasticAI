# Create the inference endpoint

* The service is `elasticsearch` and the data uses `e5` (dense vectors) for the embeddings.
* The field `body` is mapped as a multi-field, where `body.semantic` is of type `semantic_text`
*

```
PUT _inference/text_embedding/my-e5-endpoint
{
  "service": "elasticsearch",
  "service_settings": {
    "num_allocations": 1,
    "num_threads": 1,
    "model_id": ".multilingual-e5-small_linux-x86_64"
  }
}

# To check the end-point configuration
GET _inference/my-e5-endpoint

# To see the mappings
GET elastic_blogs-full-embeddings_e5/_mapping

# View the data
GET elastic_blogs-full-embeddings_e5/_search



```
