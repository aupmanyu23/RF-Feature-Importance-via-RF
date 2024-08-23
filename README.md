# RF-Feature-Importance-via-RF.

**Dataset:** Diabetic Patients' Re-admission Prediction (https://www.kaggle.com/datasets/saurabhtayal/diabetic-patients-readmission-prediction/data)


**Project Objective:**
The goal was to predict whether a diabetic patient will be readmitted to the hospital within 30 days using a dataset containing medical information about hospital admissions.

1. **Data Exploration and Preparation:**
   - We started with two datasets: `diabetic_data.csv` and `IDs_mapping.csv`.
   - We explored the dataset by examining the structure, summary statistics, and missing values using `df.describe()` and `df.isnull().sum()`.
   - Significant missing values were found in certain columns like `weight`, `payer_code`, and `medical_specialty`, and they were either removed or imputed appropriately.

2. **Data Cleaning:**
   - We handled missing values for non-critical columns and categorical columns.
   - Categorical features like `race`, `gender`, and `age` were encoded using one-hot encoding.
   - We ensured that the dataset was clean and suitable for further analysis by verifying that there were no missing values after processing.

3. **Feature Encoding:**
   - We transformed categorical columns into numerical ones using one-hot encoding.
   - This increased the number of features to 89.

4. **Correlation Matrix:**
   - A heatmap was generated to check for feature correlation, ensuring no significant collinearity issues.

5. **Feature Selection:**
   - Feature importance was determined using a RandomForestClassifier to rank the top features contributing to the prediction of readmission.
   - The most important features were `readmitted_>30`, `patient_nbr`, and `encounter_id`, among others.

6. **Model Building:**
   - The dataset was split into training and testing sets (80/20 ratio) to train a Random Forest model.
   - A GridSearchCV was applied for hyperparameter tuning, optimizing parameters like `n_estimators`, `max_depth`, `min_samples_split`, and `min_samples_leaf`.
   - Best parameters were identified as:
     ```
     max_depth=30
     min_samples_leaf=2
     min_samples_split=2
     n_estimators=200
     ```

7. **Model Evaluation:**
   - The Random Forest model achieved a **test accuracy of 67.17%**.
   - Confusion Matrix: The model performed better at predicting non-readmitted patients (True Negatives = 12100) than readmitted patients (True Positives = 1572).
   - Classification report showed that while the precision for non-readmitted patients was high, the model struggled to accurately predict readmissions with a lower recall (0.22).

### Conclusion:

- The model was able to reasonably predict whether patients would not be readmitted, but it had limited success in predicting the readmission class.
- To improve results, further work could include balancing the dataset (due to class imbalance), experimenting with different models, or improving feature selection techniques.

Let me know if you'd like to proceed with further improvements or next steps!
