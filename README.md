# GameSeeker – A Personalized Game Recommendation Engine

## Table of Contents
- [Project Overview](#-project-overview)
- [Problem Area](#-problem-area)
- [Proposed Data Science Approach](#-proposed-data-science-approach)
- [Impact of the Solution](#-impact-of-the-solution)
- [Datasets Overview/Concerns/EDA Findings](#-datasets-overview/concerns/eda-findings)
- [Next Step](#-next-step)
- [Sprint 2: Game Purchase Behavior Prediction and Recommendation](#sprint-2-game-purchase-behavior-prediction-and-recommendation)
- [Project Organization](#project-organization)
- [Credits & References](#credits-references)

## 🚀 Project Overview

The Game Recommendation System project aims to create a personalized recommendation engine for digital video game marketplaces like Steam, Epic Games Store, and PlayStation Store. With millions of games available, it’s difficult for players to discover games that match their unique preferences. The goal of this project is to build a recommendation system that goes beyond popularity-based suggestions, offering personalized recommendations tailored to each player’s preferences, such as art style, story, gameplay mechanics, and challenge level.

This project will explore and analyze user behavior data, apply data science techniques like collaborative filtering and content-based filtering, and use machine learning to recommend games.

## 🎓 Problem Area

With the increasing number of games on digital marketplaces, recommending the right game to the right player has become a challenge. Current recommendation systems often suggest the most popular games, overlooking niche or lesser-known titles that might be a better fit for the player.

- Users: Often overwhelmed by the number of games.
- Developers: Struggle to reach their target audience, especially indie developers.
- Platforms: Face difficulties in increasing user engagement and driving sales for lesser-known games.

### Problem with the Current Approach:

Top 20 Popular Games: Ranking games based on popularity or user count can lead to a selection of games that don't necessarily match the unique interests of every player.
For example: A player who enjoys a specific genre (like strategy or indie games) might not find relevant games in the top-ranked popular titles.
Why it's not enough: While the top 20 most popular games provide a starting point, they don’t account for factors like art style, story, gameplay mechanics, or challenge level that are key to individual preferences.

### Why the Recommendation System is Needed:
A personalized recommendation system will solve this by using data such as user behavior, ratings, and game features to recommend titles that match the individual’s tastes, increasing player satisfaction and engagement.

## 📝 Proposed Data Science Approach

We propose building a game recommendation system that uses a combination of collaborative filtering, content-based filtering, and NLP to provide personalized game recommendations for each player based on their behavior, ratings, and game features.

### Approach:
- **Data Collection**: Collect relevant game data from platforms like Steam, using APIs such as SteamSpy.
- **Data Preprocessing**:
  - Clean and preprocess the data to ensure it is suitable for analysis.
  - Handle missing data, outliers, and duplicates as part of data cleaning.
- **Recommendation Algorithms**:
  - **Content-based filtering**: Recommending games based on the similarity of game features such as genre, platform, and user ratings.
  - **Collaborative filtering**: Recommending games based on the preferences of similar users.
  - **Natural Language Processing (NLP)**: Analyzing text-based data such as game descriptions and reviews to further enhance recommendations.

### Tools/Technologies Used:
- **Python**: The core programming language for implementing the system.
- **Pandas**: For data manipulation and cleaning.
- **Scikit-learn**: For implementing machine learning algorithms like collaborative filtering and content-based filtering.
- **APIs**: SteamSpy: For retrieving Steam game statistics such as playtime, ratings, and genre.
- **Natural Language Processing (NLP) Tools**: 
- **Jupyter Notebook**: For developing and presenting the analysis, cleaning, and modeling process interactively.

---

## 📚 Impact of the Solution

### Impact on Stakeholders:
- **Players:** Will find games that truly match their interests, making the discovery process more enjoyable and efficient.
- **Developers:** Especially indie developers, can reach players who are genuinely interested in their specific game types, boosting visibility and sales.
- **Platforms:** Enhanced recommendation systems can improve user satisfaction, engagement, and retention, which directly translates to increased revenue.

## 🤝 Datasets Overview/Concerns/EDA Findings:

We use three main datasets for this project:

- **Steam-200k dataset**: A dataset containing information on 200,000 Steam games, including user behavior (hours played, purchase data), ratings, and game features.
- **Video Games Sales dataset**: This dataset provides global sales data, platform information, and user/critic ratings for various games.
- **SteamSpy dataset**: Aggregated statistics on Steam games, such as popularity, playtime, and genre.

### Merging Three Datasets (Steam-200k, Sales and Video Games Sales):
In the initial phase, I merged three datasets to explore and analyze the correlation between game sales and user behaviors:

The process involved merging these datasets based on the game title (Name) to analyze whether there is a significant correlation between sales and the number of players for each game.

- **Objective**:
   - To check whether more popular games (in terms of the number of users) correspond to higher global sales.
   - To see if there is any relationship between game playtime and game sales.

After merging, I conducted Exploratory Data Analysis (EDA) to identify key trends and patterns in the data. I created various visualizations to help understand the relationships between user behavior (playtime, purchases) and sales figures (global sales, region sales).

---

## 🕹️ **Sprint 2**

### **Executive Summary**:
Understanding user engagement and purchasing behavior is critical for personalized game recommendation systems.  
In this sprint, we focused on building a model to **predict whether a user will purchase a game** based on features like price, playtime, and genre.

**Key takeaways**:
- Genre plays a significant role in user purchasing decisions.
- Price alone isn't a strong predictor of purchase.
- Basic features yield strong baseline model performance, offering significant potential for personalization.

### **Demo**:
**Work in progress.** Future demo plans include:
- Visualizing genre engagement and purchasing trends.
- Interactive prototype based on user purchases and playtime behavior.

### **Methodology**:
- **Data Collection**:
  - Merged user interaction data (Steam-200k) with game sales (Sales) and game metadata (SteamSpy).
- **Data Preprocessing**:
  - Standardized column names, handled missing values (median/mode), one-hot encoded genres (will do in the future modeling).
  - Converted pricing to numeric values and aggregated user interaction by game.
- **Exploratory Data Analysis (EDA)**:
  - Visualized genre popularity and purchase rates.
  - Analyzed relationships between price, reviews, and user engagement.
- **Baseline Modeling**:
  - Trained a logistic regression model using price, playtime, and genre features.
  - Achieved 90% accuracy, 85% precision, 100% recall, and 0.87 AUC.

### **Next Steps**:
- Expand feature set (e.g., user engagement depth).
- Explore item-item collaborative filtering for personalized recommendations.
- Experiment with ensemble models like Random Forest or XGBoost for improved precision.

---

## 📃 Next Steps

Based on the findings and progress made during Sprint 2, the following steps will be undertaken to refine the data, improve the recommendation system, and prepare the model for future sprints:

1. **Data Processing**:
   - Explore cluster-based imputation or domain-specific imputation methods to improve accuracy, especially for missing values.
   - Treat outliers in sales and ratings.
2. **Feature Engineering**:
   - Create genre-based features to help identify preferences for specific genres in the recommendation system.
3. **Model Development**:
   - Build the first version of collaborative filtering and content-based filtering models.
   - Apply TF-IDF for NLP to represent text data numerically.

---

## 📁 Project Organization

The repository is organized as follows:
- **`data/`**: Contains all the datasets used for the project.
- **`model/`**: Contains trained baseline models and future item-item models.
- **`notebooks/`**: Contains Jupyter notebooks for Sprint 1 and Sprint 2.
- **`docs/`**: Contains presentation slides summarizing the project's findings and models.
- **`references/`**:
