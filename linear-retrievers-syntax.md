# Linear Retrievers - Syntax

* `body.semanic` has a `weight` of `1.5`
* `body` has a `weight` of `5`
* the `normalizer` is set to `minmax` for both retrievers

```
GET elastic_blogs-full-embeddings_e5/_search
{
  "retriever": {
    "linear": {
      "retrievers": [
        {
          "retriever": {
          "standard": {
            "query": {
              "match": {
                "body.semantic": "The best search performance"
              }
            }
            }
          },
          "weight": 1.5,
	        "normalizer": "minmax"
        },
        {
         "retriever": {
          "standard": {
            "query": {
              "match": {
                "body": "The best search performance"
              }
            }
            }
          },
          "weight": 5,
	        "normalizer": "minmax"
        }
      ],
      "rank_window_size": 100
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
  },
  "_source": "false"
}
```
