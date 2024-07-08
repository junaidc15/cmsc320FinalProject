# S&P 500 Stock Market Predictions

Summer 2024 Data Science Project  
Group Members:   
Junaid Chaudhry, Elliott Eager, Keshav Nayyar, and Francis Fynnwilliams


  
# Introduction

The S&P 500, a benchmark index comprising 500 of the largest publicly traded companies in the United States, serves as a crucial indicator of the overall health of the U.S. stock market and economy. For our Summer 2024 Data Science Project, we aim to leverage historical S&P 500 stock market data to predict future stock prices and analyze the performance of different sectors within the index. By employing advanced machine learning techniques, we seek to answer two primary questions: "Can we accurately predict future stock prices based on historical data?" and "How do different sectors within the S&P 500 compare in terms of performance over time?"

Answering these questions holds significant importance for both investors and analysts. Accurate stock price predictions can inform investment strategies, helping individuals and institutions make more informed decisions and potentially increase their returns. Additionally, understanding sector performance can provide insights into economic trends, guiding policy-making and investment allocations. By exploring these questions, our project not only showcases the practical applications of data science in finance but also contributes valuable knowledge to the field of financial analytics.



# Data Curation

The dataset used in this project is sourced from Kaggle. It contains historical stock market data for various companies listed in the S&P 500 index over a five-year period. The data includes daily records of stock prices (open, high, low, close), trading volume, and the stock ticker symbol. This dataset provides a comprehensive view of the stock performance of companies within the S&P 500, making it suitable for analyzing trends, predicting future prices, and comparing sector performances. A large data set like this (619,000 rows) gives us the perfect playing field to do some machine learning! But first, we need to transform the data to meet our needs. 

### Transforming the data set 
- Inorder to properly analyze our data set we have to transform the data so it is ready for analysis. We first import all of our necessary imports to handle the data

<img width="750" alt="Screenshot 2024-06-29 at 5 19 50 PM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/e31ca6ee-e186-40b1-8149-8978b8eaa891">

- Next, we load the data set. The data set was too large to upload directly to Google Collab so it was pushed to Git Hub and then pulled using a URL. 

<img width="864" alt="Screenshot 2024-06-29 at 5 23 02 PM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/1d071ab6-3367-4783-a94c-392baddd5c0d">

 - After loading in the data we wanted to know if there were any missing data points. Missing data points can alter our machine learning results and give inaccurate results. First, we checked for the amount of missing values per column to see if there were any missing data points. Then we dropped those rows that contained missing data points.
   
<img width="1368" alt="Screenshot 2024-06-29 at 5 27 32 PM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/7124baff-a0bd-4177-83eb-675e39e91c6e">

- Next, we gathered all of the unique ticker symbols in the data set. The S&P 500 has a rigorous set of financial rules that determine if a company can be a part of the S&P 500 or not. This means that every year certain companies are added and taken out based on their performance. For our project, we only wanted to analyze companies that are currently in the S&P 500. The way that we were able to determine what company to remove was to look at the current 500 ticker symbols and cross-reference them with the 505 unique ticker symbols in our data set.
  
![Screenshot 2024-06-29 at 5 34 50 PM](https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/cb668eda-e2b8-407b-a77e-32a5dbadc713)

- Removing tickers that are not currently in the S&P 500

![Screenshot 2024-06-29 at 5 35 42 PM](https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/abb43804-c165-4f63-977e-b084270aa14e)






# Exploratory Data Analysis
After cleaning the data and getting it ready for analysis we moved on to do some preliminary data analysis. This portion of the data analysis was mostly geared toward figuring out some large-scale statistics about the data set. What were the max and min values of all of the columns, the standard deviations, and the mean? This portion was really just for us to understand what the scale of the data set was and to look for any large variations in the data that might throw our primary analysis off course. 
<img width="702" alt="Screenshot 2024-07-03 at 10 56 39 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/cc62176a-4cd7-471e-acdf-b306ff06da8e">

We also calculated the standard deviation of each individual stock, this would help us understand if a stock had low or high volatility 

<img width="681" alt="Screenshot 2024-07-03 at 11 05 56 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/feb87c4a-8240-41a9-ad0f-ad0dd58bb935">

<img width="583" alt="Screenshot 2024-07-03 at 11 06 13 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/b1e300a8-333a-4c3c-ad54-24542195d6ba">

Through this, we were able to make the following conclusions:

#### Descriptive Statistics
- Mean Prices: The average opening, high, low, and close prices are roughly similar, hovering around $83, indicating consistent trading ranges.

- Standard Deviation: There is a high standard deviation in the price data, suggesting significant variability in stock prices, which could be due to stock volatility or differences across various stocks.

- Volume: Trading volume shows a wide range, with a mean of about 4.32 million shares traded per day. The maximum trading volume recorded is extraordinarily high at over 618 million shares.

