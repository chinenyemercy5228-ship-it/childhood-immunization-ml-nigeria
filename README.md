# Machine Learning-Based Prediction of Complete Childhood Immunization in Nigeria

## 📌 Project Overview

Childhood immunization remains an important public health challenge in Nigeria, where substantial disparities in vaccination coverage persist across socioeconomic and geographic groups.

This project applies machine learning to predict **complete childhood immunization status among children aged 12–23 months in Nigeria**, using data derived from the **2023–24 Nigeria Demographic and Health Survey (NDHS)**.

The project compares multiple machine learning algorithms, applies hyperparameter tuning and class balancing, and uses model interpretability techniques to identify the factors that contribute most strongly to immunization status.

> **Key finding:** Antenatal care (ANC) attendance and timing emerged as the strongest predictors in the final model.

---

## 🎯 Objectives

The project aimed to:

- Explore demographic, socioeconomic, and healthcare-utilization characteristics associated with childhood immunization.
- Develop machine learning models for predicting complete immunization status.
- Compare baseline and hyperparameter-tuned models.
- Evaluate models using Accuracy, Precision, Recall, F1-score, and ROC-AUC.
- Identify important predictors using feature importance and SHAP analysis.
- Translate the findings into relevant public health insights.

---

## 📊 Dataset

The analysis uses the **2023–24 Nigeria Demographic and Health Survey (NDHS) Children's Recode dataset**.

The study focused on children aged **12–23 months** and used a defined nine-dose basic immunization outcome comprising:

- BCG
- OPV 0–3
- Pentavalent 1–3
- Measles 1

After data cleaning and preprocessing, the final analytical sample contained:

**4,527 children**

### Outcome distribution

| Immunization Status | Frequency | Percentage |
|---|---:|---:|
| Not fully immunized | 3,037 | 67.09% |
| Fully immunized | 1,490 | 32.91% |

The raw NDHS dataset is **not included in this repository**.

---

## 🧹 Data Preparation

The analysis involved:

- Selecting children aged 12–23 months.
- Constructing the complete immunization outcome.
- Cleaning missing and inconsistent responses.
- Grouping high-cardinality categorical variables.
- Creating a composite media-exposure variable.
- Encoding categorical variables.
- Preparing numerical and categorical predictors for modelling.
- Addressing class imbalance during model development.

Feature engineering reduced the processed feature space from a potential **213 columns to 39 features**.

---

## 🔎 Exploratory Data Analysis

Exploratory analysis examined:

- Immunization status distribution
- Child age and sex
- Maternal characteristics
- Antenatal care attendance
- Timing of first ANC visit
- Maternal education
- Household wealth
- Place of delivery
- Geographic and socioeconomic differences
- Relationships between predictors and immunization status

The outcome was moderately imbalanced, with 67.09% of children classified as not fully immunized and 32.91% classified as fully immunized.

---

## 🤖 Machine Learning Models

The project evaluated **11 models** across five algorithm families:

1. Logistic Regression
2. Decision Tree
3. Random Forest
4. XGBoost
5. Support Vector Machine

Both baseline and tuned versions were evaluated where applicable.

Hyperparameter tuning was performed using **five-fold GridSearchCV**, with class balancing incorporated to improve minority-class detection.

---

## 🏆 Final Model

The **Tuned Random Forest** was selected as the final model.

### Final model performance

| Metric | Score |
|---|---:|
| Accuracy | 59.16% |
| Precision | 43.38% |
| Recall | 79.19% |
| F1-score | 0.5606 |
| ROC-AUC | **0.6985** |

The Tuned SVM achieved a slightly higher F1-score of 0.5642, but the Tuned Random Forest achieved the **highest ROC-AUC of all 11 models** and was selected as the final model.

### Random Forest hyperparameters

```text
n_estimators = 300
max_depth = 5
min_samples_leaf = 2
min_samples_split = 2
max_features = "sqrt"
class_weight = "balanced"
🔍 Model Interpretability

Feature importance and SHAP analysis were used to understand the predictors contributing to the final Random Forest model.

Top predictors
Rank	Feature	Importance
1	Number of ANC Visits	0.2909
2	Month of First ANC Visit	0.1931
3	Mother's Education	0.0808
4	Household Wealth Index	0.0627
5	Place of Delivery: Home	0.0623
6	Media Exposure	0.0400
7	Mother's Age	0.0340

The number of ANC visits and timing of the first ANC visit together accounted for approximately 48.4% of the model's total feature importance.

This highlights the potential importance of maternal healthcare contact as an opportunity for immunization promotion and scheduling.

💡 Public Health Significance

The findings suggest that maternal healthcare utilization, particularly antenatal care attendance and timing, is strongly associated with childhood immunization status in this dataset.

Potential programmatic implications include:

Integrating immunization counselling and scheduling into ANC contacts.
Strengthening outreach to mothers with no or late ANC attendance.
Supporting maternal education and household economic empowerment.
Promoting facility-based delivery as an additional opportunity for immunization promotion.
Testing predictive tools prospectively within routine health information systems before individual-level implementation.

These findings should be interpreted as predictive associations, not proof of causality.

🛠️ Technologies Used
Python
Pandas
NumPy
Matplotlib
Seaborn
Scikit-learn
XGBoost
SHAP
Jupyter Notebook
Git & GitHub
📁 Repository Structure
childhood-immunization-ml-nigeria/
│
├── notebooks/
│   └── Immunization_Project.ipynb
│
├── reports/
│   └── Immunization_Research_Report.docx
│
├── .gitignore
├── README.md
└── requirements.txt
▶️ How to Use
1. Clone the repository
git clone https://github.com/chinenyemercy5228-ship-it/childhood-immunization-ml-nigeria.git
2. Navigate to the project
cd childhood-immunization-ml-nigeria
3. Install dependencies
pip install -r requirements.txt
4. Open the notebook
jupyter notebook notebooks/Immunization_Project.ipynb

The raw NDHS dataset is not included in this repository and must be obtained through the appropriate DHS data access process.

📚 Research Report

The complete research report is available in:

reports/Immunization_Research_Report.docx

The report contains the detailed methodology, exploratory analysis, model evaluation, feature importance analysis, SHAP interpretation, discussion, conclusions, and recommendations.

⚠️ Limitations

This project has several limitations:

The analysis uses cross-sectional survey data.
Predictive associations should not be interpreted as causal relationships.
The model's performance is moderate and would require further validation before operational deployment.
Some potentially important factors, such as facility-level vaccine stock-outs, travel time to immunization facilities, and caregiver knowledge or attitudes, were not available in the dataset used.
Prospective validation would be necessary before using such a model for individual-level targeting.
🔮 Future Work

Future development could explore:

Additional healthcare facility-level data.
Geospatial measures such as travel time to immunization facilities.
Caregiver knowledge and attitudes.
Ensemble or stacking approaches.
Prospective validation using routine health information systems.
Fairness and equity assessment across socioeconomic and geographic groups.
Deployment as a public-health decision-support tool.
👩🏽‍💻 Author

Elechi Chinenye Mercy

Public Health Professional | AI & Machine Learning

Interested in applying data science, machine learning, and automation to public health challenges.

📌 Disclaimer

This project is an academic and research-oriented machine learning study. It is intended to demonstrate predictive modelling and public health analytics and should not be used as a standalone clinical or public-health decision-making system without further validation.