# Bitcoin-Price-Prediction-with-Sentiment-and-Google-Trends-Analysis
# Overview
## This project aims to predict Bitcoin prices on a daily basis by analyzing historical price data along with sentiment data from Reddit and public interest data from Google Trends. Through this approach, we explore if social sentiment and search trends have a quantifiable impact on Bitcoin's price movements over the last year.

# Project Structure
The main steps involved in the project are:

Fetching Bitcoin historical price data.
Collecting and processing Reddit sentiment data.
Fetching Google Trends data for public interest in Bitcoin.
Data preparation and feature engineering.
Training a predictive model to forecast daily Bitcoin prices.
Analyzing the correlations and impact of sentiment and search trends on Bitcoin price.

# Data Sources
Bitcoin Historical Price Data: Retrieved from CoinGecko API for the past 365 days.
Reddit Sentiment Data: Collected from the Cryptocurrency subreddit to gauge public sentiment around Bitcoin, focusing on posts from the past 365 days.
Google Trends Data: Collected for Bitcoin-related search trends over the past 365 days to understand public interest over time.

# Project Workflow
Here's a step-by-step breakdown of the tasks performed in the project:

1. Fetching Bitcoin Price Data
Function: fetch_bitcoin_price_data()
Description: Using CoinGecko API, this function retrieves historical Bitcoin prices for the past 365 days, enabling a detailed analysis of recent price trends.
Purpose: Provides the target variable (Bitcoin price) for the model, as well as historical data for trend analysis.
2. Collecting Reddit Data for Sentiment Analysis
Function: fetch_reddit_data(keywords, date_cutoff_days=365)
Description: Pulls Reddit posts related to Bitcoin from the cryptocurrency subreddit and filters posts based on specific keywords ("Bitcoin," "BTC," "Ethereum") for the past 365 days.
Sentiment Analysis: Uses TextBlob to assess the sentiment polarity of each post title, which is then aggregated daily.
Purpose: The daily sentiment scores provide insights into how public opinion on social media aligns with or diverges from Bitcoin's price trends.
3. Fetching Google Trends Data
Function: fetch_google_trends_data()
Description: Pulls Google Trends data for Bitcoin, split into multiple time frames over the past 365 days, to track search interest over time.
Purpose: The trends data serves as an indicator of public interest, potentially providing signals related to shifts in Bitcoin prices.
4. Data Preparation and Feature Engineering
Function: prepare_data(df_price, df_reddit)
Steps:
Converts timestamps to a daily basis and calculates the daily average for Bitcoin prices.
Aggregates daily sentiment from Reddit data.
Merges Bitcoin price data with sentiment and Google Trends data.
Creates lag features and rolling statistics (e.g., previous day prices, rolling means, and standard deviations).
Purpose: Generates a dataset with features that capture historical trends and recent patterns in Bitcoin prices, Reddit sentiment, and Google Trends.
5. Visualizations
Function: visualize_data(df_price, df_reddit, interest_over_time_df)
Visualizations:
Bitcoin Price Over Time.
Sentiment of Reddit Posts Over Time.
Google Trends Interest Over Time for Bitcoin.
Purpose: Visualizations provide a visual summary of the data to aid in understanding potential patterns and relationships between price, sentiment, and public interest.
6. Model Training
Model: Random Forest Regressor (a non-linear model)
Data Split: The data is split into training and testing sets (80% training, 20% testing).
Feature Scaling: Uses StandardScaler to normalize the features.
Target: Daily Bitcoin prices.
Purpose: The model is trained to predict daily Bitcoin prices based on sentiment and trends data, testing whether these factors have predictive power.
7. Evaluation
Metrics:
Mean Absolute Error (MAE): Measures the average magnitude of errors in predictions.
R-squared (R²): Represents the proportion of variance in the Bitcoin price explained by the model.
Results: The model's predictions are compared with actual Bitcoin prices, and metrics are reported to assess the model's accuracy.
8. Correlation Analysis
Purpose: Computes a correlation matrix to examine relationships between Bitcoin price, Reddit sentiment, and Google Trends data.
Findings:
Bitcoin Price & Reddit Sentiment: Weak correlation, suggesting minimal relationship.
Bitcoin Price & Google Trends: Weak positive correlation, indicating a slight association.
Reddit Sentiment & Google Trends: Weak negative correlation, indicating minimal inverse relationship.
Interpretation: These results indicate that Reddit sentiment and Google Trends data do not have strong direct relationships with Bitcoin's price movements in this dataset.

# Results and Insights
Bitcoin price prediction using Random Forest Regressor showed some ability to follow general trends, but with limited predictive power due to weak correlations with sentiment and search interest data.
Correlation Analysis revealed weak relationships between Bitcoin price, Reddit sentiment, and Google Trends interest. This suggests that sentiment and search interest, while potentially useful in shorter time frames or under specific conditions, do not strongly influence Bitcoin's price on a daily basis in this dataset.
Visualizations helped illustrate the independence of Bitcoin prices from social sentiment and Google search trends, showing that price fluctuations are more likely influenced by other market factors.

# Future Work
To enhance the predictive accuracy and insights, future work could include:

Incorporating additional data sources: Such as trading volume, macroeconomic indicators, and sentiment from other social media platforms like Twitter.
Testing other machine learning models: Including LSTM (Long Short-Term Memory) neural networks, which may better capture time series dependencies.
Lagged feature analysis: Explore lagged correlations to understand if past sentiment or trends data have a delayed effect on prices.
Sentiment Analysis Refinement: Use more advanced NLP models for a nuanced sentiment analysis that captures context beyond polarity.
Requirements
This project uses the following libraries:

requests: For fetching Bitcoin and Reddit data.
pandas: For data manipulation and analysis.
datetime and time: For handling date/time data.
pytrends: For fetching Google Trends data.
TextBlob: For performing sentiment analysis on Reddit posts.
matplotlib: For data visualization.
sklearn: For model training and evaluation.
StandardScaler: For feature scaling.
