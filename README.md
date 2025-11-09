# Project: Predicting Medical Insurance Charges

**Author:** Vansh Shah
**Date:** 09/11/2025
**LinkedIn:** https://www.linkedin.com/in/shahvansh18/ 

---

## 1. Project Overview

This project aims to predict medical insurance costs for individuals based on a set of personal attributes. By building an accurate linear regression model, we can understand which factors most significantly influence medical charges, providing valuable insights for an insurance company. The final model successfully explains ~79.9% of the variance in insurance charges.

---

## 2. Dataset

* **Source:** The project uses the `insurance.csv` dataset.
* **Description:** The dataset contains 1,338 rows (after cleaning) and 7 original columns.
* **Features:**
    * `age`: Age of the primary beneficiary.
    * `sex`: Gender of the beneficiary (male/female).
    * `bmi`: Body Mass Index.
    * `children`: Number of children covered by insurance.
    * `smoker`: Whether the beneficiary smokes (yes/no).
    * `region`: The beneficiary's residential area in the US.
* **Target Variable:**
    * `charges`: Individual medical costs billed by health insurance.

---

## 3. Workflow & Methodology

1.  **Data Loading & Cleaning:** Loaded the `insurance.csv` file. Checked for null values (none found) and removed one duplicate row.
2.  **Exploratory Data Analysis (EDA):**
    * Analyzed numerical features, noting `charges` was heavily right-skewed.
    * Plotted categorical features, observing a significant imbalance between smokers and non-smokers.
    * A correlation heatmap showed that `age` and `bmi` had a positive correlation with `charges`.
3.  **Data Preprocessing (Encoding):**
    * Manually mapped `sex` to `is_female` (0/1) and `smoker` to `is_smoker` (0/1).
    * Applied One-Hot Encoding to the `region` column using `pd.get_dummies`.
4.  **Feature Engineering:**
    * Created a new `bmi_category` feature by binning the `bmi` values into four groups ('Underweight', 'Normal', 'Overweight', 'Obese') to capture non-linear relationships.
    * One-hot encoded this new `bmi_category` feature as well.
5.  **Feature Selection:**
    * Used the **Pearson Correlation** for numerical features and the **Chi-squared test** for categorical features to select the most statistically significant predictors of `charges`.
    * The final feature set included: `age`, `is_female`, `bmi`, `children`, `is_smoker`, `region_southeast`, and `bmi_category_Obese`.
6.  **Model Building & Evaluation:**
    * Scaled the final numerical features (`age`, `bmi`, `children`) using `StandardScaler`.
    * Split the data into an 80% training set and a 20% testing set.
    * Trained a `LinearRegression` model.
    * The model was evaluated on the test set to measure its performance.

---

## 4. Results & Conclusion

* **Model Performance:** The final linear regression model achieved an **Adjusted R-squared of 0.799**. This means the model can explain approximately 79.9% of the variability in medical charges.
* **Key Findings:** The feature selection process confirmed that `is_smoker` was by far the **most significant predictor** of insurance charges. Other important factors included `age` and `bmi_category_Obese`.
* **Conclusion:** This project demonstrates a complete machine learning workflow. The resulting model provides a strong baseline for predicting medical costs and clearly shows that lifestyle factors (like smoking) are critical in determining health insurance expenses.

---

## 5. Technologies Used

* **Python 3.x**
* **Jupyter Notebook**
* **Pandas:** For data manipulation and analysis.
* **NumPy:** For numerical operations.
* **Matplotlib / Seaborn:** For data visualization.
* **Scikit-learn (sklearn):** For preprocessing (`StandardScaler`), model building (`LinearRegression`), and evaluation (`r2_score`).

---
