---
title: Lazy Trading Part 7 Developing Self Learning Robot
excerpt: Learn Computer and Data Science through Algorithmic Trading
date: 2018-05-03
author: vladdsm
categories:
  - topics
  - lazy trading
tags:
  - algorithmic trading
  - Statistical Control
  - Forex Calendar
  - Version Control
  - Decision Support System
  - MQL4
---

## Draft Article about 7th Course

In this blogpost [7 min read] I would like to explain the motivation behind the seventh course of the series. 

### NOTE

This post is about non existing course, yet I wanted to put my thoughts on the ‘paper’. Please feel free to comment by sending personal message through Udemy

## Big Idea

By having a honest look on the content created so far, evaluating already available options, once again considering we are in the Lazy Trading courses series… it is possible to set at least few directions about the next course. What if we will be able to:

* Automatically detecting and exploiting Market Inefficiencies
* Having a trading robot capable to automatically estimate & validate best parameters
* Having a robot capable to learn from previously performed trades
* Creating a robot scalper that is evaluating Market Type Artificial Intelligence predictions for multiple timeframes and using this information as trading trigger

I hope that what is written above do make sense, if not please continue reading as I would be trying to clarify those further.

Also please consider that these bullet points are written starting from hardest one on top and the easiest ones are those 2 below. 

By the way, **This is not a trading advice!** so just relax and have a fun reading for the next 5-7 minutes!

### Automatically detecting and exploiting Market Inefficiencies

The idea of this point would be to use Unsupervised Machine learning methods such as *k-means* or *hierarchical clustering*. We may simply collect sufficient amount of data from several indicators, perhaps perform dimensionality reduction using *Principle Component Analysis* then find clusters in the data… After having those clusters we may backtest several trading scenarios for each cluster (considering randomness of k-means algorithm). Once we know best estimate for each cluster and the model we can score the latest data and see which cluster it belongs too… this in turn may be considered as an entry point for the trading robot. Well sounds like a plan, perhaps not that clear right??? 

### Having a trading robot capable to automatically estimate & validate best parameters

This one is very interesting one, probably inspired by boredom of optimisation or strategy testing. What if we have simple trading robot capable to backtest several trading parameters automatically? For example if we are in the trending market it would do a linear regression on the last xx bars, find a slope, standard deviation around the slope… Having standard deviation and slope direction we can potentially define our entry points and targets, etc… 

Similar for the ranging markets. There we would need to use bollinger bands indicator and see how to ‘best-fit’ the bands to the past data. This way we can potentially generate good trading decisions. For instance when price crosses upper bounds from above we would sell, etc 

### Having a robot capable to learn from previously performed trades

This method is probably more difficult to comprehend but more easy to convert to the course. Reason is that kNN (k-nearest neighbour) algorithm was already implemented by fellow traders and it’s easily available in the MQL forums. Principle of functionality can be explained as follows:

- trader specify in the settings that it is a ‘learning’ phase
- robot is set to have ability to execute 20 or 30 trades at the same time
- using strategy tester robot is brute-forcing several hundreds of trades
- doing the trading process files are generated with information about indicators values for each traded instance
- learning parameter is set to false
- robot is deployed to execute only 1-2 trades at the time
- typically algorithm would compare the position of the indicator values to the model and calculate probability to win entering buy/sell orders. 
- This probability value can be used to entry the trade, hoping for best…

### Robot scalper using Market Type for multiple timeframes as trigger

This last bot not least idea is based on the previous course. In fact it is similar to the trading techniques deployed by the professional traders. What they typically doing is to look on the market on higher timeframes (days) then switch to lower timeframes (hours) finally estimate market type and select entry decision by looking to the smallest time frames (minutes). Now what if we could simply create deep learning classification models for those timeframes? Well it may be more work to do to create 3 models instead of one, however we could get, in theory, simplify trading logic and probably avoid parameters in our trading systems.

Of course there is a risk that AI would generate more mistakes than correct answers however why not to just try it? 

## conclusion

Once again, it’s a very draft article for the non-existing course yet. Nevertheless the belief is that combination of previous courses with the last one will make the entire series very very complete and interesting for anyone. More over if the entire concept will work it would definitely help to "Save Your Time and let Computer Do the Job"  
