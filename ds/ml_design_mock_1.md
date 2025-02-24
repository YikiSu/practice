# Question

It wants to improve personalized restaurant recommendations for users based on their past interactions, preferences, and reviews.

How would you design a machine learning system to recommend the top 10 restaurants for a user?

# Objective
(1) Goal: want to improve engagement or improve click-through rate or increase reservations?\
(2) how to define as a good recommendation? (popularity/user preference/?)\
(3) constraints? (scalability/real-time latency/cold-start problem?)

# Data Source
(1) User data: location, past interactions, reviews written, ratings given
  - use embeddings

(2) Restaurant data: cusine type, reservations, review
  - use embeddings

(3) Interaction data: clicks, searchs, reservation, review statement

# Model selection
1. collaborative filtering
   - Matrix factorization (SVD, ALS, PCA) for explicit ratings
2. content-based filtering
   - TF-IDF or embeddings to match restaurants with similar reviews, cusine or price range
3. Hybrid
   - could use a boosting model to rank restuarants based on multiple signals

# Model training and deployment
(1) offline training: batch prediction\
(2) real-time predictions: FastAPI and etc\
(3) Use A/B testing to compare recommendation effectiveness

# Evaluation metrics
1. Offline metrics
   - Precision@K, Recall@K (for ranking quality)
   - diversity and novelty
2. Online metrics
   - click through rate
   - coversion rate
   - user engagement




