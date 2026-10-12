# Healthcare Data Integration & Fairness Analysis

### Leakage-Safe Hospital Mortality Prediction Using MIMIC-III

**Python | Machine Learning | Healthcare Analytics | Responsible AI**

## Project Overview

This project investigates hospital mortality prediction and demographic fairness using the MIMIC-III clinical demo dataset.

The aim is to demonstrate how healthcare machine learning models can be developed and evaluated responsibly, with particular attention to data preprocessing, patient-level data leakage, predictive performance, and demographic subgroup differences.

Two classification algorithms are compared: Logistic Regression and Random Forest.

### Explore the Analysis

**[View the Complete MIMIC-III Fairness Analysis Notebook](notebooks/MIMIC_Fairness_Validated_Public.ipynb)**

This notebook contains the reproducible Python workflow for:

- Patient-level data splitting and leakage prevention
- Healthcare data preprocessing
- Logistic Regression and Random Forest modelling
- Predictive performance evaluation
- Exploratory gender and ethnicity fairness analysis

**Note:** The raw clinical dataset is not included in this repository.

## Research Objectives

- Develop a reproducible hospital mortality prediction workflow.
- Prevent patient-level data leakage during model evaluation.
- Compare interpretable and ensemble machine learning methods.
- Evaluate predictive performance using multiple classification metrics.
- Explore differences in model performance across demographic subgroups.
- Document the limitations of machine learning with small clinical datasets.

## Dataset

**Source:** MIMIC-III Clinical Database Demo

The analysis combines patient demographic information from `PATIENTS.csv` with hospital admission information from `ADMISSIONS.csv`.

**Target variable:** `hospital_expire_flag` — an indicator of in-hospital mortality.

**Predictor variables:** Age at admission, gender, and recorded ethnicity.

The dataset is used for educational research and methodological demonstration, not clinical decision-making.

## Methodology

### 1. Data Preparation

Patient and admission records are merged using patient identifiers. Age is derived from the available date information, and relevant demographic predictors are selected.

### 2. Leakage Prevention

A patient-level train/test split is implemented using `GroupShuffleSplit`, ensuring that admissions belonging to the same patient cannot appear in both datasets.

Preprocessing is fitted using training data only.

### 3. Machine Learning

Two models are developed:

- **Logistic Regression:** An interpretable classification baseline.
- **Random Forest:** An ensemble classifier capable of modelling nonlinear relationships.

The preprocessing pipeline includes missing-value imputation, categorical encoding, and numerical scaling.

### 4. Model Evaluation

Model performance is assessed using accuracy, ROC-AUC, average precision, confusion matrices, and ROC curves.

### 5. Exploratory Fairness Assessment

The analysis examines predictive performance across gender and ethnicity subgroups.

Because the demo dataset is small, subgroup findings are exploratory and cannot establish reliable population-level fairness or discrimination.

## Results and Interpretation

### Model Performance

| Metric | Logistic Regression | Random Forest |
|---|---:|---:|
| Accuracy | 40.9% | 45.5% |
| ROC-AUC | 0.371 | 0.571 |
| Average Precision | 0.390 | 0.509 |

**Evaluation:** 107 training admissions and 22 test admissions.

**Data leakage check:** Zero overlapping patients between the training and test sets.

Random Forest achieved higher scores than Logistic Regression on this particular test split. However, both models showed limited predictive performance.

The small test set means these results are unstable and should not be interpreted as evidence of clinical usefulness.


The analysis demonstrates a reproducible machine learning workflow with zero patient overlap between training and testing.

Predictive performance is limited, highlighting the challenges of developing reliable clinical prediction models using small datasets and a restricted set of demographic features.

The project prioritises methodological transparency over maximising model accuracy.

### Model Visualisations

#### Confusion Matrices

![Logistic Regression and Random Forest Confusion Matrices](figures/confusion_matrices.png)

The confusion matrices show the models' correct and incorrect mortality classifications.

#### ROC Curves

![Logistic Regression and Random Forest ROC Curves](figures/roc_curves.png)

The ROC curves compare the models' ability to distinguish between mortality outcomes across classification thresholds.


## Technology Stack

- Python
- pandas and NumPy
- scikit-learn
- Matplotlib
- Google Colab
- Git and GitHub

## Repository Structure


healthcare-data-integration-fairness/
├── data/
├── figures/
│   ├── confusion_matrices.png
│   └── roc_curves.png
├── notebooks/
│   ├── MIMIC_Fairness_Validated_Public.ipynb
│   └── archive/
│       ├── Healthcare_Fairness_Analysis.ipynb
│       └── MIMIC_Fairness_Validated (2).ipynb
├── reports/
├── requirements.txt
├── .gitignore
└── README.md


## Reproducing the Analysis

1. Clone or download this repository.
2. Open `notebooks/MIMIC_Fairness_Validated_Public.ipynb` in Google Colab.
3. Obtain authorised access to the required MIMIC-III demo CSV files.
4. Update the notebook's dataset path.
5. Run the notebook cells in order.
6. Review the generated performance metrics, visualisations, and exploratory subgroup analysis.

The raw clinical dataset is not distributed through this repository.

## Limitations

- The MIMIC-III demo dataset contains relatively few records.
- Predictive results may be unstable and sensitive to the train/test split.
- The models use only a small number of demographic predictors.
- Small subgroup sample sizes limit the reliability of fairness comparisons.
- The models are not clinically validated or suitable for deployment.

## Future Improvements

- Evaluate models on larger, appropriately authorised datasets.
- Investigate fairness across additional demographic and clinical subgroups.
- Compare alternative preprocessing and missing-data strategies.
- Introduce confidence intervals and repeated patient-level validation.
- Develop an interactive Power BI dashboard for presenting results.

## Author

**Tomiwa Emmanuel Ogunrinde**

MSc Big Data & Data Science Technology

Interests: Data Science, Healthcare Analytics, Machine Learning, Data Governance and Responsible AI.

---

*This project is intended for research, learning, and professional portfolio demonstration only.*
