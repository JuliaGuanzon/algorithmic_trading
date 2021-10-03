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
<summary>New Classifier</summary>

We trained the baseline data on a new classifier to see if we could get a better prediction outcome. For this, the use of Logisitic Regression was used. 

```
short_window = 4
long_window = 100
  
  
signals_df['SMA_Fast'] = signals_df['close'].rolling(window=short_window).mean()
signals_df['SMA_Slow'] = signals_df['close'].rolling(window=long_window).mean()
  
  
```
![image](https://user-images.githubusercontent.com/84649228/135739666-66b8d87e-8e2a-4377-973f-9655b22dc13d.png)
![image](https://user-images.githubusercontent.com/84649228/135739750-66f7563f-8a68-441d-a7ed-6234e12aa37c.png)




</details>

## Summary


