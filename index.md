# How Does Significant Exposure to ESG Risks Affect Short-term Stock Returns for Companies of Different Health Levels?


Tiancheng Xu, Ford Danielsen, Rishabh Kumar, Rama Sai Sundar Ryali, Evelyn Zhang

Apr 2022


## Role & Main Tasks in the Project
Data engineer and modeling specialist - I was in charge of collecting data from multiple databases, performing ETL, linking/compiling/storing them and feeding team members with specific datasets upon request; I also performed analysis on stock returns data and ESG data and validated the insights with statistical methods.

## Takeaways
According to our analysis, different ESG policies and different levels of exposure to ESG risks have different implications to companies. Credit-healthy companies tend to face nagative short-term stock returns when there is significant exposure to ESG risks. Credit-unhealthy companies seem to be less impacted by these similar risks. There are, inevitably, limitations with the analysis given the scope of the project. The insights can be further validated or improved once more data and resources become available.

---

## The goal
To Understand the Impact of ESG Risk Exposures on Short-term Stock Returns.


## Summary
Do the short-term stock returns of healthy companies and unhealthy companies react to negative ESG news in the same way? - NO!

Should all companies have the same ESG risks management goals? - NO!


## Assumptions & Methodology

### What is ESG?
ESG stands for Environmental, Social, and Governance. It is an approach to evaluate the extent to which a corporation works on behalf of social goals that go beyond the role of a corporation to maximize profits on behalf of the corporation's shareholders.

<img width="852" alt="image" src="https://user-images.githubusercontent.com/63265930/171541767-a946fa8f-8e45-4a21-9567-078d9f26d76e.png">

### Methodology

<img width="797" alt="image" src="https://user-images.githubusercontent.com/63265930/171542076-c14e596a-e3ed-42f5-94c1-1f0b1a47fd18.png">

### What is a healthy company?
We define companies with high credit ratings as "healthy companies", and companies with low credit ratings as "unhealthy companies".

### Database Overview

<img width="480" alt="image" src="https://user-images.githubusercontent.com/63265930/171542244-f2aef291-ef6c-4939-abdb-3ef756e05005.png">

### About RRI (RepRisk Index)
The RepRisk Index (RRI), ranges from 0 to 100, is an algorithm developed by RepRisk that dynamically captures and quantifies a company’s reputational risk exposure to ESG issues.

The RRI is purely performance-based:

The RRI of company A depends only on A’s risk incidents. The RRI reflects a company’s actual risk management performance as opposed to its communicated goals and policies.

A company's RRI gets updated by the end of each month. It represents the combined effect of risk incidents throughout the month (or decaying effect if no significant risk incidents).

## Exploratory Data Analysis

### GENERAL ANALYSIS
Objective: To understand the data with reference to credit ratings and ESG.

<img width="253" alt="image" src="https://user-images.githubusercontent.com/63265930/171700813-2e68e106-d5cc-4163-adae-525d56098eb2.png">
<img width="329" alt="image" src="https://user-images.githubusercontent.com/63265930/171700849-8b2d1b45-10ac-4311-8fed-acd832ff626e.png">

Most of the companies in our data fall in the 'good' credit rating zone (A, BBB and BB).

Companies in the 'good' credit rating zone have highest number of ESG events.

Peak reprisk index decreases as the health of a company decreases.


### RRI TRENDS BY RATINGS
Objective: To understand the ESG risk exposure based on the health of an organization.

<img width="530" alt="image" src="https://user-images.githubusercontent.com/63265930/171701121-e39ac2e8-0b24-4b58-a398-58ae0b1cc46f.png">

The RRI for each rating can be seen to fluctuate within their respective ranges, with overlapping at only few points.

Historically, companies with better health (ratings) are shown to have higher exposure to ESG risk and vice versa.


### LONG/SHORT TERM RETURNS BY ESG RISK
Objective: To understand the impact of ESG risk exposure in different ratings on short- and long-term returns.

<img width="611" alt="image" src="https://user-images.githubusercontent.com/63265930/171701532-04b5eca9-d6b9-45d1-809f-ce22e0f33449.png">
<img width="573" alt="image" src="https://user-images.githubusercontent.com/63265930/171701708-b142456e-bd44-40dd-a8d4-a0a36c859a9f.png">

We try to observe a general trend linkage between increase in the reprisk index and change in return.

These trends are observed over different ratings to establish if health of a company controls the return changes when there is negative ESG news.

There are multiple factors that influence the return of a stock but with the intention of understanding changes in stock return with ESG risk, we observe a divergence movement in high rated stocks.


## Models & Analyses

Base case: 5/10/30-day returns after >10 risk increases; later extended to >5 and >20 risk increases.
Used excess returns over SPY in order to minimize fluctuation of the market.
Healthy companies: companies with higher credit ratings (AAA, AA, A).
Unhealthy companies: those with lower credit ratings (BBB, BB, B).

### AVERAGE 5/10/30-DAY EXCESS RETURNS (ACROSS CREDIT RATINGS) FOR >10 ESG RISK INCREASES (BASE CASE)

<img width="569" alt="image" src="https://user-images.githubusercontent.com/63265930/171702189-0bbd8715-f14b-49ec-9094-7ae02c74fba4.png">

After > 10 risk increases:

Healthier companies tend to see decreased stock returns in 5/10-day periods; unhealthy companies would have relatively higher returns in a 30-day period.

### T STATISTICS: AVERAGE 5/10/30-DAY EXCESS RETURNS (BASE CASE)

Null hypothesis: excess return = 0; alternative hypothesis: excess return != 0.

<img width="548" alt="image" src="https://user-images.githubusercontent.com/63265930/171702425-449de39a-3b12-47e5-bb1f-9806661386d1.png">

If we just focus on the top-left and bottom-right corners:

Both have relatively high t-values, which suggest that there's significant evidence to reject the null hypothesis (excess return = 0); 
it supports our findings from the previous analysis.


### Alpha & Beta

<img width="557" alt="image" src="https://user-images.githubusercontent.com/63265930/171725264-de7f1fd0-55a1-4616-8379-c2a3ff9ab09a.png">

<img width="577" alt="image" src="https://user-images.githubusercontent.com/63265930/171725303-fb8f9bbc-4068-49fb-b864-c33754c0a869.png">

Alpha and Beta is calculated considering SPY returns as the Benchmark.

Base case: 5/10/30-day returns after >10 risk increases; later extended to >5 and >20 risk increases.

Used the "lm" function on R to do the regression. The results for all companies are as follows:

<img width="655" alt="image" src="https://user-images.githubusercontent.com/63265930/171725421-3a144ab9-ca4d-4003-86b2-4039b6fdeed1.png">


Output & T Statistics

<img width="638" alt="image" src="https://user-images.githubusercontent.com/63265930/171725510-ca08b16e-2133-456c-b848-afb1d27ea46a.png">

### Takeaways
Overall, we observed negative alpha (excess returns) for healthy companies and positive alpha for unhealthy ones.

There's significant evidence that healthy companies underperform in 5/10-day. All positive alphas are not statistically significant (t-stats < 1.96). 

Systematic risk (𝜷) is high for AAA and B companies.All statistically significant except for two.

Limitation of the model:

Neglects the impacts of firm size and value.


### Cumulative Abnormal Return Analysis

<img width="598" alt="image" src="https://user-images.githubusercontent.com/63265930/171725791-3704f9e3-72c6-4c01-a55e-a6f50f600e83.png">

<img width="579" alt="image" src="https://user-images.githubusercontent.com/63265930/171725827-951390c7-abbe-44e0-9d1b-c0fef59c7b62.png">


Output & T Statistics

<img width="688" alt="image" src="https://user-images.githubusercontent.com/63265930/171725935-cfcf7d10-6a2a-4ab0-8ab4-004481791268.png">

Overall, we observed negative cumulative abnormal returns (CAR) for healthy companies and positive unhealthy ones.

All negative CARs for healthy companies are significant (95% confidence interval, t-stats > 1.96). All positive CARs for unhealthy companies are significant.

There is no enough significant evidence for most CAR.

The sample size of events is small, especially for AAA, B companies. Require future research to generate more solid insights.


<img width="894" alt="image" src="https://user-images.githubusercontent.com/63265930/171726123-911bb6e6-c0ee-4d6e-ae19-37d428c9b078.png">


### Takeaways
The overall results aligned with our pervious findings.

Healthy companies underperform in the short-term; unhealthy companies outperform, especially over 5-day period.

Limitations:

Small sample size might lead to biased results.

More events of unhealthy companies (B category) in our sample.

