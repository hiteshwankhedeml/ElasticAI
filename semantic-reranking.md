# Semantic Reranking

* Reranking is the process of reordering the top-k search result set using a trained model in order to promote the most relevant hits
* The `text_similarity_reranker` retriever focuses on reranking search results to improve relevance based on text similarity. It will perform reranking on the top hits by calling a rerank inference endpoint that you will define using the Elastic Rerank model
*
