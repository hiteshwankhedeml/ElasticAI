# Retrievers: Hybrid Search with RRF - Highlight

* `highlight` displays two fragments for each field: `body.semantic` and `body`.

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

*

    <figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
