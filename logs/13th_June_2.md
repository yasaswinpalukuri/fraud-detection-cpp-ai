# 📅 Day 02 – EDA, Feature Engineering & Preparation

## ✅ Tasks Completed
- Loaded `transactions.csv` into the notebook successfully
- Checked and visualized class imbalance (fraud vs non-fraud)
- Plotted distribution of `Time` and `Amount`
- Generated correlation heatmap to inspect key fraud indicators
- Scaled `Time` and `Amount` using `StandardScaler`
- Replaced raw columns with `scaled_time` and `scaled_amount`
- Saved preprocessed DataFrame for training

## 📊 Key Insights
- Highly imbalanced dataset: fraud cases ~0.17%
- Amount feature shows high skew; required scaling
- Correlation heatmap confirms weak but useful feature associations

## 🗂️ Files Updated
- `notebooks/fraud_model_training.ipynb` → with EDA + scaling steps

## ⏭️ Next Steps (Day 3)
- Train XGBoost model with class weighting
- Evaluate performance (AUC, precision, recall)
- Export trained model to ONNX format for C++ runtime

## 🧾 Git Commands
```bash
git add notebooks/fraud_model_training.ipynb logs/13th_June_2.md
git commit -m "Day 2: EDA, imbalance check, and feature scaling complete"
git push
```