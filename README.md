# Machine Learning-Based Prediction of Complete Childhood Immunization in Nigeria

### Predicting Immunization Status Using the 2023–24 Nigeria Demographic and Health Survey

---

## 🩺 About the Project

Childhood immunization is a major public health intervention, yet many children in Nigeria do not complete the recommended basic vaccination schedule.

This project investigates whether machine learning can be used to predict **complete childhood immunization status among Nigerian children aged 12–23 months** and identify the factors that contribute most strongly to those predictions.

The study uses the **2023–24 Nigeria Demographic and Health Survey (NDHS) Children's Recode dataset** and combines exploratory data analysis, feature selection, machine learning, hyperparameter tuning, class-imbalance handling, and explainable AI.

The ultimate goal is not simply to build a model, but to explore how predictive analytics could support **earlier identification of children who may be at risk of incomplete immunization** and inform targeted public health interventions.

---

## 🎯 Research Aim

To develop and evaluate machine learning models for predicting complete childhood immunization status among Nigerian children aged 12–23 months and identify the predictors most strongly associated with complete immunization.

---

## ❓ The Problem

In the analytical sample used in this study:

- **32.91%** of children were fully immunized.
- **67.09%** were not fully immunized.
- The analysis included **4,527 children** aged 12–23 months.

Complete immunization was defined using nine basic vaccine doses:

**BCG, OPV 0–3, Pentavalent 1–3, and Measles 1.**

This creates an important public health question:

> **Can routinely available demographic, socioeconomic, and maternal healthcare information help identify children who are less likely to complete their basic immunization schedule?**

---

## 📊 Dataset

### Data Source

**2023–24 Nigeria Demographic and Health Survey (NDHS)**

The study uses the **Children's Recode (KR) file**, obtained in SPSS `.SAV` format and processed using Python.

The survey provides nationally representative information covering Nigeria's 36 states and the Federal Capital Territory. :contentReference[oaicite:1]{index=1}

### Study Population

Children aged **12–23 months**.

### Final Sample

**4,527 children**

| Immunization Status | Number | Percentage |
|---|---:|---:|
| Fully immunized | 1,490 | 32.91% |
| Not fully immunized | 3,037 | 67.09% |

### Vaccine Components

The outcome represents completion of:

- BCG
- OPV 0
- OPV 1
- OPV 2
- OPV 3
- Pentavalent 1
- Pentavalent 2
- Pentavalent 3
- Measles 1

The raw NDHS dataset is **not included in this repository**.

---

## 🧠 What Makes This Project Different?

Rather than relying on a single statistical model, the study systematically compares multiple machine learning approaches.

The project combines:

**Public Health Research**

+

**Machine Learning**

+

**Explainable AI**

+

**Predictive Modelling**

This allows the analysis to answer two different questions:

1. **How accurately can immunization status be predicted?**
2. **Which factors are most influential in those predictions?**

---

## 🔬 Methodology

The project followed a structured machine learning workflow:

**NDHS Data**

→ Data Cleaning

→ Sample Restriction

→ Immunization Outcome Construction

→ Feature Selection

→ Exploratory Data Analysis

→ Preprocessing

→ Class Imbalance Handling

→ Model Development

→ Hyperparameter Tuning

→ Model Evaluation

→ Feature Importance

→ SHAP Interpretation

→ Public Health Interpretation

---

## 🧹 Data Preparation

The study involved:

- Restricting the dataset to children aged 12–23 months.
- Constructing a binary complete-immunization outcome.
- Cleaning vaccination and predictor variables.
- Selecting relevant demographic, socioeconomic, and healthcare-utilization predictors.
- Performing exploratory analysis.
- Conducting Cramér's V association analysis.
- Encoding categorical variables.
- Preparing features for machine learning.
- Addressing class imbalance during model development.

Seventeen predictor variables were retained following the association analysis. :contentReference[oaicite:2]{index=2}

---

## 🤖 Machine Learning Models

Five algorithm families were evaluated:

1. Logistic Regression
2. Decision Tree
3. Random Forest
4. XGBoost
5. Support Vector Machine

Both baseline and tuned configurations were evaluated, resulting in **11 models in total**.

Hyperparameter optimisation was performed using:

- GridSearchCV
- Five-fold cross-validation
- Stratified train-test splitting
- Class balancing where appropriate

Models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

---

## 🏆 Final Model

### Tuned Random Forest

The **Tuned Random Forest** was selected as the final model in consultation with the project supervisor.

### Performance

| Metric | Result |
|---|---:|
| Accuracy | **59.16%** |
| Precision | **43.38%** |
| Recall | **79.19%** |
| F1-score | **0.5606** |
| ROC-AUC | **0.6985** |

The model achieved the **highest ROC-AUC among the models evaluated**. :contentReference[oaicite:3]{index=3}

### Why ROC-AUC Matters

Because the outcome was imbalanced, accuracy alone does not provide a complete picture of model performance.

The final model's relatively high recall indicates that it was able to identify a substantial proportion of children in the target class, while its ROC-AUC provided a broader measure of discrimination.

---

## 🔍 Explainable AI

Building a predictive model is only part of the problem.

For a public health application, it is also important to understand:

> **What is driving the model's predictions?**

The project therefore used:

### Feature Importance

