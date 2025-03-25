# Stock Price Analyzer
# Created by [Kimathi Owusu-Sekyere]
# A simple tool that fetches historical stock price data and plots closing prices

import yfinance as yf
import matplotlib.pyplot as plt
import datetime

# Function to fetch data for a given stock ticker
def fetch_stock_data(ticker, start_date, end_date):
    print(f"Fetching data for {ticker}...")
    data = yf.download(ticker, start=start_date, end=end_date)
    if data.empty:
        print(f"No data found for {ticker}. Please check the ticker symbol.")
    return data

# Function to plot closing prices
def plot_stock_data(data, ticker):
    if data.empty:
        return
    plt.figure(figsize=(10, 5))
    plt.plot(data['Close'], label=f'{ticker} Closing Price')
    plt.title(f'{ticker} Closing Price Over Time')
    plt.xlabel('Date')
    plt.ylabel('Price in USD')
    plt.legend()
    plt.grid()
    plt.show()

# Main execution block
if __name__ == "__main__":
    # Customize the ticker and date range
    ticker = input("Enter the stock ticker (e.g., AAPL, MSFT, TSLA): ").upper()
    start_date = input("Enter start date (YYYY-MM-DD): ")
    end_date = input("Enter end date (YYYY-MM-DD): ")

    # Fetch and plot data
data = fetch_stock_data(ticker, start_date, end_date)
plot_stock_data(data, ticker)

# This project was created by [Your Name] to practice Python, data visualization, and working with financial data.
# Feel free to use and modify!
