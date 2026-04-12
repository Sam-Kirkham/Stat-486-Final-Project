Welcome to our in depth analysis of Kyle Schwarber's 2021-2025 seasons! We are both big baseball fans and wanted to see how we could extend the machine learning concepts that we have covered in class into real sports data. Specifically, we were curious to know what factors contribute to the probability of a player getting a hit or not. This led us to our project question: How well can pitch-level variables such as pitch location, pitch type, count, velocity, and pitcher handedness predict the probability that Kyle Schwarber gets a hit, and which of these are most influential?

# Repository Structure

├── data/ # Data files
├── progress/ # Project deliverables
├── Supervised Models/ # Model fitting and exploration code
├── Unsupervised Models/ # K-means and PCA fitting code
├── Demo.ipynb # Main demo notebook
├── README.md # Project overview
├── requirements.txt # Dependencies

# Steps to Reproduce Results

1. Clone the repository

```bash
  git clone https://github.com/Sam-Kirkham/Stat-486-Final-Project.git
  cd Stat-486-Final-Project
```

2. Create a virtual environment

```bash
  #If on windows, use python instead of python3
  python3 -m venv venv
  source venv/bin/activate

  #venv\Scripts\activate     for Windows
```

3. Install dependencies

```bash
  pip install -r requirements.txt
```

4. Run the demo notebook
   Open and run Demo.ipynb

# Main Results

Three different supervised models were attempted, all using hit/no hit as the boolean response. The summary table below shows that of the three, logistic regression performed the best when evaluated using AUC, suggesting that the relationship between hits and pitch level predictors is fairly linear. The AUC of 0.769 tells us that this model is still not perfect and only moderately predicts a hit.

| Model Type          | Key Hyperparameters Explored                                    | Validation Setup                                                          | Performance Metrics & Final Values       |
| ------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------------- | ---------------------------------------- |
| Logistic Regression | C (regularization strength), penalty, max_iter                  | 75/25 train-test split with stratification to preserve class balance      | AUC = **0.769**                          |
| SVM (RBF Kernel)    | C (regularization strength), gamma                              | 75/25 train-test split with stratification to preserve class balance      | AUC = **0.743**                          |
| Random Forest       | Number of trees, max depth, min samples per split, max features | 75/25 train-test split with stratification; OOB error used for validation | OOB Score = **0.9501**, AUC = **0.6679** |

The permutation importance for the logistic regression model shows that zone is by far the strongest predictor. The importance value of 0.239 suggests that if zone were to be shuffled randomly, the AUC value would drop by 0.239. The other predictors had some effect, but very small in comparison to zone.

| Feature           | Importance |
| ----------------- | ---------- |
| zone              | 0.239019   |
| pitch_count       | 0.029867   |
| pitch_number      | 0.024371   |
| pitch_name        | 0.015921   |
| release_spin_rate | 0.004099   |
| effective_speed   | 0.002864   |
| p_throws          | 0.001692   |

After fitting the supervised models, we tested the unsupervised K-means clustering method with k = 10 to try and identify the natural groupings of pitches. The different clusters correspond to distinct pitching strategies. These clusters resulted in a wide range of hit probabilities, showing that some combinations are more effective than others.

| Cluster | Effective Speed | Release Spin Rate | Pitch Name      | Zone | Pitch Count | Hit      |
| ------- | --------------- | ----------------- | --------------- | ---- | ----------- | -------- |
| 0       | 83.81           | 2358.74           | Slider          | 13   | 0-1         | 0.035138 |
| 1       | 93.52           | 2235.58           | 4-Seam Fastball | 11   | 0-0         | 0.040890 |
| 2       | 93.44           | 2290.47           | 4-Seam Fastball | 11   | 1-0         | 0.045517 |
| 3       | 93.21           | 2221.07           | 4-Seam Fastball | 13   | 1-0         | 0.067287 |
| 4       | 82.32           | 1073.13           | Split-Finger    | 13   | 0-0         | 0.024138 |
| 5       | 86.60           | 1717.89           | Changeup        | 13   | 1-1         | 0.045694 |
| 6       | 78.61           | 2701.55           | Curveball       | 14   | 2-2         | 0.044720 |
| 7       | 94.93           | 2280.62           | 4-Seam Fastball | 11   | 1-1         | 0.056293 |
| 8       | 86.81           | 2441.30           | Slider          | 14   | 1-1         | 0.044271 |
| 9       | 83.75           | 2390.82           | Slider          | 13   | 0-0         | 0.021250 |

# Data Sources

All of our data comes from StatCast powered by Google Cloud which is hosted on baseballsavant.mlb.com. To get our specific csv file, we used the search function and filtered by Batters (Kyle Schwarber) and Season (2021-2025). This data is publicly available for research and analysis use, and all use in this project has been in compliance with the MLB StatCast terms and conditions.
