# Spot-if-AI - Final Project

This project investigates two fundamental hypotheses related to predicting song popularity and providing personalized music recommendations to users. The main objective was to evaluate whether it is possible to predict a song's market success using specific features and to develop a recommendation system that suggests potentially popular songs aligned with user preferences.

## Hypotheses:
1. **Popularity Prediction**: Factors such as genre, duration, and specific musical elements can predict a song's popularity in the market.
2. **Personalized Recommendation**: By analyzing songs saved by users, we can recommend new songs with high popularity potential that match their preferences.

## Methodology

### Data Collection:
1. **Spotify Dataset**: A large dataset of songs from Spotify was downloaded via Kaggle. This dataset included various musical features like duration, genre, energy, loudness, valence, and other factors.
2. **Spotify API**: The Spotify API was used to retrieve data on songs marked as 'liked' by users. To maintain comparability with the original Kaggle dataset, the same attributes were retrieved where available. However, since Spotify had removed the genre attribute from its API, this analysis was limited to other available factors. The code used for this step can be found [here](link).

### Data Analysis:
1. **Initial Exploration**: An exploratory data analysis was performed to understand distributions, identify outliers, and get a general overview of song features.
2. **Feature Correlation**: Correlation among features was assessed to identify possible relationships and interactions. Key findings included:
   - **Significant Positive Correlations**: Energy and loudness showed a strong positive correlation (0.81), indicating that songs with higher energy tend to be louder.
   - **Significant Negative Correlations**: Energy and acousticness exhibited a strong negative correlation (-0.82), suggesting that more acoustic songs tend to have lower energy levels.

### Data Processing and Preparation:
1. **Dataset Integration**: The datasets from Kaggle and the Spotify API were combined. A new column was added to the API-extracted songs to indicate whether they were marked as 'liked' by the user, facilitating identification in subsequent analyses.

### Popularity Prediction Model:
1. **Model Selection**: Four machine learning models were evaluated to predict song popularity based on its features:
   - **Linear Regression**: Used as a baseline model.
   - **Neural Networks**: A simple neural network model was implemented to capture nonlinear relationships.
   - **Random Forest**: Selected for its ability to handle large data volumes and capture variable interactions.
   - **Random Forest Optimized with Optuna**: Optuna, a hyperparameter optimization tool, was used to tune the Random Forest model for improved performance.
2. **Model Evaluation**: The models were evaluated using metrics like MSE (Mean Squared Error), R² (Coefficient of Determination), and MAE (Mean Absolute Error).
   - The optimized Random Forest model showed the best overall performance, balancing accuracy and generalization capability. With an MSE of 59.036 on the training set and 319.424 on the test set, it demonstrated strong predictive ability for new songs. An R² of 0.861 on training and 0.254 on test indicated effective capture of data variability. Additionally, with an MAE of 5.0, this model showed moderate prediction errors, reinforcing its suitability for popularity prediction. While other models were competent, the optimized Random Forest emerged as the top choice for predicting musical popularity.

### Song Recommendation:
1. **Initial Challenges**: Only 'liked' songs were available, posing a challenge for traditional classification models, as there was no 'disliked' category.
2. **Content-Based Filtering Model**: A content-based filtering approach was chosen. This model generated recommendations based on the similarity between songs liked by the user and other songs in the dataset, using cosine similarities to measure the closeness between musical characteristics.
3. **Recommendation Generation**: Similarities between liked and unheard songs were calculated, creating a personalized recommendation list for each user. This approach suggested songs that not only matched the user's preferences but also had high popularity potential.

## Conclusions:
The analysis confirms that the Optimized Random Forest model is the most suitable for predicting the popularity of new songs, offering a balanced trade-off between accuracy and generalization capability. With superior MSE and R² scores compared to other models, it shows a remarkable ability to fit training data and project popularity in unseen data. Additionally, the content-based filtering approach effectively generated personalized recommendations, aligning with users' preferences. These findings have practical implications for enhancing music recommendation systems on streaming platforms, helping users discover new songs that match their tastes before they gain widespread popularity. Implementing these models can significantly improve the musical experience and user satisfaction in streaming services.
