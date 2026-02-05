Credit Risk Modeling: Probability of Default (PD) & Risk-Based Decisioning

Barclays-Style Credit Risk Analytics Project

This project demonstrates an end-to-end Probability of Default (PD) modeling framework designed for regulated banking environments, with a focus on interpretability, risk governance, and portfolio-level decisioning.

The solution mirrors how credit risk and decision analytics teams at banks such as Barclays operationalize PD models — moving beyond pure model performance to risk appetite alignment and controlled lending decisions.

🏦 Business Context (Barclays Lens)

Retail and consumer lending portfolios must balance:

Credit growth

Default risk and loss prevention

Regulatory and capital constraints

Banks rely on Probability of Default (PD) models to:

Rank borrowers by credit risk

Define approval, review, and rejection strategies

Monitor portfolio risk exposure

Objective:
Design a PD modeling framework that supports governed credit decisions while maintaining transparency and regulatory suitability.

🎯 Problem Statement

Build a supervised credit risk model that:

Estimates the Probability of Default (PD) for completed loans

Evaluates risk separation using ROC–AUC (banking standard)

Optimizes probability thresholds based on risk appetite, not accuracy

Converts PD scores into Low / Medium / High risk bands for lending decisions

📦 Dataset Overview

Source: Historical anonymized consumer loan data (2007–2018)

Volume: 900,000+ loan records

Target Definition (Banking Standard)

Loans were classified as:

Default (1 – “Bad Loans”)

Charged Off

Default

Late (31–120 days)

Non-Default (0 – “Good Loans”)

Fully Paid

Only completed loans were included to avoid forward-looking bias.

📌 Observed Default Rate: ~21%

Indicates a relatively high-risk consumer lending segment, justifying PD-based decisioning.

⚙️ Data Preparation & Feature Engineering
Key Steps

Filtered completed loans only

Removed missing and inconsistent records

Converted loan term to numeric format

Encoded credit grades as ordinal risk indicators

Selected financially interpretable features

Final Modeling Features

Loan Amount

Interest Rate

Loan Term

Monthly Installment

Credit Grade (Ordinal)

Annual Income

These variables reflect common inputs used in real-world PD models.

🧠 Modeling Approach

Model Used: Logistic Regression

Rationale:

Interpretable and regulator-friendly

Stable baseline widely used in credit risk

Suitable for audit and model risk review

Train/Test Split: 70% / 30%

Output: Continuous PD score (0–1)

📊 Model Evaluation (Banking Standard)
ROC–AUC Performance

Out-of-sample ROC–AUC: 0.705

Interpretation:

The model can correctly rank a randomly selected defaulter above a non-defaulter ~70.5% of the time.

This performance aligns with production-grade baseline credit models used in regulated banking environments.

🎯 Threshold Optimization & Risk Appetite

Banks do not rely on a fixed 0.5 cutoff.

Threshold Comparison
Probability Cutoff	Default Recall	Interpretation
0.50	~9%	Conservative, misses many defaulters
0.30	~37%	Improved risk capture with controlled trade-offs

📌 Key Insight:
Thresholds were optimized to improve default detection in line with portfolio risk tolerance, demonstrating real-world credit decisioning.

🚦 Risk Banding & Decision Governance

PD scores were translated into discrete risk segments:

PD Range	Risk Band	Lending Action
< 30%	Low Risk	Approve
30–60%	Medium Risk	Manual Review / Pricing Adjustment
> 60%	High Risk	Reject

This enables governed, explainable lending decisions, consistent with banking risk frameworks.

📈 Business Impact & Insights

Demonstrated clear risk separation across borrower segments

Improved identification of high-risk borrowers through threshold tuning

Maintained interpretability and audit readiness

Created a reusable PD-to-decision pipeline suitable for retail lending

📁 Repository Structure
Credit-Risk-PD-Decisioning/
├── notebooks/
│   └── 01_PD_Model_Logistic_Regression.ipynb
├── data/
│   └── accepted_2007_to_2018Q4.csv
├── reports/
│   └── roc_curve.png
├── requirements.txt
└── README.md

📚 Tools & Libraries

Python

pandas, numpy

scikit-learn

matplotlib

🔮 Future Enhancements

Benchmark against XGBoost for performance comparison

Add SHAP-based explainability for model risk governance

Build Power BI dashboard for portfolio monitoring

Deploy PD scoring pipeline via API

👤 Author

Aakarsh Kumar Sinha
Master’s in Operational Research
Credit Risk & Decision Analytics
GitHub: https://github.com/AKS0908-pixel

🏁 Final Note

This project reflects how PD models are operationalized in real banking environments, prioritizing explainability, governance, and risk appetite alignment over black-box performance.
