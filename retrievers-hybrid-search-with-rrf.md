# Retrievers: Hybrid Search with RRF

* Reciprocal rank fusion (RRF) is a method for combining multiple result sets with different relevance indicators into a single result set.
*

    <figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
* The `rank_window_size` parameter specifes the number of top results to consider from each child retriever. Higher values can improve relevance but may impact performance.
* The `rank_constant` parameter specifies the constant `k` in the RRF formula that we discussed in the beginning of this section.

```
GET elastic_blogs-full-embeddings_e5/_search
{
  "retriever": {
    "rrf": {
      "retrievers": [
        {
          "standard": {
            "query": {
              "match": {
                "body.semantic": "The best search performance"
              }
            }
          }
        },
         {
          "standard": {
            "query": {
              "match": {
                "body": "The best search performance"
              }
            }
          }
        }
      ],
      "rank_window_size": 100,
      "rank_constant": 60
    }
  }
}
```
