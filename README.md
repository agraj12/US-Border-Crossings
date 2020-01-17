# US-Border-Crossings
This project aims to draw insights about the US-Mexico and US-Canada border crossings based on the data provided by the Bureau of Transportation Statistics (BTS) ranging from 1996 to 2018. The data is broadly divided into passenger traffic and commercial traffic. 

The dataset had about 370k rows and 8 columns drilled down to the port of entry level. Our first step was to understand the trends of border crossings over the years (1996-2018). Based on these, we aimed to identify the busiest states for entry into the US along its border with Mexico and Canada. Next, we pinpointed to all the ports of entry in the top 3 busiest states, namely New York, Texas and California, using interactive maps. Post this initial analysis, we ran a regression model to predict the future trends.

Since the most interesting aspect of the data is passenger traffic and trends of people crossing the border, we have isolated that data to perform a regression analysis using ordinary least squares model with the parameters such as year, state and means of transportation used. 

Computational challenges here were the size of the data and time taken for the regression model to run. Random sampling was not an option since there was a possibility that the sample would be skewed or imbalanced based on year. For example, we could not use data between 1996 and 2000 to predict the trends post 2018. 
To tackle the data size issue, we decided to strategically sample the data into buckets based on the year. We split the data starting from 2018 and backtracking year wise since the trends post 2018 would be more dependent on the recent years. Using this approach, we came up with 5 subsets ranging from 2018-2013, 2018-2008, 2018-2004, 2018-2000 & 2018-1996.

After running our regression model on the strategically sampled buckets, we found that the metric for model accuracy (R-sq) showed a decreasing trend as the data increased (moving backwards from 2018). This is highly unusual since in most regression problems, as the number of observations increase, the models tend to perform better. However, the discrepancy in our model can be fully attributed to the volatile nature of the political situations over the years. Different administrations enforce different immigration policies thereby fluctuating the border crossings drastically. So, when we include a greater number of years, the data becomes more random, thereby negatively impacting the model performance. 

•	Kaggle Data Source: https://www.kaggle.com/akhilv11/border-crossing-entry-data 
