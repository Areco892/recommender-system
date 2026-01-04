# Recommender System

## Overview
This project implements an item-based collaborative filtering recommender system for e-commerce. It uses user interactions, including product views, add to cart, and purchases. With these interactions, the recommender can be used to generate personalized top-N product recommendations. The system emphasizes strong user actions (like purchases) while preventing repeated weak signals (like multiple views) from dominating, producing interpretable and scalable recommendations.

## Objective
Users struggle to discover relevant products, leading to lower engagement and conversion. The goal is to build a recommendation system that personalizes product suggestions based on user behavior. 

## Data Description
Dataset: https://www.kaggle.com/datasets/waqi786/e-commerce-clickstream-and-transaction-dataset
The important features from the dataset are:
- UserID: unique identifier for each user
- ProductID: unique identifier for each product
- EventType: type of interaction - product view, add to cart, purchase

## Features
- Weighted user interactions with caps for repeated weak signals.
- Construction of user-item and item-item similarity matrices.
- Personalized recommendation function that aggregates item similarity weighted by user interation strength.
- Excludes items already interacted with, focusing on new and relevant recommendations.

## Methodology
1) Interaction weighting: each event type is assigned a weigth reflecting its importance.
   - product view -> 3
   - add to cart -> 5
   - purchase -> 8
   - Weak repeated actions are capped to prevent them from dominating
2) User-Item Matrix
   - rows = users, columns = products
   - values = summed weighted interactions for each user-item pair
3) Item-Item Similarity Matrix
   - Cosine similarity between products based on user-item matrix
   - Captures how similarly users interact with two items
4) Recommendation Function
   - For a given user:
     - Aggregate weighted similarity scores from items the user interacted with
     - Exclude already-interacted items
     - Rank remaining items -> top-N recommendations
    
## Key Insights
- Strong actions dominate weak ones, creating more meaningful recommendations
- Repeated weak actions (views) are capped to prevent misleading influence
- Cosine similarity works well for weighted interactions

