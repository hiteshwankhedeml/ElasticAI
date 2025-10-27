# Retrievers: Traditional query

* Below is full-text query and converted to retriever

```
GET elastic_blogs-full-embeddings_e5/_search
{
 "query": {
   "match": {
     "body": "How to build a search AI experience"
   }
 }
}

GET elastic_blogs-full-embeddings_e5/_search
{
  "retriever": {
    "standard": {
      "query": {
        "match": {
          "body": "How to build a search AI experience"
        }
      }
    }
  }
}
```
