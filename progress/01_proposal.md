## Project Ideas

1. NFL pass-play success prediction and anomaly detection on player movement
   - Predict whether a pass play will be successful, completed, or gain above a certain number of yards. (Classification)
   - Predict yards gained or expected points. (Regression)
   - Identify unusual defensive alignments, strange route combinations, or busted coverages.
   - NFL Big Data Bowl has public player-tracking data from the past couple of seasons.

2. NBA player performance prediction and player similarity recommender
   - Predict points, assists, rebounds, or fantasy points for a game. (Regression)
   - Predict whether a player will exceed a scoring threshold for any given game. (Classification)
   - Cluster players into groups based on play styles. (aggressive rushers, bench scorers, etc.)
   - Public NBA/player datasets are available on Kaggle, some are updated daily.

3. MLB home run distance or xwOBA prediction and hitter clustering
   - Predict home run distance, expected batting average, or hard-hit probability from launch angle, exit velocity, pitch type, count, and zone. (Regression)
   - Predict whether a batted ball will become a home run. (Classification)
   - Group hitters into profiles such as “pull-power fly-ball hitters,” “high-contact line-drive hitters,” and “three-true-outcomes sluggers.”
   - Baseball Savant hosts official Google StatCast data and includes batted-ball and pitch-level information.

## Influence of AI

We went into this project already having some idea of what we wanted to do. Both of us are interested in a wide range of sports data, AI helped us to narrow down our interest to a specific sport (baseball) and pick a specific player to focus on. Brainstorming with AI was especially helpful with narrowing down the scope of our project. Since there are so many parts to this project such as multiple supervised learning models, an additional machine learning technique, the need to find a relevant dataset, and a demo Streamlit app, AI helped make sure that whatever topic we chose would be able to meet these requirements.

## Helpful AI Exchange

Our prompt: "There are around 14,000 pitch level data points in our dataset, how can I make sure that the scope stays reasonable and keep our model from being too complicated?"

Response (ChatGPT): "With around 14,000 pitch-level data points, the best way to keep the project manageable is to simplify what counts as one data point. Instead of trying to make a prediction for every single pitch, it would make more sense to treat each plate appearance as one observation and then predict whether that plate appearance ended in a hit or not. That fits baseball better, since hits are really outcomes of full at-bats, not individual pitches. It also helps avoid making the dataset overly messy or unbalanced, since most pitches by themselves do not directly result in a hit."

## Final Research Question

How well can pitch-level variables such as pitch location, pitch type, count, velocity, and pitcher handedness predict the probability that Kyle Schwarber gets a hit, and which of these are most influential?

## Target Variable (Supervised Analysis)

The target variable for our supervised analysis will be whether Kyle Schwarber recorded a hit or not. More specifically, this will be "Hit = 1" if the plate appearance outcome is a single, double, triple, or home run, and "Hit = 0" for every other situation.

## Dataset Choice

For this analysis we are using 2021-2025 pitch-level data for Kyle Schwarber. We got this from baseballsavant.mlb.com, which is the official source of all MLB StatCast data. As a backup, there is a Python API called pybaseball that should be able to provide us similar pitch-level data in the case the BaseballSavant data doesn't work.

## Feasibility

We feel that this project idea is feasible since it uses publicly available official data, focuses on just one player instead of a group, and because pitch-level data is structured well for a classification problem like the one for our supervised analysis. The dataset is large since it covers five seasons (almost 14,000 data points), but we can easily trim this down if necessary by covering less seasons or removing data points where the batter didn't swing.

## Ethical/legal Considerations

This specific analysis doesn't seem to have any obvious ethical and legal considerations when compared to analyses on medical data or private datasets, but we will still make sure to always cite the source (baseballsavant.mlb.com) and avoid overstatement of our conclusions from this model. Since our analysis focuses on a single player, in our final report we will make sure to remind anyone following along that our model isn't a complete measure of Kyle Schwarber's abilities and that any patterns in the data should be discussed as just patterns rather than "weaknesses" or a way to judge a player.

## Planned ML Methods

We plan to use clustering as our additional ML method. We will cluster pitches seen by Schwarber based on location, pitch type, speed, movement, and count, then use these to determine which pitch clusters are associated with the highest hit probabilities. We can also explore what kinds of these combinations he faces most often and if there are clusters where he generally performs better/worse.