Event study also includes factors such as earnings announcements, M&As, and unemployment.

Small sample size might lead to biased results.


## Conclusion

<img width="781" alt="image" src="https://user-images.githubusercontent.com/63265930/171726345-134cab3f-e166-47fa-9a69-ba0c27cca092.png">

### Further Research to Improve the Analysis

Expand the S&P 500 to Russell 2000 and beyond.

Further dissect credit ratings.

Expand date pool.

Segment events.

Perform on individual ESG sections respectively.

Further dissect E, S, and G.



---
## R Code:

Load libraries and functions
```
library(data.table)
library(dplyr)
library(readxl)

DATE <- function(yyyymmdd) {
  s <- as.character(yyyymmdd)
  dte <- as.Date(sprintf("%s-%s-%s",substr(s,1,4),substr(s,5,6),substr(s,7,8)))
  return(dte)
}

DATE2 <- function(x) {
  s <- as.character(x)
  dte <- as.Date(sprintf("20%s-%s-%s",substr(s,7,8),substr(s,4,5),substr(s,1,2)))
  return(dte)
}
```

ETL
```
# The master table consists of 4 separate datasets that we managed to pull from 
# WRDS-RepRisk, WRDS-CRSP and other online sources. Each of these 4 datasets were
# were collected and compiled before loading into this R file.
# These individual tables are:

# RRI (WRDS-RepRisk)
# Stock_Returns (WRDS-CRSP)
# Credit_Ratings
# SPY_Daily_Returns


# Load RRI data collected from WRDS-RepRisk

data <- fread('S&P500_RRI.csv')
data[, date := DATE(date)]

# Data cleaning
data[data$ticker == 'BRK.', ticker := 'BRK.B']
data[data$ticker == 'CMCS', ticker := 'CMCSA']
data[data$ticker == 'UAA', ticker := 'UA']
data[data$ticker == 'NWSA', ticker := 'NWS']
data[data$ticker == 'FOXA', ticker := 'FOX']

# Create a mutated date for score_dates that fall onto a Sat. or Sun
# The mutated date is the last Friday before the weekend
data[, date_mut := case_when(weekdays(date) == "Saturday" ~ date -1, 
                             weekdays(date) == "Sunday" ~ date - 2, 
                             TRUE ~ date)]

################################################################################
# Load Stock_Returns data collected from WRDS-CRSP

stocks <- fread('stocks.csv')
stocks[, date := as.Date(date, format = "%m/%d/%y")]

# Create the master table by merging the existing 2 tables
master <- merge(data, stocks, by.x=c('permno','date_mut'), by.y=c('PERMNO','date'))

################################################################################
# Load SPY_Returns data
bench <- fread('bench_price_new.csv')
bench[,date := as.Date(date)]

# Merge the data into the master table by date
master <- merge(master, bench, by.x='date_mut', by.y='date', all.x=TRUE)

################################################################################
# Load Credit_ratings data
ratings <- fread('credit_ratings.csv', header=TRUE)

# Data cleaning. Simplify the categories
colnames(ratings) <- c('ticker', 'orig_2016', 'orig_2017', 'orig_2018', 'orig_2019', 'orig_2020')
ratings[, m2016 := str_replace_all(orig_2016, "[^[:alnum:]]", "")]
ratings[, m2017 := str_replace_all(orig_2017, "[^[:alnum:]]", "")]
ratings[, m2018 := str_replace_all(orig_2018, "[^[:alnum:]]", "")]
ratings[, m2019 := str_replace_all(orig_2019, "[^[:alnum:]]", "")]
ratings[, m2020 := str_replace_all(orig_2020, "[^[:alnum:]]", "")]
ratings <- ratings[,c('ticker', 'm2016', 'm2017', 'm2018', 'm2019', 'm2020')]

# Merge the data into the master table by ticker
master <- merge(master, ratings, by.x='ticker', by.y='ticker')

# Create the current-year rating for each update in score
master[, ratings := case_when(substr(date,1,4) == '2016' ~ m2016,
                              substr(date,1,4) == '2017' ~ m2017,
                              substr(date,1,4) == '2018' ~ m2018,
                              substr(date,1,4) == '2019' ~ m2019,
                              substr(date,1,4) == '2020' ~ m2020)]

################################################################################
# Output the master table as a csv file

write.csv(master, 'master.csv')


################################################################################
# Create dataset where RRI jump >10, >5 and >20
data_10 <- master[`RRI_trend`>10,]
data_10
write.csv(data_10, 'data_10.csv')

data_5 <- master[`RRI_trend`>5,]
data_5
write.csv(data_5, 'data_5.csv')

data_20 <- master[`RRI_trend`>20,]
data_20
write.csv(data_20, 'data_20.csv')
```

