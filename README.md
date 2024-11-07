# Foreign Exchange Rate Analysis and Prediction

This project is designed to analyze and predict the exchange rate between USD and MXN (Mexican Peso) using data from the Federal Reserve Economic Data (FRED) API. The project explores multiple economic indicators, performs a linear regression analysis to observe trends, and visualizes the results.

## User Story

Meet **Carlito**, a world traveler planning an exciting trip to Mexico in two weeks. Carlito wants to make the most of his budget and is curious about the USD to MXN exchange rate and potential shifts in the near future.

Our mission is to analyze historical exchange rate data, consider major economic events, and apply predictive models to forecast trends. With these insights, our team of seasoned analysts aims to help Carl make informed decisions on when to exchange his money for the best possible rate.


## Table of Contents
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Installation](#installation)
- [Usage](#usage)
- [Methodology](#methodology)
- [Results](#results)
- [Future Work](#future-work)
- [License](#license)


## Project Overview
The primary goal of this project is to analyze the USD to MXN exchange rate using historical data and economic indicators. The analysis includes:
- Collecting data on various economic indicators from FRED.
- Calculating the relationship between the exchange rate and these indicators.
- Performing a linear regression analysis to predict future trends.
- Visualizing the data with regression lines to understand historical trends.

## Data Sources
The data is sourced from [FRED (Federal Reserve Economic Data)](https://fred.stlouisfed.org/), a reliable government data source that provides economic data, including:
- **Exchange Rate (DEXMXUS)** - USD to MXN exchange rate
- **US Federal Funds Rate (FEDFUNDS)** - Benchmark interest rate set by the US Federal Reserve
- **US 90-Day T-bill Rate (TB3MS)** - Interest rate on 90-day treasury bills
- **Mexico 90-Day T-bill Rate (INTGSTMXM193N)** - Interest rate on Mexican 90-day treasury bills
- **US Real GDP (GDPC1)** - Inflation-adjusted Gross Domestic Product of the US
- **Mexico Real GDP (NGDPRSAXDCMXQ)** - Inflation-adjusted Gross Domestic Product of Mexico
- **Oil Prices (DCOILWTICO)** - West Texas Intermediate (WTI) crude oil prices

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/wrdhall3/fx-rate-project.git
   cd fx-rate-project


## Usage

### Run the Notebook
Open and run the `retrieve_fx_data.ipynb` notebook, which contains all code for data retrieval, analysis, and visualization. Ensure that the environment is configured correctly with the required dependencies.

### Data Retrieval and Analysis
- The notebook first retrieves the data from FRED using the API key.
- The economic indicators are then combined into a single DataFrame, with dates aligned to ensure consistency across all time series.

### Plotting and Regression Analysis
- The notebook provides visualization for each economic indicator over time.
- A linear regression model is fitted to the USD to MXN exchange rate to show trends and predict future values.

## Methodology

### Data Collection
- Historical data for the exchange rate and economic indicators are fetched from FRED using the `fredapi` package.
- Each time series is aligned to a common date range for accurate analysis.

### Preprocessing
- The data is resampled to a monthly frequency where necessary to align the time series.
- Missing values are forward-filled to avoid gaps due to holidays or data unavailability.

### Linear Regression
- Linear regression analysis is performed on the exchange rate data to compute the best-fit line \( y = mx + b \).
- The index (date) is converted to a numerical format (days since start) to fit the regression model.

### Visualization
- Each economic indicator is plotted over time.
- The regression line for the USD to MXN exchange rate is plotted to show the trend and potential future values.

## Results

### Key Findings
- The regression analysis provides insight into the trend of the USD to MXN exchange rate over time.
- Economic indicators such as the Fed Funds Rate, T-bill rates, and oil prices show varying degrees of correlation with the exchange rate.

### Visualizations
- **Interactive Time Series Line Plots**: Allow exploration of each economic indicator over time, providing flexibility to zoom in on specific periods and identify key trends.
- **Scatter Plot with Regression Line**: Display the USD to MXN exchange rate with an overlaid regression line, using Seaborn, to highlight overall trends and any linear relationship.
- **Seaborn Line Plots with Major Events**: Annotated line plots showing significant economic events that impacted the USD to MXN exchange rate, offering historical context to visualize how major events influenced the rate.


### Statistical Summary
- **Slope and Intercept:** Key components of the regression line \( y = mx + b \).
- **R-squared Value:** Indicates the goodness of fit for the linear regression model.
- **P-value and Standard Error:** Provide statistical information on the reliability of the regression.

## Future Work

### Enhanced Model Complexity
While Prophet is already employed for time series forecasting, additional models could complement Prophet and further refine predictions:

- **LSTM (Long Short-Term Memory Networks):** LSTMs, a type of recurrent neural network, excel at capturing long-term dependencies in sequential data. By incorporating LSTM models, we could detect more complex temporal patterns in exchange rates and their relationship with economic indicators, potentially enhancing forecast accuracy alongside Prophet.
- **ARIMA (AutoRegressive Integrated Moving Average):** ARIMA models can capture trend and seasonality in time series data differently than Prophet, making them suitable for comparative analysis or ensemble modeling.
- **Ensemble Models:** Combining Prophet with ARIMA and/or LSTM models could create a more robust forecasting approach. An ensemble model can leverage the strengths of each component model and average their predictions to reduce overfitting and improve overall accuracy.

These enhancements would be evaluated based on metrics like Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE) to identify their contribution to improved prediction accuracy.

### Additional Economic Indicators
Including more economic indicators can expand the model's contextual scope and potentially improve forecasting by capturing broader economic influences on the exchange rate. Indicators to consider:

- **Inflation Rates:** Both US and Mexican inflation rates impact the purchasing power of each currency and can be an important variable in exchange rate prediction.
- **Employment and Unemployment Rates:** Employment data often correlates with economic health and exchange rate strength. Including these rates might reveal valuable trends.
- **Trade Balance and Current Account Balance:** These indicators provide a view of foreign exchange demand and supply in each country, which can directly influence exchange rates.
- **Interest Rate Differentials Across Durations:** Analyzing differences between US and Mexican interest rates, especially in different durations, may enhance the understanding of short-term currency movements.
- **Commodity Prices (e.g., Gold, Silver):** Including commodity prices could offer an additional dimension of analysis, especially given the inverse relationship these often have with USD value.

Each new indicator would require reliable data sourcing, alignment with the existing dataset, and testing to ensure it adds predictive value.

### Automated Updates
Implementing an automated data and model update pipeline will allow the model to remain current with minimal intervention, ensuring timely predictions and insights:

- **Automated Data Collection:** Set up scheduled API calls to retrieve the latest data from FRED and other sources to keep the dataset continuously up-to-date.
- **Preprocessing and Feature Engineering Pipeline:** Automate data cleaning, transformation, and feature engineering steps to maintain consistency in the dataset as new data is added.
- **Automated Model Retraining:** Schedule regular Prophet model retraining or update triggers based on new data availability (e.g., monthly or quarterly) to keep the model’s predictions aligned with the latest trends.
- **Performance Monitoring and Alerts:** Implement a system to monitor model performance over time, with notifications for significant changes in forecast accuracy. This can help indicate when model tuning or additional data adjustments are needed.
- **Real-Time Forecast Dashboard:** Deploy a dashboard that presents real-time updates from Prophet, along with any ensemble model outputs, for accessible, ongoing insights into forecast trends.

An automated pipeline will ensure the model stays accurate and scalable, making it useful for real-time analysis and operational deployment.


## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

