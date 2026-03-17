#AIM:
  To perform Exploratory Data Analysis on the given data set.
EXPLANATION:
The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

#ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

#CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = pd.read_csv(r"C:\Users\acer\Documents\titanic_dataset (1).csv") 

# Display basic info
df.info()

# Display first few rows
df.head()

# Check shape
print(f"Dataset contains {df.shape[0]} rows and {df.shape[1]} columns")

# Set PassengerId as index
df.set_index("PassengerId", inplace=True)

# Summary statistics
df.describe()

# Count unique values in categorical columns
categorical_columns = ["Survived", "Pclass", "Sex", "Embarked"]
for col in categorical_columns:
    print(f"{col} unique values:\n", df[col].value_counts(), "\n")

sns.countplot(data=df, x="Survived")
plt.title("Survival Count")
plt.show()

df["Pclass"].unique()
df.rename(columns={"Sex": "Gender"}, inplace=True)
df

sns.catplot(x='Survived', hue='Gender', data=df, kind='count')
plt.title("Survival by Gender")
plt.show()

sns.boxplot(x="Survived", y="Age", data=df)
plt.title("Age Distribution by Survival")
plt.show()

sns.boxplot(x="Pclass", y="Age", hue="Gender", data=df)
plt.title("Age Distribution Across Passenger Classes and Gender")
plt.show()

plt.figure(figsize=(10,6))

# Select only numerical columns
numerical_df = df.select_dtypes(include=["number"])

# Compute correlation and plot heatmap
sns.heatmap(numerical_df.corr(), annot=True, cmap="coolwarm", fmt=".2f")
plt.title("Feature Correlation Heatmap")
plt.show()

sns.pairplot(df, hue="Survived", diag_kind="kde")
plt.show()
```

#OUTPUT
<img width="609" height="493" alt="Screenshot 2026-03-17 220105" src="https://github.com/user-attachments/assets/58304996-9dc1-45eb-9f47-e69003cf418d" />
<img width="990" height="423" alt="Screenshot 2026-03-17 220114" src="https://github.com/user-attachments/assets/8bf39054-1cca-404c-b710-e40a32bc2c44" />
<img width="456" height="639" alt="Screenshot 2026-03-17 220124" src="https://github.com/user-attachments/assets/f99e508f-ac31-47dc-8874-d464e3162733" />
<img width="710" height="567" alt="Screenshot 2026-03-17 220131" src="https://github.com/user-attachments/assets/199a5ead-8fee-4342-a415-e3d83755a82e" />
<img width="716" height="629" alt="Screenshot 2026-03-17 220200" src="https://github.com/user-attachments/assets/a06a9b41-33fa-4169-952e-6fbf3f4eea98" />
<img width="1031" height="378" alt="Screenshot 2026-03-17 220151" src="https://github.com/user-attachments/assets/a80e8e52-7a7d-4a70-ae93-84f4a52812e4" />
<img width="699" height="552" alt="Screenshot 2026-03-17 220209" src="https://github.com/user-attachments/assets/03dba577-8f40-4a2e-87c3-5cb42a4497a5" />
<img width="689" height="556" alt="Screenshot 2026-03-17 220219" src="https://github.com/user-attachments/assets/4112f131-d293-4117-aaa7-0812e05fa5f3" />
<img width="958" height="648" alt="Screenshot 2026-03-17 220231" src="https://github.com/user-attachments/assets/8a987502-2db3-4dc0-8c67-c3481b993eaa" />
<img width="1044" height="757" alt="Screenshot 2026-03-17 220249" src="https://github.com/user-attachments/assets/fccc0dce-5fda-40a0-9701-1f811d18758f" />
<img width="699" height="552" alt="Screenshot 2026-03-17 220209 - Copy" src="https://github.com/user-attachments/assets/91f802f6-04a6-40e9-87fd-ffec5e4e39f2" />



#RESULT
    
Exploratory Data Analysis on the given data set is performed successfully.