Correlation
```
# Correlation between stock returns and RRI_trend

ret_5 <- c(cor(master[ratings == 'AAA', ret_5], master[ratings == 'AAA', RRI_trend]), 
           cor(master[ratings == 'AA', ret_5], master[ratings == 'AA', RRI_trend]), 
           cor(master[ratings == 'A', ret_5], master[ratings == 'A', RRI_trend]), 
           cor(master[ratings == 'BBB', ret_5], master[ratings == 'BBB', RRI_trend]), 
           cor(master[ratings == 'BB', ret_5], master[ratings == 'BB', RRI_trend]), 
           cor(master[ratings == 'B', ret_5], master[ratings == 'B', RRI_trend]), 
           cor(master[ratings == 'NR', ret_5], master[ratings == 'NR', RRI_trend]), 
           cor(master[ratings == 'X', ret_5], master[ratings == 'X', RRI_trend]))

ret_10 <- c(cor(master[ratings == 'AAA', ret_10], master[ratings == 'AAA', RRI_trend]), 
           cor(master[ratings == 'AA', ret_10], master[ratings == 'AA', RRI_trend]), 
           cor(master[ratings == 'A', ret_10], master[ratings == 'A', RRI_trend]), 
           cor(master[ratings == 'BBB', ret_10], master[ratings == 'BBB', RRI_trend]), 
           cor(master[ratings == 'BB', ret_10], master[ratings == 'BB', RRI_trend]), 
           cor(master[ratings == 'B', ret_10], master[ratings == 'B', RRI_trend]), 
           cor(master[ratings == 'NR', ret_10], master[ratings == 'NR', RRI_trend]), 
           cor(master[ratings == 'X', ret_10], master[ratings == 'X', RRI_trend]))

ret_30 <- c(cor(master[ratings == 'AAA', ret_30], master[ratings == 'AAA', RRI_trend]), 
           cor(master[ratings == 'AA', ret_30], master[ratings == 'AA', RRI_trend]), 
           cor(master[ratings == 'A', ret_30], master[ratings == 'A', RRI_trend]), 
           cor(master[ratings == 'BBB', ret_30], master[ratings == 'BBB', RRI_trend]), 
           cor(master[ratings == 'BB', ret_30], master[ratings == 'BB', RRI_trend]), 
           cor(master[ratings == 'B', ret_30], master[ratings == 'B', RRI_trend]), 
           cor(master[ratings == 'NR', ret_30], master[ratings == 'NR', RRI_trend]), 
           cor(master[ratings == 'X', ret_30], master[ratings == 'X', RRI_trend]))

ret_180 <- c(cor(master[ratings == 'AAA', ret_180], master[ratings == 'AAA', RRI_trend]), 
             cor(master[ratings == 'AA', ret_180], master[ratings == 'AA', RRI_trend]), 
             cor(master[ratings == 'A', ret_180], master[ratings == 'A', RRI_trend]), 
             cor(master[ratings == 'BBB', ret_180], master[ratings == 'BBB', RRI_trend]), 
             cor(master[ratings == 'BB', ret_180], master[ratings == 'BB', RRI_trend]), 
             cor(master[ratings == 'B', ret_180], master[ratings == 'B', RRI_trend]), 
             cor(master[ratings == 'NR', ret_180], master[ratings == 'NR', RRI_trend]),
             cor(master[ratings == 'X', ret_180], master[ratings == 'X', RRI_trend]))

rating_ret_cor <- data.frame(ret_5, ret_10, ret_30, ret_180)
rownames(rating_ret_cor) <- c('AAA', 'AA', 'A', 'BBB', 'BB', 'B', 'NR', 'X')
rating_ret_cor

write.csv(rating_ret_cor, 'rating_ret_cor.csv')

################################################################################
# Correlation between stock returns and current_RRI

ret_5_c <- c(cor(master[ratings == 'AAA', ret_5], master[ratings == 'AAA', current_RRI]), 
           cor(master[ratings == 'AA', ret_5], master[ratings == 'AA', current_RRI]), 
           cor(master[ratings == 'A', ret_5], master[ratings == 'A', current_RRI]), 
           cor(master[ratings == 'BBB', ret_5], master[ratings == 'BBB', current_RRI]), 
           cor(master[ratings == 'BB', ret_5], master[ratings == 'BB', current_RRI]), 
           cor(master[ratings == 'B', ret_5], master[ratings == 'B', current_RRI]), 
           cor(master[ratings == 'NR', ret_5], master[ratings == 'NR', current_RRI]), 
           cor(master[ratings == 'X', ret_5], master[ratings == 'X', current_RRI]))

ret_10_c <- c(cor(master[ratings == 'AAA', ret_10], master[ratings == 'AAA', current_RRI]), 
            cor(master[ratings == 'AA', ret_10], master[ratings == 'AA', current_RRI]), 
            cor(master[ratings == 'A', ret_10], master[ratings == 'A', current_RRI]), 
            cor(master[ratings == 'BBB', ret_10], master[ratings == 'BBB', current_RRI]), 
            cor(master[ratings == 'BB', ret_10], master[ratings == 'BB', current_RRI]), 
            cor(master[ratings == 'B', ret_10], master[ratings == 'B', current_RRI]), 
            cor(master[ratings == 'NR', ret_10], master[ratings == 'NR', current_RRI]), 
            cor(master[ratings == 'X', ret_10], master[ratings == 'X', current_RRI]))

ret_30_c <- c(cor(master[ratings == 'AAA', ret_30], master[ratings == 'AAA', current_RRI]), 
            cor(master[ratings == 'AA', ret_30], master[ratings == 'AA', current_RRI]), 
            cor(master[ratings == 'A', ret_30], master[ratings == 'A', current_RRI]), 
            cor(master[ratings == 'BBB', ret_30], master[ratings == 'BBB', current_RRI]), 
            cor(master[ratings == 'BB', ret_30], master[ratings == 'BB', current_RRI]), 
            cor(master[ratings == 'B', ret_30], master[ratings == 'B', current_RRI]), 
            cor(master[ratings == 'NR', ret_30], master[ratings == 'NR', current_RRI]), 
            cor(master[ratings == 'X', ret_30], master[ratings == 'X', current_RRI]))

ret_180_c <- c(cor(master[ratings == 'AAA', ret_180], master[ratings == 'AAA', current_RRI]), 
             cor(master[ratings == 'AA', ret_180], master[ratings == 'AA', current_RRI]), 
             cor(master[ratings == 'A', ret_180], master[ratings == 'A', current_RRI]), 
             cor(master[ratings == 'BBB', ret_180], master[ratings == 'BBB', current_RRI]), 
             cor(master[ratings == 'BB', ret_180], master[ratings == 'BB', current_RRI]), 
             cor(master[ratings == 'B', ret_180], master[ratings == 'B', current_RRI]), 
             cor(master[ratings == 'NR', ret_180], master[ratings == 'NR', current_RRI]),
             cor(master[ratings == 'X', ret_180], master[ratings == 'X', current_RRI]))

rating_ret_cor_c <- data.frame(ret_5_c, ret_10_c, ret_30_c, ret_180_c)
rownames(rating_ret_cor_c) <- c('AAA', 'AA', 'A', 'BBB', 'BB', 'B', 'NR', 'X')
rating_ret_cor_c

write.csv(rating_ret_cor_c, 'rating_ret_cor_c.csv')

################################################################################
# Correlation breakdown by RepRisk Riskness



high <- master[peak_RRI >= 50,]
low <- master[peak_RRI <= 25,]
med <- master[peak_RRI > 25 & peak_RRI < 50,]

# High
ret_5_high <- c(cor(high[ratings == 'AAA', ret_5], high[ratings == 'AAA', RRI_trend]), 
                cor(high[ratings == 'AA', ret_5], high[ratings == 'AA', RRI_trend]), 
                cor(high[ratings == 'A', ret_5], high[ratings == 'A', RRI_trend]), 
                cor(high[ratings == 'BBB', ret_5], high[ratings == 'BBB', RRI_trend]), 
                cor(high[ratings == 'BB', ret_5], high[ratings == 'BB', RRI_trend]), 
                cor(high[ratings == 'B', ret_5], high[ratings == 'B', RRI_trend]), 
                cor(high[ratings == 'NR', ret_5], high[ratings == 'NR', RRI_trend]), 
                cor(high[ratings == 'X', ret_5], high[ratings == 'X', RRI_trend]))

ret_10_high <- c(cor(high[ratings == 'AAA', ret_10], high[`ratings` == 'AAA', RRI_trend]), 
                 cor(high[ratings == 'AA', ret_10], high[`ratings` == 'AA', RRI_trend]), 
                 cor(high[ratings == 'A', ret_10], high[`ratings` == 'A', RRI_trend]), 
                 cor(high[ratings == 'BBB', ret_10], high[`ratings` == 'BBB', RRI_trend]), 
                 cor(high[ratings == 'BB', ret_10], high[`ratings` == 'BB', RRI_trend]), 
                 cor(high[ratings == 'B', ret_10], high[`ratings` == 'B', RRI_trend]), 
                 cor(high[ratings == 'NR', ret_10], high[`ratings` == 'NR', RRI_trend]), 
                 cor(high[ratings == 'X', ret_10], high[`ratings` == 'X', RRI_trend]))

ret_30_high <- c(cor(high[`ratings` == 'AAA', ret_30], high[`ratings` == 'AAA', RRI_trend]), 
                 cor(high[`ratings` == 'AA', ret_30], high[`ratings` == 'AA', RRI_trend]), 
                 cor(high[`ratings` == 'A', ret_30], high[`ratings` == 'A', RRI_trend]), 
                 cor(high[`ratings` == 'BBB', ret_30], high[`ratings` == 'BBB', RRI_trend]), 
                 cor(high[`ratings` == 'BB', ret_30], high[`ratings` == 'BB', RRI_trend]), 
                 cor(high[`ratings` == 'B', ret_30], high[`ratings` == 'B', RRI_trend]), 
                 cor(high[`ratings` == 'NR', ret_30], high[`ratings` == 'NR', RRI_trend]), 
                 cor(high[`ratings` == 'X', ret_30], high[`ratings` == 'X', RRI_trend]))

ret_180_high <- c(cor(high[`ratings` == 'AAA', ret_180], high[`ratings` == 'AAA', RRI_trend]), 
                  cor(high[`ratings` == 'AA', ret_180], high[`ratings` == 'AA', RRI_trend]), 
                  cor(high[`ratings` == 'A', ret_180], high[`ratings` == 'A', RRI_trend]), 
                  cor(high[`ratings` == 'BBB', ret_180], high[`ratings` == 'BBB', RRI_trend]), 
                  cor(high[`ratings` == 'BB', ret_180], high[`ratings` == 'BB', RRI_trend]), 
                  cor(high[`ratings` == 'B', ret_180], high[`ratings` == 'B', RRI_trend]), 
                  cor(high[`ratings` == 'NR', ret_180], high[`ratings` == 'NR', RRI_trend]),
                  cor(high[`ratings` == 'X', ret_180], high[`ratings` == 'X', RRI_trend]))

rating_ret_cor_high <- data.frame(ret_5_high, ret_10_high, ret_30_high, ret_180_high)
rownames(rating_ret_cor_high) <- c('AAA', 'AA', 'A', 'BBB', 'BB', 'B', 'NR', 'X')
rating_ret_cor_high

write.csv(rating_ret_cor_high, 'rating_ret_cor_high.csv')


# Low
ret_5_low <- c(cor(low[ratings == 'AAA', ret_5], low[ratings == 'AAA', RRI_trend]), 
               cor(low[ratings == 'AA', ret_5], low[ratings == 'AA', RRI_trend]), 
               cor(low[ratings == 'A', ret_5], low[ratings == 'A', RRI_trend]), 
               cor(low[ratings == 'BBB', ret_5], low[ratings == 'BBB', RRI_trend]), 
               cor(low[ratings == 'BB', ret_5], low[ratings == 'BB', RRI_trend]), 
               cor(low[ratings == 'B', ret_5], low[ratings == 'B', RRI_trend]), 
               cor(low[ratings == 'NR', ret_5], low[ratings == 'NR', RRI_trend]), 
               cor(low[ratings == 'X', ret_5], low[ratings == 'X', RRI_trend]))

ret_10_low <- c(cor(low[ratings == 'AAA', ret_10], low[`ratings` == 'AAA', RRI_trend]), 
                cor(low[ratings == 'AA', ret_10], low[`ratings` == 'AA', RRI_trend]), 
                cor(low[ratings == 'A', ret_10], low[`ratings` == 'A', RRI_trend]), 
                cor(low[ratings == 'BBB', ret_10], low[`ratings` == 'BBB', RRI_trend]), 
                cor(low[ratings == 'BB', ret_10], low[`ratings` == 'BB', RRI_trend]), 
                cor(low[ratings == 'B', ret_10], low[`ratings` == 'B', RRI_trend]), 
                cor(low[ratings == 'NR', ret_10], low[`ratings` == 'NR', RRI_trend]), 
                cor(low[ratings == 'X', ret_10], low[`ratings` == 'X', RRI_trend]))

ret_30_low <- c(cor(low[`ratings` == 'AAA', ret_30], low[`ratings` == 'AAA', RRI_trend]), 
                cor(low[`ratings` == 'AA', ret_30], low[`ratings` == 'AA', RRI_trend]), 
                cor(low[`ratings` == 'A', ret_30], low[`ratings` == 'A', RRI_trend]), 
                cor(low[`ratings` == 'BBB', ret_30], low[`ratings` == 'BBB', RRI_trend]), 
                cor(low[`ratings` == 'BB', ret_30], low[`ratings` == 'BB', RRI_trend]), 
                cor(low[`ratings` == 'B', ret_30], low[`ratings` == 'B', RRI_trend]), 
                cor(low[`ratings` == 'NR', ret_30], low[`ratings` == 'NR', RRI_trend]), 
                cor(low[`ratings` == 'X', ret_30], low[`ratings` == 'X', RRI_trend]))

ret_180_low <- c(cor(low[`ratings` == 'AAA', ret_180], low[`ratings` == 'AAA', RRI_trend]), 
                 cor(low[`ratings` == 'AA', ret_180], low[`ratings` == 'AA', RRI_trend]), 
                 cor(low[`ratings` == 'A', ret_180], low[`ratings` == 'A', RRI_trend]), 
                 cor(low[`ratings` == 'BBB', ret_180], low[`ratings` == 'BBB', RRI_trend]), 
                 cor(low[`ratings` == 'BB', ret_180], low[`ratings` == 'BB', RRI_trend]), 
                 cor(low[`ratings` == 'B', ret_180], low[`ratings` == 'B', RRI_trend]), 
                 cor(low[`ratings` == 'NR', ret_180], low[`ratings` == 'NR', RRI_trend]),
                 cor(low[`ratings` == 'X', ret_180], low[`ratings` == 'X', RRI_trend]))

rating_ret_cor_low <- data.frame(ret_5_low, ret_10_low, ret_30_low, ret_180_low)
rownames(rating_ret_cor_low) <- c('AAA', 'AA', 'A', 'BBB', 'BB', 'B', 'NR', 'X')
rating_ret_cor_low

write.csv(rating_ret_cor_low, 'rating_ret_cor_low.csv')


# Medium
ret_5_med <- c(cor(med[ratings == 'AAA', ret_5], med[ratings == 'AAA', RRI_trend]), 
               cor(med[ratings == 'AA', ret_5], med[ratings == 'AA', RRI_trend]), 
               cor(med[ratings == 'A', ret_5], med[ratings == 'A', RRI_trend]), 
               cor(med[ratings == 'BBB', ret_5], med[ratings == 'BBB', RRI_trend]), 
               cor(med[ratings == 'BB', ret_5], med[ratings == 'BB', RRI_trend]), 
               cor(med[ratings == 'B', ret_5], med[ratings == 'B', RRI_trend]), 
               cor(med[ratings == 'NR', ret_5], med[ratings == 'NR', RRI_trend]), 
               cor(med[ratings == 'X', ret_5], med[ratings == 'X', RRI_trend]))

ret_10_med <- c(cor(med[ratings == 'AAA', ret_10], med[`ratings` == 'AAA', RRI_trend]), 
                cor(med[ratings == 'AA', ret_10], med[`ratings` == 'AA', RRI_trend]), 
                cor(med[ratings == 'A', ret_10], med[`ratings` == 'A', RRI_trend]), 
                cor(med[ratings == 'BBB', ret_10], med[`ratings` == 'BBB', RRI_trend]), 
                cor(med[ratings == 'BB', ret_10], med[`ratings` == 'BB', RRI_trend]), 
                cor(med[ratings == 'B', ret_10], med[`ratings` == 'B', RRI_trend]), 
                cor(med[ratings == 'NR', ret_10], med[`ratings` == 'NR', RRI_trend]), 
                cor(med[ratings == 'X', ret_10], med[`ratings` == 'X', RRI_trend]))

ret_30_med <- c(cor(med[`ratings` == 'AAA', ret_30], med[`ratings` == 'AAA', RRI_trend]), 
                cor(med[`ratings` == 'AA', ret_30], med[`ratings` == 'AA', RRI_trend]), 
                cor(med[`ratings` == 'A', ret_30], med[`ratings` == 'A', RRI_trend]), 
                cor(med[`ratings` == 'BBB', ret_30], med[`ratings` == 'BBB', RRI_trend]), 
                cor(med[`ratings` == 'BB', ret_30], med[`ratings` == 'BB', RRI_trend]), 
                cor(med[`ratings` == 'B', ret_30], med[`ratings` == 'B', RRI_trend]), 
                cor(med[`ratings` == 'NR', ret_30], med[`ratings` == 'NR', RRI_trend]), 
                cor(med[`ratings` == 'X', ret_30], med[`ratings` == 'X', RRI_trend]))

ret_180_med <- c(cor(med[`ratings` == 'AAA', ret_180], med[`ratings` == 'AAA', RRI_trend]), 
                 cor(med[`ratings` == 'AA', ret_180], med[`ratings` == 'AA', RRI_trend]), 
                 cor(med[`ratings` == 'A', ret_180], med[`ratings` == 'A', RRI_trend]), 
                 cor(med[`ratings` == 'BBB', ret_180], med[`ratings` == 'BBB', RRI_trend]), 
                 cor(med[`ratings` == 'BB', ret_180], med[`ratings` == 'BB', RRI_trend]), 
                 cor(med[`ratings` == 'B', ret_180], med[`ratings` == 'B', RRI_trend]), 
                 cor(med[`ratings` == 'NR', ret_180], med[`ratings` == 'NR', RRI_trend]),
                 cor(med[`ratings` == 'X', ret_180], med[`ratings` == 'X', RRI_trend]))

rating_ret_cor_med <- data.frame(ret_5_med, ret_10_med, ret_30_med, ret_180_med)
rownames(rating_ret_cor_med) <- c('AAA', 'AA', 'A', 'BBB', 'BB', 'B', 'NR', 'X')
rating_ret_cor_med

write.csv(rating_ret_cor_med, 'rating_ret_cor_med.csv')





###### Correlation with CURRENT_RRI

ret_5_c_high <- c(cor(high[ratings == 'AAA', ret_5], high[ratings == 'AAA', current_RRI]), 
                  cor(high[ratings == 'AA', ret_5], high[ratings == 'AA', current_RRI]), 
                  cor(high[ratings == 'A', ret_5], high[ratings == 'A', current_RRI]), 
                  cor(high[ratings == 'BBB', ret_5], high[ratings == 'BBB', current_RRI]), 
                  cor(high[ratings == 'BB', ret_5], high[ratings == 'BB', current_RRI]), 
                  cor(high[ratings == 'B', ret_5], high[ratings == 'B', current_RRI]), 
                  cor(high[ratings == 'NR', ret_5], high[ratings == 'NR', current_RRI]), 
                  cor(high[ratings == 'X', ret_5], high[ratings == 'X', current_RRI]))

ret_10_c_high <- c(cor(high[ratings == 'AAA', ret_10], high[ratings == 'AAA', current_RRI]), 
                   cor(high[ratings == 'AA', ret_10], high[ratings == 'AA', current_RRI]), 
                   cor(high[ratings == 'A', ret_10], high[ratings == 'A', current_RRI]), 
                   cor(high[ratings == 'BBB', ret_10], high[ratings == 'BBB', current_RRI]), 
                   cor(high[ratings == 'BB', ret_10], high[ratings == 'BB', current_RRI]), 
                   cor(high[ratings == 'B', ret_10], high[ratings == 'B', current_RRI]), 
                   cor(high[ratings == 'NR', ret_10], high[ratings == 'NR', current_RRI]), 
                   cor(high[ratings == 'X', ret_10], high[ratings == 'X', current_RRI]))

ret_30_c_high <- c(cor(high[ratings == 'AAA', ret_30], high[ratings == 'AAA', current_RRI]), 
                   cor(high[ratings == 'AA', ret_30], high[ratings == 'AA', current_RRI]), 
                   cor(high[ratings == 'A', ret_30], high[ratings == 'A', current_RRI]), 
                   cor(high[ratings == 'BBB', ret_30], high[ratings == 'BBB', current_RRI]), 
                   cor(high[ratings == 'BB', ret_30], high[ratings == 'BB', current_RRI]), 
                   cor(high[ratings == 'B', ret_30], high[ratings == 'B', current_RRI]), 
                   cor(high[ratings == 'NR', ret_30], high[ratings == 'NR', current_RRI]), 
                   cor(high[ratings == 'X', ret_30], high[ratings == 'X', current_RRI]))

ret_180_c_high <- c(cor(high[ratings == 'AAA', ret_180], high[ratings == 'AAA', current_RRI]), 
                    cor(high[ratings == 'AA', ret_180], high[ratings == 'AA', current_RRI]), 
                    cor(high[ratings == 'A', ret_180], high[ratings == 'A', current_RRI]), 
                    cor(high[ratings == 'BBB', ret_180], high[ratings == 'BBB', current_RRI]), 
                    cor(high[ratings == 'BB', ret_180], high[ratings == 'BB', current_RRI]), 
                    cor(high[ratings == 'B', ret_180], high[ratings == 'B', current_RRI]), 
                    cor(high[ratings == 'NR', ret_180], high[ratings == 'NR', current_RRI]),
                    cor(high[ratings == 'X', ret_180], high[ratings == 'X', current_RRI]))

rating_ret_cor_c_high <- data.frame(ret_5_c_high, ret_10_c_high, ret_30_c_high, ret_180_c_high)
rownames(rating_ret_cor_c_high) <- c('AAA', 'AA', 'A', 'BBB', 'BB', 'B', 'NR', 'X')
rating_ret_cor_c_high

write.csv(rating_ret_cor_c_high, 'rating_ret_cor_c_high.csv')



ret_5_c_med <- c(cor(med[ratings == 'AAA', ret_5], med[ratings == 'AAA', current_RRI]), 
                 cor(med[ratings == 'AA', ret_5], med[ratings == 'AA', current_RRI]), 
                 cor(med[ratings == 'A', ret_5], med[ratings == 'A', current_RRI]), 
                 cor(med[ratings == 'BBB', ret_5], med[ratings == 'BBB', current_RRI]), 
                 cor(med[ratings == 'BB', ret_5], med[ratings == 'BB', current_RRI]), 
                 cor(med[ratings == 'B', ret_5], med[ratings == 'B', current_RRI]), 
                 cor(med[ratings == 'NR', ret_5], med[ratings == 'NR', current_RRI]), 
                 cor(med[ratings == 'X', ret_5], med[ratings == 'X', current_RRI]))

ret_10_c_med <- c(cor(med[ratings == 'AAA', ret_10], med[ratings == 'AAA', current_RRI]), 
                  cor(med[ratings == 'AA', ret_10], med[ratings == 'AA', current_RRI]), 
                  cor(med[ratings == 'A', ret_10], med[ratings == 'A', current_RRI]), 
                  cor(med[ratings == 'BBB', ret_10], med[ratings == 'BBB', current_RRI]), 
                  cor(med[ratings == 'BB', ret_10], med[ratings == 'BB', current_RRI]), 
                  cor(med[ratings == 'B', ret_10], med[ratings == 'B', current_RRI]), 
                  cor(med[ratings == 'NR', ret_10], med[ratings == 'NR', current_RRI]), 
                  cor(med[ratings == 'X', ret_10], med[ratings == 'X', current_RRI]))

ret_30_c_med <- c(cor(med[ratings == 'AAA', ret_30], med[ratings == 'AAA', current_RRI]), 
                  cor(med[ratings == 'AA', ret_30], med[ratings == 'AA', current_RRI]), 
                  cor(med[ratings == 'A', ret_30], med[ratings == 'A', current_RRI]), 
                  cor(med[ratings == 'BBB', ret_30], med[ratings == 'BBB', current_RRI]), 
                  cor(med[ratings == 'BB', ret_30], med[ratings == 'BB', current_RRI]), 
                  cor(med[ratings == 'B', ret_30], med[ratings == 'B', current_RRI]), 
                  cor(med[ratings == 'NR', ret_30], med[ratings == 'NR', current_RRI]), 
                  cor(med[ratings == 'X', ret_30], med[ratings == 'X', current_RRI]))

ret_180_c_med <- c(cor(med[ratings == 'AAA', ret_180], med[ratings == 'AAA', current_RRI]), 
                   cor(med[ratings == 'AA', ret_180], med[ratings == 'AA', current_RRI]), 
                   cor(med[ratings == 'A', ret_180], med[ratings == 'A', current_RRI]), 
                   cor(med[ratings == 'BBB', ret_180], med[ratings == 'BBB', current_RRI]), 
                   cor(med[ratings == 'BB', ret_180], med[ratings == 'BB', current_RRI]), 
                   cor(med[ratings == 'B', ret_180], med[ratings == 'B', current_RRI]), 
                   cor(med[ratings == 'NR', ret_180], med[ratings == 'NR', current_RRI]),
                   cor(med[ratings == 'X', ret_180], med[ratings == 'X', current_RRI]))

rating_ret_cor_c_med <- data.frame(ret_5_c_med, ret_10_c_med, ret_30_c_med, ret_180_c_med)
rownames(rating_ret_cor_c_med) <- c('AAA', 'AA', 'A', 'BBB', 'BB', 'B', 'NR', 'X')
rating_ret_cor_c_med

write.csv(rating_ret_cor_c_med, 'rating_ret_cor_c_med.csv')



ret_5_c_low <- c(cor(low[ratings == 'AAA', ret_5], low[ratings == 'AAA', current_RRI]), 
                 cor(low[ratings == 'AA', ret_5], low[ratings == 'AA', current_RRI]), 
                 cor(low[ratings == 'A', ret_5], low[ratings == 'A', current_RRI]), 
                 cor(low[ratings == 'BBB', ret_5], low[ratings == 'BBB', current_RRI]), 
                 cor(low[ratings == 'BB', ret_5], low[ratings == 'BB', current_RRI]), 
                 cor(low[ratings == 'B', ret_5], low[ratings == 'B', current_RRI]), 
                 cor(low[ratings == 'NR', ret_5], low[ratings == 'NR', current_RRI]), 
                 cor(low[ratings == 'X', ret_5], low[ratings == 'X', current_RRI]))

ret_10_c_low <- c(cor(low[ratings == 'AAA', ret_10], low[ratings == 'AAA', current_RRI]), 
                  cor(low[ratings == 'AA', ret_10], low[ratings == 'AA', current_RRI]), 
                  cor(low[ratings == 'A', ret_10], low[ratings == 'A', current_RRI]), 
                  cor(low[ratings == 'BBB', ret_10], low[ratings == 'BBB', current_RRI]), 
                  cor(low[ratings == 'BB', ret_10], low[ratings == 'BB', current_RRI]), 
                  cor(low[ratings == 'B', ret_10], low[ratings == 'B', current_RRI]), 
                  cor(low[ratings == 'NR', ret_10], low[ratings == 'NR', current_RRI]), 
                  cor(low[ratings == 'X', ret_10], low[ratings == 'X', current_RRI]))

ret_30_c_low <- c(cor(low[ratings == 'AAA', ret_30], low[ratings == 'AAA', current_RRI]), 
                  cor(low[ratings == 'AA', ret_30], low[ratings == 'AA', current_RRI]), 
                  cor(low[ratings == 'A', ret_30], low[ratings == 'A', current_RRI]), 
                  cor(low[ratings == 'BBB', ret_30], low[ratings == 'BBB', current_RRI]), 
                  cor(low[ratings == 'BB', ret_30], low[ratings == 'BB', current_RRI]), 
                  cor(low[ratings == 'B', ret_30], low[ratings == 'B', current_RRI]), 
                  cor(low[ratings == 'NR', ret_30], low[ratings == 'NR', current_RRI]), 
                  cor(low[ratings == 'X', ret_30], low[ratings == 'X', current_RRI]))

ret_180_c_low <- c(cor(low[ratings == 'AAA', ret_180], low[ratings == 'AAA', current_RRI]), 
                   cor(low[ratings == 'AA', ret_180], low[ratings == 'AA', current_RRI]), 
                   cor(low[ratings == 'A', ret_180], low[ratings == 'A', current_RRI]), 
                   cor(low[ratings == 'BBB', ret_180], low[ratings == 'BBB', current_RRI]), 
                   cor(low[ratings == 'BB', ret_180], low[ratings == 'BB', current_RRI]), 
                   cor(low[ratings == 'B', ret_180], low[ratings == 'B', current_RRI]), 
                   cor(low[ratings == 'NR', ret_180], low[ratings == 'NR', current_RRI]),
                   cor(low[ratings == 'X', ret_180], low[ratings == 'X', current_RRI]))

rating_ret_cor_c_low <- data.frame(ret_5_c_low, ret_10_c_low, ret_30_c_low, ret_180_c_low)
rownames(rating_ret_cor_c_low) <- c('AAA', 'AA', 'A', 'BBB', 'BB', 'B', 'NR', 'X')
rating_ret_cor_c_low

write.csv(rating_ret_cor_c_low, 'rating_ret_cor_c_low.csv')
```

