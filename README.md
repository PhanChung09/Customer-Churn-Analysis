

# TELCO CUSTOMER CHURN DATA ANALYSIS
### THIS PROJECT PREDICT CUSTOMER CHURN USING MACHINE LEARNING

## 1. Business Problem

In the telco industry, the cost of acquiring new customers by investing considerable resources is confirmed to be significantly higher than the cost of retaining existing customers (Shuli Wu, 2021). Consequently, proactive churn management is critical for preserving monthly recurring revenue and maximizing customer life time value. To address this challenge, we propose an end- to- end Machine Learning pipeline that delivery two core capabilities:

•	Generate a reliable score for each active customer, estimating their likelihood of canceling services in next period.

•	Translates subscriber churn probabilities into an optimized, actional contact list normalized per 1,000 active customers. This policy prioritizes outreach to maximize net retained revenue while also adhering to the retention team’s operation and, budget-constrained.

## 2. Data leakage and Enforcement

**Operational Definition:**
A data leakage occurs when any feature incorporate information that would not be available at the time of prediction is made, says customer are scored at the end of a billing period to plan retention outreach for the next 30 days. This can lead to overfitting, inflated performance metrics, and ultimately, a model that fails to generalize to unseen data. Consequently, it is crucial to implement a robust data leakage policy.

In this project, we idenfity three primary sources of leakage and implement stric enforcement measure to mitigate their impact: 

**Leakage Prevention Protocol:**

1. **Target & Temporal Leakage:** 
Target leakage: customer's churn may be affacted by Post-Churn_Support_Calls as it is accidentally included in the training data. To prevent this,  we use feature engineering (drop post_billing outcome and future interaction logs)and use StratifiedShuffleSplit for X, y 

2. **Preprocessing Leakage:** 
This leakage occurs when preprocessing steps are applied to the entire dataset before splitting it into training and testing sets.To prevent this, we ensure that all preprocessing steps are applied only within the cross-validation foldsAll feature scaling (`StandardScaler`) and encoding (`OneHotEncoder`) are strictly fit inside cross-validation training folds via scikit-learn `Pipeline` objects.

3. **Holdout Isolation:** 
Holdout datasets remain untouched until the final model pipeline is frozen. This strictly enforces that the holdout set provides a true measure of model selection and generalization ability.


## 3. Technique use

- Baseline Logistic Mode


- Random Forest 
- Gradient Boosting

### 4. Model Evaluation

- Train train data using 5 fold cross validation , measure the model performance on out of fold by evaluation AUC score and Brier score  using calibration validation 
- Retrain the model again by removing groups of feature and measure its performance on AUC , Brier score 
- An ablation table that shows how AUC and Brier2 change when  dropping each feature 
group defined.


### 5. Note to Executive Manager - Turning Score into Action

### 6. Notebook [Churn Analysis](https://github.com/PhanChung09/Customer-Churn-Analysis/blob/main/Customer%20Churn_Phan_Correction.ipynb)
