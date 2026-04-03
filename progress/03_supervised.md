1. Problem Context and Research Question

The goal of this project is to use pitch level metrics such as pitch speed, pitch location, pitch type, and pitcher handedness to predict the probability of Kyle Schwarber recording a hit. We hope to be able to think of any at bat scenario and figure out how likely he is to get a hit.

2. Supervised Models Implemented

Create a table or concise summary listing:

Model type
Key hyperparameters explored
Validation setup used (for example: train/validation split or cross-validation)
Performance metrics used and final values

Model type: Random Forest
Key hyperparameters explored: Number of trees, maximum tree depth, minimum samples per split, maximum features per split, and class weight.
Validation setup used (for example: train/validation split or cross-validation): We used a train/test split with 75% training, 25% test with stratification to preserve the class balance. Out of bag error was used as our validation metric.
Performance metrics used and final values: We used out of bag error to approximate the test accuracy of the random forest. OOB score: 0.9501. We also used AUC score which resulted in a score of 0.66793.

3. Model Comparison and Selection

Discuss insights from model results:

What patterns or trends emerged across models?
Which model performed best and why?
What challenges did you face (for example: overfitting, hyperparameter tuning)?
Our dataset has a large imbalance issue due to the huge amount of observations classified as no-hit compared to hit. This caused our SVM to almost always predict no-hit. Since there was such a large imbalance, the accuracy scores were still high even with little to no hits predicted. To address this we used a SMOTE balancing method.

4. Explainability and Interpretability

Present one explainability output and interpret what it suggests about model behavior.

5. Final Takeaways

Summarize key insights gained from supervised learning.
Explain how this analysis answers your research question.
