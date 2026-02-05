# 💳 Credit Risk Analytics  
## Probability of Default (PD) Modeling & Risk-Based Loan Decisioning

An **end-to-end credit risk analytics project** focused on estimating the **Probability of Default (PD)** for loan applicants and translating model outputs into **governed, risk-based lending decisions**.

Built using **logistic regression**, this project reflects how PD models are designed, evaluated, and operationalized in **regulated banking environments** such as **Barclays, Wells Fargo, Bank of America, Citi, Mastercard, and Visa**.

---

## 🏦 Business Background

In retail and consumer lending, banks must continuously balance:

- 📈 Credit growth  
- ⚠️ Default risk and expected losses  
- 🏛️ Regulatory and capital constraints  

To achieve this, **Probability of Default (PD) models** are used to:
- Rank borrowers by credit risk  
- Define approval, review, and rejection strategies  
- Monitor portfolio-level risk exposure  

---

## 🎯 Problem Statement

Design a credit risk solution that:

- Estimates the **Probability of Default (PD)** for each borrower  
- Evaluates model quality using **ROC–AUC (banking standard)**  
- Optimizes probability thresholds based on **risk appetite**, not accuracy  
- Converts PD scores into **Low / Medium / High** risk bands for decisioning  

---

## 📦 Dataset Overview

- **Source:** Historical anonymized consumer loan data (2007–2018)  
- **Scale:** 900,000+ loan records  

### 🏷️ Default Definition (Industry Standard)

**Bad Loans (Default = 1):**
- Charged Off  
- Default  
- Late (31–120 days)  

**Good Loans (Default = 0):**
- Fully Paid  

Only **completed loans** were included to avoid forward-looking bias.

📌 **Observed Default Rate:** ~21%  
> Indicates a relatively high-risk lending segment, justifying PD-based decisioning.

---

## ⚙️ Data Preparation & Feature Engineering

### Key Steps
- Filtered completed loans only  
- Removed missing and inconsistent records  
- Converted loan term to numeric format  
- Encoded credit grades as ordinal risk indicators  
- Selected financially interpretable variables  

### Final Modeling Features
- Loan Amount  
- Interest Rate  
- Loan Term  
- Monthly Installment  
- Credit Grade (Ordinal)  
- Annual Income  

These features align with variables commonly used in real-world PD models.

---

## 🧠 Modeling Approach

- **Model Used:** Logistic Regression  
- **Why Logistic Regression?**
  - Interpretable and regulator-friendly  
  - Stable baseline used widely in banking  
  - Suitable for audit and model risk review  

- **Train/Test Split:** 70% / 30%  
- **Output:** Continuous PD score between 0 and 1  

---

## 📊 Model Evaluation (Banking Standard)

### ROC–AUC Performance
- **Out-of-sample ROC–AUC:** **0.705**

**Interpretation:**
> The model correctly ranks a randomly selected defaulter higher risk than a non-defaulter ~70.5% of the time.

This level of performance is consistent with **production-grade baseline credit models**.

---

## 🎯 Threshold Optimization & Risk Appetite

Banks do not rely on a fixed 0.5 probability cutoff.

| Probability Cutoff | Default Recall | Business Interpretation |
|-------------------|--------------|-------------------------|
| 0.50 | ~9% | Conservative, misses many risky borrowers |
| 0.30 | ~37% | Improved default capture with controlled trade-offs |

📌 **Key Insight:**  
Probability thresholds were adjusted to align model decisions with **portfolio risk tolerance**, reflecting real banking practice.

---

## 🚦 Risk Banding & Credit Decisioning

PD scores were translated into **actionable risk segments**:

| PD Range | Risk Band | Typical Action |
|--------|----------|----------------|
| < 30% | Low Risk | Approve |
| 30–60% | Medium Risk | Manual Review / Pricing Adjustment |
| > 60% | High Risk | Reject |

This step bridges **analytics and business execution**, enabling governed lending decisions.

---

## 📈 Business Insights

- Clear separation between good and bad borrowers  
- Meaningful improvement in default detection through threshold tuning  
- High interpretability and audit readiness  
- Reusable PD-to-decision framework for retail lending portfolios  

---

## 📁 Repository Structure

Credit-Risk-PD-Decisioning/
├── notebooks/
│ └── 01_PD_Model_Logistic_Regression.ipynb
├── data/
│ └── accepted_2007_to_2018Q4.csv
├── reports/
│ └── roc_curve.png
├── requirements.txt
└── README.md


---

## 🧰 Tools & Libraries

- Python  
- pandas, numpy  
- scikit-learn  
- matplotlib  

---

## 🔮 Future Enhancements

- Benchmark against XGBoost for performance comparison  
- Add SHAP-based explainability for model governance  
- Build Power BI / Streamlit dashboard for portfolio monitoring  
- Deploy PD scoring pipeline via API  

---

## 👤 Author

**Aakarsh Kumar Sinha**  
Data Analyst | Decision Analytics  

GitHub: https://github.com/AKS0908-pixel  

---

## 🏁 Final Note

This project demonstrates how **credit risk models are operationalized in real financial institutions**, prioritizing explainability, governance, and risk-aware decisioning over black-box performance.
