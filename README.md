# BigDataAnalytics

S&P 500 Stcok price minute prediction using Transformer models 

# Feb 21 handsON

# Stock Price Prediction Web Application

This project implements a Flask-based web application that predicts the next close price for a given stock (by default, the S&P 500 index, `^GSPC`) during market hours. The application uses `yfinance` to fetch stock data, applies normalization with `MinMaxScaler`, and predicts the next close price using a simple model with random fluctuations for added realism. The predictions are displayed using `Chart.js` on a dynamic line chart.

## Features

- **Live Stock Data Fetching**: Uses Yahoo Finance to fetch historical stock data.
- **Prediction Model**: Predicts the next close prices for a given stock based on historical data.
- **Market Hour Checking**: Only performs predictions during market hours (9:30 AM - 4:00 PM ET).
- **Chart Visualization**: Uses `Chart.js` to display predicted prices on a line chart.
- **Ngrok Integration**: Makes the Flask application publicly accessible via a dynamically generated ngrok URL.

## Prerequisites

Ensure you have the following installed:

- Python 3.x
- Pip (Python package installer)

You can install the required Python libraries using the following command:

```bash
pip install -r requirements.txt
```

### Requirements 


```
Flask==2.0.3
yfinance==0.1.67
numpy==1.21.4
scikit-learn==1.0.1
pyngrok==5.1.0
pytz==2021.3
Chart.js==3.8.0
```

## Running the Application

### Step 1: Clone the Repository

Clone this repository to your local machine.

```bash
git clone https://github.com/your-repo/stock-prediction-app.git
cd stock-prediction-app
```

### Step 2: Install Dependencies

Install the necessary Python packages.

```bash
install  requirements
```

### Step 3: Run the Flask App

Run the Flask application using the following command:

```bash
python app.py
```

This will start the Flask app locally on port `5000`.

### Step 4: Access the Application

Once the app is running, it will generate a public URL using `ngrok`, which you can access in your browser. The ngrok URL will be printed in the terminal like this:

```
 * ngrok URL: http://<random-string>.ngrok.io
```

Visit this URL in your browser to view the stock price predictions.

## How the Code Works

### 1. **Fetching Data**:

The `fetch_and_normalize_data()` function fetches historical stock data using the `yfinance` API. It extracts the `Open`, `High`, `Low`, and `Close` prices and normalizes them using `MinMaxScaler` to scale the data between 0 and 1.

### 2. **Market Hour Check**:

The `is_market_open()` function checks if the current time (in Eastern Time) is within market hours (9:30 AM to 4:00 PM ET) from Monday to Friday. If the market is closed, predictions are not made.

### 3. **Prediction Logic**:

The `predict_next_close()` function predicts the next close prices for the next 30 minutes. It uses the last `60` minutes of historical stock data and applies a small random fluctuation to simulate realistic price changes.

### 4. **Chart Visualization**:

The predictions are sent to the frontend where a line chart is drawn using `Chart.js`. The chart is dynamically updated with the predicted close prices and corresponding timestamps.

### 5. **Ngrok**:

The `pyngrok` library creates a tunnel from your local machine to the public internet, allowing you to access the Flask app via a publicly accessible URL.

## Adding Custom Stock Predictions

To change the stock ticker symbol (default is `^GSPC`), modify the `ticker` variable in the `predict()` route:

```python
ticker = '^GSPC'  
```

## Troubleshooting

- **ngrok Not Working**: Ensure you have a stable internet connection. If the ngrok URL is not generated, check for ngrok authentication issues or connectivity problems.
- **Flask App Not Starting**: Make sure you have installed all the dependencies and are running the app in the correct environment.

## Results

### Example Prediction

Once the app is running during market hours, you will see a line chart with predicted stock close prices over the next 30 minutes. The chart will update every minute with the next prediction.

**Add your results here** when you have completed testing or once the predictions are available.

### Sample Output:

- **Predicted Stock Price**: The y-axis will display predicted close prices in USD.
- **Time**: The x-axis will display timestamps at 1-minute intervals, representing the predicted future prices.

  

---

