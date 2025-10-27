# Retrievers: Semantic Query

* Both traditional queries and dense vector semantic queries use the `standard` type of a `retriever`

```
GET elastic_blogs-full-embeddings_e5/_search
{
  "retriever": {
    "standard": {
      "query": {
        "match": {
          "body.semantic": "How to build a search AI experience"
        }
      }
    }
  }
}
```
