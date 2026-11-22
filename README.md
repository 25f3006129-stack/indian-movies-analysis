# Analyzing Indian Cinema: Probability Models and Rating Prediction

Analysis of 5,659 Indian movies from IMDb, using Python, statistics and machine learning.

## Dataset
- Source: [IMDb Indian Movies Dataset on Kaggle](https://www.kaggle.com/datasets/arshadali12/imdb-indian-movies-dataset)
- Columns used: Year, Duration, Rating, Votes, Genre
- After cleaning: 5,659 movies, Year 1931 to 2021

## Tools
Python, Pandas, NumPy, Matplotlib, Seaborn, SciPy, scikit-learn

## What I did
1. Cleaned the data: fixed Year, Duration and Votes, removed duplicates and rows with missing values
2. Explored ratings by decade and genre, and looked at correlations
3. Tested whether the number of dramas per group of 10 movies follows a binomial or Poisson distribution
4. Built models to predict a movie's rating

## Key findings

### Exploratory analysis
- Highest-rated genre: [FILL]
- Highest-rated decade: [FILL]
- Correlation between log(Votes) and Rating: [FILL]
- Votes are very skewed (mean 2,698, median 131), so I used log(Votes)

### Probability models (binomial vs Poisson)
- I split the movies into groups of 10 and counted dramas in each group (p = 0.325)
- A chi-square test rejected the binomial model (p < 0.001)
- The Poisson model fit better (p = 0.034) but was also rejected at the 5% level
- The observed variance (2.76) is higher than the binomial variance (2.20), which shows overdispersion
- The observed variance lies between the binomial (2.20) and Poisson (3.26) values, so neither model describes the data exactly
- Likely reasons: movies are not independent, and the drama rate is not the same for every movie

### Rating prediction
- Baseline (always guess the average) RMSE: [FILL]
- Linear regression: R2 = [FILL], RMSE = [FILL]
- Random forest: R2 = [FILL], RMSE = [FILL]
- Linear regression built from scratch with gradient descent: R2 = [FILL], close to scikit-learn's result
- Most important features: [FILL]

## Limitations
- Ratings are hard to predict from these features alone
- Movies with very few votes have unreliable ratings
- The groups of 10 were made from consecutive rows in the file

## Project files
- notebook.ipynb: full analysis
- cleaned_movies.csv: cleaned data
- images: charts used in this README

## About me
[FILL: your name, one line about yourself, and your email or LinkedIn]