The Random Forest's Gini-based feature importance identified the strongest predictors.

| Rank | Predictor | Importance |
|---:|---|---:|
| 1 | Number of ANC Visits | 0.2909 |
| 2 | Month of First ANC Visit | 0.1931 |
| 3 | Mother's Education | 0.0808 |
| 4 | Household Wealth Index | 0.0627 |
| 5 | Place of Delivery: Home | 0.0623 |
| 6 | Media Exposure | 0.0400 |
| 7 | Mother's Age | 0.0340 |

The number of ANC visits and timing of the first ANC visit together contributed approximately **48.4% of the model's total feature importance**. :contentReference[oaicite:4]{index=4}

### SHAP Analysis

SHAP was used as a complementary interpretation method to examine how individual features influenced predictions.

The SHAP analysis reinforced the importance of:

- Number of ANC visits
- Timing of the first ANC visit
- Mother's education
- Household wealth
- Place of delivery :contentReference[oaicite:5]{index=5}

---

## 💡 Key Public Health Insight

One of the most important findings from the project is the prominence of **maternal healthcare utilisation**.

The two strongest predictors were:

### 1. Number of ANC Visits

### 2. Timing of the First ANC Visit

Together, these variables represented nearly half of the final model's feature importance.

This suggests that **antenatal care may provide an important point of contact for identifying and addressing barriers to childhood immunization**.

The finding supports potential approaches such as:

- Integrating immunization counselling into ANC services.
- Strengthening follow-up for mothers with limited ANC contact.
- Using maternal healthcare encounters as opportunities for immunization education and scheduling.
- Exploring predictive tools that could support targeted outreach.

However, these are **predictive associations, not evidence of causality**. :contentReference[oaicite:6]{index=6}

---

## 🌍 Why This Matters

The project sits at the intersection of **public health and artificial intelligence**.

Traditional analyses can identify relationships between variables, but machine learning provides an opportunity to explore more complex patterns and develop predictive tools.

This project demonstrates a workflow for moving from:

**Public Health Problem**

→

**National Survey Data**

→

**Machine Learning**

→

**Explainable Predictions**

→

**Potential Public Health Action**

The project is therefore not intended to replace public health professionals or existing immunization systems.

Instead, it explores how machine learning could become an additional analytical tool for **risk identification, programme planning, and targeted intervention**.

---

## 🛠️ Technologies Used

### Programming

- Python

### Data Analysis

- Pandas
- NumPy

### Visualisation

- Matplotlib
- Seaborn

### Machine Learning

- Scikit-learn
- XGBoost

### Explainable AI

- SHAP

### Development & Version Control

- Jupyter Notebook
- Git
- GitHub

---

## 📁 Repository Structure

- `notebooks/`
  - `Immunization_Project.ipynb`
- `reports/`
  - `Immunization_Research_Report.docx`
- `.gitignore`
- `README.md`
- `requirements.txt`

---

## 🚀 Getting Started

### Clone the Repository

`git clone https://github.com/chinenyemercy5228-ship-it/childhood-immunization-ml-nigeria.git`

### Enter the Project Directory

`cd childhood-immunization-ml-nigeria`

### Install Dependencies

`pip install -r requirements.txt`

### Open the Notebook

`jupyter notebook notebooks/Immunization_Project.ipynb`

> The raw NDHS dataset is not included in this repository. Users must obtain the dataset through the appropriate DHS data-access procedures.

---

## 📄 Research Report

The full research report is included in the repository:

`reports/Immunization_Research_Report.docx`

The report provides detailed documentation of the:

- Research background
- Literature review
- Methodology
- Data preparation
- Exploratory analysis
- Feature selection
- Model development
- Hyperparameter tuning
- Model evaluation
- Feature importance
- SHAP analysis
- Discussion
- Conclusions
- Recommendations
- Limitations
- Future research

---

## ⚠️ Limitations

This study has several limitations:

- The analysis uses cross-sectional survey data.
- Predictive associations should not be interpreted as causal relationships.
- Model performance is moderate.
- The model requires external and prospective validation before operational deployment.
- The dataset does not capture every factor that may influence immunization, including some facility-level and behavioural factors.
- The model should not be used independently to make decisions about individual children.

---

## 🔮 Future Work

Future work could include:

- External validation using another dataset.
- Prospective validation using routine health information systems.
- Integration of healthcare facility-level information.
- Incorporation of geospatial accessibility measures.
- Investigation of caregiver knowledge and attitudes.
- Testing additional ensemble and stacking approaches.
- Fairness assessment across socioeconomic and geographic groups.
- Development of an interpretable public health decision-support application.
- Evaluation in real-world immunization programme settings.

---

## 👩🏽‍💻 Author

### Elechi Chinenye Mercy

**Public Health Professional | AI & Machine Learning**

Interested in applying **data science, machine learning, and automation to public health challenges** and developing data-driven solutions that can support healthcare decision-making.

---

## 📌 Disclaimer

This repository represents an academic and research-oriented machine learning project.

The model is intended to demonstrate the application of machine learning and explainable AI to public health data.

It should **not** be used as a standalone clinical or public health decision-making system without appropriate validation, ethical review, and prospective evaluation.

---

## ⭐ Project Focus

**Public Health × Machine Learning × Explainable AI**

### Using data to better understand childhood immunization in Nigeria.