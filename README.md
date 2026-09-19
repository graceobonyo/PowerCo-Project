# PowerCo Customer Churn Analysis and Prediction

## Project Overview

Customer churn remains one of the most significant challenges facing utility providers in competitive energy markets. PowerCo, a major supplier of gas and electricity services to Small and Medium-sized Enterprises (SMEs), has experienced substantial customer attrition due to increasing competition, evolving pricing structures, and changing customer expectations.

This project leverages data analytics and machine learning techniques to identify the key drivers of customer churn and develop predictive models capable of identifying customers who are likely to leave. By predicting churn proactively, PowerCo can implement targeted retention strategies, improve customer loyalty, and reduce revenue loss.

---

# Business Problem

Customer acquisition costs are significantly higher than customer retention costs. Therefore, reducing churn is critical to maintaining profitability and market share.

PowerCo seeks to answer the following questions:

- What factors contribute to customer churn?
- How do pricing and consumption patterns affect retention?
- Can machine learning accurately predict customer churn?
- Which customers are most likely to leave?
- How can PowerCo proactively intervene to improve retention?

---

#  Project Objectives

The objectives of this project were to:

- Perform exploratory data analysis (EDA) to understand customer behavior.
- Identify factors influencing customer churn.
- Analyze customer consumption and pricing patterns.
- Engineer meaningful features that improve predictive performance.
- Develop and compare multiple machine learning models.
- Predict customer churn probabilities.
- Segment customers based on churn risk.
- Provide actionable business recommendations.

---

# Tools and Technologies

## Programming Language

- Python

## Development Environment

- Jupyter Notebook

## Data Manipulation

- Pandas
- NumPy

## Data Visualization

- Matplotlib
- Seaborn

## Machine Learning

- Scikit-Learn
- XGBoost

## Model Evaluation

- Accuracy Score
- Precision Score
- Recall Score
- F1 Score
- ROC-AUC Score
- Confusion Matrix

## Hyperparameter Optimization

- RandomizedSearchCV
- GridSearchCV

---

# Dataset Description

The project uses two datasets:

## 1. Client Dataset

Contains customer information including churn status, energy consumption, contract details, profitability metrics, and customer characteristics.

### Dataset Characteristics

- Records: 14,606
- Features: 26
- Target Variable: `churn`

### Target Classes

| Value | Meaning |
|---------|---------|
| 0 | Non-Churn Customer |
| 1 | Churn Customer |

### Key Variables

- `cons_12m`
- `cons_gas_12m`
- `cons_last_month`
- `forecast_cons_12m`
- `net_margin`
- `pow_max`
- `num_years_antig`
- Contract Dates

---

## 2. Price Dataset

Contains energy pricing information for customers.

### Dataset Characteristics

- Records: 193,002
- Features: 8

### Key Variables

- Off-Peak Prices
- Peak Prices
- Mid-Peak Prices
- Fixed Charges
- Pricing Dates

---

#  Data Cleaning

The following preprocessing steps were performed:

## Missing Values

Both datasets were checked for missing values.

### Result

 No missing values were identified.

---

## Duplicate Records

Both datasets were checked for duplicates.

### Result

 No duplicate records were identified.

---

## Date Conversion

Date variables were converted into datetime format:

```python
pd.to_datetime()
```

Converted columns:

- date_activ
- date_end
- date_modif_prod
- date_renewal
- price_date

---

## Outlier Detection

Outliers were identified using the Interquartile Range (IQR) method and visualized using boxplots.

### Findings

Outliers were observed in:

- Annual Consumption (`cons_12m`)
- Annual Gas Consumption (`cons_gas_12m`)
- Monthly Consumption (`cons_last_month`)
- Forecasted Consumption
- Net Margin
- Maximum Power

### Decision

Outliers were retained because they represent genuine customer behavior and contain valuable predictive information.

---

# Exploratory Data Analysis (EDA)

## Churn Distribution

The target variable is imbalanced.

| Class | Percentage |
|---------|----------|
| Retained Customers | ~90% |
| Churn Customers | ~10% |

### Insight