#### Feature Representation
- Dates: The dataset covers 1,259 unique dates.

- Stock Names (Tickers): There are 500 different stock tickers represented, implying the dataset spans a broad array of companies.

- Price Points: The dataset contains a large number of unique open, high, low, and close values, indicating a detailed and comprehensive stock price record.

## Data Analysis through testing
Along with our preliminary data exploration we employed some testing techniques that would help us gather a greater understanding of the data set for our primary analysis. 



### Chi-Squared Test
The main focus of a chi-squared test is to to determine if a difference between observed data and expected data is due to chance, or if it is due to a relationship between the variables in our data. Our hypothesis for this test was "Is there a  statistically significant association between the sectors and volatility?"

<img width="1466" alt="Screenshot 2024-07-03 at 11 12 23 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/4e93008f-ab06-45a8-9257-c075ef294912">

#### Interpretation of Chi Squared Results
<img width="1234" alt="Screenshot 2024-07-03 at 11 16 07 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/4a025c82-8b4c-4a1c-ba66-fd147e97772b">

-The Chi-Square Statistic is approximately 20.508. This value measures the difference between the observed frequencies in the contingency tables and the frequencies expected if sectors and volatility categories were independent. A higher value indicates a greater divergence from independence.

-P-Value (0.05806): This p-value tests the null hypothesis that sector and volatility classification are independent of each other.

-Since the p-value is greater than 0.05, it suggests that there is not enough evidence to reject the null hypothesis at the 5% significance level. Therefore, it is concluded that there is no statistically significant association between the sectors and volatility classes, although it's very close to the threshold.

##### Sector Specific Observations
- Consumer Discretionary, Finance, and Industrial have relatively similar median volatilities with tighter IQRs, indicating less variation within the middle 50% of data points. But, Consumer Discretionary has notably lower outliers. Energy and Healthcare show a higher median volatility compared to the others, with the Energy sector displaying more variability as evidenced by longer whiskers.

- Consumer Staples and Technology have both upper and lower outliers, with Technology displaying a wide range. This may suggest higher volatility in stock prices within these sectors compared to others like Finance. Sectors like Technology and Energy show larger variability in stock volatility, possibly indicating a more dynamic market environment or higher risk. But in contrast, Finance and Industrial show more stability.

- The presence of outliers in sectors like Consumer Discretionary and Technology could be due to specific events or conditions affecting certain companies within those sectors, meriting further investigation to understand the causes of these extreme values. Investors might use this information to assess risk and make decisions about diversifying their portfolios.



### Z - Tests
The Z-test is used to determine if there is a significant difference between the means of two groups or between a sample mean and a known population mean. The Z-value measures the number of standard deviations a data point is from the population mean, indicating the magnitude of the difference. The p-value indicates the probability that the observed difference occurred by chance; a low p-value (typically < 0.05) suggests that the difference is statistically significant.


<img width="761" alt="Screenshot 2024-07-03 at 11 23 58 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/f9cc0075-2d31-4900-bcac-0e9097799154">

#### Interpretation of z-test results 

<img width="1072" alt="Screenshot 2024-07-03 at 11 25 45 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/89a64ec9-21fa-4eb1-b434-6a8ea09aeb34">


##### Sector Specific Observations

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

#### Interpretation of the ANOVA testing

<img width="1082" alt="Screenshot 2024-07-03 at 11 40 42 AM" src="https://github.com/junaidc15/cmsc320FinalProject/assets/158375378/558fd0a0-98ca-4b75-b336-458e1f5fe281">

- The F-statistic value is 0.7327. With this F-statistic, we can expect greater variability between group means relative to the variability within the groups.

- The p-value is 0.6231. This value indicates the probability of observing the data, or something more extreme if the null hypothesis (that all group means are equal) is true.

- Statistical Significance: Since the p-value (0.6231) is more than the common significance level of 0.05, we fail to reject the null hypothesis. This suggests that there is not a statistically significant difference in the daily returns across different sectors.

- The failure of rejection of the null hypothesis implies that not all sectors have the same mean daily return. This finding strongly suggests that sector-specific factors likely influence the stock returns, and these factors cause significant differences between the average returns of different sectors.

  
##### Sector Specific Observations
Finance: This sector shows a compact distribution of returns around the median, indicating less volatility in daily returns. However, there are several outliers, particularly on the negative side.

Industrial: Similar to finance, industrial has a narrow IQR but fewer outliers. This suggests more stable returns but with occasional extremes.

Consumer Discretionary: Exhibits a slightly higher spread in returns (wider box), indicating more variability in daily returns. There are outliers on both the high and low ends.

Energy: Displays a very tight IQR with several high and low outliers, suggesting that while most daily returns are close to the median, extreme values are not uncommon.

Healthcare: Similar pattern to energy, with a tight IQR and outliers. This sector might experience occasional spikes or drops in returns.

