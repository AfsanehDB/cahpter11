# cahpter11
Copied 1 cells. You can now paste them in this or a different notebook.
forecasting_net_prophet.ipynb
forecasting_net_prophet.ipynb_Notebook unstarred
Forecasting Net Prophet
You’re a growth analyst at MercadoLibre. With over 200 million users, MercadoLibre is the most popular e-commerce site in Latin America. You've been tasked with analyzing the company's financial and user data in clever ways to make the company grow. So, you want to find out if the ability to predict search traffic can translate into the ability to successfully trade the stock.

Instructions

This section divides the instructions for this Challenge into four steps and an optional fifth step, as follows:

Step 1: Find unusual patterns in hourly Google search traffic

Step 2: Mine the search traffic data for seasonality

Step 3: Relate the search traffic to stock price patterns

Step 4: Create a time series model with Prophet

Step 5 (optional): Forecast revenue by using time series models

The following subsections detail these steps.

Step 1: Find Unusual Patterns in Hourly Google Search Traffic
The data science manager asks if the Google search traffic for the company links to any financial events at the company. Or, does the search traffic data just present random noise? To answer this question, pick out any unusual patterns in the Google search data for the company, and connect them to the corporate financial events.

To do so, complete the following steps:

Read the search data into a DataFrame, and then slice the data to just the month of May 2020. (During this month, MercadoLibre released its quarterly financial results.) Use hvPlot to visualize the results. Do any unusual patterns exist?

Calculate the total search traffic for the month, and then compare the value to the monthly median across all months. Did the Google search traffic increase during the month that MercadoLibre released its financial results?

Step 2: Mine the Search Traffic Data for Seasonality
Marketing realizes that they can use the hourly search data, too. If they can track and predict interest in the company and its platform for any time of day, they can focus their marketing efforts around the times that have the most traffic. This will get a greater return on investment (ROI) from their marketing budget.

To that end, you want to mine the search traffic data for predictable seasonal patterns of interest in the company. To do so, complete the following steps:

Group the hourly search data to plot the average traffic by the day of the week (for example, Monday vs. Friday).

Using hvPlot, visualize this traffic as a heatmap, referencing the index.hour as the x-axis and the index.dayofweek as the y-axis. Does any day-of-week effect that you observe concentrate in just a few hours of that day?

Group the search data by the week of the year. Does the search traffic tend to increase during the winter holiday period (weeks 40 through 52)?

Step 3: Relate the Search Traffic to Stock Price Patterns
You mention your work on the search traffic data during a meeting with people in the finance group at the company. They want to know if any relationship between the search data and the company stock price exists, and they ask if you can investigate.

To do so, complete the following steps:

Read in and plot the stock price data. Concatenate the stock price data to the search data in a single DataFrame.

Market events emerged during the year of 2020 that many companies found difficult. But, after the initial shock to global financial markets, new customers and revenue increased for e-commerce platforms. Slice the data to just the first half of 2020 (2020-01 to 2020-06 in the DataFrame), and then use hvPlot to plot the data. Do both time series indicate a common trend that’s consistent with this narrative?

Create a new column in the DataFrame named “Lagged Search Trends” that offsets, or shifts, the search traffic by one hour. Create two additional columns:

“Stock Volatility”, which holds an exponentially weighted four-hour rolling average of the company’s stock volatility

“Hourly Stock Return”, which holds the percent change of the company's stock price on an hourly basis

Review the time series correlation, and then answer the following question: Does a predictable relationship exist between the lagged search traffic and the stock volatility or between the lagged search traffic and the stock price returns?

Step 4: Create a Time Series Model with Prophet
Now, you need to produce a time series model that analyzes and forecasts patterns in the hourly search data. To do so, complete the following steps:

Set up the Google search data for a Prophet forecasting model.

After estimating the model, plot the forecast. How's the near-term forecast for the popularity of MercadoLibre?

