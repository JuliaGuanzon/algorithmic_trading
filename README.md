<h1 align="center">Algorithmic Trading Enhancements</h1>

## Overview of the Algorithmic Trading Enhancements

The baseline algorithmic trading system that is being used has been very effective to the firm and has gained profits by users. Although this system is good, it can be better. We have narrowed down the be best enhancements for this system to better the predictive models. We went through multiple testings to find the best outcome possible. It's our goal to keep our competitive edge on our market.

## Results

<details>
<summary>Baseline</summary>
 
```
short_window = 4
long_window = 100
  
  
signals_df['SMA_Fast'] = signals_df['close'].rolling(window=short_window).mean()
signals_df['SMA_Slow'] = signals_df['close'].rolling(window=long_window).mean()
  
  
```
![image](https://user-images.githubusercontent.com/84649228/135738937-256c2dcf-7f92-4d7a-b094-2cd328671a7b.png)
  
![image](https://user-images.githubusercontent.com/84649228/135739647-1de43043-0582-4b33-bd45-b89fb9e93e6f.png)




</details>


<details>
<summary>Tune the Baseline</summary>
 
 

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


