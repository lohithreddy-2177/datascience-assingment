1. Introduction
This project focuses on analyzing a medical dataset related to heart disease. The goal is to clean the data, explore patterns, and understand the relationships between different features to draw meaningful insights that could help in predicting heart disease risk.

The dataset includes various numerical and categorical variables such as age, cholesterol level, chest pain type, and sex. The analysis involves data cleaning, univariate, bivariate, and multivariate analysis using Python.

2. Libraries Used (with Explanation)
Library	Purpose
pandas:	For data manipulation, cleaning, and handling missing/duplicate data.
numpy:	For numerical computations like mean, median, standard deviation, and handling arrays.
matplotlib.pyplot:	For creating static visualizations like histograms, boxplots, bar charts, etc.
seaborn:	An advanced visualization library built on top of matplotlib; useful for heatmaps, pair plots, violin plots, etc.
scipy.stats:	Used for statistical analysis like detecting outliers using Z-scores.


3. Dataset Description
This dataset contains information about patients and the presence (1) or absence (0) of heart disease. Key features include:

Feature	Description
age  	     Age of the patient
sex	       Gender (1 = male, 0 = female)
cp	       Chest pain type (categorical)
trestbps	 Resting blood pressure
chol	     Serum cholesterol level
fbs	       Fasting blood sugar > 120 mg/dl
restecg	   Resting ECG results
thalach	   Maximum heart rate achieved
exang	     Exercise-induced angina
oldpeak	   ST depression induced by exercise
slope	     Slope of peak exercise ST segment
ca	       Number of major vessels colored by fluoroscopy
thal	     Thalassemia (blood disorder)
target	   Presence of heart disease (0 = no, 1 = yes)


4. Data Cleaning
a. Missing Values

Missing values can reduce model performance and mislead analysis. They were handled using median imputation (for numerical columns), which is robust to outliers.

b. Duplicate Records

Duplicates can distort the analysis and were removed using:

c. Outlier Detection

Outliers are extreme values that can skew the results. We used the Z-score method to detect and remove records where the Z-score was beyond ±3.

d. Standardizing Categorical Values

Categorical values are standardized to remove inconsistencies (e.g., encoding 0 as ‘Female’ and 1 as ‘Male’):

5. Exploratory Data Analysis (EDA)
🔹  Univariate Analysis (One variable at a time)

Summary Statistics:
Histograms: To understand the distribution shape of each numerical feature.
Box Plots: Used to visualize spread and detect outliers.
Frequency Distribution for Categorical Variables

🔹 Bivariate Analysis (Two Variables)

Correlation Matrix (Pearson Correlation):

Scatter Plot (Age vs Cholesterol):
Identifies patterns between two continuous variables and heart disease.

Box Plot (Sex vs Max Heart Rate):
Compares numerical variable distributions across categories.

🔹 Multivariate Analysis (Multiple Variables)

Pair Plot:
Visualizes relationships across all pairs of features.

Heatmap (Correlation Again):

Grouped Comparison (Sex and Chest Pain Type vs Target):
Shows combined impact of two categorical features on heart disease.

6. Insights & Interpretations
Age, cholesterol, and heart rate have some correlation with heart disease risk.
Males had a higher incidence of heart disease in this dataset.
Chest pain type and maximum heart rate were strong indicators of heart disease presence.
Pair plots and grouped bar plots reveal that combinations of features (e.g., sex + cp) offer better insight than individual features.

7. Conclusion
This project demonstrated a full data analysis workflow:

Cleaned messy data (missing, duplicates, outliers).
Visualized distributions and relationships using EDA.
Identified key features impacting heart disease.

