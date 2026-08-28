# FAISS Semantic Search – Reflection Questions

## Q1: What is the difference between IndexFlatL2 and IndexFlatIP in FAISS? When would you use each?

`IndexFlatL2` performs nearest-neighbour search using L2 (Euclidean) distance. A lower distance indicates that two vectors are closer and therefore more similar.

`IndexFlatIP` performs search using the inner product between vectors. A higher inner product indicates a better match.

I would use `IndexFlatL2` when similarity is measured using Euclidean distance. I would use `IndexFlatIP` when working with inner-product similarity. If embeddings are L2-normalized, inner product can be used to represent cosine similarity.

---

## Q2: Why do we normalize embeddings before adding them to FAISS when we want cosine similarity?

Cosine similarity measures the similarity between two vectors based on the angle or direction between them rather than their magnitude.

By L2-normalizing the embeddings, each vector has a magnitude of 1. Once the vectors are normalized, the relationship between L2 distance and cosine similarity can be used for similarity search.

In this project, both the knowledge base embeddings and the query embedding are normalized before searching so that vectors are compared based mainly on their direction.

---

## Q3: FAISS uses ANN (Approximate Nearest Neighbour) search. What does "approximate" mean here and why is it acceptable?

Approximate Nearest Neighbour search means that instead of always checking every vector and guaranteeing the mathematically exact nearest neighbour, the search can use optimized indexing techniques to quickly find very close matches.

This is acceptable because, in large vector databases containing millions or billions of embeddings, exact search can become computationally expensive. ANN provides a trade-off between search accuracy and speed.

In most real-world semantic search and RAG applications, retrieving highly relevant results quickly is often more important than finding the exact nearest neighbour every time.
