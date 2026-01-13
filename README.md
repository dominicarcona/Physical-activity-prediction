# Physical Activity Prediction from Wearable Sensors
Originally a MATH 550 (Seminar in Statistical Consulting) project at USC, this repository contains a comprehensive machine learning analysis of the PAMAP2 Physical Activity Monitoring dataset in R. The project focuses on the classification of 13 unique physical activities using high-frequency heart rate and inertial measurement unit (IMU) data collected from multiple body locations. Results of the analysis can be digested via the .html knit (activity_classification.html) or the presentation slides ('M550 PAP.pptx') included in this repository.

# Executive Summary
The primary objective of this study was to evaluate the predictive performance of various classification architectures in identifying specific physical activities from raw sensor streams. By comparing Multinomial Logistic Regression and Random Forest ensembles, the analysis demonstrates that tree-based models effectively capture the non-linear boundaries inherent in physiological and motion data, achieving a classification accuracy of 97.2%. Additionally, the project investigates the trade-offs between multi-sensor arrays and single-sensor configurations for consumer wearable applications.

# Model Performance Summary
-Baseline Random Forest: 97.2% Accuracy across 13 activity classes.

-Reduced Feature Random Forest: 93.8% Accuracy using only 3 key predictors (Scaled Heart Rate, Chest Z-Axis Acceleration, and Body Temperature).

-Binary Exercise Detection: 0.9968 AUC in distinguishing deliberate exercise from sedentary or transient activities.

-Sensor Localization: Hand and Chest sensors demonstrated superior predictive power (95%+ accuracy) compared to Ankle-worn sensors.

# Methodology and Feature Engineering
The dataset comprises over 2.86 million observations from 8 participants. To ensure model robustness and generalizability, the following preprocessing steps were implemented:

-Heart Rate Scaling: Heart rate data was normalized to each participant's recorded maximum to account for individual fitness variances and resting heart rate differences.

-Sensor Fusion: Correlated temperature readings from the chest, hand, and ankle were synthesized into a single body temperature metric to reduce feature redundancy.

-Missing Value Imputation: Linear interpolation was used to handle missing heart rate values within the time-series data.

-Class Weighting: Custom weights were applied to the training phase to mitigate class imbalance, ensuring that infrequent activities like "rope jumping" were prioritized alongside common activities like "walking".

# Technical Stack
-Environment: R (R Markdown)

-Classification Models: Random Forest, Multinomial Logistic Regression

-Evaluation Metrics: Confusion Matrices, Sensitivity/Recall, ROC/AUC analysis

-Primary Libraries: tidyverse, randomForest, caret, pROC, zoo

# Findings and Future Work
The results indicate that Random Forest classifiers significantly outperform linear models in this domain due to their ability to handle non-linear activity clusters in the predictor space. Furthermore, the study suggests that single-sensor placement on the wrist or chest provides nearly equivalent performance to multi-sensor configurations, which has significant implications for the development of consumer-facing health technology.

## Future iterations of this research could focus on:

-Temporal Smoothing: Implementing Hidden Markov Models (HMM) or similar sequences to account for the temporal continuity of human movement.

-Hyperparameter Optimization: Refining mtry and increasing ntree counts beyond default settings to maximize predictive precision.

-Context-Aware Models: Exploring 2-step classification approaches where exercise is first detected before identifying the specific activity type.

# Setup and Usage
- Download `dataset2.csv` from the [Kaggle data source](https://www.kaggle.com/datasets/diegosilvadefrana/fisical-activity-dataset/data) made publicly available thanks to Diego Silva.
-  Ensure the CSV is located in the project root directory.
- Open `activity_classification.Rmd` in RStudio and knit to HTML.

### Author: Dominic Arcona 
### Date: December 2023
