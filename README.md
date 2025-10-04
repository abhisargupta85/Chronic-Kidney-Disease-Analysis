# Chronic-Kidney-Disease-Analysis
Machine learning classification project on Chronic Kidney Disease data


# Chronic Kidney Disease (CKD) Prediction Model

## Project Overview

This project focuses on developing a Machine Learning classification model to predict whether an individual is likely to have Chronic Kidney Disease (CKD) based on various diagnostic and physiological parameters. Early detection of CKD is critical as timely intervention can significantly slow down or halt the progression of kidney failure.

The analysis involves extensive data preprocessing, feature engineering, and training of a Random Forest Classifier to achieve high predictive accuracy.



## Motivation and Value

Chronic Kidney Disease is a major and growing global health concern, affecting millions worldwide. This project contributes to the field by demonstrating a high-accuracy, data-driven tool for early patient discovery based on a minimal set of factors.

 - **Goal:** To create a prediction model to identify individuals with CKD.

 - **Impact:** Early discovery allows healthcare providers to implement life-saving interventions sooner.

 - **Final Accuracy:** The Random Forest model achieved a predictive accuracy of 97% on the test set.


## Technical Details

### Dependencies

The project is built using Python and requires the following libraries. You can install them using pip:


Bash

    pip install pandas numpy matplotlib scikit-learn

## Key Libraries Used

 - pandas and numpy: For data manipulation, cleaning, and numerical operations.

 - matplotlib.pyplot: For data visualization (histograms, density plots, correlation matrix, feature importance).

 - sklearn: The core library for machine learning tasks, including:

    - **MinMaxScaler:** For data scaling.
  
    - **ExtraTreesClassifier:** For initial feature importance analysis.
  
    - **RandomForestClassifier:** The primary classification model used.
  
    - **train_test_split:** For dividing data into training and testing sets.


## Data Set Information
The data used for this project is publicly available and was collected from multiple hospitals.

 - **Data Source:** Chronic Kidney Disease Dataset, UCI Machine Learning Repository
 - **Original Link:** http://archive.ics.uci.edu/dataset/336/chronic+kidney+disease
 - **Original Format:** .arff (used in the reading step).
 - **Number of Instances:** 400
 - **Number of Attributes (Features):** 24 + 1 Class/Label

### Project Delimitations
 1. Data collected only from 1 country (India), which may limit generalizability.
 2. Relatively small sample size of 400 instances.

## Data Preprocessing & Feature Engineering
The reliability of the high accuracy stems from extensive data cleaning and preparation steps:

 1. **Missing Value Handling:**
     - Missing values (? and \t?) were converted to np.NaN.
     - Numerical columns (age, bloodPressure, bloodUrea, etc.) were imputed using the column mean.
     - Categorical columns were imputed using the most frequent value (mode).

 2. **Nominal to Numerical Conversion:** All nominal (text-based) features (e.g., redBloodCells, hypertension, appetite) were mapped to binary numerical values (e.g., yes → 1, no → 0).

 3. **Outlier Removal:** The Interquartile Range (IQR) method (using standard deviation checks) was used to identify and remove extreme outliers in key physiological attributes (e.g., bloodPressure, bloodUrea) to prevent model skew.

 4. **Data Scaling:** Numerical columns were scaled using MinMaxScaler to normalize values between 0 and 1, a best practice for distance-based and gradient-based algorithms.

 5. **Feature Selection:**
     - ExtraTreesClassifier was used to determine the feature importance of all 24 attributes.
     - Features with the lowest impact (like bacteria, coronaryArteryDisease, pusCellClumps) were removed.
     - The final model utilizes 10 highly predictive features to reduce complexity and improve interpretability.

## Model Training and Results

### Training Strategy
 - **Model:** Random Forest Classifier (random_state=42).
 - **Data Split:** The cleaned and prepared dataset was split into 70% for training and 30% for testing (random_state=5).
 - **Class Distribution Check:** The initial dataset showed a balanced distribution of ckd (59.07%) and notckd (40.93%) cases, minimizing bias issues.

    **Performance**

       Metric	       Training Set      Test Set
       Accuracy	      100.00%	      97.00%

The high accuracy and successful external validation (testing against new, synthetic data) confirm the model's robustness and strong generalization ability.


## How to Run

 1. Clone this repository:
    Bash

        git clone [Your-Repo-Link]

 2. Ensure you have the required libraries installed (see Dependencies).

 3. Open the main Jupyter Notebook (Chronic Kidney Disease Project.ipynb) and run all cells sequentially.

(**Note:** The notebook also includes an interactive final step where a user can input 10 feature values to get a real-time prediction.

This project uses publicly available data for educational and analytical purposes. No personal data is stored or processed beyond what is publicly accessible.
)