Average Excess Returns Table & T Statistics
```
# Create the excess return table for >10
ex_ret_5 <- c(mean(data_10[ratings == 'AAA', ret_5 - `5_day_spy_ret`]),
              mean(data_10[ratings == 'AA', ret_5 - `5_day_spy_ret`]),
              mean(data_10[ratings == 'A', ret_5 - `5_day_spy_ret`]),
              mean(data_10[ratings == 'BBB', ret_5 - `5_day_spy_ret`]),
              mean(data_10[ratings == 'BB', ret_5 - `5_day_spy_ret`]),
              mean(data_10[ratings == 'B', ret_5 - `5_day_spy_ret`]),
              mean(data_10[ratings == 'NR', ret_5 - `5_day_spy_ret`]),
              mean(data_10[ratings == 'X', ret_5 - `5_day_spy_ret`]))

ex_ret_10 <- c(mean(data_10[ratings == 'AAA', ret_10 - `10_day_spy_ret`]),
               mean(data_10[ratings == 'AA', ret_10 - `10_day_spy_ret`]),
               mean(data_10[ratings == 'A', ret_10 - `10_day_spy_ret`]),
               mean(data_10[ratings == 'BBB', ret_10 - `10_day_spy_ret`]),
               mean(data_10[ratings == 'BB', ret_10 - `10_day_spy_ret`]),
               mean(data_10[ratings == 'B', ret_10 - `10_day_spy_ret`]),
               mean(data_10[ratings == 'NR', ret_10 - `10_day_spy_ret`]),
               mean(data_10[ratings == 'X', ret_10 - `10_day_spy_ret`]))

ex_ret_30 <- c(mean(data_10[ratings == 'AAA', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_10[ratings == 'AA', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_10[ratings == 'A', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_10[ratings == 'BBB', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_10[ratings == 'BB', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_10[ratings == 'B', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_10[ratings == 'NR', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_10[ratings == 'X', ret_30 - `30_day_ret`], na.rm=TRUE))

ratings_exret <- data.table(ex_ret_5, ex_ret_10, ex_ret_30)
rownames(ratings_exret) <- c('AAA', 'AA', 'A', 'BBB', 'BB', 'B', 'NR', 'X')

# T Statistics
sd <- c(sd(data_10[ratings == 'AAA', ret_5 - `5_day_spy_ret`]),
        sd(data_10[ratings == 'AA', ret_5 - `5_day_spy_ret`]),
        sd(data_10[ratings == 'A', ret_5 - `5_day_spy_ret`]),
        sd(data_10[ratings == 'BBB', ret_5 - `5_day_spy_ret`]),
        sd(data_10[ratings == 'BB', ret_5 - `5_day_spy_ret`]),
        sd(data_10[ratings == 'B', ret_5 - `5_day_spy_ret`]),
        sd(data_10[ratings == 'NR', ret_5 - `5_day_spy_ret`]),
        sd(data_10[ratings == 'X', ret_5 - `5_day_spy_ret`]))
n <- c(length(data_10[ratings == 'AAA', ret_5 - `5_day_spy_ret`]),
       length(data_10[ratings == 'AA', ret_5 - `5_day_spy_ret`]),
       length(data_10[ratings == 'A', ret_5 - `5_day_spy_ret`]),
       length(data_10[ratings == 'BBB', ret_5 - `5_day_spy_ret`]),
       length(data_10[ratings == 'BB', ret_5 - `5_day_spy_ret`]),
       length(data_10[ratings == 'B', ret_5 - `5_day_spy_ret`]),
       length(data_10[ratings == 'NR', ret_5 - `5_day_spy_ret`]),
       length(data_10[ratings == 'X', ret_5 - `5_day_spy_ret`]))
se <- sd/sqrt(n)
t_5 <- ratings_exret$ex_ret_5/se

sd <- c(sd(data_10[ratings == 'AAA', ret_10 - `10_day_spy_ret`]), 
        sd(data_10[ratings == 'AA', ret_10 - `10_day_spy_ret`]),
        sd(data_10[ratings == 'A', ret_10 - `10_day_spy_ret`]),
        sd(data_10[ratings == 'BBB', ret_10 - `10_day_spy_ret`]),
        sd(data_10[ratings == 'BB', ret_10 - `10_day_spy_ret`]),
        sd(data_10[ratings == 'B', ret_10 - `10_day_spy_ret`]),
        sd(data_10[ratings == 'NR', ret_10 - `10_day_spy_ret`]),
        sd(data_10[ratings == 'X', ret_10 - `10_day_spy_ret`]))

n <- c(length(data_10[ratings == 'AAA', ret_10 - `10_day_spy_ret`]), 
       length(data_10[ratings == 'AA', ret_10 - `10_day_spy_ret`]),
       length(data_10[ratings == 'A', ret_10 - `10_day_spy_ret`]),
       length(data_10[ratings == 'BBB', ret_10 - `10_day_spy_ret`]),
       length(data_10[ratings == 'BB', ret_10 - `10_day_spy_ret`]),
       length(data_10[ratings == 'B', ret_10 - `10_day_spy_ret`]),
       length(data_10[ratings == 'NR', ret_10 - `10_day_spy_ret`]),
       length(data_10[ratings == 'X', ret_10 - `10_day_spy_ret`]))
se <- sd/sqrt(n)
t_10 <- ratings_exret$ex_ret_10/se

sd<- c(sd(data_10[ratings == 'AAA', ret_30 - `30_day_ret`], na.rm=TRUE), 
       sd(data_10[ratings == 'AA', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_10[ratings == 'A', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_10[ratings == 'BBB', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_10[ratings == 'BB', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_10[ratings == 'B', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_10[ratings == 'NR', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_10[ratings == 'X', ret_30 - `30_day_ret`], na.rm=TRUE))
se <- sd/sqrt(n)
t_30 <- ratings_exret$ex_ret_30/se

t <- data.table(t_5, t_10, t_30)
rownames(t) <- c('AAA', 'AA', 'A', 'BBB', 'BB', 'B', 'NR', 'X')
write.csv(t, 't.csv')

# Annualize the excess returns
ratings_exret[, ex_ret_5 := (1+ex_ret_5)^(252/5)-1]
ratings_exret[, ex_ret_10 := (1+ex_ret_10)^(252/10)-1]
ratings_exret[, ex_ret_30 := (1+ex_ret_30)^(252/30)-1]
ratings_exret
write.csv(ratings_exret, 'ratings_exret_10.csv')




# More cases: >5
ex_ret_5 <- c(mean(data_5[ratings == 'AAA', ret_5 - `5_day_spy_ret`]),
              mean(data_5[ratings == 'AA', ret_5 - `5_day_spy_ret`]),
              mean(data_5[ratings == 'A', ret_5 - `5_day_spy_ret`]),
              mean(data_5[ratings == 'BBB', ret_5 - `5_day_spy_ret`]),
              mean(data_5[ratings == 'BB', ret_5 - `5_day_spy_ret`]),
              mean(data_5[ratings == 'B', ret_5 - `5_day_spy_ret`]),
              mean(data_5[ratings == 'NR', ret_5 - `5_day_spy_ret`]),
              mean(data_5[ratings == 'X', ret_5 - `5_day_spy_ret`]))

ex_ret_10 <- c(mean(data_5[ratings == 'AAA', ret_10 - `10_day_spy_ret`]),
               mean(data_5[ratings == 'AA', ret_10 - `10_day_spy_ret`]),
               mean(data_5[ratings == 'A', ret_10 - `10_day_spy_ret`]),
               mean(data_5[ratings == 'BBB', ret_10 - `10_day_spy_ret`]),
               mean(data_5[ratings == 'BB', ret_10 - `10_day_spy_ret`]),
               mean(data_5[ratings == 'B', ret_10 - `10_day_spy_ret`]),
               mean(data_5[ratings == 'NR', ret_10 - `10_day_spy_ret`]),
               mean(data_5[ratings == 'X', ret_10 - `10_day_spy_ret`]))

ex_ret_30 <- c(mean(data_5[ratings == 'AAA', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_5[ratings == 'AA', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_5[ratings == 'A', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_5[ratings == 'BBB', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_5[ratings == 'BB', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_5[ratings == 'B', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_5[ratings == 'NR', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_5[ratings == 'X', ret_30 - `30_day_ret`], na.rm=TRUE))

ratings_exret <- data.table(ex_ret_5, ex_ret_10, ex_ret_30)
rownames(ratings_exret) <- c('AAA', 'AA', 'A', 'BBB', 'BB', 'B', 'NR', 'X')

# T Statistics
sd <- c(sd(data_5[ratings == 'AAA', ret_5 - `5_day_spy_ret`]),
        sd(data_5[ratings == 'AA', ret_5 - `5_day_spy_ret`]),
        sd(data_5[ratings == 'A', ret_5 - `5_day_spy_ret`]),
        sd(data_5[ratings == 'BBB', ret_5 - `5_day_spy_ret`]),
        sd(data_5[ratings == 'BB', ret_5 - `5_day_spy_ret`]),
        sd(data_5[ratings == 'B', ret_5 - `5_day_spy_ret`]),
        sd(data_5[ratings == 'NR', ret_5 - `5_day_spy_ret`]),
        sd(data_5[ratings == 'X', ret_5 - `5_day_spy_ret`]))
n <- c(length(data_5[ratings == 'AAA', ret_5 - `5_day_spy_ret`]),
       length(data_5[ratings == 'AA', ret_5 - `5_day_spy_ret`]),
       length(data_5[ratings == 'A', ret_5 - `5_day_spy_ret`]),
       length(data_5[ratings == 'BBB', ret_5 - `5_day_spy_ret`]),
       length(data_5[ratings == 'BB', ret_5 - `5_day_spy_ret`]),
       length(data_5[ratings == 'B', ret_5 - `5_day_spy_ret`]),
       length(data_5[ratings == 'NR', ret_5 - `5_day_spy_ret`]),
       length(data_5[ratings == 'X', ret_5 - `5_day_spy_ret`]))
se <- sd/sqrt(n)
t_5 <- ratings_exret$ex_ret_5/se

sd <- c(sd(data_5[ratings == 'AAA', ret_10 - `10_day_spy_ret`]), 
        sd(data_5[ratings == 'AA', ret_10 - `10_day_spy_ret`]),
        sd(data_5[ratings == 'A', ret_10 - `10_day_spy_ret`]),
        sd(data_5[ratings == 'BBB', ret_10 - `10_day_spy_ret`]),
        sd(data_5[ratings == 'BB', ret_10 - `10_day_spy_ret`]),
        sd(data_5[ratings == 'B', ret_10 - `10_day_spy_ret`]),
        sd(data_5[ratings == 'NR', ret_10 - `10_day_spy_ret`]),
        sd(data_5[ratings == 'X', ret_10 - `10_day_spy_ret`]))

n <- c(length(data_5[ratings == 'AAA', ret_10 - `10_day_spy_ret`]), 
       length(data_5[ratings == 'AA', ret_10 - `10_day_spy_ret`]),
       length(data_5[ratings == 'A', ret_10 - `10_day_spy_ret`]),
       length(data_5[ratings == 'BBB', ret_10 - `10_day_spy_ret`]),
       length(data_5[ratings == 'BB', ret_10 - `10_day_spy_ret`]),
       length(data_5[ratings == 'B', ret_10 - `10_day_spy_ret`]),
       length(data_5[ratings == 'NR', ret_10 - `10_day_spy_ret`]),
       length(data_5[ratings == 'X', ret_10 - `10_day_spy_ret`]))
se <- sd/sqrt(n)
t_10 <- ratings_exret$ex_ret_10/se

sd<- c(sd(data_5[ratings == 'AAA', ret_30 - `30_day_ret`], na.rm=TRUE), 
       sd(data_5[ratings == 'AA', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_5[ratings == 'A', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_5[ratings == 'BBB', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_5[ratings == 'BB', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_5[ratings == 'B', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_5[ratings == 'NR', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_5[ratings == 'X', ret_30 - `30_day_ret`], na.rm=TRUE))
se <- sd/sqrt(n)
t_30 <- ratings_exret$ex_ret_30/se

t <- data.table(t_5, t_10, t_30)
rownames(t) <- c('AAA', 'AA', 'A', 'BBB', 'BB', 'B', 'NR', 'X')
t
write.csv(t, 't5.csv')

# Annualize the excess returns
ratings_exret[, ex_ret_5 := (1+ex_ret_5)^(252/5)-1]
ratings_exret[, ex_ret_10 := (1+ex_ret_10)^(252/10)-1]
ratings_exret[, ex_ret_30 := (1+ex_ret_30)^(252/30)-1]
write.csv(ratings_exret, 'ratings_exret_5.csv')





# More cases: >20
ex_ret_5 <- c(mean(data_20[ratings == 'AAA', ret_5 - `5_day_spy_ret`]),
              mean(data_20[ratings == 'AA', ret_5 - `5_day_spy_ret`]),
              mean(data_20[ratings == 'A', ret_5 - `5_day_spy_ret`]),
              mean(data_20[ratings == 'BBB', ret_5 - `5_day_spy_ret`]),
              mean(data_20[ratings == 'BB', ret_5 - `5_day_spy_ret`]),
              mean(data_20[ratings == 'B', ret_5 - `5_day_spy_ret`]),
              mean(data_20[ratings == 'NR', ret_5 - `5_day_spy_ret`]),
              mean(data_20[ratings == 'X', ret_5 - `5_day_spy_ret`]))

ex_ret_10 <- c(mean(data_20[ratings == 'AAA', ret_10 - `10_day_spy_ret`]),
               mean(data_20[ratings == 'AA', ret_10 - `10_day_spy_ret`]),
               mean(data_20[ratings == 'A', ret_10 - `10_day_spy_ret`]),
               mean(data_20[ratings == 'BBB', ret_10 - `10_day_spy_ret`]),
               mean(data_20[ratings == 'BB', ret_10 - `10_day_spy_ret`]),
               mean(data_20[ratings == 'B', ret_10 - `10_day_spy_ret`]),
               mean(data_20[ratings == 'NR', ret_10 - `10_day_spy_ret`]),
               mean(data_20[ratings == 'X', ret_10 - `10_day_spy_ret`]))

ex_ret_30 <- c(mean(data_20[ratings == 'AAA', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_20[ratings == 'AA', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_20[ratings == 'A', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_20[ratings == 'BBB', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_20[ratings == 'BB', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_20[ratings == 'B', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_20[ratings == 'NR', ret_30 - `30_day_ret`], na.rm=TRUE),
               mean(data_20[ratings == 'X', ret_30 - `30_day_ret`], na.rm=TRUE))

ratings_exret <- data.table(ex_ret_5, ex_ret_10, ex_ret_30)
rownames(ratings_exret) <- c('AAA', 'AA', 'A', 'BBB', 'BB', 'B', 'NR', 'X')

# T Statistics
sd <- c(sd(data_20[ratings == 'AAA', ret_5 - `5_day_spy_ret`]),
        sd(data_20[ratings == 'AA', ret_5 - `5_day_spy_ret`]),
        sd(data_20[ratings == 'A', ret_5 - `5_day_spy_ret`]),
        sd(data_20[ratings == 'BBB', ret_5 - `5_day_spy_ret`]),
        sd(data_20[ratings == 'BB', ret_5 - `5_day_spy_ret`]),
        sd(data_20[ratings == 'B', ret_5 - `5_day_spy_ret`]),
        sd(data_20[ratings == 'NR', ret_5 - `5_day_spy_ret`]),
        sd(data_20[ratings == 'X', ret_5 - `5_day_spy_ret`]))
n <- c(length(data_20[ratings == 'AAA', ret_5 - `5_day_spy_ret`]),
       length(data_20[ratings == 'AA', ret_5 - `5_day_spy_ret`]),
       length(data_20[ratings == 'A', ret_5 - `5_day_spy_ret`]),
       length(data_20[ratings == 'BBB', ret_5 - `5_day_spy_ret`]),
       length(data_20[ratings == 'BB', ret_5 - `5_day_spy_ret`]),
       length(data_20[ratings == 'B', ret_5 - `5_day_spy_ret`]),
       length(data_20[ratings == 'NR', ret_5 - `5_day_spy_ret`]),
       length(data_20[ratings == 'X', ret_5 - `5_day_spy_ret`]))
se <- sd/sqrt(n)
t_5 <- ratings_exret$ex_ret_5/se

sd <- c(sd(data_20[ratings == 'AAA', ret_10 - `10_day_spy_ret`]), 
        sd(data_20[ratings == 'AA', ret_10 - `10_day_spy_ret`]),
        sd(data_20[ratings == 'A', ret_10 - `10_day_spy_ret`]),
        sd(data_20[ratings == 'BBB', ret_10 - `10_day_spy_ret`]),
        sd(data_20[ratings == 'BB', ret_10 - `10_day_spy_ret`]),
        sd(data_20[ratings == 'B', ret_10 - `10_day_spy_ret`]),
        sd(data_20[ratings == 'NR', ret_10 - `10_day_spy_ret`]),
        sd(data_20[ratings == 'X', ret_10 - `10_day_spy_ret`]))

n <- c(length(data_20[ratings == 'AAA', ret_10 - `10_day_spy_ret`]), 
       length(data_20[ratings == 'AA', ret_10 - `10_day_spy_ret`]),
       length(data_20[ratings == 'A', ret_10 - `10_day_spy_ret`]),
       length(data_20[ratings == 'BBB', ret_10 - `10_day_spy_ret`]),
       length(data_20[ratings == 'BB', ret_10 - `10_day_spy_ret`]),
       length(data_20[ratings == 'B', ret_10 - `10_day_spy_ret`]),
       length(data_20[ratings == 'NR', ret_10 - `10_day_spy_ret`]),
       length(data_20[ratings == 'X', ret_10 - `10_day_spy_ret`]))
se <- sd/sqrt(n)
t_10 <- ratings_exret$ex_ret_10/se

sd<- c(sd(data_20[ratings == 'AAA', ret_30 - `30_day_ret`], na.rm=TRUE), 
       sd(data_20[ratings == 'AA', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_20[ratings == 'A', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_20[ratings == 'BBB', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_20[ratings == 'BB', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_20[ratings == 'B', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_20[ratings == 'NR', ret_30 - `30_day_ret`], na.rm=TRUE),
       sd(data_20[ratings == 'X', ret_30 - `30_day_ret`], na.rm=TRUE))
se <- sd/sqrt(n)
t_30 <- ratings_exret$ex_ret_30/se

t <- data.table(t_5, t_10, t_30)
rownames(t) <- c('AAA', 'AA', 'A', 'BBB', 'BB', 'B', 'NR', 'X')
t
write.csv(t, 't20.csv')

# Annualize the excess returns
ratings_exret[, ex_ret_5 := (1+ex_ret_5)^(252/5)-1]
ratings_exret[, ex_ret_10 := (1+ex_ret_10)^(252/10)-1]
ratings_exret[, ex_ret_30 := (1+ex_ret_30)^(252/30)-1]
write.csv(ratings_exret, 'ratings_exret_20.csv')
```

