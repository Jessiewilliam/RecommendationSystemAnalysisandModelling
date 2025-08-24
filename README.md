# RecommendationSystemAnalysisandModelling
📊 Recommendation System Analysis & Modeling

This project develops and evaluates a Recommendation System using user–item interaction data. It follows the CRISP-DM methodology to provide insights, build models, and generate recommendations across different domains such as e-commerce, content, and services.

🚀 Project Overview

Recommendation systems power modern platforms like Amazon, Netflix, and Spotify, delivering personalized experiences.
This project leverages historical interaction data (events.csv, item_properties, category_tree) to:

Enhance user engagement and retention

Improve conversion rates

Provide diverse and scalable recommendations

📂 Project Structure
📁 data/
 ├── events.csv
 ├── item_properties_part1.csv
 ├── item_properties_part2.csv
 └── category_tree.csv

📁 notebooks/
 └── RecommendationSystemAnalysisandModelling.ipynb   # Main analysis

📁 outputs/
 └── visualizations, metrics, and trained models

🧠 CRISP-DM Methodology
1. Business Understanding

Develop personalized recommendations to improve engagement.

Address multiple use cases: product, content, service.

Balance accuracy vs diversity to avoid repetitive suggestions.

2. Data Understanding

events.csv: user interactions (view, add-to-cart, transaction).

item_properties: metadata (brand, category, availability).

category_tree: hierarchy of item categories.

✅ Key EDA Insights:

Views dominate interactions – most users only browse, few purchase.

Item popularity is skewed – top 10% of items drive most transactions.

Peak activity occurs evenings & weekends – strong behavioral cycles.

Items cluster together – collaborative filtering surfaces bundles.

Content metadata helps cold-start items – properties like brand/category are crucial.

3. Data Preparation

Filtered meaningful events: view, addtocart, transaction.

Assigned weights (view=1, addtocart=3, transaction=5).

Built user–item interaction matrix with 20k top users & items (for memory safety).

Pivoted item properties into wide-format metadata.

Cleaned missing values in categorical/numeric columns.

4. Modeling

Collaborative Filtering (Item–Item Similarity):

Constructed sparse user–item matrix.

Applied cosine similarity to compute item–item relationships.

Generated top-N recommendations per user.

Content-Based Filtering (TF-IDF on item metadata):

Created "bag of properties" text for each item.

Applied TF-IDF + cosine similarity for metadata-driven item matching.

Used for cold-start items with no prior interactions.

5. Evaluation

Evaluated using Precision@K and Recall@K:

Precision@10: 0.1420  
Recall@10:    0.0975


✅ Interpretation: The recommender captures ~14% precision and ~10% recall at top-10 suggestions.

6. Deployment (Future Work)

Expose via an API for integration into platforms.

Real-time scoring using streaming data (e.g., Kafka + Spark).

Monitor feedback loops to retrain models periodically.

⚙️ Technologies Used

Python 3.11

Pandas / NumPy

Scikit-learn (cosine similarity, TF-IDF)

Matplotlib for visualization

Google Colab for computation

📊 Sample Visualization
# Distribution of Event Types
events['event'].value_counts().plot(kind='bar', figsize=(8,5), title="User Event Distribution")

✅ Recommendations

Boost conversion by retargeting frequent viewers with cart/buy nudges.

Highlight trending items – top 10% items generate most interactions.

Time-based personalization – push recommendations during evening peaks.

Cold-start solution – rely on content metadata for new items.

Hybrid approach – combine collaborative + content-based for robustness.

📁 Files Included

RecommendationSystemAnalysisandModelling.ipynb – Main notebook (EDA, modeling, evaluation).

events.csv, item_properties_part1.csv, item_properties_part2.csv, category_tree.csv – Raw data.

Visualizations & metrics (outputs).

👩‍💻 Author

Jessica William

📜 License: For educational and analytical purposes only.
