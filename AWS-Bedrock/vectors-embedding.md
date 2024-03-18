# Vectors & Embedding

The following document pertains to vectors/embedding and their related terminilogies.

## Vectors

Vectors are a list of numbers.
- arrays
  - [1,6]
- Vectors are also a mathematical representation of documents, words or sentences.

## Embedding

Embedding allows us to convert documents, words or sentences into Vectors with thousands of dimensions.
- Amazon Titan Embeddings is the service that AWS provides to do this.

## Data Chunking / Text Splitting

Data Chunking allows you to split a document that is too large into smaller chunks by:
- token, character or code

## Vector Store

A type of database that allows you to store Vectors. For example:
- Pinecone, Chroma DB, etc.

## Vector Search

A user asks a question, titan turns it into an embedding, then finds the others vectors that are similair to the embedding.

### Cosine Similarity (Similarity Search)

You basically use geometry to find the similarities between different vectors.

## Nearest Neighbor Algorithm (KNN)

Another algorithm to determine similarity between vectors. This algorithm however is a supervised ML algorithm used in classification and regression. It places the  vector embedding on a graph and finds it's nearest neighbor.
- KNN unfortunately is high in cost since it compares multiple neighbors so ANN should be used.
