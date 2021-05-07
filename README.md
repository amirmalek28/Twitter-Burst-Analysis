# Twitter-Burst-Analysis

## Comparative Analysis between Bursty Twitter Events and Real-Time Trends


The data for this project was collected with rtweet, an R package that uses Twitter’s REST and stream API to collect and organize tweets. The goal of the data collection process was to collect tweets over several hours such that an analysis could be performed over several cycles and updates of Twitter’s trend list. As mentioned previously, trends are updated in real time, so it was important to collect data regularly.

Using rtweet, we designed a data crawler which streams live tweets for 2 minutes, then sleep for 15 minutes before running the next iteration. Although the rtweet package does support random tweet selection, the function prioritized recent tweets without the ability to specify a time range with a uniform distribution. Thus, the best option was to simulate a random sampling of data by using the stream_tweets function, which collects a live stream of Twitter data when called. With the stream duration and sleep duration parameters set to 2 minutes and 15 minutes, respectively, we were able to collect on average 1000 tweets every 15 minutes. The data crawler was then set to run for around 24 hours, resulting in a randomly sampled dataset of around 50,000 tweets.

![Figure 1](/figures/tweet_stream_frequency.png)

In order to discover latent structure or correlation among the data, we performed several data manipulations to consolidate all of the data and metrics in one dataframe. First, we iterate through all instances of the trends list from various times of day, appending each instance as one column. We can then compute the mean, minimum, and best ranking for each trend in the dataframe (called all_trends_ranked). Next, we iterate through each row of this dataframe, and compute the mean, minimum and maximum of the burstiness level and duration for each trend, and also append the number of mentions of the trend, computed by filtering from the top features of the dfm.

![Table 1](/figures/all_trends_ranked_df.png)

Using the dataframe shown above, we can plot various relationships that provide some insight into how Twitter trends are determined.

![Figure 2](/figures/plot1.png)
![Figure 3](/figures/plot2.png)
![Figure 4](/figures/plot3.png)
![Figure 5](/figures/plot4.png)
