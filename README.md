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
![Rating distribution](Distribution20%IMDB20%rating.png)
![Average rating by decade](Average20%rating20%By20%decade.png)
![Log votes vs rating](Log20%voted20%vs20%rating.png)

### Exploratory analysis
- Highest-rated genre: Biography (average 6.70, 84 movies), then Family (6.30, 52 movies) and Drama (6.25, 1,842 movies)
- Drama is by far the most common genre, so its average is the most reliable
- Highest-rated decade: 1940s (average about 6.8), followed by the 1950s
- Lowest-rated decades: 1990s and 2000s (average about 5.4)
- Correlation between log(Votes) and Rating: 0.134 (weak positive)
- Correlation between Year and Rating: -0.205 (newer movies rate slightly lower)
- Correlation between Duration and Rating: 0.002 (almost none)
- Votes are very skewed (mean 2,698, median 131), so I used log(Votes)

### Probability models (binomial vs Poisson)
- I split the movies into groups of 10 and counted dramas in each group (p = 0.325)
- A chi-square test rejected the binomial model (p < 0.001)
- The Poisson model fit better (p = 0.034) but was also rejected at the 5% level
- The observed variance (2.76) is higher than the binomial variance (2.20), which shows overdispersion
- The observed variance lies between the binomial (2.20) and Poisson (3.26) values, so neither model describes the data exactly
- Likely reasons: movies are not independent, and the drama rate is not the same for every movie

### Rating prediction
- Baseline (always guess the average) RMSE: 1.361
- Linear regression: R2 = 0.194, RMSE = 1.222
- Random forest: R2 = 0.272, RMSE = 1.161
- Linear regression built from scratch with gradient descent: R2 = 0.194, identical to scikit-learn's result
- Most important features: log(Votes), then Year, then Duration. Genre had very little effect.
- Both models beat the baseline, and the random forest was best, but ratings remain hard to predict from these features alone

## Limitations
- Ratings are hard to predict from these features alone
- Movies with very few votes have unreliable ratings
- The 1930s and 2020s have very few movies, and old decades only include well-known films, so their averages should be read with care
- The groups of 10 were made from consecutive rows in the file

## Project files
- notebook.ipynb: full analysis
- cleaned_movies.csv: cleaned data

## About me
Bitu Robidas, biturobidas34@gmail.com
