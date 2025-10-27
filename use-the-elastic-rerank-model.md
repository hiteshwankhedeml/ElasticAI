# Use the elastic Rerank model

* &#x20;&#x20;

```
GET elastic_blogs-full-embeddings_e5/_search
{
"retriever": { // Retriever query
 "text_similarity_reranker": { // Outermost retriever will perform reranking
  "retriever": {
    "rrf": {
      "retrievers": [
        {
          "standard": {
            "query": {
              "match": {
                "body.semantic": "How does semantic search work?"
              }
            }
          }
        },
        {
          "standard": {
            "query": {
              "match": {
                "body": "How does semantic search work?"
              }
            }
          }
        }
      ],
        "rank_window_size": 100,
        "rank_constant": 60
     }
    },
    "field": "body",
    "inference_id": "elastic-rerank",
    "inference_text": "The best search performance"
    }
  },
  "highlight": {
    "fields": {
      "body.semantic": {
        "order": "score",
        "number_of_fragments": 2
      },
      "body": {
        "order": "score",
        "number_of_fragments": 2
      }
    }
  }
}
```

