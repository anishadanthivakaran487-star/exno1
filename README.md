# Exno:1
Data Cleaning Process
# NAME:ANIAH ADAN THIVAKARAN
# REF NO:25017997

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
    # Exno:1
Data Cleaning Process
```pythonimport pandas as pd
import pandas as pd

df = pd.read_csv('Data_set.csv')

print("Before Cleaning:\n", df.isnull().sum())

for col in ['show_name', 'country', 'original_network']:
    df[col] = df[col].fillna(df[col].mode()[0])

df['aired_on'] = df['aired_on'].fillna(method='ffill')

for col in ['rating', 'current_overall_rank', 'watchers']:
    df[col] = df[col].fillna(df[col].median())

df = df.drop_duplicates()

print("\nAfter Cleaning:\n", df.isnull().sum())

df.to_csv('Cleaned_Data_set.csv', index=False)

print("\nData cleaning completed and saved as 'Cleaned_Data_set.csv'")

<img width="414" height="513" alt="Screenshot 2025-10-14 133518" src="https://github.com/user-attachments/assets/20446378-6b10-4e0d-8b6b-b32b85509fec" />


# Result

Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method
