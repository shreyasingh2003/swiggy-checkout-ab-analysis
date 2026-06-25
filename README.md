# 🛵 Swiggy Checkout A/B Test Analysis

**MBA Business Analytics Project**

An end-to-end A/B testing pipeline built on real Swiggy restaurant data (1,40,657 records across 600+ Indian cities, 2024), testing whether displaying **Estimated Delivery Time (ETA) prominently on the checkout page** improves order conversion rate.

---

## 📌 Research Question

> Does displaying ETA prominently on the Swiggy checkout page improve order conversion rate?

| Group | Experience |
|-------|-----------|
| **A — Control** | Standard checkout layout |
| **B — Variant** | ETA shown prominently before payment |

- **H₀:** ETA display has no effect on conversion rate
- **H₁:** ETA display increases conversion rate
- **Significance level:** α = 0.05

---

## 📊 Key Results

| Metric | Value |
|--------|-------|
| Control conversion rate | ~38% |
| Variant conversion rate | ~44% |
| Uplift | **~+16%** |
| Chi-Square p-value | **< 0.001** ✅ |
| Z-Test p-value | **< 0.001** ✅ |
| Model ROC-AUC | ~0.73 |
| Estimated annual revenue opportunity | **~Rs. 95 Crore** |
| Payback period | < 7 days |
| ROI on dev investment | > 2000% |

---

## 📈 Visualizations

### 1. Exploratory Data Analysis — Rating & Price Distribution
![EDA Rating & Price](images/swiggy_eda.png)

### 2. EDA — Top Cities & Cuisines
![EDA Cities & Cuisines](images/swiggy_eda_cities.png)

### 3. A/B Test Results Dashboard — Conversion Overview
![AB Dashboard Part 1](images/swiggy_ab_dashboard_1.png)

### 4. A/B Test Results Dashboard — Segment Analysis
![AB Dashboard Part 2](images/swiggy_ab_dashboard_2.png)

### 5. ML Model — Feature Importance & ROC Curve
![ML Results](images/swiggy_ml_result.png)

---

## 🗂️ Project Structure

```
swiggy-ab-test/
│
├── Swiggy_AB_Test.ipynb    # Main analysis notebook
├── images/                  # Output graphs & visualizations
│   ├── swiggy_eda.png
│   ├── swiggy_eda_cities.png
│   ├── swiggy_ab_dashboard_1.png
│   ├── swiggy_ab_dashboard_2.png
│   └── swiggy_ml_result.png
├── requirements.txt         # Python dependencies
└── README.md
```

> **Note:** The dataset (`swiggy_file.csv`) is not included due to size. Upload it to your Colab session before running. The CSV contains restaurant-level data scraped from Swiggy, February 2024.

---

## 🔬 Methodology

### 1. Data Cleaning
- Extracted numeric ratings, prices, and offer counts from raw string columns
- Dropped rows with missing rating or price
- Derived features: `Has_Offer`, `Is_Veg`, `Primary_Cuisine`

### 2. A/B Test Simulation
- 10,000 user sessions simulated with parameters drawn directly from the real dataset
- Conversion probability modelled as a function of rating, offers, user history, device, time slot, distance, and A/B group assignment

### 3. Power Analysis
- Confirmed sample size is sufficient to detect a 5 pp MDE at 80% power (α = 0.05)

### 4. Statistical Tests
- **Chi-Square Test** on the 2×2 contingency table
- **Two-proportion Z-Test** with 95% confidence interval on uplift

### 5. Logistic Regression
- Trained on 13 features; `is_variant` included as a feature
- Evaluated via classification report and ROC-AUC

### 6. Segment Analysis
- Uplift broken down by: new vs. returning users, device, offer, weekend, rating band, and distance

### 7. Business Impact
- Revenue projections grounded in dataset median order value and public Swiggy estimates

---

## 🚀 Quickstart

```bash
# Clone the repo
git clone https://github.com/<your-username>/swiggy-ab-test.git
cd swiggy-ab-test

# Install dependencies
pip install -r requirements.txt

# Open the notebook
jupyter notebook Swiggy_AB_Test.ipynb
```

Upload `swiggy_file.csv` to your environment (or Colab session) before running Cell 2.

---

## 📦 Requirements

See `requirements.txt`. Core libraries:

- `pandas`, `numpy`
- `matplotlib`, `seaborn`
- `scipy`
- `scikit-learn`

---

## 💡 Key Findings

- Uplift is **statistically significant** across both Chi-Square and Z-tests
- **Returning users** and **high-rated restaurants** show the strongest response
- **Discount availability** and **restaurant rating** are the top conversion drivers
- The variant (ETA display) is confirmed as a meaningful feature in the ML model
- High-distance users (≥7 km) showed lower uplift — worth a follow-up test

---

## 📢 Recommendation

Roll out **Variant B** to 100% of users. Monitor average order value, repeat order rate, and conversion for 30 days post-launch.

---

## 🏷️ Tags

`python` `ab-testing` `swiggy` `logistic-regression` `hypothesis-testing` `mba-project` `business-analytics` `data-science` `chi-square` `z-test` `power-analysis`

---

## 👤 Author

MBA Business Analytics Project  
*Dataset: Swiggy Restaurants India — 1,40,657 records (2024)*
