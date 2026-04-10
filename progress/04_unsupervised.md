We decided to use K-means clustering as our unsupervised machine learning method.

# Why does this fit our data?

This fits our data well because each pitch-level event is a combination of many different variables that a lot of times work together instead of independently. For example, if a pitcher wants to reduce the likelihood of a batter getting a hit, they might throw a fastball at 90+ MPH up and inside of the zone. Another option aimed at the same outcome would be a curveball at 78 MPH toward the middle-bottom of the zone. Instead of considering these variables individually, _then_ combining them like in our supervised models, we are able to group different combinations of pitches based on their similarity without using hit/no hit. This helps us to see the natural groupings of pitches and then analyze which combinations of variables are more/less effective.

# Key Parameter Choices

We decided to use 10 clusters for our K-means model. We believe that with the number of variable levels in our dataset, this parameter choice allowed us to get a good range of different pitch combinations without making the model too complex.

# Visualization

After we finished with the clustering, we calculated the hit rate within each cluster to see how different groups performed. We found that the hit rate does vary significantly between clusters, ranging from 2.1% to 6.7%. This tells us that the clusters are finding meaningful differences in variable combinations and that certain combinations are much more likely to result in a hit than others.

| Cluster | Effective Speed | Release Spin Rate | Pitch Name      | Zone | Pitch Count |
| ------- | --------------- | ----------------- | --------------- | ---- | ----------- |
| 0       | 83.81           | 2358.74           | Slider          | 13   | 0-1         |
| 1       | 93.52           | 2235.58           | 4-Seam Fastball | 11   | 0-0         |
| 2       | 93.44           | 2290.47           | 4-Seam Fastball | 11   | 1-0         |
| 3       | 93.21           | 2221.07           | 4-Seam Fastball | 13   | 1-0         |
| 4       | 82.32           | 1073.13           | Split-Finger    | 13   | 0-0         |
| 5       | 86.60           | 1717.89           | Changeup        | 13   | 1-1         |
| 6       | 78.61           | 2701.55           | Curveball       | 14   | 2-2         |
| 7       | 94.93           | 2280.62           | 4-Seam Fastball | 11   | 1-1         |
| 8       | 86.81           | 2441.30           | Slider          | 14   | 1-1         |
| 9       | 83.75           | 2390.82           | Slider          | 13   | 0-0         |

# Connection to Supervised Results

Our supervised model helped us see that zone was the biggest predictor by far, with other variables having only minor influences on hit probability. The clustering analysis we have done helps build on this by showing that its not just the individual predictors, but also combinations of our variables that influence hit outcomes. Our supervised model focused on prediction, this unsupervised model helps us better understand why certain pitch combinations are more effective.

# Final Conclusion

Overall, we found that pitch-level variables such as pitch location, pitch type, count, velocity, and pitcher handedness can predict hit outcomes moderately well, with pitch location being the most important factor. Although we tried a variety of more complex models, logistic regression turned out to be the best way to model Kyle Schwarber's hit probability. Our clustering results further helped us see that certain combinations of pitch characteristics lead to significantly different hit probabilities. Predicting hits is inherently challenging due to large imbalance in the data and variability, but we have found that both individual variables, like pitch location, and the interactions of these variables play a key role in hitting success.
