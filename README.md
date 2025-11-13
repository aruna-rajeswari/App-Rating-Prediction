Predicting Google Play Store App Ratings
Objective
The objective of this project is to develop a predictive model that estimates the rating of an app on the Google Play Store using other available app attributes. Accurate predictions can help the Google Play Store team identify promising apps for increased visibility and promotion.

Problem Statement
Google Play Store is introducing a feature to boost visibility for apps with high potential. The boost will appear in recommendations sections, search results, and other app discovery channels. Since app ratings are strong indicators of user satisfaction and app quality, predicting the rating of an app using available metadata can help in identifying apps that deserve this boost.

Domain
General – Mobile applications

Dataset DescriptionDataset: googleplaystore.csv

Columns:

Column	Description
App	Name of the app
Category	Main category of the app
Rating	Average user rating
Reviews	Number of user reviews
Size	App size (in Kb or Mb)
Installs	Number of downloads
Type	Free or Paid
Price	Price of the app
Content Rating	Age group (Children, Mature 21+, Adult)
Genres	Multiple genres associated with the app
Last Updated	Last update date
Current Ver	Current version
Android Ver	Minimum required Android version

Data Cleaning and Preprocessing
Loading Data: Imported using Pandas.
Null Values: Checked and dropped rows with any nulls.

Correcting Data Types and Formats:
Size: Converted Kb and Mb to numeric values (Mb × 1,000).
Reviews: Converted from string to numeric.
Installs: Removed ‘+’ and ‘,’ symbols, converted to integer.
Price: Removed ‘$’ symbol and converted to numeric.

Sanity Checks:
Dropped ratings outside 1–5 range.
Removed apps with reviews > installs.
Dropped free apps with price > 0.

Exploratory Data Analysis (EDA)
Univariate Analysis:
Price: Boxplot revealed outliers (e.g., $200 apps), which were removed.
Reviews: Very high reviews were outliers and dropped (threshold > 2 million).
Rating: Histogram showed distribution skewed toward higher ratings.
Size: Some extreme values were identified and cleaned.

Bivariate Analysis:
Rating vs. Price: Scatter plots suggested little correlation; very expensive apps do not necessarily have higher ratings.
Rating vs. Size: Larger apps do not always have better ratings.
Rating vs. Reviews: Higher reviews do not guarantee higher ratings.
Rating vs. Content Rating: Some age-targeted apps had slightly higher ratings.
Rating vs. Category: Certain categories like “Music” and “Education” had marginally higher ratings.

Outlier Treatment
Removed apps with extreme price (> $50), reviews (> 2 million), and installs (top 1% percentile).
Applied percentile-based cutoffs to normalize distributions.
Data Preprocessing for Modeling
Log Transformation: Applied np.log1p() to Reviews and Installs to reduce skewness.
Dropping Irrelevant Columns: App name, Last Updated, Current Ver, Android Ver.
Encoding Categorical Features: Dummy variables created for Category, Genres, and Content Rating.
Final DataFrame: Named inp2 and ready for model building.

Train-Test Split
Split data into 70% training and 30% testing.
Created X_train, y_train, X_test, y_test datasets.

Model Building
Technique: Linear Regression

Steps:

Fit the model on training data (X_train, y_train).
Evaluated R² score on training data.
Made predictions on test data and reported R² score.

Results
Metric	Value
R² (Train)	Insert train R² here
R² (Test)	Insert test R² here

Observations:
Model captured some variance in ratings but may not fully explain all user behaviors.
Further improvement possible using advanced regression models or feature engineering (e.g., text analysis of app descriptions).

Conclusion
This project successfully demonstrated a workflow for predicting app ratings using structured app metadata. The linear regression model provides a baseline that can guide Google Play Store in identifying promising apps for promotion. Future enhancements could include additional features, such as app description sentiment, developer reputation, and user engagement metrics.
