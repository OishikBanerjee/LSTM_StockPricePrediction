# Stock Price Prediction and Impact Analysis Using LSTM Model

## Contributors
- **Amrit Agarwal**: 055004  
- **Oishik Banerjee**: 055028  
- **Group No**: 23  

---

## 1. Objective
This project aims to develop a Long Short-Term Memory (LSTM)-based deep learning model to forecast NIFTY 50 and Tata Steel stock prices using historical daily market data. The model seeks to provide insights into stock price movements and analyze how Tata Steel's stock performance influences the NIFTY 50 index.

---

## 2. Problem Statement
The main challenge addressed is predicting stock prices using time series data, which involves capturing complex patterns and trends. Additionally, this project evaluates how fluctuations in a key stock (Tata Steel) impact the NIFTY 50 index.

### Key Questions:
- Can we accurately predict future stock prices using historical data?
- What is the correlation between NIFTY 50 and Tata Steel stock movements?
- How effectively does the LSTM model capture stock market trends compared to actual market fluctuations?

---

## 3. Analysis and Approach

### 3.1 Data Collection and Preprocessing
- **Data Source**: Yahoo Finance (`yfinance` package)
- **Stocks**: Nifty 50 Index (^NSEI) and Tata Steel (TATASTEEL.NS)
- **Date Range**: January 31, 2005 – January 31, 2025
- **Focus**: Closing prices (normalized using MinMaxScaler for a range of 0–1)

### 3.2 Sequence Creation for LSTM Model
- **Window Size**: 60 days (past closing prices used to predict the next day’s price)
- **Input (X)**: Sliding window of past 60 consecutive closing prices
- **Target (y)**: Next day's closing price

### 3.3 Data Splitting
- Train-Test Split: 80% training, 20% testing

---

## 4. LSTM Model Architecture
- **Input Layer**: Takes sequences of shape `(60 time steps, 1 feature)`
- **LSTM Layers**: Three layers with `50 units` each and Dropout(0.2) to prevent overfitting
- **Dense Layers**:
    - One hidden layer with `25 units` (ReLU activation)
    - One output layer with `1 unit`
- **Optimizer**: Adam (learning rate = `0.001`)
- **Loss Function**: Mean Squared Error (MSE)

---

## 5. Model Training and Evaluation
- **Training Duration**: Trained for `10 epochs` (~13 seconds per epoch)
- **Performance Metrics**:
    - Training Loss decreased steadily across epochs.
    - Validation Loss followed a similar trend, indicating good generalization.

---

## 6. Observations

### 6.1 NIFTY 50 Prediction
The LSTM model effectively captured long-term trends but showed minor deviations during volatile periods.

#### Insights:
1. Strong overall trend capture with minor deviations.
2. Underestimation during sharp market fluctuations.
3. Better performance during stable growth phases.
4. Lag observed in predictions during rapid market movements.

---

### 6.2 Tata Steel Prediction
The model captured long-term trends but smoothed out short-term spikes.

#### Insights:
1. Good overall trend estimation but underestimation during high volatility.
2. Improved accuracy during moderate price movements.
3. Lag in capturing sharp peaks and dips.

---

### 6.3 Correlation Between NIFTY 50 & Tata Steel
Tata Steel significantly impacts NIFTY 50 movements, especially post-2022.

#### Insights:
1. Strong correlation between their trends.
2. Synchronized movements during market volatility.
3. Tata Steel acts as a leading indicator for broader market trends.

---

## 7. Managerial Insights
1. The model assists in forecasting price trends for informed investment decisions.
2. Highlights blue-chip stocks' influence on index movement.
3. Suggests the need for enhancements:
   - Incorporate technical indicators or sentiment analysis.
   - Use advanced models like Transformers for improved accuracy.
4. Risk management strategies can be optimized using predictions from this model.

---

## Project Statistics

| Parameter               | Details                                      |
|-------------------------|----------------------------------------------|
| Dataset                 | Historical closing prices of Nifty 50 & Tata Steel |
| Date Range              | January 31, 2005 – January 31, 2025         |
| Train-Test Split        | 80% training, 20% testing                   |
| Sequence Length         | Sliding window of past `60 days`            |
| Model Architecture      | LSTM with three layers                      |
| Optimizer               | Adam (learning rate = `0.001`)              |
| Loss Function           | Mean Squared Error (MSE)                    |
| Accuracy                | Nifty 50 (~97.78%), Tata Steel (~89.23%)    |

---

## Limitations & Future Work
1. Excludes macroeconomic factors and market sentiment.
2. Future enhancements:
   - Integrate technical indicators like RSI or Bollinger Bands.
   - Explore Transformer-based models for better performance.
   - Incorporate sentiment analysis for a holistic prediction approach.

---

This project demonstrates the potential of LSTM models in stock price forecasting while highlighting areas for improvement to handle market volatility more effectively.