Consumer Staples: Shows moderate variability with few outliers, indicating relatively stable returns.

Technology: This sector has one of the widest IQRs, reflecting significant day-to-day variation in returns. Also, there are many outliers, particularly on the positive side, suggesting the potential for high returns.






# Primary Analysis 

Based on our two primary questions: "Can we accurately predict future stock prices based on historical data?" and "How do different sectors within the S&P 500 compare in terms of performance over time?" A regression analysis would be the most suitable. Regressions are designed for scenarios just like this where predictions are needed to be made. Taking in past trends and data a regression model can help us make informative decisions for the future. The regression machine learning technique can take in many variables from our data that will be needed to make predictions. Many variables in economics such as stock price, volume, and other factors are crucial so the machine can make more accurate decisions.

# Visualization
Regression Analysis:
Purpose: Used to predict future stock prices based on historical data.
Findings: Predictive models like regression can leverage past price movements, volume, and other economic indicators to forecast future price trends, though accuracy can be influenced by market volatility and external factors.
Sector Performance Analysis:

Method: Comparison of different sectors' performances using statistical tests (ANOVA, Chi-Squared, Z-tests).
Key Insights:
Consumer Discretionary and Consumer Staples sectors demonstrated statistically significant outperformance.
Finance, Industrial, and Technology sectors exhibited more stability with occasional deviations.
ANOVA results indicated no significant overall differences in daily returns across sectors, suggesting similar intra-sector performance variability.
Data Curation and Transformation
Data Source: Historical stock market data from Kaggle, covering various metrics over five years.
Process: Data was cleaned to handle missing values and filtered to include only current S&P 500 companies. This ensures analysis is relevant to the current market composition.
Statistical Analysis
Chi-Squared Test: Aimed to explore the independence between sectors and stock volatility, finding no significant associations.
Z-Test: Evaluated how different sectors' returns deviate from the overall mean, identifying specific sectors that either outperformed or underperformed.
ANOVA: Analyzed variance in daily returns across sectors and concluded no substantial differences, suggesting external factors may influence sector-specific performances.

# Insights and Conclusions

Project Overview:
The Summer 2024 Data Science Project aimed to harness historical S&P 500 data to predict future stock prices and analyze sector performance. This initiative not only targeted enhancements in investment strategies through predictive analytics but also sought to deepen the understanding of sector dynamics within the index.

Informed Understanding:

For Uninformed Readers: The project meticulously explains the S&P 500's significance, outlines the machine learning methodologies employed, and discusses the findings in a way that educates readers about the basics of stock market analytics. Uninformed readers gain a foundational understanding of how data science can predict stock market trends and the factors influencing sector performances.
For Informed Readers: Even those familiar with financial analytics would find the detailed examination of sector-specific performances enlightening. The application of various statistical tests (Chi-Squared, Z-Tests, ANOVA) to real-world data offers insights into the practical challenges and complexities of predicting stock prices and sector behaviors.
Key Findings:

Predictive Modeling: Regression analysis indicated that while stock prices can be predicted using historical data, the accuracy is subject to market volatility and economic indicators. This finding is crucial for investors considering reliance on predictive models.
Sector Analysis: The project revealed nuanced insights into sector performance:
Consumer Discretionary and Consumer Staples sectors showed significant outperformance.
Finance, Industrial, and Technology sectors demonstrated stability with fewer fluctuations.
The ANOVA test revealed no significant differences in daily returns across sectors, challenging the notion that some sectors consistently outperform others.
Statistical Analysis:

Chi-Squared Test: No significant association between sectors and stock volatility was found, suggesting that sector categorization does not inherently dictate volatility levels.
Z-Test: Highlighted sectors that statistically differed from the market average, providing a basis for targeted investment strategies.
ANOVA: The lack of significant differences among sectorial daily returns suggests that external factors might play a larger role in influencing stock prices than previously considered.
Implications for Stakeholders:

Investors: Insights from this project can guide portfolio diversification strategies, especially in understanding sector-specific risks and returns.
Policy Makers and Economists: Understanding sector dynamics can aid in crafting economic policies that enhance the stability and growth of critical market segments.
Data Scientists: The project underscores the importance of robust data preprocessing and the potential of machine learning in financial forecasting.
Conclusions:
The project successfully demonstrates the application of data science in finance, providing valuable insights into the predictability of stock prices and the comparative performance of sectors within the S&P 500. While it establishes a strong foundation for forecasting and sector analysis, it also highlights the limitations imposed by external economic factors and market volatility. Future work could expand on refining predictive models and exploring deeper inter-sectoral dynamics to enhance the granularity and accuracy of forecasts.

Overall Experience:
Both uninformed and informed readers are likely to find the project's approach comprehensive and its conclusions insightful. It effectively bridges the gap between theoretical data science applications and practical financial market analytics, enriching the reader's understanding of both domains.




