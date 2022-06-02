# How Does Significant Exposure to ESG Risks Affect Short-term Stock Returns for Companies of Different Health Levels?


Tiancheng Xu, Ford Danielsen, Rishabh Kumar, Rama Sai Sundar Ryali, Evelyn Zhang

Apr 2022


## The goal
To Understand the Impact of ESG Risk Exposures on Short-term Stock Returns


## Executive Summary
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
Objective: To understand the data with reference to credit ratings and ESG

<img width="253" alt="image" src="https://user-images.githubusercontent.com/63265930/171700813-2e68e106-d5cc-4163-adae-525d56098eb2.png">
<img width="329" alt="image" src="https://user-images.githubusercontent.com/63265930/171700849-8b2d1b45-10ac-4311-8fed-acd832ff626e.png">

Most of the companies in our data fall in the 'good' credit rating zone (A, BBB and BB).

Companies in the 'good' credit rating zone have highest number of ESG events.

Peak reprisk index decreases as the health of a company decreases.


### RRI TRENDS BY RATINGS
Objective: To understand the ESG risk exposure based on the health of an organization 

<img width="530" alt="image" src="https://user-images.githubusercontent.com/63265930/171701121-e39ac2e8-0b24-4b58-a398-58ae0b1cc46f.png">

The RRI for each rating can be seen to fluctuate within their respective ranges, with overlapping at only few points.

Historically, companies with better health (ratings) are shown to have higher exposure to ESG risk and vice versa.


### LONG/SHORT TERM RETURNS BY ESG RISK
Objective: To understand the impact of ESG risk exposure in different ratings on short- and long-term returns

<img width="611" alt="image" src="https://user-images.githubusercontent.com/63265930/171701532-04b5eca9-d6b9-45d1-809f-ce22e0f33449.png">
<img width="573" alt="image" src="https://user-images.githubusercontent.com/63265930/171701708-b142456e-bd44-40dd-a8d4-a0a36c859a9f.png">

We try to observe a general trend linkage between increase in the reprisk index and change in return.

These trends are observed over different ratings to establish if health of a company controls the return changes when there is negative ESG news.

There are multiple factors that influence the return of a stock but with the intention of understanding changes in stock return with ESG risk, we observe a divergence movement in high rated stocks.



###
