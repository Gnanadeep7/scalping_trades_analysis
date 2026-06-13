scalping_trades_analysis
This project analyzes XAUUSD trading data, focusing on realized Profit/Loss, trade duration, and daily performance metrics. It examines price attributes, risk/reward ratios and reveals the best trading times. Histograms, Box plots, Coloured daily PnL calendars give insight into the trade characteristics.

Project Progress & Analysis Summary

It describes the chronological process performed in exploratory data analysis (EDA) and the data preparation of the XAUUSD trading data set, and mentions the important technical progress made at each step.

1. Loading Data & Initial Inspection.
Action: Converted raw xauusd.csv data to Pandas DataFrame. Performed basic structure and statistical tests, such as df.head(), df.info(), and df.describe(), of the data frame.
Achievement: Successfully identified the nature of the data set, the type of data and missing/null data values that needed to be cleaned.

2. Data Cleaning & Preparation**
Action: Converted temporal columns (dateStart and dateEnd) to normal datetime objects.
    Eliminated the wholly empty tags column to reduce memory usage of dataframe.
    Replaced missing values of maxTP in the target column with the median of maxTP.
Achievement: Produced a clean and high-quality baseline data set that was fully ready for feature engineering and downstream modeling.

3. Feature Engineering**
Created analytical variables from existing ones for:
    tradeDuration: min based on dateEnd - dateStart.
    hourStart: Extracted the hour part from dateStart.
Achievement: Identified important time-based metrics for determining behavioral trends and hourly performance.

Exploratory Data Analysis (EDA) & Data Visualizations
Created distribution histograms for rPnL, tradeDuration, transaction volume (amount, amountClosed), risk/reward parameters, and price (entryPrice, initialSL, maxTP, idealTP, avgClosePrice).
    Used box plots to assess the variance in the rPnL based on buy/sell direction.
    A few time-series line charts were created to show the currentRealizedBalance over time.
Achievement: Statistically identified properties, identified potential properties, and mapped out the trend of macro account balance growth.

Advanced Trade Segment Analysis
Action: Low-Risk Segment: Filtered and evaluated “low-risk” trades – trades whose rPnL is less than 30% in absolute value – with analyzing the distribution of their durations and finding specific winning windows (e.g. for this specific group of “low-risk” trades 100% of the profitable ones are of 5 AM and 6 PM duration).
    Generated separate volume and PnL distributions for high risk trades (|rPnL| > $100).
    Created feature correlation heatmap, multi-segment scatter plots (rPnL vs tradeDuration), hourly perform box plots, custom dual colored bar charts (green for winning days and red for losing days).
    Created a daily max drawdown metrics plot to properly preserve drawdowns to account equity over time.
Achievement: Identified actionable, granular information that connects particular times of day, risk levels and time in game to overall win rates.

6. Refinements & Code Optimization**
Action:Eliminated syntax errors and updated syntax to meet the requirements of modern libraries in script execution blocks. This involved fixing a FutureWarning from Seaborn with properties on the daily net profit plot:
    `sns.barplot(..., hue='tradeDate', legend=False)`
* **Achievement:** Improved the robustness of the script code base, ensuring that there are no warnings and no future problems with the script base due to deprecations in the packages.
