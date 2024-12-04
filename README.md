# Stock Technical Indicators Interface

## Overview
Alpha Vantage provides free API to access realtime and historical financial market data and technical indicators. This interface allows users to:
- Fetch combinations of multiple configurations of technical indicators and stocks
- Clean and preprocess the retrieved data.
- Download the cleaned data to a single CSV file or multiple csv files for further analysis.
- Saves the configuration for future use.
  
Get your free API key here http://www.alphavantage.co/support/#api-key and see the technical indicator configurations here https://www.alphavantage.co/documentation/

## Installation
1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/<your-username>/stock-technical-indicators
   ```

2. Navigate to the project directory:
   ```bash
   cd stock-technical-indicators
   ```

3. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage
1. Set up your AlphaVantage API key in the indicators.py file.
   ```python
   apikey = 'Your API key'
   ```
2. Run the indicators.py file:
   ```bash
   python indicators.py
   ```
3. Follow the prompts to input. Below is the example to produce the output/merged/merged_indicators.csv: 
     ```bash
   `Enter the company ticker symbols you want(e.g. LTH,ETD,..)`
   ABNB,ABT
   ```
     ```bash
   `Input the path to your output folder`
   output/merged
   ```
    ```bash
   `Enter the names of technical indicator you want (e.g. WMA,MAMA,..)`
   WMA,MAMA
   ```
    ```bash
   `Do you want to merge the result to one CSV? [Y/n]`
   Y
   ```
    ```bash
   `for WMA, enter the combination of interval e.g. 5,10,..(numeric) or 60min,daily,..(words)
   enter: back to go back to the previous configuration`
   daily
   ```
    ```bash
   `for WMA, enter the combination of time_period e.g. 5,10,..(numeric) or 60min,daily,..(words)
   enter: back to go back to the previous configuration`
   5,10
   ```
    ```bash
   `for WMA, enter the combination of series_type e.g. 5,10,..(numeric) or 60min,daily,..(words)
   enter: back to go back to the previous configuration`
   close
   ```
    ```bash
   `for MAMA, enter the combination of interval e.g. 5,10,..(numeric) or 60min,daily,..(words)
   enter: back to go back to the previous configuration`
   daily
   ```
    ```bash
   `for MAMA, enter the combination of series_type e.g. 5,10,..(numeric) or 60min,daily,..(words)
   enter: back to go back to the previous configuration`
   close
   ```
    ```bash
   `for MAMA, fast_slow_limit_pair in brackets e.g. (0.1,0.1),(0.25,0.25),..
   enter: back to go back to the previous configuration`
   (0.1,0.1),(0.25,0.25)
   ```
    - Once all configuration options for the chosen indicators have been exhausted, the configuration will be saved to indicator_cache.json and will be automatically loaded when the same indicators are selected again.
    - Delete the indicator_cache.json file to build new configurations.
    - Rename indicator_cache_extended.json to indicator_cache.json if you want to use the extended version of the existing configuration.
5. After processing, the cleaned data will be saved as CSV file(s) in the given output path.
  - Columns result output/merged/merged_indicators.csv :
    | time       | Company  | WMA_daily_5_close | WMA_daily_10_close| FAMA_MAMA_daily_close_(0.1, 0.1) | MAMA_daily_close_(0.1, 0.1)| FAMA_MAMA_daily_close_(0.25, 0.25)|MAMA_daily_close_(0.25, 0.25)|
    |------------------|-------------------|------------------|------------------|------------------|------------------|------------------|------------------|
