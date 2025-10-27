# Highlight Syntax

* Extract the most relevant fragments from a semantic text field and display them in the query response
* `number_of_fragments` is set to 2, which is the number of fragments for each hit

```
GET my-index/_search
{
"query": {
  "match": {
    "topic.semantic": "What is semantic search?"
  }
},
"highlight": {
 "fields": {
  "topic.semantic": {
     "number_of_fragments": 2,
      "order": "score"
   }
  }
 }
}
```

*

    <figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
