# Used Car Price Prediction Pipeline

## 📌 Project Overview
This repository features a comprehensive, end-to-end statistical pipeline developed in **R** to predict used car prices. Unlike basic regression models, this project emphasizes **statistical integrity**, utilizing advanced imputation techniques, power transformations, and rigorous diagnostic checks to ensure the model's reliability and robustness.

---

## 🛠️ Key Technical Highlights

* **Advanced Data Cleaning & Imputation**: 
    * Implemented **MICE (Multiple Imputation by Chained Equations)** for numerical predictors like `original_price` to handle missing data without biasing the distribution.
    * Used mode imputation for categorical features to maintain data consistency.
* **Feature Engineering**: 
    * Handled high-cardinality categorical variables (Make, Model, City) using **frequency-based lumping** (`fct_lump`) to prevent over-parameterization.
    * Applied **Binary and One-Hot Encoding** for model compatibility.
* **Multicollinearity Management**: 
    * Conducted iterative **VIF (Variance Inflation Factor)** analysis to prune redundant features and ensure a lean, interpretable model.
* **Target Transformation**: 
    * Applied **Box-Cox Transformation** ($\lambda \approx 0.05$) to normalize the response variable (`sale_price`), significantly improving adherence to linear regression assumptions.
* **Automated Model Selection**: 
    * Leveraged **Stepwise BIC (Bayesian Information Criterion)** for a parsimonious model that balances explanatory power with simplicity.
* **Rigorous Diagnostics**: 
    * Combined **Cook’s Distance**, **Hat Values (Leverage)**, and **Studentized Residuals** to identify influential outliers.
    * Visualized outlier intersections using **Venn Diagrams** for precise data pruning.

---

## 📊 Performance & Validation

The model was validated using a **5-Fold Cross-Validation** approach to ensure stability across different data subsets.

| Metric | Training Set | Test Set |
| :--- | :--- | :--- |
| **RMSE** | 0.513 | 0.484 |
| **MAE** | 0.348 | 0.340 |
| **R²** | 0.741 | 0.764 |

> **Note:** The high consistency between Training and Testing metrics demonstrates that the model generalizes well and is not overfitted.

---

## 📂 Repository Structure

* `Used_Car_Price_Prediction.R`: The core R script containing the full pipeline.
* `Used_Car_Price_Prediction.csv`: The raw dataset used for analysis.
* `plots/`: Directory containing diagnostic plots (Residuals, QQ-plot, Venn Diagram).

---

## 🚀 Getting Start

### 1. Prerequisites
You will need **R** or **RStudio** installed. The following libraries are required:
```r
install.packages(c("mice", "car", "rsample", "fastDummies", "dplyr", "forcats", "VennDiagram", "ggplot2", "lmtest", "sandwich", "MASS"))
