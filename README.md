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
<summary>Tune the Baseline</summary>

```
training_end = X.index.min() + DateOffset(months=6) 
``` 
![image](https://user-images.githubusercontent.com/84649228/135740484-95e6fbad-cbde-4fb3-8b9e-cb95665b4106.png)

```
training_end = X.index.min() + DateOffset(months=1) 
```  
 ![image](https://user-images.githubusercontent.com/84649228/135740503-48207e2c-c639-47ce-99e3-34c21a50fae5.png)

 
```
short_window = 50
long_window = 100
``` 
![image](https://user-images.githubusercontent.com/84649228/135740447-97db1d22-ef60-479a-bccc-c5006b725953.png)
 
 
```
short_window = 50
long_window = 200
``` 
 ![image](https://user-images.githubusercontent.com/84649228/135740265-10a88449-535f-47e7-bd6e-56ab89c433db.png)

```
short_window = 100
long_window = 200
```  
![image](https://user-images.githubusercontent.com/84649228/135740321-f43a7301-20da-4c91-9b57-e4fb8376cda2.png)
 

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

We trained the baseline data on a new classifier to see if we could get a better prediction outcome. For this, the use of Logisitic Regression was used. 

```
short_window = 4
long_window = 100
  
  
signals_df['SMA_Fast'] = signals_df['close'].rolling(window=short_window).mean()
signals_df['SMA_Slow'] = signals_df['close'].rolling(window=long_window).mean()
  
  
```
![image](https://user-images.githubusercontent.com/84649228/135740067-0adc9622-9be9-4ed6-989a-ce477c33dc4b.png)
![image](https://user-images.githubusercontent.com/84649228/135740080-295e16c8-b447-4b68-a381-60f418e78bc0.png)


</details>




## Summary


