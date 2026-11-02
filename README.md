# Heart Disease Prediction (PRCP-1016)

Machine learning project that predicts whether a patient has heart disease from clinical and exercise test measurements, using Python and Scikit-learn, to support early screening in hospitals.

## Business Problem
Cardiovascular diseases are the number one cause of death worldwide, and early detection is key to prevention. This project analyzes patient data and builds a model that can help hospitals flag patients who may need further clinical assessment.

## Project Tasks
1. Prepare a complete data analysis report on the given data.
2. Build machine learning models to predict the presence of heart disease.
3. Compare multiple models and recommend a candidate for production.
4. Report the challenges faced and the techniques used.
5. Suggest ways hospitals can use the predictions for early identification and prevention.

## Dataset
- 180 patient records and 14 columns (a patient ID plus 13 clinical features)
- Features and labels come in two files (`values.csv` and `labels.csv`) and were merged on `patient_id`
- Target: `heart_disease_present` (1 = heart disease present, 0 = not present)
- Features include age, sex, chest pain type, resting blood pressure, serum cholesterol, fasting blood sugar, resting ECG results, maximum heart rate, exercise-induced angina, ST depression (`oldpeak`), slope of the peak exercise ST segment, number of major vessels, and the thallium stress test result (`thal`)
- No missing values and no duplicate records were found
- The data is not included in this repository. It is available from the course project source.

## Approach
1. **Data preparation:** merged the feature and label files, checked missing values and duplicates, and removed the patient ID before modeling
2. **EDA:** target distribution, histograms and boxplots for numeric features, count plots of categorical features against the target, and a correlation heatmap
3. **Outlier analysis:** identified outliers with the IQR method and boxplots. They were reviewed but not removed, since extreme medical readings may be genuine patient conditions.
4. **Preprocessing pipeline:** median imputation and scaling for numeric features; most-frequent imputation and one-hot encoding for categorical features (`thal`)
5. **Train/test split:** stratified 80/20 split to keep the class proportions
6. **Modeling:** compared 5 classification models and selected a candidate using F1-score, with recall and the confusion matrix also considered

## Models Compared
Logistic Regression, Decision Tree, Random Forest, Support Vector Machine, K-Nearest Neighbors

## Results
Results on the hold-out test set (36 patients):

| Model | Accuracy | Precision | Recall | F1 | ROC-AUC |
|---|---|---|---|---|---|
| Logistic Regression | `<value>` | `<value>` | `<value>` | `<value>` | `<value>` |
| Decision Tree | `<value>` | `<value>` | `<value>` | `<value>` | `<value>` |
| Random Forest | `<value>` | `<value>` | `<value>` | `<value>` | `<value>` |
| Support Vector Machine | `<value>` | `<value>` | `<value>` | `<value>` | `<value>` |
| K-Nearest Neighbors | `<value>` | `<value>` | `<value>` | `<value>` | `<value>` |

**Candidate model:** `<model name>`, selected for the highest F1-score. Recall was also considered, because missing a patient who has heart disease is costly in a healthcare setting.

## Key Insights
- `<insight 1: for example, which features are most associated with heart disease, from the correlation or feature importance output>`
- `<insight 2: for example, the thal test result or chest pain type vs heart disease>`
- `<insight 3: for example, the top features from the Random Forest feature importance>`

## Recommendations for Hospitals
1. Use the model as a screening and decision-support tool to flag patients who need further assessment.
2. Monitor the patient characteristics that the analysis shows to be most important.
3. Use high-risk predictions to generate alerts for healthcare professionals.
4. Keep patient records accurate, complete and consistent.
5. Re-evaluate the model regularly with new, representative patient data.
6. Keep a clinician in the loop: predictions should support, not replace, medical judgment.
7. Follow healthcare data privacy, security and governance requirements.

## Challenges and Techniques
| Challenge | Technique | Reason |
|---|---|---|
| Features and labels in separate files | Merged on `patient_id` | Create one complete modeling dataset |
| Patient identifier | Removed before modeling | A random ID is not a useful medical feature |
| Categorical feature (`thal`) | One-hot encoding | Convert categories to model-ready numbers |
| Different numeric scales | StandardScaler | Comparable scales for scale-sensitive models such as SVM and KNN |
| Outliers | IQR and boxplot analysis, reviewed but kept | Extreme medical readings may be genuine |
| Missing a positive case is costly | Recall and confusion matrix analysis | Missed cases matter most in screening |
| Model selection | Accuracy, Precision, Recall, F1, ROC-AUC and confusion matrix | A broader view than accuracy alone |
| Small dataset (180 patients) | Stratified split and awareness of validation limits | Results may change on a larger population |

## Limitations
- The dataset is small (180 patients), so the test set has only 36 patients and results can change noticeably with a different split.
- A single train/test split gives one evaluation sample; cross-validation and larger datasets would make the results more reliable.
- The model is a decision-support idea, not a medical diagnostic system.

## Tech Stack
Python, Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn, Jupyter Notebook

## How to Run
1. Clone the repository.
2. Install the requirements: `pip install -r requirements.txt`
3. Download the dataset from the course project source and place `values.csv` and `labels.csv` in a folder named `Data` beside the notebook.
4. Run `PRCP-1016-HeartDiseasePrediction_Complete.ipynb` from top to bottom.