The minority churn class is underrepresented, requiring careful model evaluation beyond accuracy.

---

## Consumption Analysis

Key findings:

- Annual consumption is highly right-skewed.
- Most customers consume relatively low amounts of energy.
- A small group of customers exhibits extremely high energy consumption.
- Over half of customers report no gas consumption.

### Business Insight

Customers with higher energy consumption tend to be more loyal and less likely to churn.

---

## Pricing Analysis

Key findings:

- Off-peak prices remain relatively stable.
- Peak prices vary more significantly.
- Customers exposed to higher peak prices show a greater likelihood of churning.

### Business Insight

Pricing plays an important role in customer retention.

---

## Customer Tenure Analysis

Key findings:

- Non-churn customers generally have longer tenure.
- Churn customers tend to have shorter tenure.

### Business Insight

Long-term customers demonstrate higher loyalty.

---

## Contract Duration Analysis

Key findings:

- Non-churn customers generally maintain longer contracts.
- Customers with shorter contract durations exhibit higher churn tendencies.

### Business Insight

Contract duration contributes to customer retention.

---

# Feature Engineering

Several new variables were created to improve predictive performance.

## Average Monthly Consumption

```python
avg_monthly_cons = cons_12m / 12
```

Measures average customer consumption.

---

## Consumption Trend Ratio

```python
cons_trend_ratio =
cons_last_month / avg_monthly_cons
```

Measures changes in customer consumption patterns.

---

## Contract Duration

```python
contract_duration_days
```

Measures the lifespan of customer contracts.

---

## Customer Tenure

```python
customer_tenure
```

Measures the duration of a customer's relationship with PowerCo.

---

# Correlation Analysis

Correlation analysis was performed to identify multicollinearity.

## Highly Correlated Features Removed

```python
avg_monthly_cons
margin_net_pow_ele
num_years_antig
contract_duration_days
imp_cons
```

### Reason

Several variables exhibited strong multicollinearity, meaning they contained similar information. Removing one feature from each correlated pair reduced redundancy and improved model stability.

---

# Machine Learning Models

Three machine learning classifiers were evaluated.

## 1. Logistic Regression

### Performance

| Metric | Value |
|---------|---------|
| Accuracy | 90.29% |
| Recall | 0.00% |
| F1 Score | 0.00% |

### Interpretation

Although accuracy appeared high, the model classified every customer as non-churn and failed to identify any churners.

### Conclusion

 Not suitable for churn prediction.

---

## 2. XGBoost

### Performance

| Metric | Value |
|---------|---------|
| Accuracy | 95.03% |
| Recall | 49.00% |
| F1 Score | 66.00% |

### Interpretation

The model improved churn detection but failed to identify approximately half of all churners.

### Conclusion

Moderate performance.

---

## 3. Random Forest

### Performance

| Metric | Value |
|---------|---------|
| Accuracy | 99.99% |
| Recall | 99.85% |
| F1 Score | 99.93% |

### Confusion Matrix

| Actual Class | Predicted No Churn | Predicted Churn |
|--------------|-------------------|-----------------|
| No Churn | 31,629 | 0 |
| Churn | 5 | 3,396 |

### Interpretation

The model correctly identified nearly all churners and non-churners, making only five classification errors.

### Conclusion

Best-performing model.

---

# Model Comparison

| Model | Accuracy |
|---------|---------|
| Logistic Regression | 90.29% |
| XGBoost | 95.03% |
| Random Forest | 99.99% |

### Findings

- Logistic Regression failed to identify churners.
- XGBoost improved churn detection.
- Random Forest outperformed all models across evaluation metrics.

---

#  ROC Curve Analysis

| Model | AUC |
|---------|---------|
| Logistic Regression | 0.592 |
| XGBoost | 0.984 |
| Random Forest | 1.000 |

### Interpretation

Random Forest demonstrated near-perfect ability to distinguish between churners and non-churners.

---

# Hyperparameter Tuning

RandomizedSearchCV was used to optimize the Random Forest model.

## Best Parameters

