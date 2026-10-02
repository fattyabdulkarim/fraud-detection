# Fraud Detection Project

## Project Overview
This project is about analysing transaction data to understand the data and identify information that could be useful for fraud detection.

I used Python and Jupyter Notebook to work with the dataset and carry out my checks.

## What I Did

### 1. Set Up the Project

I created a project folder called `Fraud-detection`.

I created folders for my data and notebook and also created a Python virtual environment called `fraud-venv`.

I used the virtual environment so that the Python packages for this project were kept separate from my other projects.

### 2. Added the Dataset

I added the `nova_pay_combined.csv` dataset to the `Data` folder.

I then loaded the dataset into my Jupyter Notebook using pandas so I could start working with it.

### 3. Explored the Data

I started by looking at the dataset to understand its structure and the information contained in each column.

I checked the first few rows of the dataset and looked at the number of rows and columns.

I also checked the column names and data types to understand what type of information each column contained.

### 4. Checked the Data for Issues

I carried out some basic data quality checks before continuing with the analysis.

I checked for:

- Missing values
- Duplicate values
- Data types
- Possible spelling mistakes
- Inconsistencies in categorical values
- Possible outliers

I did these checks to understand the quality of the data before making any changes.

### 5. Checking for Duplicates

I checked the dataset for duplicate records.

The purpose of this was to find out whether the same record appeared more than once before deciding whether anything needed to be removed.

I inspected the duplicate values first rather than automatically deleting them.

### 6. Checking for Spelling Mistakes and Inconsistencies

I checked the categorical columns for unusual values, spelling mistakes and inconsistencies.

I also used a spell-checking approach to help identify possible spelling mistakes in text values.

I added known terms such as country codes and currency codes so that valid terms would not be incorrectly identified as spelling mistakes.

### 7. Checking for Data Types

I checked the data types of the columns to make sure that the variables were being stored in an appropriate format.

This helped me understand which columns were numerical, categorical or other types of data.

### 8. Checking for Outliers

I checked the numerical variables for possible outliers.

The purpose of this check was to identify values that were unusually high or low compared with the rest of the data.

I did not automatically remove any outliers because an unusual value does not necessarily mean that the value is incorrect.

### 8i Outliers in Amount_usd 
II used the IQR method to check for outliers. After doing the calculation, my upper bound was $600.08, so any amount_usd 

value above $600.08 is considered a statistical outlier.

### 9. Git and GitHub

I used Git to keep track of my project and GitHub to store my work.

I connected my local project to my GitHub repository and pushed my project to the `main` branch.

I initially had a problem when trying to push the project because GitHub returned a `403` permission error.

I checked my GitHub connection and re-authenticated through VS Code. After fixing the authentication issue, I was able to push my project successfully.

### 10. `.env` File

After I pushed my project to GitHub, the specialist noticed that my `.env` file was visible in the repository and told me to fix it.

I learned that `.env` files should not be uploaded to GitHub because they can contain sensitive information.

I removed the `.env` file from Git tracking and made sure it was added to my `.gitignore` file.

I then committed the change and pushed the updated project to GitHub.

This means the `.env` file remains available locally but is no longer included in the GitHub repository.


## Tools I Used

- Python
- Pandas
- Jupyter Notebook
- VS Code
- Git
- GitHub
- SpellChecker

