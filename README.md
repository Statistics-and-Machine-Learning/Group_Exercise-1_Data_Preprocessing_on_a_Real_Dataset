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

The target variable is typically **Item_Outlet_Sales**.

## Preprocessing Steps

The notebook covers the following steps:

 1. Handling Missing Values 
Identified via df.isnull().sum(): ItemWeight (976 missing), OutletSize (1606 missing).

Imputed ItemWeight with mean (df['Item_Weight'].fillna(df['Item_Weight'].mean(), inplace=True)), OutletSize with mode (df['Outlet_Size'].fillna(df['Outlet_Size'].mode()[0], inplace=True)).

Verified: 0 missing values post-imputation.
​

2️. Scaling Numerical Features 
Z-Score Standardization: Applied StandardScaler() to ItemWeight, ItemVisibility, ItemMRP, OutletEstablishmentYear → mean=0, std=1, unbounded range.

Min-Max Normalization: Applied MinMaxScaler() to same columns → scaled to range.
​

Difference: Z-score centers data (unbounded); Min-Max bounds to fixed interval. Outputs: df_zscore, df_minmax.
​

3️ . Handling Noise 
Selected ItemMRP as numerical feature.

Injected artificial Gaussian noise: np.random.normal(0, scale=df['Item_MRP'].std()*0.2, size=len(df)) (seed=42).

Applied rolling mean smoothing: df['Item_MRP_smoothed'] = df['Item_MRP_noisy'].rolling(window=10, min_periods=1).mean().

Visualized before/after with plot.
​

4️ .Handling Outliers
Detection: Z-score (>3 threshold) on numerical columns: ItemVisibility (81 outliers), ItemMRP_smoothed (14 outliers).

Handling: Log1p transformation (np.log1p()) on numerical columns with values >0 to compress extremes without removal.

Justification: Preserves data (no removal), suitable for skewed retail data like sales/MRP; avoids losing genuine high-value transactions. Compared original vs. transformed DataFrames.
​

5️ .Feature Selection 
Method: Filter (correlation matrix on numerical columns: ItemWeight, ItemVisibility, ItemMRP, OutletEstablishmentYear).

Correlation threshold: >0.8 for removal (none found; max ~0.1).

Retained all features; saved as df_selected.

Justification: Reduces multicollinearity efficiently without target variable; simple & fast for preprocessing. Final output: BigMart_preprocessed_final.csv 


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
   git clone <https://github.com/Statistics-and-Machine-Learning/Group_Exercise-1_Data_Preprocessing_on_a_Real_Dataset>
   ```
2. Navigate to the project directory:

   ```bash
   cd <Group_Exercise-1_Data_Preprocessing_on_a_Real_Dataset>
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
