# 🚀 UNORG Predictive Inventory Planning System

> AI-powered warehouse inventory forecasting and demand optimization system for large-scale B2B grocery operations.

---

# 📌 Overview

UNORG is a rapidly growing B2B grocery procurement and delivery platform supplying raw materials and grocery products to:

- Restaurants
- Dhabas
- Street Food Vendors
- General Stores
- Cafeterias
- Manufacturers

With rapid business expansion, UNORG faced major operational challenges such as:

- Irregular bulk ordering patterns
- Seasonal demand fluctuations
- Frequent stockouts
- Overstocking of low-demand SKUs
- Perishable inventory losses
- Warehouse inventory imbalance

To solve these problems, we developed a **2-stage machine learning pipeline** that predicts:

✅ Which customers are likely to place orders  
✅ Which SKUs they are likely to purchase  
✅ Quantity required per SKU  
✅ Warehouse-level demand for the next 14 days  

The system converts customer-level forecasts into optimized warehouse stocking plans that reduce wastage, minimize stockouts, and improve fulfillment efficiency.

---

# 🎯 Business Objectives

- Improve warehouse fulfillment rates
- Reduce perishable inventory wastage
- Optimize SKU-level inventory planning
- Enable proactive procurement
- Reduce logistics and storage costs
- Improve customer satisfaction
- Generate warehouse-specific inventory forecasts

---

# 🧠 Solution Architecture

The project follows a **2-stage forecasting pipeline**.

## 🔹 Stage 1 — Customer Order Prediction

Predicts whether a customer will place an order on a given day within the next 14 days.

### Model Used
- LightGBM Classifier

### Features Used
- Historical order frequency
- Customer recency metrics
- Previous order activity
- Temporal features
- Seasonal behavior patterns

### Output

```python
(customer_id, date) → Probability(Order)
```

---

## 🔹 Stage 2 — SKU & Quantity Prediction

For customers predicted to order:

### SKU Prediction
- LightGBM Classifier

### Quantity Prediction
- Random Forest Regressor

### Output

```python
(customer_id, SKU, predicted_quantity)
```

---

# 🔄 Forecasting Pipeline

```text
Customer Order Prediction
            ↓
SKU Prediction
            ↓
Quantity Estimation
            ↓
Warehouse Aggregation
            ↓
Inventory Planning
```

---

# 📦 Inventory Optimization Logic

Warehouse-level demand forecasts are generated using:

```math
ExpectedDemand(i,j)
=
Σ [ P(Order) × PredictedQuantity ]
```

Where:
- i = SKU
- j = Warehouse

---

## 🛡️ Safety Stock Buffering

To minimize stockouts:

```math
FinalQuantity
=
ExpectedQuantity + α × σ
```

Where:

| Symbol | Meaning |
|---|---|
| α | Service-level multiplier |
| σ | Historical demand volatility |

Higher volatility SKUs receive larger safety buffers.

---

# 📊 Key Business Insights

## Prime Demand Months
- May
- September

## Low Demand Periods
- November
- December
- January

## High-Risk SKU Categories
- Oils & Ghee
- Flours
- Salt & Sugar

These categories showed:
- Highest stockout frequency
- Maximum inventory mismatch
- Significant operational losses

---

# 📈 Results & Performance

## Model Performance

| Metric | Score |
|---|---|
| Accuracy | 65% – 93% |
| F1 Score | 0.20 – 0.33 |
| Cross-Validation F1 | Up to 0.33 |

---

## Business Impact

| Metric | Improvement |
|---|---|
| Fulfillment Rate | +15% to +20% |
| Inventory Waste Reduction | Up to 25% |
| Stockout Reduction | 15% – 25% |
| SLA Compliance | Improved |
| Emergency Procurement | Reduced |

---

## Financial Impact

| Metric | Before | After |
|---|---|---|
| Stockout Penalty | ₹3.5L | ₹1.0L |
| Overstock Penalty | ₹2.2L | ₹0.9L |

### ✅ Estimated ROI: ~63.3%

---

# ⚙️ Tech Stack

## Programming
- Python

## Machine Learning
- LightGBM
- Scikit-learn
- Random Forest

## Data Processing
- Pandas
- NumPy

## Visualization
- Matplotlib
- Seaborn

---

# 🔬 Evaluation Metrics

## Order Prediction
- Accuracy
- F1 Score
- Cross-validation score

## Quantity Prediction
- MAE
- RMSE

## Inventory Metrics
- Stockout reduction
- Wastage reduction
- Service-level improvement

---

# 🏁 Conclusion

This project demonstrates how machine learning and predictive analytics can transform inventory planning for large-scale B2B grocery operations.

By combining:
- Customer demand forecasting
- SKU prediction
- Quantity estimation
- Warehouse aggregation
- Volatility-aware buffering
- Perishability optimization

the system enables:

✅ Smarter inventory decisions  
✅ Reduced wastage  
✅ Higher fulfillment rates  
✅ Improved profitability  
✅ Scalable warehouse operations  
