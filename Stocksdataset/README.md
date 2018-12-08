# S&P 500 stock data
Results using the S&P 500 stock dataset: https://www.kaggle.com/camnugent/sandp500

The dataset is composed of the historical stock prices (last 5 years) for all the companies currently found on the S&P 500 index. We extracted the daily average value of the stocks; each time series contains a month of measurement of a certain stock.
Our goal is to generate fake new time series that mimic the distribution of the original S&P 500 index.
We are able to generate new data without anonymization:

The results are accurate, but it is still possible to identify the different companies present in the index.

![Alt text](pub1plot_sensor42.png?raw=true "Title")

Moreover, we can generate new time-series in a private, anonymized manner (epsilon = 8):

![Alt text](priv1plot_sensor543.png?raw=true "Title")

In this case it is no more possible to associate a certain time series with a company; in addition, a weird behaviour of a stock in a certain month is filtered by the dp-GAN
