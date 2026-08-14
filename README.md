# Machine Learning-Based Prediction of Complete Childhood Immunization in Nigeria

## Overview

This project develops and evaluates machine learning models for predicting **complete childhood immunization status among Nigerian children aged 12–23 months**, using the **2023–24 Nigeria Demographic and Health Survey (NDHS) Children's Recode (KR) dataset**.

The project combines public health research with machine learning to explore whether routinely collected child, maternal, household, socioeconomic, media-exposure, and healthcare-utilization characteristics can help identify patterns associated with childhood immunization completeness.

## Research Question

Which characteristics are most useful for predicting complete childhood immunization among Nigerian children aged 12–23 months, and which machine learning approach provides the strongest overall predictive performance?

## Dataset

The analysis used the 2023–24 NDHS Children's Recode (KR) file. The raw DHS dataset is **not included in this repository** because it is subject to DHS data-use terms.

After restricting the data to children aged 12–23 months, constructing the immunization outcome, and applying the documented cleaning rules, the final analytic sample contained **4,527 children**:

- 3,037 (67.09%) not fully immunized
- 1,490 (32.91%) fully immunized

Complete immunization was defined from nine basic vaccine doses: BCG, OPV0–3, Pentavalent 1–3, and Measles 1.

## Methodology

The project followed a reproducible machine learning workflow:

1. Data cleaning and outcome construction
2. Exploratory data analysis
3. Feature engineering and cardinality reduction
4. Stratified 80/20 train-test split
5. Mixed-type preprocessing using `ColumnTransformer`
6. Model training and comparison
7. Hyperparameter tuning with five-fold `GridSearchCV`
8. Evaluation using Accuracy, Precision, Recall, F1-score, and ROC-AUC
9. Feature-importance analysis
10. SHAP-based model interpretation

### Models evaluated

Eleven model configurations were compared across five algorithm families:

- Logistic Regression
- Decision Tree
- Random Forest
- XGBoost
- Support Vector Machine (SVM)

## Final Model

The **Tuned Random Forest** was selected as the final model in consultation with the project supervisor.

| Metric | Tuned Random Forest |
|---|---:|
| Accuracy | 59.16% |
| Precision | 43.38% |
| Recall | 79.19% |
| F1-score | 0.5606 |
| ROC-AUC | 0.6985 |

The tuned Random Forest achieved the **highest ROC-AUC among all eleven models**. The Tuned SVM achieved a marginally higher F1-score (0.5642), but the difference was small; the Random Forest was preferred based on its ROC-AUC, competitive F1-score, Precision, Accuracy, interpretability, and the project supervisor's recommendation.

## Key Findings

The strongest predictors in the final Random Forest were primarily related to maternal healthcare utilization and socioeconomic conditions.

The top features included:

1. Number of ANC visits — 29.09%
2. Month of first ANC visit — 19.31%
3. Mother's education — 8.08%
4. Household wealth index — 6.27%
5. Place of delivery: Home — 6.23%
6. Media exposure — 4.00%

The number and timing of antenatal care visits together accounted for approximately **48.4% of the model's total feature importance**.

These findings suggest that antenatal care represents an important point of contact for integrating immunization counselling, scheduling, and follow-up interventions.

## Repository Structure

```text
immunization-ml-project/
├── notebooks/
│   └── Immunization_Project.ipynb
├── reports/
│   └── Immunization_Research_Report.docx
├── README.md
├── requirements.txt
└── .gitignore
```

The notebook expects the cleaned modelling dataset used during development. Because the original NDHS data are governed by data-use restrictions, the dataset is intentionally excluded from this repository.

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- SHAP
- Joblib
- Jupyter Notebook

## Public Health Relevance

The project demonstrates how machine learning can complement public health analysis by moving beyond descriptive associations toward predictive screening. The findings highlight antenatal care as a potentially valuable entry point for strengthening immunization promotion and identifying populations that may require additional outreach.

The model is a **research prototype**, not a clinical diagnostic or autonomous decision-making system. Prospective validation, fairness assessment, and integration with appropriate routine health information systems would be required before operational use.

## Ethical Considerations

The study used secondary, de-identified NDHS data accessed under the applicable DHS data-use terms. No personally identifiable information is included in this repository.

## Author

**Elechi Chinenye Mercy**  
Public Health | AI & Machine Learning

## Citation / Project Reference

This repository accompanies the research project:

**“Machine Learning-Based Prediction of Complete Childhood Immunization Among Nigerian Children Using the Nigeria Demographic and Health Survey (NDHS) 2023–24 Dataset.”**
