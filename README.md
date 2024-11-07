# CryptoTrend Predictor Tool

### Overview
CryptoTrend Forecasting Tool is a Python-based project designed to analyze historical cryptocurrency trading data, calculate key trading metrics, and predict future price trends. Using the Binance API for data retrieval, this tool processes data to provide insights and trend predictions for top-traded cryptocurrency pairs. The project leverages machine learning to forecast potential high and low prices, assisting in crypto trend analysis and decision-making.

### Features
- Retrieves historical cryptocurrency data from the Binance API
- Calculates trading metrics such as historical highs/lows, percentage differences, and future highs/lows
- Trains and evaluates predictive models using Random Forest to forecast future price trends
- Provides predictions based on user input and historical trends

### Tech Stack
- **Languages**: Python
- **Libraries**: `requests`, `pandas`, `scikit-learn`
- **Platforms**: Binance API

### Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Functions](#functions)
- [Example](#example)
- [License](#license)

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/cryptotrend-forecasting-tool.git
   cd cryptotrend-forecasting-tool
   ```

2. **Install the required Python libraries**:
   ```bash
   pip install requests pandas scikit-learn
   ```

### Usage

1. **Data Retrieval**:
   Use the `fetch_crypto_data` function to retrieve historical data for a specified cryptocurrency pair from a given start date.

2. **Metric Calculation**:
   Use the `calculate_metrics` function to calculate historical highs, lows, and percentage differences. This function also provides future high/low metrics based on specified look-back and look-forward periods.

3. **Model Training**:
   Train the machine learning model with `train_model` to prepare for future trend prediction.

4. **Prediction**:
   Use `predict_outcomes` to forecast future percentage differences in prices, or use `evaluate_crypto_trend` to evaluate trends across an entire dataset.

### Project Structure
```plaintext
├── README.md                # Project documentation
├── main.py                  # Main script with functions and flow
├── requirements.txt         # Dependencies for the project
└── data                     # Folder for storing downloaded crypto data (optional)
```

### Functions

- **fetch_crypto_data(crypto_pair, start_date)**:
  Retrieves historical cryptocurrency data from Binance API.
  - **Parameters**: `crypto_pair` (str), `start_date` (str)
  - **Returns**: DataFrame with columns: Date, Open, High, Low, Close

- **calculate_metrics(data, variable1, variable2)**:
  Calculates historical and future trading metrics.
  - **Parameters**: `data` (DataFrame), `variable1` (int), `variable2` (int)
  - **Returns**: DataFrame with calculated metrics

- **train_model(data)**:
  Trains a Random Forest model for price prediction.
  - **Parameters**: `data` (DataFrame with metrics)
  - **Returns**: Trained models for predicting high and low price differences

- **predict_outcomes(model1, model2, input_features)**:
  Predicts future percentage differences based on user input.
  - **Parameters**: `model1`, `model2`, `input_features` (list)
  - **Returns**: Predicted percentage differences from future high and low prices

- **evaluate_crypto_trend(data, model1, model2, variable1, variable2)**:
  Evaluates and appends predictions to the dataset based on historical metrics.
  - **Parameters**: `data` (DataFrame), `model1`, `model2`, `variable1` (int), `variable2` (int)
  - **Returns**: DataFrame with predictions

### Example

1. **Retrieve Data**:
   ```python
   crypto_data = fetch_crypto_data('BTCUSDT', '2023-01-01')
   ```

2. **Calculate Metrics**:
   ```python
   metrics_data = calculate_metrics(crypto_data, variable1=7, variable2=5)
   ```

3. **Train the Model**:
   ```python
   model1, model2 = train_model(metrics_data)
   ```

4. **Predict Future Trends**:
   ```python
   input_features = [3, -1.2, 5, 2.3]  # Example feature values
   predicted_high_diff, predicted_low_diff = predict_outcomes(model1, model2, input_features)
   ```

5. **Evaluate Trends on Entire Dataset**:
   ```python
   evaluated_data = evaluate_crypto_trend(crypto_data, model1, model2, variable1=7, variable2=5)
   ```

### License
This project is licensed under the MIT License.
