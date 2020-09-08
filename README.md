# Stock-Prediction-LSTM-AAPL
if loading fail on the github, please go to this link to see the code online: https://nbviewer.jupyter.org/github/Bucky-Cheng/Stock-Prediction-LSTM-AAPL/blob/master/LSTM_Stock_AAPL_G_1.ipynb
# Predict AAPL Stock Close Price

## Compare the consequent wheather using some Technical Indicators
## Compare the consequent the price gap prediction and MinMAXScaler Price prediction
### pipeline
1.import data<br>
2.data cleaning<br>
3.add technical indicators<br>
4.technical indicators visualization<br>
5.technical indicators interpretation<br>
6.more feature engineering<br>
7.rebuild dataset, split train/val/test set<br>
8.create model(LSTM)<br>
9.train model, prediction<br>
10.compare prediction<br>
11.conclusion and future<br>

# data 1: Add technical indicators

Date<br>
Open<br>
High<br>
Close<br>
Adj Close<br>
Day of week<br>
Close price mean<br>
Close price Variance<br>
Close price tandard deviation<br>
##  technical indicators
 
 Stochastic Relative Strength Index (StoRSI) and RSI<br>
 %K and %D<br>
 Chaikin Money Flow(CMF)<br>
 Parabolic SAR<br>
 Rate of Change<br>
 Volume Weighted Average Price (VWAP)<br>
 Momentum 10Days<br>
 Moving Average Convergence Divergence(MACD)<br>
 Average Directional Movement Index (ADX) <br>
 Williams %R<br>
 The Ichimoku Cloud<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Conversion Line<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Base Line<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Leading Span A<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Leading Span B<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Cloud(Leading Span A, Leading Span B)<br>
Bollinger Bands<br>

# data 2: Raw data
Date<br>
Open<br>
High<br>
Close<br>
Adj Close<br>
# split data, (train, val, test)
### 30 data for test<br>
### 1 data for val<br>
### others for train<br>
## Option 1
## Use the gap of previous day.
### (today close/precious day close)-1
#### 0th-9th day train --------------- 10th day for prediction
#### 1st-10th day train --------------- 11th day for prediction
#### 2nd-11th day train --------------- 12th day for prediction
#### .....
## Option 2
### Put the data fit the MinMaxScaler, the Stock values between 0 and 1

# Evaluation, Conclusion and Future
## Data 1 the gap of previous day prediction
![image](https://github.com/Bucky-Cheng/Stock-Prediction-LSTM-AAPL/blob/master/data1_gap.png)
Data 1 MSE:0.0005706506187007371
## Data 2 the gap of previous day prediction
![image](https://github.com/Bucky-Cheng/Stock-Prediction-LSTM-AAPL/blob/master/data2_gap.png)
Data 2 MSE:0.0008784179054824572
### The line chart illustrate the difference clearly. The data1 is much better than data2, and data2 line is like a stright line after 5th, which have not any help, the price will remain same as previous day. So, the technical indiacators are prvide the meaningful features for the price predication.

### But, there are some problems, the trend can't remain the one direction 2days, like the 13th-15th, when up to 14th from 13th, the trend change the direction to bottom, but the truth remian upward. And the 20th, the price has a big rising, but model can not to predict this big rising, and this the limitation of the dataset which only have price.

### The model can not to predict big suddenly increasing, so I think we need to use the News or Filings to identify this situation, the 20th is 30/07/2020, and Apple reported Third Quarter Results Reports, which is called a historically strong quarter, a lot of News report this and all have the positive sentiments, for example, the News of CNBC which said "Apple posts blowout third quarter, with sales up 11% despite coronavirus disruptions "(URL: https://www.cnbc.com/2020/07/30/apple-aapl-earnings-q3-2020.html).

### So, I believe the News, filings and reports are significant features for stock predication, and I will using NLP to research it ,for example use BERT to analysis sentiments.

## Data 1 price prediction
![image](https://github.com/Bucky-Cheng/Stock-Prediction-LSTM-AAPL/blob/master/data1_price.png)
Data 1 Close Price MSE:90.61528315553844
## Data 2 price prediction
![image](https://github.com/Bucky-Cheng/Stock-Prediction-LSTM-AAPL/blob/master/data2_price.png)
Data 2 Close Price MSE:135.424431323489


## Conclusion
### The difference between different data is very clearly. And it shows the data 1 option 1 has the best score.The data 1 option 1 has technical indicators and rebuild to the gap of previous dayCclose Price, Adj Close Price, and to predict the gap of previous day.
### The MSE of gap prediction with data 1 is 0.00044, and the MSE of gap prediciton with data 2 is 0.00085. And the final result, the MSE of data 1 price prediction is 86.1199, the MSE of data 2 price prediction is 166.3624.
### So, the data has technical indicators and try to predict gap is much better than raw data to predict gap or price.
### But, the predication has bias with the true price, so this model still have many problems, and there is serious problem, the stock movement is not precise, the stock movement is the one of important features of stock and stock prediction. And, as we know, the stock market is very complicated, so only to use the history data and technical indicators is insufficient.

## Future
### The stock market is really complicated, it has a lot of influencing factors, such as the golobal economy situation, politics and others. So, the predict stock market is a very complex task, and in the real life, we need predict a lot of different stocks, select the some stocks and build up a stable wonderful financial investment portfolio. Every different stock has different influencing factors.

### Since, a lot of external factors influence the stock market, so the Twitter, News, and annual reports 10-K 10-Q filings are very important for the stock movement prediction, and I am researching that using NLP technology, for example, BERT to analysis the Twitter, New, Filings sentiments, and believe it will to generate some significant features to stock dataset.

### As we see in this note, the technical indicators are important to stock predictions, so I believe the technical indicators are impotant features in the stock predication dataset. But in the note, the iterpretation of technical indicators have room for improvement.
### And we also realize that data only have price has limitation, the News or Filings are vety important, so I will to research the News, Filings and Report influence, using BERT to analysis sentiment.
### May be we can add Autoregressive Integrated Moving Average (ARIMA) which is a popular techniques for values prediction before the neural network era, and add it in the dataset if it can provide the important feature. And also wil do more complicated feature enginnerring and feature importance.

### At the model part, may be we can use  Generative Adversarial Network (GAN), LSTM and CNN, and to use the Bayesian optimisation to tune the GAN model hyper parameters. But, this is just some thinking and potential strategy, and I will to study it and may be to implement it.

# Disclaimer
### This note only use to study and researching. It is no providing any invesment suggestions, strategies and predictions. All investments have significant risk.
### All investments and all strategies are used at your own risk.

# Thanks for watching and welcome to leave comments
