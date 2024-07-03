# S&P 500 Stock Market Perdictions

Summer 2024 Data Science Project  
Group Members:   
Junaid Chaudhry, Elliott Eager, Keshav Nayyar and Francis Fynnwilliams


  
# Introduction

The S&P 500, a benchmark index comprising 500 of the largest publicly traded companies in the United States, serves as a crucial indicator of the overall health of the U.S. stock market and economy. For our Summer 2024 Data Science Project, we aim to leverage historical S&P 500 stock market data to predict future stock prices and analyze the performance of different sectors within the index. By employing advanced machine learning techniques, we seek to answer two primary questions: "Can we accurately predict future stock prices based on historical data?" and "How do different sectors within the S&P 500 compare in terms of performance over time?"

Answering these questions holds significant importance for both investors and analysts. Accurate stock price predictions can inform investment strategies, helping individuals and institutions make more informed decisions and potentially increase their returns. Additionally, understanding sector performance can provide insights into economic trends, guiding policy-making and investment allocations. By exploring these questions, our project not only showcases the practical applications of data science in finance but also contributes valuable knowledge to the field of financial analytics.

# Data Curation

The dataset used in this project is sourced from Kaggle. It contains historical stock market data for various companies listed in the S&P 500 index over a five-year period. The data includes daily records of stock prices (open, high, low, close), trading volume, and the stock ticker symbol. This dataset provides a comprehensive view of the stock performance for companies within the S&P 500, making it suitable for analyzing trends, predicting future prices, and comparing sector performances. A large data set like this (619,000 rows) gives us the perfect playing field to do some machine learning! But first we need to transform the data to meet our needs. 

### Transforming the data set 
- Inorder to properly analysize our data set we have to tranform the data so it is ready for analysis. We first import all of our necassary imports to handle the data

<img width="750" alt="Screenshot 2024-06-29 at 5 19 50 PM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/e31ca6ee-e186-40b1-8149-8978b8eaa891">

- Next we load the data set. The data set was to large to upload directly to Google Collab so it was pushed to github and then pulled using a url. 

<img width="864" alt="Screenshot 2024-06-29 at 5 23 02 PM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/1d071ab6-3367-4783-a94c-392baddd5c0d">

 - After loading in the data we wanted to know if there were any missing data point. Missing data points can alter our machine learning results and give inaccurate results. First we checked for the amount of missing values per column to see if there were any missing data points. Then we dropped those rows that contained missing data points.
   
<img width="1368" alt="Screenshot 2024-06-29 at 5 27 32 PM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/7124baff-a0bd-4177-83eb-675e39e91c6e">

- Next we gathered all of the unique ticker symbols in the data set. The S&P 500 has a rigourous set of fincial rules that determine if a componay can be a part of the S&P 500 or not. This means that every year certain companies are added and taken out based on thier performance. For our project we only wanted to analyze componies that are currently in the S&P 500. The way that we were able to determine what company to remove was to look at the current 500 ticker symbols and cross reerence them with the 505 unique ticker symbols in our data set.
  
![Screenshot 2024-06-29 at 5 34 50 PM](https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/cb668eda-e2b8-407b-a77e-32a5dbadc713)

- Removing tickers that are not currenlty in the S&P 500

![Screenshot 2024-06-29 at 5 35 42 PM](https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/abb43804-c165-4f63-977e-b084270aa14e)


# Exploratory Data Analysis
After cleaning the data and getting it ready for analysis we moved on to do some prelimanary data analysis. This portion of the data analysis was mostly geared towards figuring out som large scale statisitcs about the data set. What were the max and min values of all of the coloumns, the standard deviations, and the mean. This portion was really just for us to understand what the scale of the data set was and to look for any large variations in the data that might throw our primary analysis off course. 
<img width="702" alt="Screenshot 2024-07-03 at 10 56 39 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/cc62176a-4cd7-471e-acdf-b306ff06da8e">

We also calculated the standard deefviations of each individual stock, this would help us understand if a stock had low or high volatility 