Plot the individual time series components of the model to answer the following questions:

What time of day exhibits the greatest popularity?

Which day of the week gets the most search traffic?

What's the lowest point for search traffic in the calendar year?

Step 5 (Optional): Forecast Revenue by Using Time Series Models
A few weeks after your initial analysis, the finance group follows up to find out if you can help them solve a different problem. Your fame as a growth analyst in the company continues to grow!

Specifically, the finance group wants a forecast of the total sales for the next quarter. This will dramatically increase their ability to plan budgets and to help guide expectations for the company investors.

To do so, complete the following steps:

Read in the daily historical sales (that is, revenue) figures, and then apply a Prophet model to the data.

Interpret the model output to identify any seasonal patterns in the company's revenue. For example, what are the peak revenue days? (Mondays? Fridays? Something else?)

Produce a sales forecast for the finance group. Give them a number for the expected total sales in the next quarter. Include the best- and worst-case scenarios to help them make better plans.

Double-click (or enter) to edit

Install and import the required libraries and dependencies
[4]
40s
# Install the required libraries

# Import the required libraries and dependencies

Step 1: Find Unusual Patterns in Hourly Google Search Traffic
The data science manager asks if the Google search traffic for the company links to any financial events at the company. Or, does the search traffic data just present random noise? To answer this question, pick out any unusual patterns in the Google search data for the company, and connect them to the corporate financial events.

To do so, complete the following steps:

Read the search data into a DataFrame, and then slice the data to just the month of May 2020. (During this month, MercadoLibre released its quarterly financial results.) Use hvPlot to visualize the results. Do any unusual patterns exist?

Calculate the total search traffic for the month, and then compare the value to the monthly median across all months. Did the Google search traffic increase during the month that MercadoLibre released its financial results?

Step 1: Read the search data into a DataFrame, and then slice the data to just the month of May 2020. (During this month, MercadoLibre released its quarterly financial results.) Use hvPlot to visualize the results. Do any unusual patterns exist?
[7]
13s
# Upload the "google_hourly_search_trends.csv" file into Colab, then store in a Pandas DataFrame
# Set the "Date" column as the Datetime Index.

# Review the first and last five rows of the DataFrame
# Review the data types of the DataFrame using the info function
# Holoviews extension to render hvPlots in Colab
# Slice the DataFrame to just the month of May 2020

# Use hvPlot to visualize the data for May 2020

Step 2: Calculate the total search traffic for the month, and then compare the value to the monthly median across all months. Did the Google search traffic increase during the month that MercadoLibre released its financial results?

# Calculate the sum of the total search traffic for May 2020

# View the traffic_may_2020 value

# Calcluate the monhtly median search traffic across all months 
# Group the DataFrame by index year and then index month, chain the sum and then the median functions

# View the median_monthly_traffic value

# Compare the seach traffic for the month of May 2020 to the overall monthly median value

traffic_may_2020/median_monthly_traffic

Question: Did the Google search traffic increase during the month that MercadoLibre released its financial results?

Answer: yes there was 8% increase in month of May compaire to other monthes

Step 2: Mine the Search Traffic Data for Seasonality
Marketing realizes that they can use the hourly search data, too. If they can track and predict interest in the company and its platform for any time of day, they can focus their marketing efforts around the times that have the most traffic. This will get a greater return on investment (ROI) from their marketing budget.

To that end, you want to mine the search traffic data for predictable seasonal patterns of interest in the company. To do so, complete the following steps:

Group the hourly search data to plot the average traffic by the day of the week (for example, Monday vs. Friday).

Using hvPlot, visualize this traffic as a heatmap, referencing the index.hour as the x-axis and the index.dayofweek as the y-axis. Does any day-of-week effect that you observe concentrate in just a few hours of that day?

Group the search data by the week of the year. Does the search traffic tend to increase during the winter holiday period (weeks 40 through 52)?

