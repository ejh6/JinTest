# Government Travel Expenses Analysis

## 📊 Data Source
The dataset used for this assignment was obtained from the Government of Canada - Proactive Disclosure - Travel Expenses portal. It includes records of government officials' travel expenses, covering costs such as airfare, lodging, meals, and other transport expenses. The dataset was downloaded on January 28th.

https://open.canada.ca/data/en/dataset/009f9a49-c2d9-4d29-a6d4-1a228da335ce/resource/8282db2a-878f-475c-af10-ad56aa8fa72c

## 🔹 Why This Dataset is Useful
This dataset provides valuable insights into government spending on travel. By analyzing this data, we can:

- Identify spending patterns and trends over time.
- Detect anomalies or inefficiencies in expenditures.
- Compare travel expenses across different government organizations.
- Make data-driven recommendations for cost optimization.

## 📁 Files in This Repository
- **merged_travel_data_YYYY-MM-DD.csv**: Merged dataset saved with today's date.
- **README.md**: Project overview and details about the dataset.

## 🔹 Data Cleaning and Handling
To ensure accurate analysis, the dataset underwent preprocessing, including:

### Standardizing Columns:
- Numeric columns (e.g., airfare, lodging, meals) were converted to numeric types and rounded to 2 decimal places.
- Non-numeric columns were converted to strings for consistency.

### Removing Unnecessary Columns:
- Columns such as `disclosure_group`, `title_fr`, `purpose_fr`, and others were removed to simplify the dataset.

### Handling Outliers:
- Outliers in numeric columns were identified using the Interquartile Range (IQR) method and replaced with NaN.

### Cleaning Text Data:
- The `owner_org_title` column was cleaned to remove French translations, ensuring consistency in organization names.

## 📈 Merging Datasets
The primary dataset (`travelq.csv`) was merged with a secondary dataset (`orgdetail.csv`) to enrich the data with additional organization details. The merge was performed using a LEFT JOIN on the following columns:

### Compound Key:
The merge was performed using a compound key consisting of `owner_org_title` and `owner_org`. This ensures that each row in the merged dataset is uniquely identified by the combination of these two columns.

### Merge Parameters:
- **left**: The primary dataset (`dtravel`).
- **right**: The secondary dataset (`otravel`).
- **how**: left (to preserve all rows from the primary dataset).
- **on**: `["owner_org_title", "owner_org"]` (the compound key).


## 📊 Explanation of Variables

- **dtravel**: The main dataset containing travel details.
- **otravel**: The secondary dataset containing organization details.
- **numeric_col**: List of columns that should be treated as numeric.
- **non_numeric_col**: List of columns that should be treated as strings.
- **columns_to_remove**: List of columns to be removed from the dataset.
- **numerical_columns**: List of numeric columns for outlier detection.
- **mmerge**: The merged dataset combining `dtravel` and `otravel`.

## 🔹 Explanation of Join vs Merge
- **Join**: A join operation combines rows from two or more tables based on a related column between them. It is typically used in SQL and can be thought of as a way to combine rows from different tables based on a condition.
- **Merge**: A merge operation in pandas is similar to a join but is more flexible. It allows for more complex combinations of dataframes, including different types of joins (inner, outer, left, right). In this case, we used a LEFT JOIN to ensure that all rows from the `dtravel` dataset are preserved, even if there are no matching rows in the `otravel` dataset.

## 📁 Final Output
The merged dataset was saved as `merged_travel_data_YYYY-MM-DD.csv`, where `YYYY-MM-DD` is the current date. This file contains the combined data from both datasets, ready for further analysis or visualization.

## 🔹 How to Run the Code
1. Ensure the datasets (`travelq.csv` and `orgdetail.csv`) are in the same directory as the notebook.
2. Open the `assignment6.ipynb` notebook in Jupyter or any compatible environment.
3. Run the cells sequentially to perform data cleaning, merging, and analysis.
4. The merged dataset will be saved as `merged_travel_data_YYYY-MM-DD.csv`.

## 📌 Conclusion
This project demonstrates the power of data cleaning and merging to uncover insights from complex datasets. By combining travel expense data with organization details, we can better understand spending patterns and identify areas for improvement.
