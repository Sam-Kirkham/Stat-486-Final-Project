## Main Research Question

Our question of interest is: How well can pitch-level variables such as pitch location, pitch type, count, velocity, and pitcher handedness predict the probability that Kyle Schwarber gets a hit, and which of these variables are most influential?

## Our Data Set

For this analysis we are using 2021-2025 pitch-level data for Kyle Schwarber. We chose to only include pitch data from the MLB Regular Season. We got this from baseballsavant.mlb.com, which is the official source of all MLB StatCast data. As a backup, there is a Python API called pybaseball that should be able to provide us similar pitch-level data in the case the BaseballSavant data doesn't work.

This specific analysis doesn't seem to have any obvious ethical and legal considerations when compared to analyses on medical data or private datasets, but we will still make sure to always cite the source (baseballsavant.mlb.com) and avoid overstatement of our conclusions from this model. We determined that we could utilize our source for the data since there is no mention of not being able to use the data they provide as well as our data was easily accessible through download from the site without needing an account. Since our analysis focuses on a single player, in our final report we will make sure to remind anyone following along that our model isn't a complete measure of Kyle Schwarber's abilities and that any patterns in the data should be discussed as just patterns rather than "weaknesses" or a way to judge a player.

Here is the citation for the website we found our data at: _Baseball savant: Statcast, trending MLB players and visualizations. baseballsavant.com. (n.d.). https://baseballsavant.mlb.com/_

# Data Description and Variables

Our data includes lots of variables but the key variables for our analysis will be: - Pitch Zone (zone) - Pitcher Handedness (p_throws) - Pitch Count (balls, strikes) - Pitch Speed (effective_speed) - Pitch Spin (release_spin_rate) - Pitch Number in AB (pitch_number) - Type of Pitch (pitch_name)

Pitch Zone: The zone the ball passes through as it goes over home plate.
Pitcher Handedness: Tells whether the pitcher is right or left handed.
Pitch Count: How many balls and strikes there are pre-pitch, allowing us to see the pitch situation.
Pitch Speed: The speed of the pitch as it leaves the pitcher's hand.
Pitch Spin: The spin rate on the ball as it leaves the pitcher's hand.
Pitch Number in AB: How many pitches has Kyle Schwarber seen in this at bat (AB).
Type of Pitch: What kind of pitch was thrown.

Target Variable: - Hit

Hit: Whether or not the result was a single, double, triple, or homerun

Preprocessing Steps:
We need to create the target variable 'Hit'. We will do this using the variable 'events' from the dataset, anything that says 'single', 'double', 'triple' or 'homerun' will get a True and everything else will get False. The only other preprocessing that we will be doing is getting rid of irrelevant variables that will not be needed in our analysis.

# Challenges and Reflection

Once we knew that we wanted to focus on MLB data, we immediately knew that the Google Cloud StatCast data would be the best source. The process is very streamlined on the website. We were able to search for the player we wanted and had many, many options for metrics to filter by and include. We did have some issue with finding how to get pitch level data instead of summary statistics, but were able to download a csv with the data we wanted in the end. The next challenge was sorting through all of the variables and choosing which ones we thought would be applicable to our model (by default, the file includes around 50 columns). There were many statistics that were redundant or not relevant to our research question.

Since we have so many data points, around 14,000, this past week we have had to discuss options for keeping the scope of our project manageable. We decided not to go with treating each at-bat as an observation like we had previously considered in our proposal. This means that we do have to deal with the larger amount of observations, but we felt it was important in order to get all of the data we need for our analysis. We are wanting to see the combinations that lead to both the highest probability of a hit as well as the highest probability of no hit.
