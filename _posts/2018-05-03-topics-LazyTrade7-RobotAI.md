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

## Draft Article about 7th Course

In this blogpost [5 min read] I would like to explain the motivation behind the seventh course of the series. 

## Big Idea

The entire idea of Lazy Trading Series was to automate as much as possible by using Decision Support System. However by looking on the content of the course created so far it is possible to realize that still a lot of things would have to be done manually! Coding strategy, looking for indicators, optimizing the parameters, testing and choosing best parameters... This 'due-deligence' is still not a guarantee, because 'Past results are not necessary guarantee future performance'

The big idea of this course number 7 was exactly to overcome this. Trying to generate future predictions inside Decision Support System algorithms. At the end of this course we are coming up *creating a robot scalper that is using Deep Learning Classification and Regression models to make predictions for multiple timeframes and using this information as trading trigger*

I hope that what is written above do make sense, if not please continue reading as I would be trying to clarify those further.

By the way, **This is not a trading advice!** so just relax and have a fun reading for the next 5-7 minutes!

## Self-Learning Trading Robot

This trading system is having three parts:

- Data Writer Robot
- Pattern Recognition Modeling and data scoring in Decision Support System
- Expert Advisor or trading robot capable to evaluate and apply predictions

Further we discuss these in details:

### Data Writer robot

It's all about 'for' loops. Our robot will write just two datasets: Prices and Technical Indicator data for 

### Pattern Recognition Modeling and data scoring

All magic happens using *tidyverse* verbs and pipes, h2o deep learning algorithm, some pipes again to perform strategy back tests... The great deal about this process is that everything is happening in a modular fashion. Code is packed into functions which could be re-used several times.

### Expert Advisor or trading robot

Robot uses ideas captured somewhere in the traders books. What they typically do is to look on the market on higher timeframes (days) then switch to lower timeframes (hours) finally estimate market type and select entry decision by looking to the smallest time frames (minutes). Robot will use some filters and just handle the rest. 

Of course this is a very brief description. There are much more to try and discuss. System is of course prone to generate more mistakes than correct answers. Saying that again: "Past performance is no guarantee for the future results"...

## conclusion

Once again, this course is about learning Computer and Data Science using trading. Independently if this concept would work or not it would definitely help to "Save Your Time and let Computer Do the Job"  
