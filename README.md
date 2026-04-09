# Auto Scout Car Price Prediction Project

## Project Overview
This project involves the end-to-end processing of a 2019 online vehicle dataset, transforming raw, inconsistent data into a production-ready predictive model. The dataset initially consists of **15,919 rows and 54 columns** covering 9 different car models. 

The primary goal is to clean, prepare, and engineer features to build a machine learning regression model capable of accurately **predicting car prices** based on vehicle characteristics.

---

## Workflow Phases

### 1. Data Cleaning
The initial stage focuses on fixing inconsistencies and converting raw data into a structured format.
* **Column Management:** Removal of broken, irrelevant, or redundant columns.
* **Merging:** Consolidating overlapping information, such as merging owner-related columns into a single unified field.
* **Feature Extraction:** Extracting numeric values from strings and splitting complex list values into separate features like Fuel and Gears.
* **String Parsing:** Creating new columns like Paint Type and Upholstery through parsing or external lookups.

### 2. Missing Value Analysis
Filling gaps in the dataset to ensure a complete data structure for modeling.
* **Mode Imputation by Group:** Filling categorical gaps by calculating the mode within specific groups.
* **Multi-Level Grouping:** Using advanced grouping to fill values in a contextually accurate manner.

### 3. Outlier Analysis
Instead of a blanket removal of extreme values, this phase uses domain knowledge to distinguish between valid high-end data and errors.
* **Visualization:** Identifying outliers using domain knowledge.
* **Logical Validation:** Identifying unrealistic values and treating them as missing data.
* **Imputation:** Re-applying missing value techniques to handle these identified misprints responsibly.

### 4. Dummy Variable Analysis
Final preparation of categorical data for machine learning algorithms.
* **Binary Encoding:** Transforming categorical variables into numeric formats.
* **Multi-Label Handling:** Utilizing specialized functions for complex fields like Comfort, Convenience, and Extras.

---

## Modeling and Evaluation
The final prepared dataset contains approximately **15,918 rows and 158 columns**, with all features converted to numeric types.

* **Model Testing:** Implementing several regression models to find the most accurate price predictor.
* **Hyperparameter Tuning:** Utilizing automated optimization for model refinement.
* **Feature Importance:** Analyzing variable importance to understand which vehicle characteristics most significantly impact price.
* **Efficiency:** Retraining the top-performing model on a reduced feature set to improve computational speed and model interpretability.

---
