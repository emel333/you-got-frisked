# you-got-frisked

Completed by: Marvin L. Mills II

# Key Question: Can we predict whether someone is frisked during a Terry Stop?


<ul>
    <li>Is there bias in the stops made by police officers?</li>
    <li>If the Terry v. Ohio ruling by the Supreme Court justified frisks, why are only some frisked?</li>
    <li>Which features are most important to those stopped being frisked as well?</li>
</ul>


# Process (& Data Science Tools) Used:


<ul>
    <li>Used the <i>Terry Stops dataset</i> provided by Data.gov, a publicly avaialable dataset, for cleaning, analyzing and modeling</li>
    <li>With "frisk_flag" as the target dependent variable, developed a classification model</li>
    <li>Engineered multiple features so as to use cleaner data -- Time of Day, Reported Quarter, Reported Year</li>
    <li>Separated data into train-test splits for the modeling process</li>
    <li>Focused on improving Recall and F1 scores to determine model effectiveness</li>
    <li>SMOTE data to increase the presence of the minority class in the dataset</li>
    <li>Performed modeling with KNN, Random Forests, Logistic Regression, Decision Trees, and XGBoost.</li>
</ul>


# Findings:


### Evening/Overnight 911 Calls have the strongest presence in the dataset; ages 26-35 do as well.

With more than 24,000 stops occurring in either the Evening or Overnight, this sheds light on the nature of the "Stops" most frequent in the dataset. It was also revealed that Calls with unreported reasoning have a strong presence, and individuals ages 26-35 were those most stopped during the Evening/Overnight times of day.

![alt text](https://github.com/emel333/you-got-frisked/blob/main/call_type_and_time_of_day.JPG "Call-Type-Time-of-Day-Heatmap")
![alt text](https://github.com/emel333/you-got-frisked/blob/main/time_of_day_with_age_group.JPG "Age-Group-Time-of-Day")



### Baseline model with significant class imbalance reveals high Accuracy score and low Recall, F1 and Precision scores

Using both scikit-learn's Dummy Classifier and K-nearest Neighbors, baseline Accuracy scores of 64.7% (Dummy classifier) and 72.9% (KNN) were established. F1, Recall and Precision scores were all below 25%. SMOTE data in response to increase presence of minority class, and focused on increasing Recall (True Positives) and Precision scores (True Positives / (True Positive + False Positive)).

![alt text](https://github.com/emel333/you-got-frisked/blob/main/initial_baseline_model.JPG "Baseline-Model")



### Logistic Regression modeling on fluctuating SMOTE Data Analysis revealed Recall score having the greatest sensitivity

By increasing the test size over a range, the resulting Recall scores show a clear downward trend, from ~0.515 to ~0.485, for both training and test samples. Precision and F1 scores did not improve significantly, either, showing the limitation of SMOTE Data on performance.

![alt text](https://github.com/emel333/you-got-frisked/blob/main/log_reg_smote_analysis_recall_score.JPG "Logistic-Regression-SMOTE-Date-Results")



# Winning Model -- Random Forests:

Achieved 70-72% Recall, 40-41% F1 and 28-29% Precision scores, with accuracy suffering and decreasing to 49-53%. 

![alt text](https://github.com/emel333/you-got-frisked/blob/main/final_model_scores_and_confusion_matrix.JPG "Final-Model-Random-Forests")



### Call Type (Not Reported) had the highest Feature Importance score, with 30% and 10%, respectively.

With greater than 0.04 between "Call Type - Not Reported" and the next feature, it consistently proved to be the most important. The second most important feature was "Call Type - 911." These features competed with demographic data for individuals stopped as well.

![alt text](https://github.com/emel333/you-got-frisked/blob/main/feature_importance_random_forest.JPG "Feature-Importance-Graphic")



#### The key adjustments made along the way:

<ul>
    <li>SMOTE Dataset to increase presence of minority class</li>
    <li>Tuned hyperparameters for Random Forests, Logistic Regression and XGBoost.</li>
</ul>



# Summary + Further Research:


<ul>
    <li>The features engineered did not prove reliable for predicting whether an individual was frisked.</li>
    <li>Undersampling of the dataset is recommended in order to further reduce class imbalance.</li>
    <li>Seek out datasets that contain more non-emergency Stops, as it seems 911 call Stops are different in nature.</li>
    <li>Pursue further hyperparameter tuning with XGBoost and Logistic Regression, after Undersampling is done.</li>
    <li>Generally, an increase in True Positives (Recall) comes with False Positives (Type I errors) as a package deal.</li>
</ul>