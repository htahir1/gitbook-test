---
description: Add reranking to your RAG inference for better retrieval performance.
---

# Reranking for better retrieval

Rerankers are a crucial component of retrieval systems that use LLMs. They help improve the quality of the retrieved documents by reordering them based on additional features or scores. In this section, we'll explore how to add a reranker to your RAG inference pipeline in ZenML.

In previous sections, we set up the overall workflow, from data ingestion and preprocessing to embeddings generation and retrieval. We then set up some basic evaluation metrics to assess the performance of our retrieval system. A reranker is a way to squeeze a bit of extra performance out of the system by reordering the retrieved documents based on additional features or scores.

![](../../../.gitbook/assets/reranking-workflow.png)

As you can see, reranking is an optional addition we make to what we've already set up. It's not strictly necessary, but it can help improve the relevance and quality of the retrieved documents, which in turn can lead to better responses from the LLM. Let's dive in!

<figure><img src="https://static.scarf.sh/a.png?x-pxid=f0b4f458-0a54-4fcd-aa95-d5ee424815bc" alt="ZenML Scarf"><figcaption></figcaption></figure>
