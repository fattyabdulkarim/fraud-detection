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

## 9. Handling missing amount_usd
There were missing values in the amount_usd column. Instead of replacing them with the mean or median, I calculated the value using the available amount_src and the relevant currency conversion rate.
First, I checked the different source currencies and the available exchange rates. The source currencies were USD, CAD and GBP, with the following conversion rates to USD:
- USD → USD = 1.00
- CAD → USD = 0.74
- GBP → USD = 1.25
I then multiplied amount_src by the appropriate conversion rate based on the source_currency. This allowed me to derive the missing amount_usd values rather than estimating them.
After filling the missing values, I checked the column again to make sure there were no remaining null values.

## 10. Handling missing kyc_tier
For kyc_tier, I decided to use a group-based approach rather than simply filling all missing values with the overall most common KYC tier.
Before doing this, I noticed that some KYC values had inconsistent formatting, such as standard, STANDARD, standrd and values with extra spaces. I cleaned these values by removing unnecessary spaces, converting them to lowercase and correcting obvious spelling variations.
I then grouped the data by home_country and calculated the mode of kyc_tier within each group. The mode represents the KYC tier that occurred most frequently within each country.
I used these group-specific modes to fill any missing KYC values. I also used "Unknown" as a fallback where a suitable group value was not available.
Finally, I checked the column again and confirmed that there were no remaining missing values.

## 11. Handling missing fee
For the fee column, I used the channel column because the fee can vary depending on the transaction channel.
I grouped the data by channel and calculated the median fee for each channel. I chose the median because it is less affected by unusually high or low fee values than the mean.
The median for each channel was then used to fill any missing fee values within that channel.
I checked the column afterwards to confirm that there were no remaining missing values.

## Outlier Detection for fee
I also checked the fee column for potential outliers using the IQR (Interquartile Range) method.
I calculated:
- Q1 — the 25th percentile
- Q3 — the 75th percentile
- IQR — Q3 minus Q1
I initially used the standard constant of 1.5 to calculate the lower and upper bounds:
However, this identified a large number of values as potential outliers, even though many of the values were relatively close together. Based on the instruction to increase the constant, I tested a much larger constant of 100 to make the boundaries wider and reduce the number of values being classified as outliers.
I also visualised the fee distribution using a boxplot to better understand the potential outliers and the effect of the IQR boundaries. but the result loo the same.

## Hyperparameter Tuning Findings
I used `RandomizedSearchCV` to tune the Random Forest model by testing 10 combinations of hyperparameters with 3-fold cross-validation. The best configuration used 300 trees, a maximum depth of 10, a minimum of 4 samples per leaf, and `balanced_subsample` class weighting.

The baseline model achieved a test Average Precision of 0.8717, while the tuned model achieved 0.8766. This represents a small improvement in Average Precision. However, fraud recall remained at 0.82, and the fraud F1-score decreased slightly from 0.89 to 0.88.

Overall, hyperparameter tuning slightly improved the model's ranking performance, but further work is needed to improve the detection of fraudulent transactions.
