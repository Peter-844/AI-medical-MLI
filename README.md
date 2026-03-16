# 🩺 糖尿病預測：結構化醫療數據的 ML 分析流程
### (Pima Indians Diabetes Prediction & Statistical Analysis)

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Machine%20Learning-Scikit--Learn-orange?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Statistics](https://img.shields.io/badge/Statistics-Medical%20Analysis-green)](#)

本專案實作了一套嚴謹的醫療機器學習流程。不同於一般的黑箱模型預測，本流程遵循**六個關鍵階段**，結合「統計學」作為品質管理工具，確保模型的臨床可解釋性 (Interpretability) 與預測穩定性。

---

## 🚀 專案核心流程 (6-Stage Pipeline)

本專案嚴格執行以下流程，確保從數據探索到模型解釋的每一步都具備醫學統計意義：

1.  **數據探索 (Exploration)**：描述統計、偏態/峰態分析、QQ圖檢測數據分佈。
2.  **特徵篩選 (Selection)**：透過 t-test / 卡方檢定篩選 $p < 0.05$ 的顯著因子。
3.  **共線性檢測 (Collinearity)**：利用 VIF (膨脹因子) 排除冗餘特徵（VIF > 10）。
4.  **不平衡診斷 (Imbalance)**：針對稀有疾病樣本，使用 SMOTE 技術平衡類別分布。
5.  **模型驗證 (Validation)**：計算 AUC 與 Bootstrap 95% 信賴區間，並繪製校準曲線。
6.  **臨床解釋 (Interpretation)**：將係數轉化為 **Odds Ratio (勝算比)**，提供白話醫療解釋。



---

## 📊 數據來源
本專案使用著名的 **Pima Indians Diabetes Dataset** (透過 `kagglehub` 自動載入)。
* **目標變數**：`Outcome` (0: 非糖尿病, 1: 糖尿病)
* **特徵欄位**：
    * `Pregnancies`: 懷孕次數
    * `Glucose`: 血糖濃度
    * `BloodPressure`: 血壓
    * `SkinThickness`: 皮膚厚度
    * `Insulin`: 胰島素
    * `BMI`: 身體質量指數
    * `DiabetesPedigreeFunction`: 糖尿病家族病史函數
    * `Age`: 年齡

---

## 🛠️ 技術棧
* **數據處理**：`Pandas`, `NumPy`
* **統計分析**：`SciPy`, `Statsmodels`
* **機器學習**：`Scikit-Learn`, `Imbalanced-Learn (SMOTE)`
* **視覺化**：`Seaborn`, `Matplotlib`

---

## 📈 關鍵實驗結果

### 1. 數據品質管理
在資料預處理階段，我們識別出 `Glucose`, `BMI` 等欄位中存在生理上不合理的「0」值，並採用中位數進行臨床補值，顯著提升模型穩定度。

### 2. 模型表現 (Evaluation)
* **AUC Score**: 展現模型優異的區分能力。
* **Bootstrap 95% CI**: 透過 1000 次重抽樣證明模型非偶然結果。
* **校準度 (Calibration)**：校準曲線顯示預測機率與實際觀測值高度吻合。



### 3. 臨床價值 (Odds Ratio)
模型輸出結果可轉化為臨床易懂的指標。例如：
> **「Glucose (血糖) 每增加一個單位，罹病勝算比 (Odds Ratio) 增加 X.XX 倍。」**

---
