<img width="1194" height="514" alt="image" src="https://github.com/user-attachments/assets/730576ce-d915-4438-829b-6d373c9ce58a" />

**Find presentation file attached.**

# Identifying Key Factors Influencing Income Levels for U.S. Policy Interventions

## Table of Contents
* [Project Overview](#project-overview)
* [Problem Statement](#problem-statement)
* [Dataset](#dataset)
* [Machine Learning Process Overview](#machine-learning-process-overview)
* [Modeling (Classification)](#modeling-classification)
* [Clustering](#clustering)
* [Recommendations](#recommendations)
* [Technologies Used](#technologies-used)

## Project Overview
This project leverages machine learning techniques to identify the key factors influencing income levels in the United States. The primary goal is to provide data-driven insights to policymakers, enabling them to design more effective programs aimed at addressing income disparities. Through classification and cluster analysis, the project segments the population to recommend targeted policy interventions.

## Problem Statement
The core problem addressed is to analyze the key factors that determine whether an individual in the United States earns more than $50,000 per year. By understanding these influential factors, policymakers can develop more effective support programs for specific demographic and socio-economic groups.

## Dataset
The project utilizes the **Income Evaluation dataset**, derived from the 1994 U.S. Census.
- **Records**: 32,561
- **Features**: 15
- **Target Variable**: `income` (binary: `<=50K` or `>50K`)

**Key Attributes:**
- `age`
- `Sex`
- `marital-status`
- `Race`
- `native-country`
- `education` (Highest level of education)
- `education-num` (Number of years of education)
- `workclass` (Type of employer)
- `occupation` (Job type)
- `hours-per-week`
- `fnlwgt` (weight)
- `capital-gain` (Profit from capital investments)
- `capital-loss` (Loss from capital investments)

## Machine Learning Process Overview
The project follows a structured machine learning workflow:
- **Exploratory Data Analysis (EDA)**: Explored variable distributions and relationships with income level to uncover initial patterns and detect data quality issues.
- **Feature Engineering**: Encoded categorical variables, scaled numerical ones, and removed redundant or highly correlated features.
- **Modeling (Classification)**: Built and compared various classification models to predict income class and evaluate feature importance.
- **Clustering**: Applied K-Means on selected features and SHAP values to segment the population into policy-relevant groups.
- **Interpretation of Results and Recommendations**: Proposed targeted educational policies based on cluster needs to effectively reduce income disparities.

## Modeling (Classification)
The project implemented and compared three classification models, with **XGBoost** demonstrating overall better performance due to higher accuracy and F1-score.

**Classification Models Implemented:**
- **Logistic Regression**: Used as a baseline model for its simplicity and interpretability in binary classification tasks.
- **Random Forest**: Selected for its robustness and ability to handle feature interactions; optimized through hyperparameter tuning using grid search.
- **XGBoost**: Chosen for its high predictive power and efficiency on structured data; underwent hyperparameter tuning via random search.

**Comparison of Results:**

| Model             | Accuracy | F1-Score | Precision | Recall | AUC-ROC |
|-------------------|----------|----------|-----------|--------|---------|
| Logistic Reg.     | 0.859    | 0.675    | 0.750     | 0.613  | 0.914   |
| Random Forest     | 0.869    | 0.695    | 0.779     | 0.628  | 0.921   |
| XGBoost           | 0.876    | 0.710    | 0.798     | 0.640  | 0.928   |

## Clustering
K-Means clustering was applied to segment the population, revealing clear education-based groups to guide targeted policy action.
- **Methodology**: Clustering was based on educational level, occupation, and key demographic attributes (native country, sex, and race).
- **Clusters**: K-Means clustering with 3 optimal clusters (determined by the Elbow method), achieving a silhouette score of 0.65.

**Identified Clusters:**
- **"Yellow" Cluster (2)**: Represents the lowest-educated group, primarily in manual and unskilled labor (11.7% of the sample). This is identified as the **1st priority target group**, requiring urgent basic education and vocational support.
- **"Purple" Cluster (0)**: Represents the mid-educated workforce in manual and service jobs (60.3% of the sample). This is the **2nd priority target group**, targeted for second-wave upskilling and community college access.
- **"Green" Cluster (1)**: Represents highly educated professionals in specialized roles. No immediate policy intervention is needed for this group.

## Recommendations
The U.S. Government should address income gaps through a **two-wave educational policy strategy**:

### 1st Wave (Priority Program) - "Yellow" Cluster (11.7% of sample)
- **Focus**: Basic education completion (e.g., GED, adult literacy), vocational training.
- **Responsible Organizations**: Department of Education, Local School Districts, Community Centers.
- **Avg. time for Implementation**: 2-3 years.
- **Monitoring Method**: Track high school completion rates, GED certification rates, vocational training enrollment.
- **Expected Results**: Higher literacy and education attainment, increased entry into skilled labor, income uplift.

### 2nd Wave (Target Program) - "Purple" Cluster (60.3% of sample)
- **Focus**: Upskilling through community college access, vocational-to-degree bridge programs.
- **Responsible Organizations**: Department of Labor, Community Colleges, Workforce Development Boards.
- **Avg. time for Implementation**: 3-4 years.
- **Monitoring Method**: Monitor enrollment in bridge programs, community college graduation rates, and upskilling certifications.
- **Expected Results**: Improved access to skilled job markets, increased education level, and income mobility.

## Technologies Used
- Python (for data processing, ML modeling, and analysis)
- Scikit-learn (for classification and clustering algorithms)
- XGBoost (for gradient boosting classification)
- Pandas (for data manipulation)
- Matplotlib / Seaborn (for data visualization, inferred from plots)
- SHAP (for model interpretability, mentioned in clustering section)
