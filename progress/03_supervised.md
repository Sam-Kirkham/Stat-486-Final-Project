1. Problem Context and Research Question

The goal of this project is to use pitch level metrics such as pitch speed, pitch location, pitch type, and pitcher handedness to predict the probability of Kyle Schwarber recording a hit. We hope to be able to think of any at bat scenario and figure out how likely he is to get a hit.

2. Supervised Models Implemented

| Model Type          | Key Hyperparameters Explored                                    | Validation Setup                                                          | Performance Metrics & Final Values       |
| ------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------------- | ---------------------------------------- |
| Logistic Regression | C (regularization strength), penalty, max_iter                  | 75/25 train-test split with stratification to preserve class balance      | AUC = **0.769**                          |
| SVM (RBF Kernel)    | C (regularization strength), gamma                              | 75/25 train-test split with stratification to preserve class balance      | AUC = **0.743**                          |
| Random Forest       | Number of trees, max depth, min samples per split, max features | 75/25 train-test split with stratification; OOB error used for validation | OOB Score = **0.9501**, AUC = **0.6679** |

Due to large imbalance in our dataset, accuracy is a misleading metric. We decided to use AUC as it works much better when one class appears a lot more frequently than the other.

3. Model Comparison and Selection

Discuss insights from model results:

What patterns or trends emerged across models?
One pattern that we noticed in all of our models is that zone is the most important feature in the models. This makes sense because pitch location can make it really hard for the hitter to reach and or get hits. Another thing that we saw in our models was that the pitcher's throwing hand does not greatly impact the model.

Which model performed best and why?
The best model was the Logistic Regression, SVM second and Random Forest was last. The Logistic regression model was the best because the features that we have in our data all improved the model predictions where as the other models had some features that were not greatly impactful in the models.

What challenges did you face (for example: overfitting, hyperparameter tuning)?
Our dataset has a large imbalance issue due to the huge amount of observations classified as no-hit compared to hit. This caused our SVM to almost always predict no-hit. Since there was such a large imbalance, the accuracy scores were still high even with little to no hits predicted. To address this we used a SMOTE balancing method.

4. Explainability and Interpretability

For our explainable AI Method we used Permutation Importance. What this importance shows is that if we randomly change the feature in the model how much does the AUC score decrease. From this table it is clear that zone is the most important feature. What the value of 0.239 tells us is that if we randomly shuffle zone in our model that means that our AUC score drops by 0.239. That is a huge drop, so we can see that zone is a major contributer in the model.

| Feature           | Importance |
| ----------------- | ---------- |
| zone              | 0.239019   |
| pitch_count       | 0.029867   |
| pitch_number      | 0.024371   |
| pitch_name        | 0.015921   |
| release_spin_rate | 0.004099   |
| effective_speed   | 0.002864   |
| p_throws          | 0.001692   |

5. Final Takeaways

During this analysis we fit an SVM, a random forest, and a logistic regression model to our pitch level data. We were able to see that although SVM and random forests are more flexible, the logistic regression model performed the best. This suggests that the relationship between the variables we chose as predictors and hit probability can be approximated pretty well by a linear decision boundary. When looking at feature importance, all three models had zone (pitch location) as the strongest predictor. This was further supported by the permutation importance that showed a substantial drop in AUC when zone was shuffled.

A huge part of the learning curve with this project has been dealing with imbalanced data. Since the data is so imbalanced, it is easy for our models to predict the majority class every time and still make out with a high accuracy score. To combat this we used methods such as SMOTE with the SVM and class_weight = "balanced" with the random forest combined with the use of AUC to get better insights on the true effectiveness of our models.

This analysis directly helps answer our research question. Our results show that pitch-level predictors can meaningfully predict hit probability with a moderate predictive power (AUC = 0.77). This predictive power is not evenly spread across our chosen features, however, and instead is heavily concentrated in pitch location with the other variables contributing to only small improvements. Overall, this means that while multiple pitch and batter characteristics contribute to outcomes, the location of the pitch is by far the most critical factor in determining whether Kyle Schwarber records a hit. The relationship seems to be pretty simple and structured, which is why using a simple, linear modeling type (logistic regression) performed better than some of the more complex models.
