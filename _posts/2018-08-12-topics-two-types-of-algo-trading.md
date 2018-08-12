---
title: Model based Algorithmic Trading
excerpt: Considerations about model derived Trading Decisions for Algorithmic Trading
date: 2018-08-12
author: vladdsm
background-image: code_roxygen.JPG
categories:
  - topics
tags:
  - algorithmic trading
  - Trading Decision
  - Decision Support System
  - MQL4
  - Udemy
  - Artificial Intelligence
  - Optimization
  - Modelling
  - Overfitting
---

## Two common types of Algorithmic Trading and why I would choose Model Based type?

Three years ago I came across this fascinating subject called Algorithmic Trading. That time everything was very new however I was 'eating' this interesting subject by researching, reproducing, spending literally hours and hours on it. Very soon I realized that it is not for me! Although it was pretty clear what is going on the idea to spend hours on what is called 'Algorithmic Trading' that was using brute-force search of trading logic was not for me. Luckily there were already 'Model Based' Algorithmic Trading systems. Typically these systems are directly trained on the historical data to produce probability of success for a certain trading decision.

After having studied and practiced the two methods it is finally possible to take a 'Helicopter View' on the situation. This blog post [5 min read] will attempt to compare the two methods helping the reader to choose the right approach. By the way this is not a trading advise but one more suggestion on how to use Algorithmic Trading to learn Computer and Data Science!

<img src ="https://raw.githubusercontent.com/vladdsm/myblog_attempt/master/images/compareAIvsOptim.JPG" alt="speakom"   />

## Summary of the two methods

Table below, already discussed in the (seventh course of the Lazy Trading Series)[https://www.udemy.com/self-learning-trading-robot/?couponCode=LAZYTRADE7-10] summarize both Algorithmic Trading approaches:

<img src ="https://raw.githubusercontent.com/vladdsm/myblog_attempt/master/images/compareOptimizeVSModels.PNG" alt="speakom"   />

Hard-coded and clear trading logic is opposed to 'black-box' type derived trading decision.

### Optimization not Over-fitting

Algorithmic trading was created to 'hard code' trading decisions and make it execute using computer programs. Probably the most famous program of such type is MT4 platform and the entire programming language MQL4 developed to make it a reality. There are literally tonns of information out there with many more blogs and trading forums. Very interesting and interactive for the users seems to be so called *Strategy Tester* option. Possibility to brute-force many different scenarios of trading by leaving computer working over-night was first very great, however it was bringing the need of selecting parameters, forward testing them and then still having unknown future...

### Models as black-boxes for trading decision

For those who want to be more creative several other options of Algorithmic Trading would come handy. It could be Regression, Machine Learning classification, Neural Networks, Decision Trees, others. Typically implementation of modeling and trading decision is done outside of the Trading Platform. Trading Platform is just used to produce data, receive trading decision and manage orders.

Final implementation may be very complex and not be suitable for majority of retail traders however several advantages are still worth to pursue this path:

* Process can be automated and repeated
* Back-test strategy and automated evaluation
* Access to open-source easy to reproduce and understand functions

On the other hand one should not forget about possible caveats:

* Slower execution
* Harder to interpret
* Requires knowledge of R/Python or other specific Machine Learning Platform, link to Trading Platform

## Conclusion

One of the big advantages of the Model Based trading is a possibility of fully automate the trading process. Once again, for those who are keen to try using model-based algorithmic trading at least one reward is guaranteed. By experimenting with open-source functions and algorithms one will surely learn many new concepts of Data Science. This knowledge can be certainly applied in any other field apart of Financial Trading and even provide added value at work or in your academia!

Feel free to send your feedback if this would be ever helpful and make sense! 