# Import necessary libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats

# Load the dataset
df = pd.read_csv('heart.csv')  # (Assuming you're using the UCI Heart Disease dataset or Kaggle version)

# Inspect structure
print(df.info())
print(df.head())

# Check missing values
print(df.isnull().sum())

# Option 1: Imputation (if missing values exist)
df.fillna(df.median(numeric_only=True), inplace=True)  # for numerical columns
# OR drop missing rows
# df.dropna(inplace=True)

df.drop_duplicates(inplace=True)

# Z-score method
z_scores = np.abs(stats.zscore(df.select_dtypes(include='number')))
df = df[(z_scores < 3).all(axis=1)]  # Keeping data within 3 standard deviations


# Example: Fixing typos or standardizing strings (if any exist)
df['sex'] = df['sex'].replace({0: 'Female', 1: 'Male'})
df['cp'] = df['cp'].astype('category')

# Summary Statistics
print(df.describe())
print(df.skew())

# Histograms
df.hist(figsize=(12,10))
plt.tight_layout()
plt.show()

# Box Plots
for col in df.select_dtypes(include='number').columns:
    sns.boxplot(y=col, data=df)
    plt.title(f'Box plot of {col}')
    plt.show()


# Frequency counts
for col in df.select_dtypes(include='category').columns:
    print(df[col].value_counts())
    sns.countplot(x=col, data=df)
    plt.title(f'Frequency of {col}')
    plt.show()

# Correlation Matrix
plt.figure(figsize=(10,6))
sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
plt.title("Correlation Matrix")
plt.show()

# Scatter Plots (example)
sns.scatterplot(x='age', y='chol', hue='target', data=df)
plt.title("Age vs Cholesterol")
plt.show()

# Categorical vs Numerical
sns.boxplot(x='sex', y='thalach', data=df)
plt.title("Max Heart Rate by Sex")
plt.show()


# Pair Plot
sns.pairplot(df, hue='target')
plt.show()

# Heatmap (again for numerical correlation)
sns.heatmap(df.corr(), annot=True, fmt=".2f", cmap='YlGnBu')
plt.show()

# Grouped Comparison
grouped = df.groupby(['sex', 'cp'])['target'].mean().unstack()
grouped.plot(kind='bar', stacked=True)
plt.title("Heart Disease Rate by Sex and Chest Pain Type")
plt.ylabel("Proportion of Heart Disease")
plt.show()



