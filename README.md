Clean and preprocess a 2019 online vehicle dataset (≈15,919 rows, 54 columns, 9 car models) containing many inconsistent, broken, and messy values, so it becomes suitable for machine learning. The project is broken up into four main phases: 

1. Data Cleaning: 
    * Removing broken, irrelevant, or redundant columns
    * Creating new columns with clean, meaningful, and usable values
2. Missing Value Analysis:
    * Filling in the gabs where data is missing
    * With techniques such as mean, median, or mode
3. Outlier Analysis:
    * Outliers are detected and visualized using boxplots and histograms.
    * Rather than removing all outliers (since extreme but valid values are expected for certain car models, e.g. luxury vehicles with high prices or powerful engines), the focus is on identifying and addressing only clear misprints or logically inconsistent entries.
4. Dummy Variable Analysis:
    * Categorical and multi-label columns (e.g. Comfort_Convenience, Extras) are converted to numeric format to create binary indicator variables suitable for machine learning.
    * Key techniques include pd.get_dummies() and str.get_dummies(sep=",")
