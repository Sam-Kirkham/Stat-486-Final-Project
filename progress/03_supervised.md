1. Problem Context and Research Question

The goal of this project is to use pitch level metrics such as pitch speed, pitch location, pitch type, and pitcher handedness to predict the probability of Kyle Schwarber recording a hit. We hope to be able to think of any at bat scenario and figure out how likely he is to get a hit.

2. Supervised Models Implemented

Create a table or concise summary listing:

Model type: Logistic Regression
Key hyperparameters explored: C (Regularization Strength), penalty, max_iter.
Validation setup used (for example: train/validation split or cross-validation): We used a train/test split with 75% training, 25% test with stratification to preserve the class balance. 
Performance metrics used and final values: We used AUC score which resulted in a score of 0.769.

Model type: SVM (RBF Kernel)
Key hyperparameters explored: C (Regularization Strength), gamma.
Validation setup used (for exaxmple: train/validation split of cross validation): We used a train/test split with 75% training, 25% test with stratification to preserve the class balance.
Performance metrics used and final values: We used AUC score which resulted in a score of 0.743.

Model type: Random Forest
Key hyperparameters explored: Number of trees, maximum tree depth, minimum samples per split, maximum features per split, and class weight.
Validation setup used (for example: train/validation split or cross-validation): We used a train/test split with 75% training, 25% test with stratification to preserve the class balance. Out of bag error was used as our validation metric.
Performance metrics used and final values: We used out of bag error to approximate the test accuracy of the random forest. OOB score: 0.9501. We also used AUC score which resulted in a score of 0.66793.

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
|-------------------|------------|
| zone              | 0.239019   |
| pitch_count       | 0.029867   |
| pitch_number      | 0.024371   |
| pitch_name        | 0.015921   |
| release_spin_rate | 0.004099   |
| effective_speed   | 0.002864   |
| p_throws          | 0.001692   |

5. Final Takeaways

Summarize key insights gained from supervised learning.
Explain how this analysis answers your research question.
