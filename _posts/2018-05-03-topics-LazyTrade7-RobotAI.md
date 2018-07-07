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
  - Deep Learning
  - h2o
  - Pattern Recognition
  - Version Control
  - Decision Support System
  - MQL4
---

## Article about 7th Course

In this blogpost [5 min read] some explaination about the motivation behind the seventh course of the series. 

## Big Idea

The entire idea of Lazy Trading Series was to automate as much as possible by using Decision Support System. However by looking on the content of the course created so far it is possible to realize that still a lot of things would have to be done manually! Coding strategy, looking for indicators, optimizing the parameters, testing and choosing best parameters... This 'due-deligence' is still not a guarantee, because 'Past results are not necessary guarantee future performance'

The big idea of this course number 7 was exactly to overcome this. Trying to generate future predictions inside Decision Support System algorithms. At the end of this course we are coming up with a trading decision *created using Deep Learning Regression models to make predictions for the price change on multiple timeframes*. Finally consuming this prediction in a specially designed trading robot.

The most important part of the idea is in the fact that system is going to mimic more traditional algorithmic trading approaches. The goal will be to automatically learn patterns of the indicator corresponding to the future price changes and use them for predictions. 

By the way, **This is not a trading advice!** so just relax and have a fun reading for the next 5-7 minutes!

## Self-Learning Trading Robot

This trading system will be having three parts:

- Data Writer Robot
- Pattern Recognition Modeling and data scoring in Decision Support System
- Expert Advisor or trading robot capable to evaluate and apply predictions

Further we discuss these in details:

### Data Writer robot

It's all about 'for' loops running on MT4 platform. Our robot will write just two datasets: Prices and corresponding Technical Indicator data. Price data will be used as a label and indicator data will be used as a pattern. It will be all repeated on the defined time frames...

### Pattern Recognition Modeling and data scoring

As usual modeling requires prepared data. All magic to do so happens using *tidyverse* verbs and pipes. Thanks to few R functions it is possible to use code several times for both modeling and predictions.

Once the dataset is ready the *h2o* deep learning algorithm will be used to train the model. Of course this model will be tested using logical code composed of few more 'pipes' and independent dataset (indicator data and price label). The result of the model testing is an index that can be in the range from -1 to +1. Negative values represent model that is not performing well while positive values would indicate good results.

Once again, the great deal about this process is that everything is happening in a modular fashion. Code is packed into functions which could be re-used several times. Thanks to *h2o* model training is happening in very efficient way using all available CPU's of the machine.

After these modeling steps data scoring is just a little detail. Latest indicator data will be used together with the model to simply predict the future based on the indicator pattern.

### Expert Advisor

Robot uses ideas captured somewhere in the traders books. What they typically do is to look on the market on higher timeframes (days) then switch to lower timeframes (hours) finally estimate market type and select entry decision by looking to the smallest time frames (minutes). Robot will use some filters and just handle the rest like opening or closing orders, etc

Because of the fact that model will be directly predicting the price change there is no need to search for Take Profit levels. Stop Loss levels can be defined using appropriate 'risk-reward' ratio, for example 3:2 or 2:1, etc...

Of course this is a very brief description. There are much more to try and discuss. System is of course prone to generate more mistakes than correct answers. Saying that again: "Past performance is no guarantee for the future results"...

## conclusion

Once again, this course is about learning Computer and Data Science using trading. Independently if this concept would work or not it would definitely help to "Save Your Time and let Computer Do the Job"  
