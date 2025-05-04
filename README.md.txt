# 📦 Device Insurance Pricing Portfolio Project – UK Market

This project simulates the end-to-end pricing workflow used in the insurance industry — specifically focused on **device protection plans** offered in the UK market. Inspired by the business model of companies like **SquareTrade (Allstate)**, it showcases how insurance firms price risk differently from retail or manufacturing using **Generalized Linear Models (GLMs)**.

---

## 🎯 Project Objective

- Apply GLM-based modeling to **estimate claim risk** (frequency & cost)
- Build a **technical premium table** based on modeled risk
- Simulate **final premiums** with business adjustments (loadings, discounts)
- Evaluate **profitability** using margin and loss ratio metrics
- Visualize performance breakdowns by device type, brand, region, and vendor

---

## 🗂️ Folder Structure

├── data/
│ ├── raw/ # Original dataset
│ └── processed/ # Cleaned data with predictions and premiums
├── notebooks/
│ ├── 01_data_cleaning_eda.ipynb
│ ├── 02_glm_frequency_model.ipynb
│ ├── 03_glm_severity_model.ipynb
│ ├── 04_technical_pricing_table.ipynb
│ ├── 05_final_premium_simulation.ipynb
│ └── 06_profitability_analysis.ipynb
├── reports/
│ └── *.png (plots and charts)
└── README.md


---

## 📊 Dataset Overview

- **Size**: 5,000 policies (synthetically generated for realism)
- **Features**:
  - `Device_Type`: Phone, Laptop, Tablet, TV, etc.
  - `Brand`: Apple, Samsung, Sony, Dell, etc.
  - `Vendor`: Amazon, Currys, John Lewis, etc.
  - `Region`, `Age_Band`, `Sales_Channel`
  - `Claim_Made`: Whether a claim occurred
  - `Claim_Cost`: If claim occurred, its amount
  - `Plan_Price`: Price paid by the customer

---

## 📈 Modeling Approach

### 1. **Claim Frequency (Poisson GLM)**
- Predicts probability of a claim (`Claim_Made`)
- Key drivers: Age band, device type, vendor, brand
- Insight: Young users and portable devices (phones, laptops) have higher claim likelihood

### 2. **Claim Severity (Gamma GLM)**
- Predicts claim cost for claimants (`Claim_Cost`)
- Insight: Brands like Apple and Sony had higher average claim amounts

---

## 💡 Pricing Methodology

### 🧮 Technical Premium
\[
\text{Predicted Frequency} \times \text{Predicted Severity}
\]

- Represents **pure risk premium**
- Used to create the baseline price per policy

### 🏷️ Final Premium Simulation
- +25% loading for expenses/profit
- +10% for high-risk segment (age 18–25)
- –10% discount for tablets (low severity, low penetration)

---

## 💰 Key Business Metrics

| Metric                     | Value               |
|----------------------------|---------------------|
| Final Loss Ratio           | **0.79**            |
| Average Portfolio Margin % | **–7.12%**          |
| Underpriced Policies       | **47.96%** of total |
| Most Profitable Segment    | Tablets & TVs       |
| Highest Risk Segment       | Phones for ages 18–25 |

---

## 📊 Visualizations

All saved in `/reports/` folder:
- 📈 Actual vs Predicted Claim Severity
- 💡 Relativity Chart (GLM Coefficients)
- 🔁 Plan Price vs Final Premium (Scatter)
- 📉 Loss Ratio and Margin % by:
  - Region
  - Vendor
  - Device Type
- 📦 Premium Distribution (Histogram)

---

## 🧠 Takeaways

- Nearly **48% of policies were underpriced**, highlighting the importance of rigorous risk modeling before final pricing
- Portfolio margin was **–7.12%**, indicating pricing adjustments or vendor negotiations may be needed
- Insurance pricing **uses GLMs** to project risk-adjusted premiums, unlike retail or pharma which focus on margin and demand curves
- The project mirrors the workflow of pricing teams at insurers like **SquareTrade, Aviva, Bupa**

---

## 🧪 Tools Used

- Python, Pandas, Seaborn, Matplotlib
- GLMs via `statsmodels`
- Structured output management (raw vs processed data)
- Saved visualizations for report generation

---

## 📌 Author Note

This project was originally created as a personal learning exercise and is now published to invite feedback from the pricing and insurance community.  
If you're a pricing analyst, manager, or actuary — I'd love to hear your views and improvements!

---