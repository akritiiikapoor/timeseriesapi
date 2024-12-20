# Time Series API Usage Prediction

## Overview

This project predicts future API usage based on historical data using deep learning techniques. The dataset is aggregated by time (hourly) and analyzed using models like TabTransformer to forecast the number of API calls in the future.

## Requirements

Before running the project, ensure you have the following dependencies installed:

- Python 3.7 or higher
- TensorFlow 2.x
- Scikit-learn
- Pandas
- NumPy
- Matplotlib
- PyWavelets
- Keras

  ## Dataset

The dataset used contains API usage data over time. The data should be in CSV format, containing at least:

- **Time of Call**: Timestamp of the API call.
- **API Code**: Unique identifier for each API call.

The dataset is processed by converting the `Time of Call` column to datetime and resampling the data to an hourly frequency. After preprocessing, the data is normalized using MinMaxScaler for better model performance.

## Project Workflow

### 1. Data Loading and Preprocessing:
- Load the dataset using Pandas.
- Convert the `Time of Call` column to datetime and set it as the index.
- Resample the data to aggregate API usage on an hourly basis.
- Normalize the data using MinMaxScaler for better model performance.

### 2. Supervised Learning Dataset Creation:
- Create a supervised learning dataset where each input is the past `n` hours of data, and the target is the next hour's API usage.

### 3. Model Training and Evaluation:
Several deep learning models are built for predicting API usage:
- **TabTransformer**: A model using transformer architecture, specifically designed for time series data.
- The model is trained and evaluated using RMSE (Root Mean Squared Error) on the test set.

### 4. Model Selection and Prediction:
- The model with the best performance (lowest RMSE) is selected.
- The selected model is retrained on the entire dataset and used to make predictions for the next hour, day, week, and month.

### 5. Prediction Output:
- The model predicts the number of API calls for the next hour, day, week, and month.
- Predictions are transformed back to the original scale using inverse normalization.

## Best Model

The **TabTransformer** model was selected as the best-performing model based on its ability to predict future API calls with low RMSE.

## Predictions

Based on the model's output, the predictions for the next time periods are as follows:

- **Next Hour Prediction (Calls):** 1
- **Total Calls Next Day (Day 1, 24 hours):** 17
- **Total Calls Next Week (Days 1-7):** 118
- **Total Calls Next Month (Days 1-30):** 505

## Conclusion

The **TabTransformer** model is effective in predicting the number of API calls over short and long periods. These predictions can be utilized for API load balancing or scaling purposes, helping to manage infrastructure resources efficiently.
