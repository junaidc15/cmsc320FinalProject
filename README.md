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

# Primary Analysis 

# Visualization

# Insights and Conclusions






