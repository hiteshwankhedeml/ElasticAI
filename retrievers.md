# Retrievers

* With traditional queries, the query is part of the overall search API call.&#x20;
* Retrievers differ by being designed as standalone entities, allowing more flexibility when designing search strategies.&#x20;
* Retrievers allow a `_search` to perform various types of searching in a single request
* Include traditional search, semantic search as well as other types



**RRF:**

* Reciprocal Rank Fusion
* Combines results from multiple retrievers by defining each as a retriever, and then merging and ranking the results