<img width="681" alt="Screenshot 2024-07-03 at 11 05 56 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/feb87c4a-8240-41a9-ad0f-ad0dd58bb935">

<img width="583" alt="Screenshot 2024-07-03 at 11 06 13 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/b1e300a8-333a-4c3c-ad54-24542195d6ba">

Through this we were able to make the following conclusions:

#### Descriptive Statistics
- Mean Prices: The average opening, high, low, and close prices are roughly similar, hovering around $83, indicating consistent trading ranges.

- Standard Deviation: There is a high standard deviation in the price data, suggesting significant variability in stock prices, which could be due to stock volatility or differences across various stocks.

- Volume: Trading volume shows a wide range, with a mean of about 4.32 million shares traded per day. The maximum trading volume recorded is extraordinarily high at over 618 million shares.

#### Feature Representation
- Dates: The dataset covers 1,259 unique dates.

- Stock Names (Tickers): There are 500 different stock tickers represented, implying the dataset spans a broad array of companies.

- Price Points: The dataset contains a large number of unique open, high, low, and close values, indicating a detailed and comprehensive stock price record.

## Data Analysis through testing
Along with our prelimanary data exploraiton we employed some testing techniques that would help us gather greater understanding of the data set for our primary analysis. 

### Chi Squared Test
The main focus of a chi squared test is to to determine if a difference between observed data and expected data is due to chance, or if it is due to a relationship between the variables in our data. Our hypothesis for this test was "Is there a  statistically significant association between the sectors and volatility?"

<img width="1466" alt="Screenshot 2024-07-03 at 11 12 23 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/4e93008f-ab06-45a8-9257-c075ef294912">

#### Interpertation of Chi Squared Results
<img width="1234" alt="Screenshot 2024-07-03 at 11 16 07 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/4a025c82-8b4c-4a1c-ba66-fd147e97772b">

-The Chi-Square Statistic is approximately 20.508. This value measures the difference between the observed frequencies in the contingency tables and the frequencies expected if sectors and volatility categories were independent.A higher value indicates a greater divergence from independence.

-P-Value (0.05806): This p-value tests the null hypothesis that sector and volatility classification are independent of each other.

-Since the p-value is greater than 0.05, it suggests that there is not enough evidence to reject the null hypothesis at the 5% significance level. Therefore, it is concluded that there is no statistically significant association between the sectors and volatility classes, although it's very close to the threshold.

#### Sector Specific Observations
- Consumer Discretionary, Finance, and Industrial have relatively similar median volatilities with tighter IQRs, indicating less variation within the middle 50% of data points. But, Consumer Discretionary has notable lower outliers. Energy and Healthcare show a higher median volatility compared to the others, with the Energy sector displaying more variability as evidenced by longer whiskers.

- Consumer Staples and Technology have both upper and lower outliers, with Technology displaying a wide range. This may suggest higher volatility in stock prices within these sectors compared to others like Finance. Sectors like Technology and Energy show larger variability in stock volatility, possibly indicating a more dynamic market environment or higher risk. But in contrast, Finance and Industrial show more stability.

- The presence of outliers in sectors like Consumer Discretionary and Technology could be due to specific events or conditions affecting certain companies within those sectors, meriting further investigation to understand the causes of these extreme values.Investors might use this information to assess risk and make decisions about diversifying their portfolios.



### Z - Tests
The Z-test is used to determine if there is a significant difference between the means of two groups or between a sample mean and a known population mean. The Z-value measures the number of standard deviations a data point is from the population mean, indicating the magnitude of difference. The p-value indicates the probability that the observed difference occurred by chance; a low p-value (typically < 0.05) suggests that the difference is statistically significant.


<img width="761" alt="Screenshot 2024-07-03 at 11 23 58 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/f9cc0075-2d31-4900-bcac-0e9097799154">

#### Interpertation of z - test results 

<img width="1072" alt="Screenshot 2024-07-03 at 11 25 45 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/89a64ec9-21fa-4eb1-b434-6a8ea09aeb34">


###### Sector-Specific Results Analysis:

- Consumer Discretionary
Z-Statistic: 2.746715 P-Value: 0.006020 Interpretation: This sector performed significantly better than average, with strong statistical evidence (p-value < 0.05) supporting this performance.

- Finance
Z-Statistic: -0.886539 P-Value: 0.375327 Interpretation: This sector underperformed relative to the average, but the result is not statistically significant (p-value > 0.05), indicating the performance could be due to chance.

- Industrial
Z-Statistic: -0.226402 P-Value: 0.820889 Interpretation: This sector also underperformed, but the result is not statistically significant, suggesting the performance could be random.

- Energy
Z-Statistic: 0.882831 P-Value: 0.377328 Interpretation: The sector slightly outperformed the average, but the result is not statistically significant, indicating the performance could be due to chance.

- Healthcare
Z-Statistic: -0.370419 P-Value: 0.711070 Interpretation: This sector underperformed, but the result is not statistically significant, suggesting randomness in the performance.

- Consumer Staples
Z-Statistic: 2.907144 P-Value: 0.003647 Interpretation: This sector performed significantly better than average, with strong statistical evidence (p-value < 0.05) supporting this performance.

- Technology
Z-Statistic: -0.786593 P-Value: 0.431520 Interpretation: This sector underperformed, but the result is not statistically significant, indicating the performance could be due to chance.

Overall, Consumer Discretionary and Consumer Staples sectors show notable outperformance based on historical data, whereas other sectors do not show significant deviations from the average performance.


### ANOVA Test 
The ANOVA (Analysis of Variance) test is used to determine if there are statistically significant differences between the means of three or more independent groups. The F-value in ANOVA measures the ratio of variance between the group means to the variance within the groups, indicating the extent of difference among group means. The p-value indicates the probability that the observed differences among group means occurred by chance; a low p-value (typically < 0.05) suggests that the differences are statistically significant.

<img width="993" alt="Screenshot 2024-07-03 at 11 35 30 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/3d8af463-d12b-4f78-9ecb-3d1b022f529a">

<img width="862" alt="Screenshot 2024-07-03 at 11 36 19 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/582562c9-9246-4c0c-b4ad-3111ae698bb5">

#### Interpertation of the ANOVA testing
- The F-statistic value is 0.7327. With this F-statistic, we can expect greater variability between group means relative to the variability within the groups.

- The p-value is 0.6231. This value indicates the probability of observing the data, or something more extreme, if the null hypothesis (that all group means are equal) is true.

- Statistical Significance: Since the p-value (0.6231) is more than the common significance level of 0.05, we fail to reject the null hypothesis. This suggests that there is not a statistically significant difference in the daily returns across different sectors.

- The failure of rejection of the null hypothesis implies that not all sectors have the same mean daily return. This finding strongly suggests that sector-specific factors likely influence the stock returns, and these factors cause significant differences between the average returns of different sectors.

  
<img width="1082" alt="Screenshot 2024-07-03 at 11 40 42 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/558fd0a0-98ca-4b75-b336-458e1f5fe281">

##### Sector Analysis 
Finance: This sector shows a compact distribution of returns around the median, indicating less volatility in daily returns. However, there are several outliers, particularly on the negative side.

Industrial: Similar to finance, industrial has a narrow IQR but fewer outliers. This suggests more stable returns but with occasional extremes.

Consumer Discretionary: Exhibits a slightly higher spread in returns (wider box), indicating more variability in daily returns. There are outliers on both the high and low ends.

Energy: Displays a very tight IQR with several high and low outliers, suggesting that while most daily returns are close to the median, extreme values are not uncommon.

Healthcare: Similar pattern to energy, with a tight IQR and outliers. This sector might experience occasional spikes or drops in returns.

Consumer Staples: Shows moderate variability with few outliers, indicating relatively stable returns.

Technology: This sector has one of the widest IQRs, reflecting significant day-to-day variation in returns. Also, there are many outliers, particularly on the positive side, suggesting the potential for high returns.

# Primary Analysis 

# Visualization

# Insights and Conclusions