```python
{
'n_estimators': 300,
'max_depth': None,
'min_samples_split': 2,
'min_samples_leaf': 1
}
```

## Tuned Model Performance

| Metric | Value |
|---------|---------|
| Accuracy | 99.99% |
| Recall | 99.85% |
| F1 Score | 99.93% |

The tuned model maintained exceptional predictive performance.

---

# Error Analysis

Error analysis focused on misclassified customers.

### Results

- False Positives = 0
- False Negatives = 5

### Findings

The five misclassified churners exhibited consumption patterns similar to correctly identified churners.

### Conclusion

The model demonstrated extremely strong predictive capability with minimal errors.

---

# Feature Importance Analysis

Top predictive features included:

1. `cons_12m`
2. `margin_gross_pow_ele`
3. `forecast_meter_rent_12m`
4. `net_margin`
5. `forecast_cons_12m`
6. `date_renewal`
7. `cons_last_month`
8. `pow_max`

### Business Insight

Consumption behavior, profitability indicators, and contract-related variables were the strongest drivers of churn prediction.

---

# Churn Risk Analysis

The Random Forest model generated churn probabilities for individual customers.

## Risk Categories

| Risk Level | Churn Probability |
|------------|------------------|
| High Risk | ≥ 80% |
| Medium Risk | 50% - 79% |
| Low Risk | < 50% |

---

## High-Risk Customers

The model identified:

**3,373 High-Risk Customers**

These customers represent the segment most likely to churn and should be prioritized for retention campaigns.

---

# Key Business Insights

- Higher energy prices increase churn likelihood.
- Pricing-related features are powerful churn predictors.
- Consumption patterns influence customer loyalty.
- Customer tenure improves retention.
- Contract duration impacts churn behavior.
- Profitability metrics provide valuable churn signals.

---

# Recommendations

### 1. Target High-Risk Customers

Use churn risk scores to proactively engage customers before churn occurs.

### 2. Review Pricing Strategies

Offer competitive pricing plans to customers sensitive to peak rates.

### 3. Build Loyalty Programs

Reward long-term customers through incentives and discounts.

### 4. Monitor Consumption Changes

Track unusual variations in customer consumption behavior.

### 5. Improve Forecast Accuracy

Enhance forecasting processes to improve customer confidence.

### 6. Increase Customer Engagement

Contact customers approaching contract renewal.

### 7. Continuous Monitoring

Deploy the churn model into production and monitor customer risk continuously.

---

# Future Improvements

Future enhancements may include:

- SHAP Explainability Analysis
- Handling class imbalance using SMOTE
- Real-time churn prediction pipelines
- CRM integration
- Web application deployment
- Model validation on new unseen customer data

---

# Conclusion

This project successfully developed a machine learning solution capable of identifying customers at risk of churn. Analysis revealed that pricing, consumption behavior, profitability, customer tenure, and contract characteristics significantly influence churn decisions.

Among the evaluated models, the tuned Random Forest classifier achieved the strongest performance, delivering **99.99% accuracy**, **99.85% recall**, and an **AUC of 1.00**. The model identified **3,373 high-risk customers**, providing PowerCo with actionable insights for targeted customer retention strategies.

By implementing the recommendations from this analysis, PowerCo can proactively reduce customer attrition, improve customer lifetime value, and strengthen its competitive position within the energy market.


# Project Structure

```text
PowerCo-Customer-Churn/
│
├── data/
│   ├── client_data.csv
│   ├── price_data.csv
│   └── client_price_data.csv
│
├── notebooks/
│   └── PowerCo_Churn_Analysis.ipynb
│
├── outputs/
│   ├── churn_risk_predictions.csv
│   ├── high_risk_customers.csv
│   └── model_results.csv
│
├── images/
│   ├── churn_distribution.png
│   ├── correlation_heatmap.png
│   ├── roc_curve.png
│   ├── feature_importance.png
│   └── risk_distribution.png
│
├── presentation/
│   └── PowerCo_Churn_Presentation.pptx
│
└── README.md

---


## Author

**Grace Obonyo**

PowerCo Customer Churn Analysis and Prediction