Step 1: Group the hourly search data to plot the average traffic by the day of the week (for example, Monday vs. Friday).[13]2s
# Holoviews extension to render hvPlots in Colab

# Group the hourly search data to plot (use hvPlot) the average traffic by the day of week 

Step 2: Using hvPlot, visualize this traffic as a heatmap, referencing the index.hour as the x-axis and the index.dayofweek as the y-axis. Does any day-of-week effect that you observe concentrate in just a few hours of that day?

# Holoviews extension to render hvPlots in Colab

# Use hvPlot to visualize the hour of the day and day of week search traffic as a heatmap.

Answer the following question:
Question: Does any day-of-week effect that you observe concentrate in just a few hours of that day?

Answer: the search in the first 2 days of the week is higher than the other days.

Step 3: Group the search data by the week of the year. Does the search traffic tend to increase during the winter holiday period (weeks 40 through 52)?

# Holoviews extension to render hvPlots in Colab

# Group the hourly search data to plot (use hvPlot) the average traffic by the week of the year

Answer the following question:
Question: Does the search traffic tend to increase during the winter holiday period (weeks 40 through 52)?

Answer: there is no segnifican increase or decrease during holiday period

Step 3: Relate the Search Traffic to Stock Price Patterns
You mention your work on the search traffic data during a meeting with people in the finance group at the company. They want to know if any relationship between the search data and the company stock price exists, and they ask if you can investigate.

To do so, complete the following steps:

Read in and plot the stock price data. Concatenate the stock price data to the search data in a single DataFrame.

Market events emerged during the year of 2020 that many companies found difficult. But, after the initial shock to global financial markets, new customers and revenue increased for e-commerce platforms. Slice the data to just the first half of 2020 (2020-01 to 2020-06 in the DataFrame), and then use hvPlot to plot the data. Do both time series indicate a common trend that’s consistent with this narrative?

Create a new column in the DataFrame named “Lagged Search Trends” that offsets, or shifts, the search traffic by one hour. Create two additional columns:

“Stock Volatility”, which holds an exponentially weighted four-hour rolling average of the company’s stock volatility

“Hourly Stock Return”, which holds the percent change of the company's stock price on an hourly basis

Review the time series correlation, and then answer the following question: Does a predictable relationship exist between the lagged search traffic and the stock volatility or between the lagged search traffic and the stock price returns?

Step 1: Read in and plot the stock price data. Concatenate the stock price data to the search data in a single DataFrame.

# Upload the "mercado_stock_price.csv" file into Colab, then store in a Pandas DataFrame
# Set the "date" column as the Datetime Index.

# View the first and last five rows of the DataFrame

# Holoviews extension to render hvPlots in Colab

# Use hvPlot to visualize the closing price of the df_mercado_stock DataFrame

# Concatenate the df_mercado_stock DataFrame with the df_mercado_trends DataFrame
# Concatenate the DataFrame by columns (axis=1), and drop and rows with only one column of data

# View the first and last five rows of the DataFrame

Step 2: Market events emerged during the year of 2020 that many companies found difficult. But, after the initial shock to global financial markets, new customers and revenue increased for e-commerce platforms. Slice the data to just the first half of 2020 (2020-01 to 2020-06 in the DataFrame), and then use hvPlot to plot the data. Do both time series indicate a common trend that’s consistent with this narrative?

# For the combined dataframe, slice to just the first half of 2020 (2020-01 through 2020-06) 

# View the first and last five rows of first_half_2020 DataFrame

# Holoviews extension to render hvPlots in Colab

# Use hvPlot to visualize the close and Search Trends data
# Plot each column on a separate axes using the following syntax

Answer the following question:
Question: Do both time series indicate a common trend that’s consistent with this narrative?

Answer: there was a gap in both data fram in March 2020 other than that the tow datafram are not showing same patern. search data fram has a repiting patern each week it increach during the day.

