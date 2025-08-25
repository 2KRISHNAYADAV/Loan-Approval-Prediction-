# 📊 Results Summary

### 🔹 Logistic Regression
- **Val Accuracy:** <span style="color:orange; font-weight:bold;">0.639</span>  
- **Test Accuracy:** <span style="color:red; font-weight:bold;">0.613</span>  
- **F1:** 🟡 decent, but accuracy is low → **underfitting**

---

### 🌲 Random Forest
- **Val Accuracy:** <span style="color:orange; font-weight:bold;">0.656</span>  
- **Test Accuracy:** <span style="color:red; font-weight:bold;">0.613</span>  
- **F1:** 🟡 similar to Logistic → also underperforming on test

---

### 🚀 XGBoost
- **Val Accuracy:** <span style="color:green; font-weight:bold;">0.705 ✅</span> (best on validation)  
- **Test Accuracy:** <span style="color:red; font-weight:bold;">0.613</span> (still not generalizing well)  
- **F1:** 🟢 higher than others, but not translating to test accuracy  

---

# 🔍 Observations
- Models are **failing to generalize** → all three are stuck at  
  <span style="color:red; font-weight:bold;">~61% Test Accuracy</span>  
  despite XGBoost showing good validation performance.  

This suggests:
1. ⚠️ **Overfitting** (XGBoost especially).  
2. 🔄 **Data leakage / distribution shift** between Train/Val/Test.  
3. 🎭 **PCA may have removed important signal** from the data.  

---

# ✅ Next Steps

1. **🚫 Try without PCA**  
   - PCA can reduce predictive power if target-related variance is lost.  
   - Re-train models **without dimensionality reduction**.  

2. **🎯 Hyperparameter Tuning**  
   - Use **GridSearchCV / RandomizedSearchCV** for XGBoost & Random Forest.  
   - Key params:  
     - `n_estimators`, `max_depth`, `learning_rate`,  
       `min_child_weight`, `subsample`.  

3. **🔁 Cross-Validation (k-fold)**  
   - Replace single validation split with **5-fold CV**  
     for more reliable results.  

4. **🧐 Check Data Leakage / Shift**  
   - Compare **feature distributions** in Train vs Test.  
   - If distributions differ → preprocessing split issue.  

5. **🆕 Try Other Models**  
   - **LightGBM, CatBoost** → strong with categorical data.  
   - Try **Ensemble (stacking XGBoost + Logistic)**.  

---

# Loan-Approval-Prediction-
