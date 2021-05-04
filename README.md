# Predicting the Outcomes of NBA Games 

The goal of this project is to create models that are able to predict the outcomes of NBA games more accurately than gold standard models, like the ones used to set moneylines.  

A moneyline bet is a bet on which team will win the game.  Generally, there is a favorite and an underdog which are determined by the moneyline odds set for each team.  Vegas (i.e. professional sports betting organizations) does a very good job at picking the favorite for each game; in the data I have acquired, the Vegas favorite wins 68% of the time!  My goal is to consistently beat this accuracy.



## A High Level Overview

### Part 1: Data Acquisition 

The first step in this project was to acquire all of the needed data.  

The data can be split into two groups: NBA team data and sports betting data.  The former was acquired via [Basketball Reference](https://www.basketball-reference.com/), a popular basketball statistics website. Basketball Reference makes all of its data very accessible, which allowed me to scrape all of the needed data via pandas alone.  Meanwhile, the sports betting data was obtained from [Sports Book Review](https://www.sportsbookreview.com/), a website which compiles sports betting data from a variety of books (i.e. a company that hosts betting).  This data was scraped using Beautiful Soup.

The data I acquired contains most basic and advanced team statistics from every game dating back to the 1994 season and moneyline and spread betting data from nine different sports book from the 2007 season on.

- Code in [data_acquisition_and_prep](https://github.com/gsyann/nba_game_models/tree/main/data_acquisition_and_prep) folder  


### Part 2: Designing Features and Creating the Dataset

Now I had to format the data in a way where it would be useful for prediction.  I accomplished this by taking moving averages of each team’s previous games. This is so that the model will predict the outcomes of games from teams’ previous performances.  I included linearly weighted moving averages with different window sizes as well as exponential moving averages with different smoothing factor sizes. This gives me a wider variety of features to choose from when tuning the models.  I then created unique IDs for each game, which allowed me to merge in the betting data. 

- Code in [data_acquisition_and_prep](https://github.com/gsyann/nba_game_models/tree/main/data_acquisition_and_prep) folder

### Part 3: Modeling

#### Part 3.1 - Creating a Baseline Model

In general, it is good practice to create a baseline model, as it provides something to compare all future modifications/improvements to.  

The baseline model I created uses a decision tree on moneyline data as well as a few advanced statistics from teams’ previous games to predict which team will win (i.e. classify whether the home team will win the game or not).  

My baseline model is able to predict games about as well as Vegas’ models.  However, this is largely because I include the moneyline odds as features.

- For more detailed analysis check out [this notebook](https://github.com/gsyann/nba_game_models/blob/main/models/baseline_model.ipynb)


#### Part 3.2 - Modeling improvements are currently underway!

<br />
<br />

## Next Steps

### Housekeeping
- Create pipelines
- Move to py files
- Get real-time results (for current season)
- Host results online?

### Model Improvement Ideas
- Try different moving average types
- Try different model types
- Use indicator for is_favorite, rather than using odds?
- Check out feature selection methods
- More complex EDA 
  - ex: how does time affect impact of features (I'd imagine 3-pointer stats have become more useful in the past 7 years)
- Profit analysis for model predictions
- Optimal Betting Strategy
  - Kelly Criterion - "a formula for bet sizing that leads almost surely to higher wealth compared to any other strategy in the long run"
- Predict winners against the spread
  