Step 3: Create a new column in the DataFrame named “Lagged Search Trends” that offsets, or shifts, the search traffic by one hour. Create two additional columns:
“Stock Volatility”, which holds an exponentially weighted four-hour rolling average of the company’s stock volatility

“Hourly Stock Return”, which holds the percent change of the company's stock price on an hourly basis
# Create a new column in the mercado_stock_trends_df DataFrame called Lagged Search Trends
# This column should shift the Search Trends information by one hour

# Create a new column in the mercado_stock_trends_df DataFrame called Stock Volatility
# This column should calculate the standard deviation of the closing stock price return data over a 4 period rolling window

# Holoviews extension to render hvPlots in Colab

# Use hvPlot to visualize the stock volatility

Solution Note: Note how volatility spiked, and tended to stay high, during the first half of 2020. This is a common characteristic of volatility in stock returns worldwide: high volatility days tend to be followed by yet more high volatility days. When it rains, it pours.

# Create a new column in the mercado_stock_trends_df DataFrame called Hourly Stock Return
# This column should calculate hourly return percentage of the closing price

# View the first and last five rows of the mercado_stock_trends_df DataFrame

Step 4: Review the time series correlation, and then answer the following question: Does a predictable relationship exist between the lagged search traffic and the stock volatility or between the lagged search traffic and the stock price returns?

# Construct correlation table of Stock Volatility, Lagged Search Trends, and Hourly Stock Return

Answer the following question:
Question: Does a predictable relationship exist between the lagged search traffic and the stock volatility or between the lagged search traffic and the stock price returns?

Answer: # there is a negative corolation between lagged search and stock volatility,but the corrolation between lagged search traffic and stock price is positive but in a smaller scale

Step 4: Create a Time Series Model with Prophet
Now, you need to produce a time series model that analyzes and forecasts patterns in the hourly search data. To do so, complete the following steps:

Set up the Google search data for a Prophet forecasting model.

After estimating the model, plot the forecast. How's the near-term forecast for the popularity of MercadoLibre?

Plot the individual time series components of the model to answer the following questions:

What time of day exhibits the greatest popularity?

Which day of the week gets the most search traffic?

What's the lowest point for search traffic in the calendar year?

Step 1: Set up the Google search data for a Prophet forecasting model.

# Using the df_mercado_trends DataFrame, reset the index so the date information is no longer the index

# Label the columns ds and y so that the syntax is recognized by Prophet

# Drop an NaN values from the prophet_df DataFrame

# View the first and last five rows of the mercado_prophet_df DataFrame

# Call the Prophet function, store as an object

# Fit the time-series model.

# Create a future dataframe to hold predictions
# Make the prediction go out as far as 2000 hours (approx 80 days)

# View the last five rows of the future_mercado_trends DataFrame

# Make the predictions for the trend data using the future_mercado_trends DataFrame

# Display the first five rows of the forecast_mercado_trends DataFrame

Step 2: After estimating the model, plot the forecast. How's the near-term forecast for the popularity of MercadoLibre?

# Plot the Prophet predictions for the Mercado trends data

Answer the following question:
Question: How's the near-term forecast for the popularity of MercadoLibre?

Answer: looks like popularity of the merdacolibre is decreasing

Step 3: Plot the individual time series components of the model to answer the following questions:
What time of day exhibits the greatest popularity?

Which day of the week gets the most search traffic?

What's the lowest point for search traffic in the calendar year?

# Set the index in the forecast_mercado_trends DataFrame to the ds datetime column

# View the only the yhat,yhat_lower and yhat_upper columns from the DataFrame

Solutions Note: yhat represents the most likely (average) forecast, whereas yhat_lower and yhat_upper represents the worst and best case prediction (based on what are known as 95% confidence intervals).
# Holoviews extension to render hvPlots in Colab

# From the forecast_mercado_trends DataFrame, use hvPlot to visualize
#  the yhat, yhat_lower, and yhat_upper columns over the last 2000 hours 

