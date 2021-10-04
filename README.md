<h1 align="center">Algorithmic Trading Enhancements</h1>

## Overview of the Algorithmic Trading Enhancements

The baseline algorithmic trading system that is being used has been very effective to the firm and has gained profits by users. Although this system is good, there is always room for improvement. We have narrowed down the be best enhancements for this system to better the predictive models. We went through multiple testings to find the best outcome possible. It's our goal to keep our competitive edge on our market.

## Results

<details>
<summary>Baseline</summary>
 
Our baseline consisted of using the rolling average of short and long windows of our data. We created signals to tell us when to buy stock (1) and when to sell stock (-1). 
 
```
short_window = 4
long_window = 100
  
signals_df['SMA_Fast'] = signals_df['close'].rolling(window=short_window).mean()
signals_df['SMA_Slow'] = signals_df['close'].rolling(window=long_window).mean()  
 
signals_df['Signal'] = 0.0
signals_df.loc[(signals_df['Actual Returns'] >= 0), 'Signal'] = 1 
signals_df.loc[(signals_df['Actual Returns'] < 0), 'Signal'] = -1 
```
 
Using *value_counts()*, we had 2,368 signals to buy and 1,855 sginals to sell. We then trained three months worth of data to our support vector machine to train and make predictions with our data. Based on the classification report, the predictive powers of our model proved to be fairly good at predicting when we should buy, but performed poorly when predicting when to sell.
 
![image](https://user-images.githubusercontent.com/84649228/135740655-a6bb62f0-39c9-4b3b-9026-1ca4bc297823.png)

Using *cumprod().plot()*, we were able to plot how our predictive model compares to the actual. The model created was fairly close to the actual data.                                                  
  
![image](https://user-images.githubusercontent.com/84649228/135740641-a6d9dba2-5d49-4244-afbd-ff14d553d899.png)

</details>


<details>
<summary>Tuning the Baseline</summary>

As we are improving our baseline, we believed that the first step is to play with different indicators and segments of data.

First, the periods of data were tinkered with. The orignal baseline used three months worth of data for training. Now we tested the extremes of using six months and one month worth of data.
```
training_end = X.index.min() + DateOffset(months=6) 
``` 
![image](https://user-images.githubusercontent.com/84649228/135773342-179c45c9-3dbb-4733-b003-0ff75b868a5e.png)
![image](https://user-images.githubusercontent.com/84649228/135773356-38e4176a-4a59-40e0-aaef-b8e07d77176f.png)
 
```
training_end = X.index.min() + DateOffset(months=1) 
```  
![image](https://user-images.githubusercontent.com/84649228/135773295-0abdd5ff-6d4b-4c82-8e2f-0426d99c7f49.png)
![image](https://user-images.githubusercontent.com/84649228/135773311-6c832083-483d-4df7-907a-7c28fba1f849.png)

Next, we adjusted the SMA inputs to find the best predictive model. We tested this theory of changing the SMA four times to see what a difference that could make.
 
First, we changed the long window. 
```
short_window = 4
long_window = 50
```  
![image](https://user-images.githubusercontent.com/84649228/135773673-48e7aa38-6dc8-4197-8896-a2ee55a3e80c.png)
![image](https://user-images.githubusercontent.com/84649228/135773700-5f55a5f1-f073-4fbf-b857-058235449a09.png)
 
Second, we changed the short window. 
```
short_window = 50
long_window = 100
``` 
![image](https://user-images.githubusercontent.com/84649228/135773637-c4a51a9f-da77-4b35-9f83-1a46d6a26a5f.png)
![image](https://user-images.githubusercontent.com/84649228/135773640-ee620fc5-786c-4381-a7e7-8361dccf5417.png)

Then, we used a standard rolling average window indicator of 50/200.
```
short_window = 50
long_window = 200
``` 
![image](https://user-images.githubusercontent.com/84649228/135773547-cbeec5fa-d244-48fe-80fa-e1695d939da3.png)
![image](https://user-images.githubusercontent.com/84649228/135773545-7174af7e-16fb-443b-904d-e0c5b6ce42bc.png)

Lastly, we increased the short window. 
```
short_window = 100
long_window = 200
```  
![image](https://user-images.githubusercontent.com/84649228/135773590-270713e2-b0bc-49ab-8104-eedde61cd8e1.png)
![image](https://user-images.githubusercontent.com/84649228/135773594-efe749fc-e555-4303-8d5a-57c3358c6c19.png)
 
</details>

<details>
<summary>New Classifier-Logisitic Regression</summary>

We trained the baseline data on a new classifier to see if we could get a better prediction outcome. For this, the use of Logisitic Regression was used. 

```
short_window = 4
long_window = 100
  
signals_df['SMA_Fast'] = signals_df['close'].rolling(window=short_window).mean()
signals_df['SMA_Slow'] = signals_df['close'].rolling(window=long_window).mean()
```
![image](https://user-images.githubusercontent.com/84649228/135740124-6e2a817b-1e35-4ab5-973d-38f1b0c230cd.png)
![image](https://user-images.githubusercontent.com/84649228/135740119-66b66669-0eda-47b0-98c2-735d19b8c2ed.png)

</details>

<details>
<summary>New Classifier-AdaBoost</summary>

We trained the baseline data on a new classifier to see if we could get a better prediction outcome. For this, the use of AdaBoost was used. 

```
short_window = 4
long_window = 100
  
signals_df['SMA_Fast'] = signals_df['close'].rolling(window=short_window).mean()
signals_df['SMA_Slow'] = signals_df['close'].rolling(window=long_window).mean() 
```
![image](https://user-images.githubusercontent.com/84649228/135785809-81ccdc54-adcc-430b-81dc-64bd3a923b96.png)
![image](https://user-images.githubusercontent.com/84649228/135785830-8a5c1052-9f7f-40db-8d88-62c79362ddc5.png)



</details>

## Summary

Now that we have tried tuning the data and training it on different classifiers, we can compare all the different outcomes. 
 
Comparing the tuned data was simple. The sixth month, one month, and the short window, 4, and long window, 50, were nearly the same outcomes. We can state that the predictive powers do not change if we change the length of time. The 100/200 windows came back with the worst outcome. This test had a low accuracy rate, but was able to predict the sell strategy better. The 50/100 and the 50/200 were similar as well, but had the best outcomes from the tuned data. It was clear that the short window, 50, and long window, 200, was the best set of indicators as each score was equivalent or better than the baseline data, with only a .01 of accuracy dropped. 
 
The baseline compared to the new classifiers was very interesting. Their precision scores were nearly the same. AdaBoost and the original baseline had the almost the same recall scores, while logisitic regression was able to predict more instances where one should sell. The graphs of cumulative products looked nearly identical between the two classifiers, but AdaBoost predicted higher returns than then actual. Overall, these classifiers had nearly the same scores in precision, but their recall scores is where they differed.
 
Based on the scores and the cumulative product graphs, it is apparent that the short window, 50, and long window, 200, was the best way to increase our predictive powers for our algorithmic trading system.
