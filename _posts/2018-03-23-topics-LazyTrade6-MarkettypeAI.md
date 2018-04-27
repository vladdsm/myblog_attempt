---
title: Lazy Trading Part 6 Detect Market status with AI
excerpt: Learn to use Supervised Deep Learning modelling to detect patterns of Financial Assets
date: 2018-03-23
author: vladdsm
categories:
  - topics
  - lazy trading
tags:
  - algorithmic trading
  - Statistical Control
  - Deep Learning
  - Pattern Recognition
  - Artificial Intelligence
  - AI
  - h2o
  - Version Control
  - Decision Support System
  - MQL4
---

## Detect Market Status with Artificial Intelligence

In this blogpost [7 min read] I would like to explain the motivation behind the sixth course of the series. 

Previous courses of the series were mostly about getting a basis. We tried to look into having a systematic approach in our trading ecosystem. Getting the robot, having ability to analyse results, taking basic decision based on collected information…

At this point of time we can further develop this ecosystem, enriching it with other elements at our desire. One of the most important elements is probably trading system capability to detect market status. According to Mr. Van K.Tharp it’s insane to expect that one trading system would work in all market types. So this course is just designed to close this ‘requirement’. 

At the end of this course you will be capable to learn how to teach Artificial Intelligence to recognise patterns of six specific Market Types. We will focus on doing that for:

* Bullish Normal Market (BUN)
* Bullish Volatile Market (BUV)
* Bearish Normal Market (BEN)
* Bearish Volatile Market (BEV)
* Ranging Normal Market (RAN)
* Ranging Volatile Market (RAV)

The final outcome of the course will consist in creating an automated task capable to generate Market Type status information for main 28 Forex Currency Pairs! The course was design to let you **learn by doing**. In other words lectures are structured to help student to replicate provided examples. Overall, the concepts covered in this course will help to :

* Get intuitive understanding of proposed method 
* Set up a system capable to deliver automatic Asset data generation (‘data robot’ is provided with the course) 
* Learn how to prepare data for both Deep Learning Regression and Classification algorithms
* Perform both training, testing, productionising Deep Learning Models
* Clarify on example how to use Market Type status with trading robot (provided with the course)
* Getting a workflow of using this robot: How to optimise and deploy to production
* Understand limitations of this method (no holy grail)

**As usual, author hopes that concepts of the course would help to get inspiration and knowledge on how to use Artificial Intelligence to get value for the society!**  

By the way, **This is not a trading advice!** so just relax and have a fun reading for the next 7 minutes!

## Why to detect Market Type status?
 
Theoretically Market Type can be split in several categories. Simplest categories may include Trending or Ranging types. Trending can in turn be both Upward looking or Downward looking, or Bullish and Bearish respectively. Categories may be extended also considering volatility. Finally we can have 6 market types. Typically used methods [parameters] to define Entry and Exit conditions may be completely different for those different market types, hence specific trading system may get deteriorated if Market Type is not considered in the Trading System. 

The shorter answer may be formulated as to have an ability to get a high level trading filter. For example avoiding Short trades in generally Bullish market 

## The 3 assumptions

First of all Market Type can be only found assuming we are defining the *timeframe* and we are looking to specific *time period duration*. For example it can be M15 chart with the duration of 16 hours. Provided this input data we can start identification. What is the third assumption?

Assume we are able to properly detect market type for a given asset. There is still a chance that market type will change. For that we have to define the third assumption. We should assume that there will be sufficiently long period of time when such *condition would persist* in the future.

The short summary of assumptions:

- timeframe
- time period duration
- detected market type condition would persist

## How to do that?

Simple research in the internet would result in many different approaches including getting ‘powerful’ indicators. According to the current state of the art, author opinion about this is about these methods:

- Indicators
- Machine Learning methods
- Deep Learning

Everyone is free to choose specific method to use, the course however only focuses on using Deep Learning as it’s famous to be great in pattern recognition…

The main idea would be to use indicators as a source of data to train the model. For the purpose of the course MACD indicator was used. In fact simply by looking to the chart we can easily identify market types and may be spot some dependency of market period with values of indicator. For example whenever market is of Bullish type MACD indicator values will be mostly in the positive area; whenever values of the indicator are within both positive and negative areas we are most likely inside of the Ranging market type…

Note: course would allow to adapt the data source and use any standard or custom MQL4 indicator.

The rest is probably just technical details on how to use Supervised Deep Learning…   

## Main steps to achieve the goal

Course is split in few logical steps to perform the task. Main idea is to:

- Get the financial data
- Manually classify specific market periods simply by selecting proper pattern
- Train/Test/Use Deep Learning Model
- Use Deep Learning model with Trading Robot

### Selecting data

Available data [asset indicator data] would be used to visually select data for each specific period. In fact why not to use the most advanced and unique computer on the planet [our own brain] for that? Overall data size would probably not be too big, however several weeks of data points divided by for example 64 bars may bring us 80 - 90 training instances. Each of those instances would contain pattern specific for selected market type. Of course some instances would contain wrong patterns however as long as those would not dominate the rest it should be fine.

### Training model…

As many people would say data wrangling would take 80% of the time. This is true. In the course we would however spend some time to look how to setup different type of models. For example if we define categories as numeric property we can end up using Regression Model. Should we keep categories we can of course remain with Classification Model. 

Training Deep Learning model can be tricky. For example one may find different performances just because of using more processors to make parallel calculations. The other possible challenge is modelling results reproducibility. Even using the same data, computer and code may result in different accuracy outcomes.

### Saving Model

Once the model would be tested we can of course save it persistently to the file object.

### Using the Model

This is always the most fascinating time. Especially when our model would be capable to correctly predict at least 80 % of the time correctly. It would be even great if our model would be smart enough to automatically re-train itself to even further improve it’s functionality… Nevertheless course is for the moment focuses only on Trading Robot capable to use different sets of parameters for different Market Types. In addition to that Robot allows us to completely disable trading for one or more specific market types.

## Demo trial

In order to perform the demo trial we would need to optimise our robot. The idea is to use the same Asset, Market type of the asset and find best parameters for those periods by optimisation.
 
## It is not a holy grail but probably better…

Few important words about some limitations in this course. Course is focusing to quickly achieve the results by reproducing provided example. It is however not focusing much on explaining details. This is why it’s probably important to try this method relatively fast and then go through the method with much slower pace. For example after reproducing the code students may try to change few parameters. For example try using M5 or M1 charts, or using 128 bars instead of 64 used in the course, etc

Once again the third assumption is also very important. There might be conditions when market type will be changing. More over there might be some dependencies or even rule when certain patterns would lead to the future market changes. Solution is not provided in the course, yet one may try to start using this system, log how AI classify patterns and then re-train model with ‘shifted’ label.

In any case, author believes that methods provided in the course are providing value and great examples on how to build the entire modular system.   

## Conclusion

We know that Market Type is important to avoid insanity of trying to expect that Trading Robot will work in all the market types. The hope is that this course will also help students to ‘engineer’ luck. This is derived from Seneca’s definition of term Luck. It is only coming when we are prepared for the opportunity. Even better if it’s done automatically so we can… "Save Your Time and let Computer Do the Job"