# Reset the index in the forecast_mercado_trends DataFrame

# Use the plot_components function to visualize the forecast results 
# for the forecast_canada DataFrame 

Answer the following questions:
Question: What time of day exhibits the greatest popularity?

Answer: late night between 8:30 pm to 3:30 am

Question: Which day of week gets the most search traffic?

Answer: Tuseday has more traffic

Question: What's the lowest point for search traffic in the calendar year?

Answer: in November it is getting close to -4

Step 5 (Optional): Forecast Revenue by Using Time Series Models
A few weeks after your initial analysis, the finance group follows up to find out if you can help them solve a different problem. Your fame as a growth analyst in the company continues to grow!

Specifically, the finance group wants a forecast of the total sales for the next quarter. This will dramatically increase their ability to plan budgets and to help guide expectations for the company investors.

To do so, complete the following steps:

Read in the daily historical sales (that is, revenue) figures, and then apply a Prophet model to the data. The daily sales figures are quoted in millions of USD dollars.

Interpret the model output to identify any seasonal patterns in the company's revenue. For example, what are the peak revenue days? (Mondays? Fridays? Something else?)

Produce a sales forecast for the finance group. Give them a number for the expected total sales in the next quarter. Include the best- and worst-case scenarios to help them make better plans.

Step 1: Read in the daily historical sales (that is, revenue) figures, and then apply a Prophet model to the data.
[37]
8s
# Upload the "mercado_daily_revenue.csv" file into Colab, then store in a Pandas DataFrame
# Set the "date" column as the DatetimeIndex
# Sales are quoted in millions of US dollars

# Holoviews extension to render hvPlots in Colab

# Use hvPlot to visualize the daily sales figures 

# Apply a Facebook Prophet model to the data.

# Set up the dataframe in the neccessary format:
# Reset the index so that date becomes a column in the DataFrame

# Adjust the columns names to the Prophet syntax

# Visualize the DataFrame

# Create the model

# Fit the model

# Predict sales for 90 days (1 quarter) out into the future.

# Start by making a future dataframe

# Display the last five rows of the future DataFrame

# Make predictions for the sales each day over the next quarter

# Display the first 5 rows of the resulting DataFrame

Step 2: Interpret the model output to identify any seasonal patterns in the company's revenue. For example, what are the peak revenue days? (Mondays? Fridays? Something else?)

# Use the plot_components function to analyze seasonal patterns in the company's revenue

Answer the following question:
Question: For example, what are the peak revenue days? (Mondays? Fridays? Something else?)

Answer: # Wednesday is pick revenue day

Step 3: Produce a sales forecast for the finance group. Give them a number for the expected total sales in the next quarter. Include the best- and worst-case scenarios to help them make better plans.

# Plot the predictions for the Mercado sales
mercado_sales_prophet_model.plot(mercado_sales_prophet_forecast)

# For the mercado_sales_prophet_forecast DataFrame, set the ds column as the DataFrame Index

# Display the first and last five rows of the DataFrame

# Produce a sales forecast for the finance division
# giving them a number for expected total sales next quarter.
# Provide best case (yhat_upper), worst case (yhat_lower), and most likely (yhat) scenarios.
# Create a forecast_quarter Dataframe for the period 2020-07-01 to 2020-09-30
# The DataFrame should include the columns yhat_upper, yhat_lower, and yhat

# Update the column names for the forecast_quarter DataFrame-
# to match what the finance division is looking for 
mercado_sales_forecast_quarter = mercado_sales_forecast_quarter.rename(
 
# Review the last five rows of the DataFrame

# Displayed the summed values for all the rows in the forecast_quarter DataFrame

Based on the forecast information generated above, produce a sales forecast for the finance division, giving them a number for expected total sales next quarter. Include best and worst case scenarios, to better help the finance team lan.
Answer: lowest expected sale is 887.39 and highest expected sale is 1051.14
