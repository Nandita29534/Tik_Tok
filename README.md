# 🎵 TikTok Data Analysis & Machine Learning Project  
### From Hypothesis Testing → Logistic Regression → Ethical ML Classification

This project follows the complete TikTok Lab series from the **Google Advanced Data Analytics Certificate**, covering statistical testing, regression analysis, and machine learning model development.  
The goal is to understand user behavior, predict verification status, and ethically automate claim–vs–opinion classification for content moderation at scale.

---

## 📁 Project Overview

This project is divided into three major phases:

1. **Exploratory Data Analysis & Hypothesis Testing (Course 4)**
2. **Logistic Regression on User Verification (Course 5)**
3. **Machine Learning Classification for Claims vs. Opinions (Course 6)**

Each phase builds on the last to develop deeper insights and progressively more sophisticated predictive models.

---

# 1️⃣ Phase 1: Exploratory Data Analysis & Hypothesis Testing  
### *TikTok Project Lab – EDA (Course 4: Power of Statistics)*

### 🎯 Objective  
Determine whether verified accounts receive different average viewership than unverified accounts.

### 🧪 Hypotheses  
- **Null Hypothesis (H₀):** There is *no* difference in average viewership between verified and unverified accounts.  
- **Alternate Hypothesis (Hₐ):** There *is* a difference in average viewership between verified and unverified accounts.

### 📈 Result  
- The **p-value < α (0.05)**.

### ✅ Conclusion  
**Rejected the null hypothesis.**  
Verified accounts and unverified accounts **do have significantly different average viewership**.

---

# 2️⃣ Phase 2: Logistic Regression — Predicting Verified Users  
### *TikTok Project Lab (Course 5: Regression Analysis)*

### 🎯 Objective  
Understand which video characteristics are associated with users being *verified* on TikTok.

TikTok wants to predict *verified status* to help understand how content and creator behavior correlate with verification. This supports downstream modeling about predicting whether videos are **claims vs. opinions**.

---

## 📊 Dataset Characteristics

- **93.7%** videos were from **unverified** accounts  
- **6.3%** were from **verified** accounts  

➡️ **Outcome variable is imbalanced**, requiring careful interpretation.

---

## 🧠 Key Findings from Logistic Regression

### 📌 Correlation & Multicollinearity  
- Some features were strongly correlated  
- **`video_like_count` was dropped** to reduce multicollinearity

### 📌 Interpretability  
- **Each additional second of video length increases the log-odds of verification by 0.009**  
- Other features had relatively small coefficient values

---

## 📉 Model Performance

| Metric | Value |
|-------|-------|
| **Precision (not verified)** | **61%** |
| **Recall (not verified)** | **84%** |
| **Accuracy** | **65%** |

### 🔍 Interpretation  
- **Recall was strong**, meaning the model is effective at identifying unverified users  
- **Precision is moderate**, suggesting some false positives  
- Overall accuracy is *acceptable but not ideal*

### ⭐ Insight  
Longer videos are slightly more associated with verified creators, while most other variables show weak relationships.

---

# 3️⃣ Phase 3: Ethical Machine Learning — Claim vs. Opinion Classification  
### *TikTok Project Lab (Course 6: ML Basics)*

### 🎯 Business Need  
TikTok receives millions of daily reports on videos. Human moderators cannot review all content.

TikTok wants a model that can:

- **Classify videos as “claim” or “opinion”**
- Automatically prioritize *claims* for further human review  
- Improve efficiency and response time in content moderation workflows  

---

## ⚠️ Ethical Considerations

When the model is wrong, two mistakes can happen:

1. **False Positive:** Opinion classified as claim  
2. **False Negative:** Claim classified as opinion

### Why Minimizing False Negatives is Critical  
- A false negative means a *claim* goes unreviewed  
- Claims are more likely to violate TikTok’s Terms of Service  
- Missing these is riskier than sending an opinion for human review  

➡️ **Primary metric = RECALL (for claim class)**

---

## 🤖 Model Comparison Result

Both models were tested:

- **Random Forest**
- **XGBoost**

### 📊 Performance Summary

| Metric (Claim Class) | Random Forest | XGBoost |
|----------------------|---------------|---------|
| **Recall** | **1.00** | **1.00** |
| **Precision** | 0.97 | **0.99** |
| **Opinion Class Recall** | 0.97 | **0.99** |

### 🏆 Best Model: **XGBoost**

- Perfect **recall** → meets primary business requirement  
- Higher **precision** → fewer false positives  
- Better balance across all metrics  

---

# 📚 Summary of Key Insights

### ✅ Phase 1  
Verified users receive significantly different viewership — statistically proven.

### ✅ Phase 2  
Logistic regression shows moderate predictive power.  
Longer videos slightly increase odds of account verification.

### ✅ Phase 3  
XGBoost is the best model for claims vs. opinions under ethical constraints.  
Perfect recall ensures no harmful content bypasses moderation.

---



