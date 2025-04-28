<<<<<<< HEAD
# GameSeeker – A Personalized Game Recommendation Engine

## Table of Contents
- [Project Overview](#-project-overview)
- [Problem Area](#-problem-area)
- [Proposed Data Science Approach](#-proposed-data-science-approach)
- [Impact of the Solution](#-impact-of-the-solution)
- [Datasets Overview/Concerns/EDA Findings:](#-datasets-overview/Concerns/EDA-Findings:)
- [Next Step](#-next-step)

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

We propose building a game recommendation system that uses a combination of collaborative filtering, content-based filtering and NLP to provide personalized game recommendations for each player based on their behavior, ratings, and game features.

### Approach:
- Data Collection: Collect relevant game data from platforms like Steam, using APIs such as SteamSpy.
- Data Preprocessing:
  - Clean and preprocess the data to ensure it is suitable for analysis.
  - Handle missing data, outliers, and duplicates as part of data cleaning.
- Recommendation Algorithms:
  - Content-based filtering: Recommending games based on the similarity of game features such as genre, platform, and user ratings.
  - Collaborative filtering: Recommending games based on the preferences of similar users.
  - Natural Language Processing (NLP): Analyzing text-based data such as game descriptions and reviews to further enhance recommendations.

### Tools/Technologies Used:
- Python: The core programming language for implementing the system.

- Pandas: For data manipulation and cleaning.
- Scikit-learn: For implementing machine learning algorithms like collaborative filtering and content-based filtering.
- APIs: SteamSpy: For retrieving Steam game statistics such as playtime, ratings, and genre.
- Natural Language Processing (NLP) Tools:
- Jupyter Notebook: For developing and presenting the analysis, cleaning, and modeling process interactively.



## 📚 Impact of the Solution

### Impact on Stakeholders:
- **Players:** Will find games that truly match their interests, making the discovery process more enjoyable and efficient.
- **Developers:** Especially indie developers, can reach players who are genuinely interested in their specific game types, boosting visibility and sales.
- **Platforms:** Enhanced recommendation systems can improve user satisfaction, engagement, and retention, which directly translates to increased revenue.

## 🤝 Datasets Overview/Concerns/EDA Findings:

We use three main datasets for this project:

Steam-200k dataset: A dataset containing information on 200,000 Steam games, including user behavior (hours played, purchase data), ratings, and game features.
Video Games Sales dataset: This dataset provides global sales data, platform information, and user/critic ratings for various games.
SteamSpy dataset: Aggregated statistics on Steam games, such as popularity, playtime, and genre.

### Merging the First Two Datasets (Steam-200k and Video Games Sales):
In the initial phase, I merged two datasets to explore and analyze the correlation between game sales and user behaviors:

The process involved merging these datasets based on the game title (Name) to analyze whether there is a significant correlation between sales and the number of players for each game.

- Objective:
   - To check whether more popular games (in terms of the number of users) correspond to higher global sales.
   - To see if there is any relationship between game playtime and game sales.

After merging, I conducted Exploratory Data Analysis (EDA) to identify key trends and patterns in the data. I created various visualizations to help understand the relationships between user behavior (playtime, purchases) and sales figures (global sales, region sales).

#### Combining Multiple Datasets for Genre-Specific Game Analysis:
In the next step, I combined 10 different datasets related to Steam games from different genres using SteamSpy API. These datasets include games from different genres like Action, Indie, RPG, and more. Each dataset contains specific game data related to genre, popularity, playtime, and ratings.

Objective:
To combine the datasets and explore the correlation between game genre and various factors like playtime, sales, and ratings.
To examine how genre-specific preferences affect game recommendations and to ensure the recommendation system can suggest games that match specific player interests. The work steps are in the "Data prepare.ipynb".

### Data Quality Concerns: 
- Missing Data: Handled using KNN imputation for numerical columns and a simple strategy for categorical columns.
  - KNN Imputation is used to fill missing values in numeric columns. This method uses the average of the 5 nearest neighbors' values to estimate and fill in the missing values.
  - Missing values in categorical columns are replaced with a default value of "Unknown".

**While KNN imputation with 5 neighbors is commonly used, I’m concerned that it may not be the best fit for handling missing values in variables like Critic_Score and User_Score. If the nearest neighbors are from very different game types or genres, it could lead to inaccurate imputation. In the next steps, I plan to explore more appropriate methods, such as clustering games by genre before imputation or trying weighted KNN, and will consider alternatives like mean or median imputation for better accuracy.**

- Duplicates & Inconsistencies: Drop the duplicates.

- Outliers
"global sales distribution by platform":
This plot reveals that modern platforms such as PS4 and X360 have much higher sales and a larger spread of sales values, while older or less popular platforms show more concentrated and lower sales distributions. The outliers reflect exceptional games that significantly exceeded sales expectations on certain platforms.

## EDA Findings
1. Genre Distribution in SteamSpy Data:
The first plot presents the frequency distribution of different game genres in the SteamSpy dataset. Here are the key findings:

- Top Genres:
  - Indie is the most prevalent genre, with over 60,000 games, indicating a large number of games categorized under indie titles.
  - Action, Adventure, and Simulation genres also have significant counts, suggesting their popularity among developers and players.

- Less Popular Genres:
  - Massively and Ex Early Access are among the least represented genres, indicating that these categories may have fewer games or are niche categories with less developer focus.

2. Correlation Analysis: Multiple Variables:
The second plot shows the correlation heatmap for multiple variables in the dataset. The following insights can be drawn from the heatmap:

- Global Sales Correlations:

  - Global Sales is highly positively correlated with both NA_Sales (0.94) and EU_Sales (0.96), meaning that games with higher sales in North America and Europe tend to have higher Global Sales.
  - Global Sales is also moderately positively correlated with Critic_Score (0.42), indicating that games with higher critic scores generally have better sales performance globally.

- Hours Played:

  - The correlation between Hours Played and Global Sales (0.02) is very low, suggesting that there is no strong relationship between the total time spent playing a game and its global sales.

- Sales in North America and Europe:

  - Both NA_Sales and EU_Sales show a strong correlation with Global Sales, reinforcing the significance of regional performance in determining overall sales success.


## 📃 Nest Step

Based on the exploratory data analysis (EDA) findings, the following steps will be undertaken to refine the data, improve the recommendation system, and prepare the model for future sprints:
1. Data Processing:
- Handle Missing Values: Although KNN imputation was used for numeric columns and "Unknown" was assigned to categorical columns, further review will be conducted. The next step is to explore cluster-based imputation or domain-specific imputation methods to improve the accuracy of missing values, especially when the neighbors are from highly different game genres.
- Outlier Treatment: Outliers detected in sales and ratings need further consideration.
  
2. Feature Engineering:
Game Genre Features: Given the dominance of Indie and Action genres, we will create genre-based features that help identify preferences for specific genres in the recommendation system. We will also analyze niche genres and their correlation with sales and ratings.

3. Model Development:
- Collaborative Filtering: We will build the first version of the collaborative filtering model, which will use user behavior data (e.g., playtime, ratings) to recommend similar games.
- Content-Based Filtering: The system will incorporate game features (e.g., genre, developer, critic score) to recommend games similar to those the user has played or rated highly.
- NLP Model: TF-IDF (Term Frequency-Inverse Document Frequency) will be applied to represent the text data numerically.




=======
# GameSeeker – A Personalized Game Recommendation Engine

## Table of Contents
- [Project Overview](#-project-overview)
- [Problem Area](#-problem-area)
- [Proposed Data Science Approach](#-proposed-data-science-approach)
- [Impact of the Solution](#-impact-of-the-solution)
- [Datasets Overview/Concerns/EDA Findings:](#-datasets-overview/Concerns/EDA-Findings:)
- [Next Step](#-next-step)

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

We propose building a game recommendation system that uses a combination of collaborative filtering, content-based filtering and NLP to provide personalized game recommendations for each player based on their behavior, ratings, and game features.

### Approach:
- Data Collection: Collect relevant game data from platforms like Steam, using APIs such as SteamSpy.
- Data Preprocessing:
  - Clean and preprocess the data to ensure it is suitable for analysis.
  - Handle missing data, outliers, and duplicates as part of data cleaning.
- Recommendation Algorithms:
  - Content-based filtering: Recommending games based on the similarity of game features such as genre, platform, and user ratings.
  - Collaborative filtering: Recommending games based on the preferences of similar users.
  - Natural Language Processing (NLP): Analyzing text-based data such as game descriptions and reviews to further enhance recommendations.

### Tools/Technologies Used:
- Python: The core programming language for implementing the system.

- Pandas: For data manipulation and cleaning.
- Scikit-learn: For implementing machine learning algorithms like collaborative filtering and content-based filtering.
- APIs: SteamSpy: For retrieving Steam game statistics such as playtime, ratings, and genre.
- Natural Language Processing (NLP) Tools:
- Jupyter Notebook: For developing and presenting the analysis, cleaning, and modeling process interactively.



## 📚 Impact of the Solution

### Impact on Stakeholders:
- **Players:** Will find games that truly match their interests, making the discovery process more enjoyable and efficient.
- **Developers:** Especially indie developers, can reach players who are genuinely interested in their specific game types, boosting visibility and sales.
- **Platforms:** Enhanced recommendation systems can improve user satisfaction, engagement, and retention, which directly translates to increased revenue.

## 🤝 Datasets Overview/Concerns/EDA Findings:

We use three main datasets for this project:

Steam-200k dataset: A dataset containing information on 200,000 Steam games, including user behavior (hours played, purchase data), ratings, and game features.
Video Games Sales dataset: This dataset provides global sales data, platform information, and user/critic ratings for various games.
SteamSpy dataset: Aggregated statistics on Steam games, such as popularity, playtime, and genre.

### Merging the First Two Datasets (Steam-200k and Video Games Sales):
In the initial phase, I merged two datasets to explore and analyze the correlation between game sales and user behaviors:

The process involved merging these datasets based on the game title (Name) to analyze whether there is a significant correlation between sales and the number of players for each game.

- Objective:
   - To check whether more popular games (in terms of the number of users) correspond to higher global sales.
   - To see if there is any relationship between game playtime and game sales.

After merging, I conducted Exploratory Data Analysis (EDA) to identify key trends and patterns in the data. I created various visualizations to help understand the relationships between user behavior (playtime, purchases) and sales figures (global sales, region sales).

#### Combining Multiple Datasets for Genre-Specific Game Analysis:
In the next step, I combined 10 different datasets related to Steam games from different genres using SteamSpy API. These datasets include games from different genres like Action, Indie, RPG, and more. Each dataset contains specific game data related to genre, popularity, playtime, and ratings.

Objective:
To combine the datasets and explore the correlation between game genre and various factors like playtime, sales, and ratings.
To examine how genre-specific preferences affect game recommendations and to ensure the recommendation system can suggest games that match specific player interests. The work steps are in the "Data prepare.ipynb".

### Data Quality Concerns: 
- Missing Data: Handled using KNN imputation for numerical columns and a simple strategy for categorical columns.
  - KNN Imputation is used to fill missing values in numeric columns. This method uses the average of the 5 nearest neighbors' values to estimate and fill in the missing values.
  - Missing values in categorical columns are replaced with a default value of "Unknown".

**While KNN imputation with 5 neighbors is commonly used, I’m concerned that it may not be the best fit for handling missing values in variables like Critic_Score and User_Score. If the nearest neighbors are from very different game types or genres, it could lead to inaccurate imputation. In the next steps, I plan to explore more appropriate methods, such as clustering games by genre before imputation or trying weighted KNN, and will consider alternatives like mean or median imputation for better accuracy.**

- Duplicates & Inconsistencies: Drop the duplicates.

- Outliers
"global sales distribution by platform":
This plot reveals that modern platforms such as PS4 and X360 have much higher sales and a larger spread of sales values, while older or less popular platforms show more concentrated and lower sales distributions. The outliers reflect exceptional games that significantly exceeded sales expectations on certain platforms.

## EDA Findings
1. Genre Distribution in SteamSpy Data:
The first plot presents the frequency distribution of different game genres in the SteamSpy dataset. Here are the key findings:

- Top Genres:
  - Indie is the most prevalent genre, with over 60,000 games, indicating a large number of games categorized under indie titles.
  - Action, Adventure, and Simulation genres also have significant counts, suggesting their popularity among developers and players.

- Less Popular Genres:
  - Massively and Ex Early Access are among the least represented genres, indicating that these categories may have fewer games or are niche categories with less developer focus.

2. Correlation Analysis: Multiple Variables:
The second plot shows the correlation heatmap for multiple variables in the dataset. The following insights can be drawn from the heatmap:

- Global Sales Correlations:

  - Global Sales is highly positively correlated with both NA_Sales (0.94) and EU_Sales (0.96), meaning that games with higher sales in North America and Europe tend to have higher Global Sales.
  - Global Sales is also moderately positively correlated with Critic_Score (0.42), indicating that games with higher critic scores generally have better sales performance globally.

- Hours Played:

  - The correlation between Hours Played and Global Sales (0.02) is very low, suggesting that there is no strong relationship between the total time spent playing a game and its global sales.

- Sales in North America and Europe:

  - Both NA_Sales and EU_Sales show a strong correlation with Global Sales, reinforcing the significance of regional performance in determining overall sales success.


## 📃 Nest Step

Based on the exploratory data analysis (EDA) findings, the following steps will be undertaken to refine the data, improve the recommendation system, and prepare the model for future sprints:
1. Data Processing:
- Handle Missing Values: Although KNN imputation was used for numeric columns and "Unknown" was assigned to categorical columns, further review will be conducted. The next step is to explore cluster-based imputation or domain-specific imputation methods to improve the accuracy of missing values, especially when the neighbors are from highly different game genres.
- Outlier Treatment: Outliers detected in sales and ratings need further consideration.
  
2. Feature Engineering:
Game Genre Features: Given the dominance of Indie and Action genres, we will create genre-based features that help identify preferences for specific genres in the recommendation system. We will also analyze niche genres and their correlation with sales and ratings.

3. Model Development:
- Collaborative Filtering: We will build the first version of the collaborative filtering model, which will use user behavior data (e.g., playtime, ratings) to recommend similar games.
- Content-Based Filtering: The system will incorporate game features (e.g., genre, developer, critic score) to recommend games similar to those the user has played or rated highly.
- NLP Model: TF-IDF (Term Frequency-Inverse Document Frequency) will be applied to represent the text data numerically.




>>>>>>> b13759a (Initial project upload)
