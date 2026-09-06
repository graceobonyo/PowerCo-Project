# PowerCo
PowerCo is a major gas and electricity utility provider serving small and medium sized enterprises in a higly competitive energy market.The energy market has undergone dynamic transfromation with the introduction of new prices,shift to the renewable energy options and technological advanced experiences by the incoming energy providers offering flexibilty to the consumers .This has led to an increase in market competition where the Powerco has recorded a significant loss in customers to the competitors with more than 50% rate reported. We aim to investigate the drivers of the clients switching to the other service providers.

# 📊 Customer Churn Analysis

## Project Overview

Customer retention is a critical business challenge because acquiring new customers is often more expensive than retaining existing ones. This project analyzes customer behavior and subscription data to identify factors contributing to customer churn and provide actionable recommendations to improve retention.

The analysis combines data cleaning, exploratory data analysis (EDA), visualization, and business insights to support data-driven decision-making.

---

## Business Problem

The organization has experienced increasing customer attrition over recent months, resulting in reduced revenue and increased customer acquisition costs.

Management seeks answers to the following questions:

- Which customers are most likely to churn?
- What factors drive customer attrition?
- Which customer segments are at the highest risk?
- What actions can be taken to improve retention?

---

## Project Objectives

The primary objectives of this analysis are:

✅ Understand customer demographics and behavior

✅ Identify key churn drivers

✅ Discover patterns and trends associated with customer attrition

✅ Generate actionable business recommendations

✅ Support retention strategy development

---

## Dataset Information

### Source

Customer subscription and service usage dataset.

### Dataset Summary

| Metric | Value |
|----------|----------|
| Records | 7,043 |
| Features | 21 |
| Missing Values | 0 |
| Target Variable | Churn |

### Key Variables

- CustomerID
- Gender
- SeniorCitizen
- Tenure
- Contract Type
- Monthly Charges
- Total Charges
- Internet Service
- Payment Method
- Churn

---

## Tools & Technologies

### Data Analysis

- Python
- Pandas
- NumPy

### Data Visualization

- Matplotlib
- Seaborn

### Business Intelligence

- Power BI / Tableau

### Database

- SQL

### Environment

- Jupyter Notebook

---

## Data Cleaning

The following preprocessing steps were performed:

### Missing Values

- Verified missing records
- Removed null observations where necessary

### Data Type Corrections

- Converted TotalCharges to numeric format
- Standardized categorical variables

### Duplicate Records

- Checked and removed duplicates

### Feature Engineering

Created additional analytical variables including:

- Customer tenure groups
- Spending categories
- Risk segments

---

# Exploratory Data Analysis (EDA)

## Customer Distribution

### Observation

The customer base consists primarily of medium-tenure subscribers, with relatively fewer long-term customers.

### Business Implication

Retention efforts should focus on newly acquired customers who are more vulnerable to churn.

---

## Churn Distribution

### Observation

Approximately 26% of customers have churned.

### Business Implication

The churn rate represents a significant revenue risk and warrants targeted intervention.

---

## Contract Type Analysis

### Observation

Month-to-month customers exhibit substantially higher churn rates than customers on annual or multi-year contracts.

### Business Implication

Contract commitment appears to improve customer retention.

---

## Monthly Charges Analysis

### Observation

Customers with higher monthly charges show a greater tendency to churn.

### Business Implication

Price sensitivity may influence customer decisions to leave.

---

## Customer Tenure Analysis

### Observation

New customers experience the highest churn rate.

### Business Implication

The onboarding and early customer experience phases are critical.

---

# Key Insights

## Insight 1: Contract Type Is the Strongest Churn Driver

Customers on month-to-month contracts are significantly more likely to leave than those on longer-term contracts.

### Impact

Contract structure directly influences customer retention.

---

## Insight 2: Customer Tenure Reduces Churn Risk

The longer customers remain with the company, the less likely they are to churn.

### Impact

Customer loyalty grows over time and should be nurtured.

---

## Insight 3: High Monthly Charges Increase Churn Probability

Customers paying premium rates exhibit higher churn tendencies.

### Impact

Price optimization strategies may improve retention.

---

## Insight 4: Electronic Check Users Have Higher Churn Rates

Payment method appears strongly associated with customer attrition.

### Impact

Customer experience associated with billing may influence retention.

---

# Business Recommendations

## 1. Promote Long-Term Contracts

### Actions

- Offer annual subscription discounts
- Introduce loyalty incentives
- Provide contract renewal benefits

### Expected Outcome

Reduction in churn among month-to-month subscribers.

---

## 2. Strengthen Customer Onboarding

### Actions

- Improve onboarding communications
- Create welcome campaigns
- Monitor customer engagement during the first 90 days

### Expected Outcome

Improved retention among new customers.

---

## 3. Review Pricing Strategy

### Actions

- Evaluate premium package pricing
- Provide flexible service plans
- Offer targeted discounts

### Expected Outcome

Reduced churn among high-paying subscribers.

---

## 4. Improve Customer Experience

### Actions

- Monitor customer complaints
- Enhance support responsiveness
- Implement proactive customer outreach

### Expected

