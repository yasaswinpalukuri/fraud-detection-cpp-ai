# 📅 Day 03 – June 15 – Attempted Model Export (Blocked by Environment Issues)

## 🧠 Goals
- Train XGBoost model
- Evaluate with AUC, precision, recall
- Export model to ONNX format for C++ runtime

## ⚠️ Outcome
- Model trained successfully on scaled dataset
- Faced multiple critical issues:
  - NumPy C-extension DLL load error (`_multiarray_umath`)
  - Pip + Python 3.12 compatibility problems
  - Kernel crashes due to mismatched library versions

## 🧱 Fix Attempted
- Switched to new Python 3.10 environment (`fraud-env`)
- Installed dependencies from scratch: `xgboost`, `onnxmltools`, `skl2onnx`, `numpy==1.23.5`
- Kernel stability restored but ONNX export failed due to:
  - Input type mismatch (`FloatTensorType`)
  - Shape calculator missing for `XGBClassifier`
  - Feature name conversion error: `ValueError: could not convert string to float: 'V14'`

## 🧭 Final Decision
- Postponed ONNX export
- Deferred fixes for next day due to fatigue