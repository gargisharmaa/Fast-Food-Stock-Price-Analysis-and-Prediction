This project aims to provide a comprehensive analysis of fast food stocks by fetching real-time and historical stock data, processing it, and applying machine learning models to predict future stock prices. It also includes a Power BI dashboard for visualizing insights from the stock data.

## Features

- **Data Collection**: Fetches historical and real-time stock data using the Yahoo Finance API.
- **Data Preprocessing**: Cleans and processes the stock data for analysis and prediction.
- **Stock Price Prediction**: Uses Prophet to forecast future stock prices based on historical data.
- **SQL Database Integration**: Stores processed stock data and predictions in a MySQL database.
- **Power BI Dashboard**: Provides a Power BI dashboard that visualizes stock trends, volumes, and predictions for better decision-making.

## Technologies Used

- **Python**: Core programming language used for data fetching, processing, and analysis.
- **Pandas**: For data manipulation and cleaning.
- **SQLAlchemy**: For interfacing with the MySQL database.
- **yFinance**: To fetch stock data from Yahoo Finance.
- **Prophet**: For time series forecasting.
- **Power BI**: For data visualization and reporting.

## Project Structure

```plaintext
├── config.py                # Configuration file with database URL, stock tickers, and CSV directory
├── database.py              # Functions to handle database operations (fetching, inserting data)
├── data_preprocessing.py    # Data preprocessing for cleaning and preparing the stock data
├── stock_data_fetch.py      # Real-time stock data fetching using yFinance API
├── prediction.py            # Stock price prediction using Prophet
├── main.py                  # Main execution file to load, update, and predict stock data
├── README.md                # Project overview and instructions
└── PowerBI/                 # Power BI dashboard and reports
    └── Stock_Market_Dashboard.pbix
```

### File Descriptions

1. **config.py**
   - Contains configurations such as database connection URL, stock ticker symbols, and the directory where CSV files are stored.

2. **database.py**
   - Handles all the database-related operations:
     - Insert Data: Inserts cleaned and preprocessed data into MySQL tables.
     - Fetch Data: Fetches historical stock data from the SQL database.

3. **data_preprocessing.py**
   - Cleans and preprocesses the stock data:
     - Converts raw CSV data to a format suitable for SQL insertion.
     - Handles missing values, adds columns such as Month, Quarter, and Adj Close.

4. **stock_data_fetch.py**
   - Fetches real-time stock data from Yahoo Finance:
     - Retrieves data from the start date to the current date.
     - Adds stock-specific columns such as Company (ticker), Adj Close, Month, and Quarter.

5. **prediction.py**
   - Performs stock price predictions using Prophet:
     - Train: Fits a model based on historical data.
     - Predict: Forecasts future stock prices for a given number of days.
     - Inserts the predictions into the SQL database.

6. **main.py**
   - The central module that orchestrates the loading, updating, and predicting of stock data:
     - Loads historical CSV data into the database.
     - Updates real-time stock data on a daily basis.
     - Generates predictions and stores them in the database.

## Installation and Setup

### Prerequisites

- Python 3.8+ installed on your system.
- MySQL installed and running.
- Power BI Desktop (for viewing and editing the dashboard).

### Python Libraries

You can install all the required Python libraries using the following command:

```bash
pip install -r requirements.txt
```

### Database Setup

1. Install and set up MySQL.
2. Update the `DB_URL` in `config.py` with your MySQL credentials:

```python
DB_URL = 'mysql+pymysql://<user>:<password>@localhost/<database_name>'
```

3. Create a MySQL database and necessary tables for storing stock data and predictions.

### Fetching and Inserting Data

Run the main Python script to load historical data and update real-time stock data into the SQL database:

```bash
python main.py
```

### Prediction

Stock price predictions are automatically run after updating real-time data. Predictions for the next 7 days are saved in the database.

## Power BI Dashboard

We have created a Power BI dashboard to visualize insights gained from the stock data. This dashboard contains:

- **Stock Price Trends**: Line charts showing closing prices of fast food stocks over time.
- **Volume Analysis**: Bar charts showing trading volume for each stock.
- **Predicted Prices**: Visualizations of predicted stock prices with confidence intervals.
- **Comparison of Companies**: A comparative analysis of different companies based on their stock performance.

### How to Use the Power BI Dashboard:

1. Open the `Stock_Market_Dashboard.pbix` file located in the PowerBI folder using Power BI Desktop.
2. Refresh the data source to load the most up-to-date data from your MySQL database.
3. Explore various visuals to gain insights into stock performance, trends, and future predictions.

## Future Improvements

- Add more advanced machine learning models for more accurate predictions.
- Enhance the Power BI dashboard with real-time updates.
- Expand analysis to include more companies from other industries.
