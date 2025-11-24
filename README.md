# 📱 Google Play Store App Rating Prediction

Predicting app ratings based on app features using **Python** and **linear regression**.

---

## 🎯 Objective

Build a model to predict the **app rating** using other app-related features such as category, reviews, size, installs, price, content rating, and genres.  

This helps Google Play identify **promising apps** for promotional boosts in recommendations and search results.

---

## 📝 Problem Statement

The Google Play Store plans to highlight certain apps with high potential by boosting their visibility.  
Predicting app ratings allows the platform to **identify apps likely to receive positive user ratings**, helping management decide which apps to promote.

---

## 📊 Dataset

Dataset: `googleplaystore.csv`  

### Columns:

- **App:** Name of the application  
- **Category:** App category  
- **Rating:** Overall user rating  
- **Reviews:** Number of user reviews  
- **Size:** App size (Kb or Mb)  
- **Installs:** Number of user installs  
- **Type:** Paid or Free  
- **Price:** Price of the app  
- **Content Rating:** Age group target (Children / Mature 21+ / Adult)  
- **Genres:** Multiple genres apart from main category  
- **Last Updated:** Last update date  
- **Current Ver:** Current version  
- **Android Ver:** Minimum Android version  

---

## 🛠 Steps Performed

### 1️⃣ Data Loading & Cleaning
- Loaded dataset using **pandas**  
- Checked for null values and removed rows with nulls  
- Corrected data types:
  - **Size:** Converted Kb/Mb to numeric  
  - **Reviews:** Converted to numeric  
  - **Installs:** Removed commas and '+' symbols, converted to numeric  
  - **Price:** Removed `$`, converted to numeric  

---

### 2️⃣ Sanity Checks
- Ratings must be between 1 and 5  
- Reviews ≤ Installs  
- Free apps should have price = 0  
- Dropped records violating above rules  

---

### 3️⃣ Univariate Analysis
- **Boxplots:** Price, Reviews  
- **Histograms:** Rating, Size  
- Observed potential outliers in Price, Reviews, Installs  

---

### 4️⃣ Outlier Treatment
- Removed apps with extremely high price (e.g., > $200)  
- Removed apps with reviews > 2,000,000  
- Removed apps with unusually high installs based on percentile cut-offs  

---

### 5️⃣ Bivariate Analysis
Explored relation between **Rating** and other features:
- **Rating vs Price** – scatter/join plot  
- **Rating vs Size** – scatter/join plot  
- **Rating vs Reviews** – scatter/join plot  
- **Rating vs Content Rating** – boxplot  
- **Rating vs Category** – boxplot  

---

### 6️⃣ Data Preprocessing
- Created a copy `inp1` for transformations  
- Applied **log transformation** to Reviews and Installs to reduce skew  
- Dropped irrelevant columns: `App`, `Last Updated`, `Current Ver`, `Android Ver`  
- Created **dummy variables** for categorical fields (`Category`, `Genres`, `Content Rating`) → `inp2`  

---

### 7️⃣ Train-Test Split
- Split data into **70% train** and **30% test**  
- Created `X_train`, `y_train`, `X_test`, `y_test`  

---

### 8️⃣ Model Building
- **Linear Regression** model  
- Trained on `X_train`, `y_train`  
- Evaluated **R² score** on training set  

---

### 9️⃣ Predictions
- Predicted app ratings on test set  
- Reported **R² score** on test set  

---

## 📈 Observations & Insights
- Rating is influenced by category, installs, and reviews  
- Most apps have ratings between 4 and 5  
- Very high-priced apps and extremely high installs/reviews are outliers  
- Linear regression provides baseline predictive capability  

---

## 🛠 Tools & Technologies
- Python 3.x  
- Pandas, NumPy, Matplotlib, Seaborn  
- Scikit-learn (Linear Regression)  
- Jupyter Notebook  

---
---