Alphas & Betas
```
# Alphas and Betas
df <- fread("data_10 (2).csv")
head(df)

#30 day Pf vs spy
model_30 <- lm(df$ret_30 ~ df$`30_day_ret`)
summary(model_30)

model_30_alpha <- model_30$coefficients[1]
model_30_alpha 
model_30_beta <- model_30$coefficients[2]
model_30_beta

#10 day Pf vs spy

model_10 <- lm(df$ret_10 ~ df$`10_day_spy_ret`)
summary(model_10)

model_10_alpha <- model_10$coefficients[1]
model_10_alpha
model_10_beta <- model_10$coefficients[2]
model_10_beta

#5 day Pf vs spy

model_5 <- lm(df$ret_5 ~ df$`5_day_spy_ret`)
summary(model_5)

model_5_alpha <- model_5$coefficients[1]
model_5_alpha
model_5_beta <- model_5$coefficients[2]
model_5_beta


# Ratings AAA
ratings_AAA <- df[ratings == 'AAA' , c('ret_30', 'ret_10','ret_5', '5_day_spy_ret','10_day_spy_ret','30_day_ret')]
ratings_AAA

model_AAA_30 <- lm(ratings_AAA$ret_30 ~ ratings_AAA$`30_day_ret`)
summary(model_AAA_30) 
#0.03496
#0.24376

model_AAA_10 <- lm(ratings_AAA$ret_10 ~ ratings_AAA$`10_day_spy_ret`)
summary(model_AAA_10)
#-0.013610
#1.468055

model_AAA_5 <- lm(ratings_AAA$ret_5 ~ ratings_AAA$`5_day_spy_ret`)
summary(model_AAA_5)
#-0.019472
#2.454115


# ratings AA
ratings_AA <- df[ratings == 'AA' , c('ret_30', 'ret_10','ret_5', '5_day_spy_ret','10_day_spy_ret','30_day_ret')]
ratings_AA

model_AA_30 <- lm(ratings_AA$ret_30 ~ ratings_AA$`30_day_ret`)
summary(model_AA_30) 

#-0.00424
#1.16928

model_AA_10 <- lm(ratings_AA$ret_10 ~ ratings_AA$`10_day_spy_ret`)
summary(model_AA_10)

#-0.005039
#1.229519

model_AA_5 <- lm(ratings_AA$ret_5 ~ ratings_AA$`5_day_spy_ret`)
summary(model_AA_5)
#-0.006453
#1.270732


#ratings A
ratings_A <- df[ratings == 'A' , c('ret_30', 'ret_10','ret_5', '5_day_spy_ret','10_day_spy_ret','30_day_ret')]
ratings_A

model_A_30 <- lm(ratings_A$ret_30 ~ ratings_A$`30_day_ret`)
summary(model_A_30) 
#-0.002665
#0.952869

model_A_10 <- lm(ratings_A$ret_10 ~ ratings_A$`10_day_spy_ret`)
summary(model_A_10)
#0.004253
#0.875958

model_A_5 <- lm(ratings_A$ret_5 ~ ratings_A$`5_day_spy_ret`)
summary(model_A_5)
#0.0009832
#0.7899841


#Ratings BBB
ratings_BBB <- df[ratings == 'BBB' , c('ret_30', 'ret_10','ret_5', '5_day_spy_ret','10_day_spy_ret','30_day_ret')]
ratings_BBB

model_BBB_30 <- lm(ratings_BBB$ret_30 ~ ratings_BBB$`30_day_ret`)
summary(model_BBB_30) 
#-0.004562
#1.163415

model_BBB_10 <- lm(ratings_BBB$ret_10 ~ ratings_BBB$`10_day_spy_ret`)
summary(model_BBB_10)
#-0.0008108
#1.2086962

model_BBB_5 <- lm(ratings_BBB$ret_5 ~ ratings_BBB$`5_day_spy_ret`)
summary(model_BBB_5)
#-0.000901
#1.073146


#Ratings BB
ratings_BB <- df[ratings == 'BB' , c('ret_30', 'ret_10','ret_5', '5_day_spy_ret','10_day_spy_ret','30_day_ret')]
ratings_BB

model_BB_30 <- lm(ratings_BB$ret_30 ~ ratings_BB$`30_day_ret`)
summary(model_BB_30) 
#-0.001674
#1.928403

model_BB_10 <- lm(ratings_BB$ret_10 ~ ratings_BB$`10_day_spy_ret`)
summary(model_BB_10)
#0.002108
#1.419596

model_BB_5 <- lm(ratings_BB$ret_5 ~ ratings_BB$`5_day_spy_ret`)
summary(model_BB_5)
#0.001062
#1.217683


#Ratings B

ratings_B <- df[ratings == 'B' , c('ret_30', 'ret_10','ret_5', '5_day_spy_ret','10_day_spy_ret','30_day_ret')]
ratings_B

model_B_30 <- lm(ratings_B$ret_30 ~ ratings_B$`30_day_ret`)
summary(model_B_30) 
#0.05815
#2.46478

model_B_10 <- lm(ratings_B$ret_10 ~ ratings_B$`10_day_spy_ret`)
summary(model_B_10)
#0.01803
#2.35661

model_B_5 <- lm(ratings_B$ret_5 ~ ratings_B$`5_day_spy_ret`)
summary(model_B_5)
#0.004328
#2.969216
```
