# ✅ Daily Log – Day 5  
**🗓️ Date:** 22nd June 2025  
**📁 Project:** Real-Time Credit Card Fraud Detection Engine  
**🎯 Goal:** Fix ONNX model export to return class probabilities instead of only class labels.

---

## 🔧 What We Did

1. **Reviewed ONNX Export Problem:**  
   Previously, ONNX inference output was always `[0]`, confirming it returned class labels (argmax), not probabilities.

2. **Investigated Multiple Export Approaches:**  
   - Attempted using `skl2onnx` and `onnxmltools` converters.
   - Faced errors like `MissingShapeCalculator`, `AttributeError`, and `KeyError` for `XGBClassifier`.

3. **Confirmed Incompatible Paths:**
   - `skl2onnx` does not directly support XGBoost’s `predict_proba()` unless registered with a proper shape calculator.
   - `onnxmltools.convert.xgboost.convert_xgboost` does not exist in the latest versions.

4. ✅ **Final Fix Applied:**
   - Used `xgboost.to_onnx()` instead of `skl2onnx.convert_sklearn`.
   - Exported ONNX model with probability support.

   ```python
   import xgboost as xgb
   from onnxmltools.convert import convert_xgboost
   from onnxruntime import InferenceSession
   ```

   - Verified correct ONNX output using:

   ```python
   sess.get_outputs()
   sess.run([output_name], {input_name: X_test[:1].astype(np.float32)})
   ```

   ✅ Got valid probability output like: `[[0.98 0.02]]`.

---

## 🧪 Challenges

- Repeated conversion failures due to:
  - `MissingShapeCalculator` error
  - Wrong converters being referenced
  - Output mapping failure
- Kernel switching wiped packages due to a clean `3.10` environment.

---

## ✅ Achievements

- Successfully exported the `XGBClassifier` to ONNX with probability output.
- Inference using ONNX Runtime now returns `predict_proba()` values.
- Set up clear inference flow with correct `input_name` and `output_name`.

---

## 🔄 Next Steps (Day 6 - 23rd June 2025)

1. Build a simple **Streamlit UI** to:
   - Upload CSV or enter features manually
   - Visualize prediction with probability

2. Integrate **SHAP Visualizations** to explain predictions.

3. Push updates to GitHub and prepare for C++ inference in the upcoming days.
