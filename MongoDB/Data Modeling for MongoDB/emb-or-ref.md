# Embedding or Referencing Guidelines

Go through the questions below to determine if entities should be embedded or referenced to one another. Answer yes or no for each question.

- Yes == +1 embedding
- No == +1 referencing

After answering, tally up the points to determine your answer.

### Simplicity

Would keeping the pieces of information together lead to a simpler data model and code?

### Go Together

Do the pieces of information have a "has-a", "contains" or similar relationship?

### Query Atomicity

Does the application query the pieces of information together?

### Update Complexity

Are the pieces of information updated together?

### Archival

Should the pieces of information be archived at the same time?

### Cardinality

Is there a high cardinality (current or growing) in the child side of the relationship?

> "NO" is a point for embedding.

### Data Duplication

Would data duplication be too complicated to manage and undesired?

> "NO" is a point for embedding.

### Document Size

Would the combined size of the pieces of information take too much memory or transfer bandwidth for the application?

> "NO" is a point for embedding.

### Document Growth

Would the embedded piece grow without bound?

> "NO" is a point for embedding.

### Workload

Are the pieces of information written at different times in a write-heavy workload?

> "NO" is a point for embedding.

### Individuality

For the child side of the relationship, can the pieces exist by themselves without a parent?

> "NO" is a point for embedding.