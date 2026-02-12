# Cross-Domain Restaurant Recommendation System

A multi-modal recommendation framework built using Yelp data.

This project investigates how user reviews, ratings, and restaurant categories in Philadelphia can be used to recommend restaurants in surrounding cities where users have little or no prior activity. The system integrates Natural Language Processing (NLP), Hybrid Recommender Systems, Social Network Analysis (SNA), and Time Series Forecasting into a unified analytical pipeline.

------------

## Problem Statement

Traditional recommender systems rely on user interactions within a single domain. This project explores whether user taste profiles constructed from one city (Philadelphia) can be transferred to another city to generate meaningful cross-domain recommendations. he core objective is to model user preferences using review-derived features and evaluate how effectively those preferences generalize geographically.

------------

## Methodology

### 1. Natural Language Processing

- Category normalization and text cleaning
- Custom tokenization
- Stopword removal
- TF-IDF feature engineering
- Restaurant feature matrix construction

These features serve as the foundation for user taste modeling.

------------

### 2. Hybrid Recommender System

User taste profiles were constructed as weighted averages of restaurant feature vectors, where weights were based on user ratings:

- Positive weights for highly rated restaurants
- Neutral weights for average ratings
- Negative weights for poorly rated restaurants

Recommendations were generated using a hybrid scoring mechanism:

Blending score= α × Similarity + (1 − α) × Credibility

Where:

- Similarity = cosine similarity between user profile and candidate restaurant
- Credibility = Bayesian-adjusted rating score

Evaluation was performed using a hold-out domain simulation with bridge users.

Metrics:
- Precision@K
- Recall@K
- Mean Average Precision (MAP@K)

------------

### 3. Social Network Analysis

User taste vectors were used to construct a similarity graph:

- Pairwise cosine similarity matrix
- Threshold-based graph construction
- Louvain community detection (modularity optimization)
- Centrality-based influencer detection

This analysis revealed structured taste communities and preference clustering patterns.

------------

### 4. Time Series Forecasting

For users not belonging to any detected community:

- Monthly review counts were aggregated
- Log transformation applied to stabilize variance
- STL decomposition performed
- ETS model selected via grid search
- Residual diagnostics conducted (ADF & Portmanteau tests)

The forecasting model demonstrated strong fit and stable residual behavior.

------------

## Key Results

- Cross-domain recommendation achieved strong baseline performance.
- Restaurant credibility proved more predictive than pure content similarity.
- Five distinct user preference communities were identified.
- Influencer detection revealed central users within communities.
- ETS forecasting model demonstrated good fit and stationary residuals.

------------

## Business & Analytical Impact

- Demonstrates how user preference modeling can support geographic expansion strategies.
- Shows how credibility-adjusted scoring prevents misleading recommendations driven by sparse data.
- Identifies structured customer taste communities for targeted marketing segmentation.
- Forecasts independent user activity patterns to understand engagement evolution over time.

------------

## Tech Stack

- Python
- Pandas / NumPy
- Scikit-learn
- NetworkX
- Statsmodels
- Matplotlib / Seaborn
- Jupyter Notebook

------------

## Future Improvements

- Integrate structured restaurant attributes (price, ambiance, services)
- Use transformer-based embeddings (e.g., BERT) for review semantic modeling
- Explore graph-based recommender extensions
- Possible deployment as an interactive web application

------------

## Academic Context

This project was developed as part of the Master's in Data Science and Engineering at  
FEUP – Faculty of Engineering, University of Porto (Portugal).

------------

### Team
- Carolina Madaleno
- Jorge Gamonal
- Ricardo Jorge Correia 
- Vitor Souza
