# BigMart Data Preprocessing

## Overview

This repository contains a complete data preprocessing pipeline applied to the **BigMart Sales Dataset**. The objective of this project is to clean, transform, and prepare raw retail data for downstream statistical analysis and machine learning models.

The work focuses on handling missing values, encoding categorical variables, feature scaling, and generating clean, model-ready data.

## Dataset

The dataset includes product-level and outlet-level information such as:

* Item weight
* Item visibility
* Item type
* Item MRP
* Outlet size
* Outlet location type
* Outlet establishment year

The target variable (if used later) is typically **Item_Outlet_Sales**.

## Preprocessing Steps

The notebook covers the following steps:

1. **Data Loading and Inspection**

   * Reading the dataset
   * Shape, data types, and summary statistics

2. **Missing Value Handling**

   * Imputation of numerical features (mean/median)
   * Logical handling of categorical missing values

3. **Data Cleaning**

   * Fixing inconsistent category labels
   * Handling zero or invalid values where applicable

4. **Feature Encoding**

   * Label encoding / one-hot encoding for categorical variables

5. **Feature Scaling**

   * Z-score standardization of numerical features

6. **Final Dataset Preparation**

   * Cleaned and transformed dataset ready for modeling

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib / Seaborn (for exploratory analysis)
* Jupyter Notebook

## File Structure

```
├── BigMart_Data_Preprocessing.ipynb
├── README.md
```

## How to Run

1. Clone the repository:

   ```bash
   git clone <repository-url>
   ```
2. Navigate to the project directory:

   ```bash
   cd <repository-name>
   ```
3. Open the notebook:

   ```bash
   jupyter notebook BigMart_Data_Preprocessing.ipynb
   ```

## Results

The final output is a clean, standardized dataset suitable for:

* Regression models
* Classification tasks
* Further feature engineering



## Collaborators

Saniya Shaikh
Shruti Bhandari
Hadassah Mercy
Sakshi Manjrekar
## License

This project is for academic and learning purposes.
