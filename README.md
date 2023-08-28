![image](https://github.com/dylan860/Forecasting_Net_Prophet/assets/127907809/9126bd04-e014-4b82-b78c-df978ab2d966)![image](https://github.com/dylan860/Forecasting_Net_Prophet/assets/127907809/8ee38264-6454-4ae9-8cec-5468089fbf3b)

# Module-11-Challenge

# Forecasting_Net_Prophet

# Overview
The objective of this Google Colab program is to perform a financial analysis on e-commerce company MercadoLibre. The purpose of the main body of the program is in fact to see if predictions in search traffic can be found, and if so, be a proxy to successfully trade the underlying stock.

# Features
The main tasks outlined in this project will include:

1.) Step 1: Installing and importing the required libraries and dependencies including Pystan, (Facebook) Prophet, hvPlot, Holoviews, datetime, and Matplotlib.

1b.) Step 1b: Finding patterns in the hourly Google Search traffic that may be of use. Essentially, one of the main sub-tasks of the program is to see if Google Search traffic has any link/correlation to financial events at the company. Or, alternatively, is the search traffic data just representative of random noise. The data here is first read from a locally sourced file and put into a Panda's DataFrame. Afterwards, the data is then sliced and analyzed for the month of May 2020 (coinciding with the release of MercadoLibre's quarterly financial results). HvPlots is utilized to visually represent the results. The data set is also used to calculate the total search traffic for the month and then compared to the monthly median across all months. (See Figure 1 & 2)

2.) Step 2: Next, hourly search traffic data was isolated and analyzed, per marketing department instructions. The goal was to predict interest in the company & platform at any time of day. The theory being, that they can more efficiently advertise and get a higher ROI from their marketing budget deficit if they can pinpoint the optimal advertising windows. This is achieved by grouping the hourly search data and plotting the average traffic by the day of the week. This was done by compartmentalizing search traffic volume into indexed 'hours' [index.hour] and indexed 'days of the week' [index.dayofweek] as separate variable lists. Using hvPlot, they were plotted against one another in order to form a heatmap that compared search traffic during each day of the week as a function of hours of the day. Additionally, search traffic trends were found to be in an increasing uptrend through the last quarter of the year prior to Christmas, accompanied with a sharp drop afterwards. Lulls in traffic volume appear to occur right after Christmas, and during week 34 of the year. (See Figure 3, 4 & 5)

3.) Step 3: Afterwards, the relationship between search data volume and the company's stock price is analyzed to check for correlation. Stock price data, once again, is read in using panda's read_csv and the stock price data is plotted (See Figure 6). The stock price data and search data (dataframe for Google Trends created earlier) is then concatenated to a single dataframe. The time series indexing of this dataframe was then sliced between 2020-01 and 2020-06 (in order to analyze the first half of the year during and after the initial onslaught of the COVID-19 pandemic to see how e-commerce companies adapted & responded to the evolving market environment). This is then again plotted as a visual comparison chart (See Figure 7). A new column in the dataframe called 'Lagged Search Trends' that offsets search traffic by one hour is added. Ontop of this, an additional two columns of data are added to the dataframe to capture 'Stock Volatility' and 'Hourly Stock Return' (percentage of change in the company stock price on an hourly basis). (See Figure 8)

4.) Step 4: A time series model that analyzes & forecasts patterns in the hourly search data is then created. A Prophet model is first instantiated with the Google Search data set to said model. Estimations/predictions are made with the model framework & the forecast is then plotted in order to predict the near-term popularity of MercadoLibre. (See Figure 9). Individual time series components of the model are also produced for analysis. (See Figure 10)

5.) Step 5: The next portion of the program involves assisting the finance group with forecasting the total sales for the next quarter in order to give some guidance in terms of budget planning and to guide expectations for company investors. Here, historical sales revenue (in millions USD) is read in as a dataframe and then applied to another instantiated Prophet model in order to forecast future probable trends. (See Figure 11 & 12)

# Data Analysis Results and Observations

MercadoLibre - Google Search Trend Data for the Month of May 2020
![image](https://github.com/dylan860/Forecasting_Net_Prophet/assets/127907809/90562371-5a86-4389-b62d-784a9ffad783)
Figure 1. MercadoLibre Google Search Trend data for the month of May 2020.

# MercadoLibre - Monthly Median Search Traffic Across All Months
![image](https://github.com/dylan860/Forecasting_Net_Prophet/assets/127907809/a23bea82-8e6a-47e0-a9d7-14133b8da3e4)
Figure 2. The monthly median search traffic across all months is calculated by creating a dataframe whereby group indexing using the mean monthly values is calculated view pandas. Here, we can see that the search traffic did in fact increase during the month that MercadoLibre released its financial results - and appears to have in fact broken the decreasing trend of the past 3 years (leading up to and after May, 2020).

# MercadoLibre - Average Traffic By Day of the Week
![image](https://github.com/dylan860/Forecasting_Net_Prophet/assets/127907809/75b3eab3-b399-4588-b43f-9e8e47d2d7b1)
Figure 3. MercadoLibre search traffic displaying maximum search traffic volume during Tuesday's [*actually normalized to Monday's - see argument outlined below], followed by Wednesday in a decreasing trend as the week progresses.

# MercadoLibre - Hour of Day vs Day of the Week Search Traffic Volume






