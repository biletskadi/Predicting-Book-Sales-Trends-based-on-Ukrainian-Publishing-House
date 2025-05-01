# Predicting Book Sales Trends based on Ukrainian Publishing House

This repository contains the code, data, and methodology behind a two-part analysis of the Ukrainian book publishing industry:

Sales Forecasting — predicting future monthly sales for each book.

Success Rate Classification — identifying the success level of books based on their features.

This work was part of a bachelor thesis project focused on applying machine learning to real-world publishing data provided by a Ukrainian publishing house Svichado.


## Data Files

**Books_Metadata.csv**: Static book metadata (e.g., title, author, cover, format, price).

**Books_Print_Run_Info.xlsx**: Print-run numbers, used to determine book success labels.

**Books_Monthly_Sales_2020-2024.xlsx**: Monthly sales per book over 5 years.

**Note**: These files are used in the data preprocessing stage to generate training-ready datasets.

## 1. Data Preprocessing (Data_Processing.ipynb)
### Description
This notebook:

- Loads and merges all raw data files.

- Cleans metadata and sales records.

- Creates success rate from print-run data.

- Extracts new features (e.g. target audience from description).

- Outputs datasets for forecasting and classification tasks.


### Output Files (save/export):
**final_books_for_classification.csv**: Input for Classification_Success_Rate.ipynb

**final_books_for_forecasting.csv**: Input for Forecasting_Book_Sales.ipynb

## 2. Forecasting Task(Forecasting_Book_Sales.ipynb)
**Goal**: Forecast future monthly sales for each book.

Input Required:

**final_books_for_forecasting.csv** (from preprocessing)

#### Models Trained:

- Linear Regression

- Random Forest

- MLP

#### Metrics:

Mean Absolute Error (MAE)

RMSE

R² Score

MAE per Sales Range



## 3. Classification part (Classification_Success_Rate.ipynb)
**Goal**: Train models to classify books into success categories (e.g., Low, High) based on their characteristics.

Input Required:

**final_books_for_classification.csv** (from preprocessing)

#### Models Trained:

- Logistic Regression

- Decision Tree

- Naive Bayes

- Random Forest

- MLP

- Voting Ensemble (best performer)

#### Metrics:

- Accuracy

- F1-Score

- Confusion Matrix

Output Files (save/export for Classification Pipeline):
- **author_counts.pkl**: Saved author count from trained model
- **voting_ensemble.pkl**: Serialized model for future use
- **label_encoder.pkl**: Label encoder for transforming success categories
- **preprocessor.pkl**: Feature preprocessing pipeline for reuse

## 4. Custom Pipeline (Classification_Pipeline.ipynb)
**Goal**: Classify new books based on pre-sale data using the trained model pipeline.

Input Required:

- **author_counts.pkl**
- **voting_ensemble.pkl**
- **label_encoder.pkl**
- **preprocessor.pkl**
- **Pre-sale Metadata**
  
This Notebook:

- Accepts metadata for a new book.

- Applies consistent preprocessing.

- Predicts the book's likely success class.
