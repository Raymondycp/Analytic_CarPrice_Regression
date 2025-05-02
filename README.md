# Car Price Classification

In the competitive automotive industry, accurately predicting car prices or classifying vehicles into price categories (high vs. low price) is essential for manufacturers, dealers, and consumers. This project uses a Logistic Regression model to classify cars based on their features, such as engine size, horsepower, and fuel efficiency, to determine whether they fall into a high or low price category. 

## Objectives

- **Exploratory Data Analysis (EDA)**: Analyze the distribution and relationships of car features (e.g., `enginesize`, `horsepower`, `citympg`) and the target variable (`price`, converted to binary) to identify key predictors.  
- **Model Development**: Implement and train a Logistic Regression model to classify cars into high or low price categories.  
- **Evaluation**: Assess model performance using accuracy and confusion matrix to evaluate classification effectiveness.  
- **Business Insights**: Provide recommendations for pricing strategies and market segmentation based on model results and feature importance.

## Dataset

The dataset, `Car_Price.csv`, contains 205 car records with 26 columns, including both numerical and categorical features. Key columns include:

- `car_ID`: Unique identifier for each car (1 to 205).  
- `symboling`: Insurance risk rating (-3 to 3).  
- `CarName`: Car brand and model (e.g., alfa-romero giulia, audi 100ls).  
- `fueltype`: Fuel type (gas or diesel).  
- `aspiration`: Aspiration type (std or turbo).  
- `doornumber`: Number of doors (two or four).  
- `carbody`: Body type (e.g., convertible, sedan, hatchback).  
- `drivewheel`: Drive type (fwd, rwd, 4wd).  
- `enginelocation`: Engine location (front or rear).  
- `wheelbase`, `carlength`, `carwidth`, `carheight`: Car dimensions (in inches).  
- `curbweight`: Car weight (in pounds).  
- `enginetype`, `cylindernumber`, `enginesize`, `fuelsystem`: Engine characteristics.  
- `boreratio`, `stroke`, `compressionratio`, `horsepower`, `peakrpm`: Engine performance metrics.  
- `citympg`, `highwaympg`: Fuel efficiency (miles per gallon).  
- `price`: Target variable, car price (in dollars, ranging from \~$5,000 to \~$45,000, assumed to be binarized for classification).

**Key Details**:

- The dataset has no missing values (all columns have 205 non-null entries).  
- Data types include integers (8 columns), floats (8 columns), and objects (10 categorical columns).  
- The target variable `price` is continuous but likely binarized (e.g., above/below median or a specific threshold) for Logistic Regression, as inferred from the classification approach.  
- Numerical features (e.g., `enginesize`, `horsepower`) and categorical features (e.g., `fueltype`, `carbody`) are typically used after preprocessing (e.g., encoding, scaling).

## Key Steps

1. **Data Loading and Preprocessing**:  
     
   - The dataset is loaded using `pandas` into a DataFrame (`car`).  
   - EDA (inferred as typical) includes:  
     - Descriptive statistics and data inspection via `car.info()` and `car.head(10)` to understand feature distributions.  
     - Visualizations such as histograms for numerical features (e.g., `enginesize`, `horsepower`), box plots for `price`, and correlation heatmaps to identify relationships.  
     - Categorical feature analysis (e.g., bar plots for `fueltype`, `carbody` vs. `price`).

   

2. **Data Preparation**:  
     
   - **Feature Selection**: Numerical features (e.g., `enginesize`, `horsepower`, `curbweight`) and possibly encoded categorical features (e.g., `fueltype`, `drivewheel`) are selected for modeling (inferred based on dataset and Logistic Regression requirements).  
   - **Target Binarization**: The continuous `price` is converted to a binary variable (e.g., 1 for high price, 0 for low price, possibly using median or a threshold like $15,000) to enable classification.  
   - **Encoding**: Categorical variables are encoded (e.g., one-hot encoding for `fueltype`, `carbody`) using `pandas.get_dummies` or `scikit-learn`’s `OneHotEncoder`.  
   - **Scaling**: Numerical features are scaled using `StandardScaler` to ensure compatibility with Logistic Regression (inferred as a standard step).  
   - **Train-Test Split**: The dataset is split into training (`X_train`, `y_train`) and testing (`X_test`, `y_test`) sets, likely using an 80-20 split (inferred).

   

3. **Model Training**:  
     
   - A Logistic Regression model (`lm`) is initialized and trained on `X_train` and `y_train` using `lm.fit()`.  
   - The model learns to classify cars into high or low price categories based on selected features.

   

4. **Prediction and Evaluation**:  
     
   - Predictions are made on `X_test` using `lm.predict()`, producing a binary output (`0` or `1`) stored in `prediction`.  
   - Model performance is evaluated using:  
     - **Accuracy**: Achieves 92.67% accuracy on the test set (`accuracy_score(y_test, prediction)`).  
     - **Confusion Matrix**: Shows 149 true negatives, 129 true positives, 8 false positives, and 14 false negatives, indicating strong performance with some misclassifications.  
   - Visualizations (inferred) may include:  
     - Confusion matrix heatmap to visualize true/false positives/negatives.  
     - Feature importance plots (e.g., based on Logistic Regression coefficients) to highlight key predictors.

---

