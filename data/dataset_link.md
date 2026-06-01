
# Dataset

The dataset used in this project was obtained from Kaggle:

https://www.kaggle.com/datasets/palvinder2006/zepto-inventory-dataset

## Import Notes

The original CSV file required UTF-8 encoding before it could be successfully imported into PostgreSQL.

Steps followed:

1. Download the dataset from Kaggle.
2. Open the CSV file in a spreadsheet editor (e.g., Excel).
3. Save the file using **CSV UTF-8 (Comma delimited)** format.
4. Import the UTF-8 encoded CSV file into PostgreSQL.
5. Run the SQL script located in the `sql/` folder.

This preprocessing step was necessary to avoid character encoding issues during data import.
