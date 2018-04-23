---
title: Lazy Trading Part 4 Statistical Control of Trades
excerpt: Learn Computer and Data Science through Algorithmic Trading
date: 2018-02-02
author: vladdsm
categories:
  - topics
  - lazy trading
tags:
  - algorithmic trading
  - Statistical Control
  - Reinforcement Learning
  - Version Control
  - Decision Support System
  - MQL4
---

## Statistical control of trades

In this blogpost [5 min read] I would like to explain the motivation behind the forth course of the series. 

This course is all about decision and continuous independent management of risks. There are a lot of courses and methods out there about how to develop, optimize and use Automated Trading Systems. However it is quite often that parameters are not working anymore. Market Type may change, there might be “overfit” during optimisation process. Even though we may opt for exploiting robot that should be doing everything by itself, yet life shows that we [humans] are still need to be there and to decide to use this robot or not… At the end of this course you will learn to program your decision and automate it. You will have a chance to use either Profit Factor or more advance principle of Reinforcement Learning for doing that. The final idea is that we will create a Robot which will supervise all other robots! The concepts covered in this course will help you to:

* Set up Automated Monitoring for your Trading Systems
* Dynamically calculating Profit Factors of the Trading Systems and using it for decision making
* Using Reinfocement Learning algorithm to make more advanced decision support using RL Policy
* Stay more calm psychologically as you will have your own system that can manage your risks
* Learn by reproducing provided examples and further improve them (including Trading Robot)
* Understand limitations of this method (no holy grail)

By the way, **This is not a trading advice!** so just relax and have a fun reading for the next 5 minutes!

## Why to use Statistical Methods to supervise your trades?

The theoretical section of the course introduces the 2 proposed methods and why we should do that in the first place. Once again it is all about risk management. The idea would be to deploy many different trading systems [on Demo trading account], or one system with different parameters, and then only use the most successful system for trading. 

## How to use it?

Obviously one can decide to apply different methods of doing so:

- Stop trading system if lost more than X
- Trade if Profit Factor is more than Y for the N trades
- Apply Reinforcement Learning Policy estimating reward R for the decision D

Further below I would expand each concept in higher level details. In order to better get the idea proposed two actors are: *Researchers* and *Attackers*. Researchers are the trading systems deployed on Demo Account that are not afraid of loosing. Attackers are exactly same trading systems which are deployed on the different Demo Account. Latter systems would be considered to be as profitable as possible

### Stop Trading System if it’s lost more than X 

It is probably the simplest way to automate decision. We can just monitor how much system win or loss. This is also called PnL. If that PnL would exceed pre-defined amount then we stop. However this method is not even explained nor implemented in the course and for a simple reason. Imagine we have a trading system. It’s super powerful, gained so much and then started to deteriorate. Nothing will secure our profits because this method will still be waiting for the pre-defined amount of loss to stop nowadays un-successful system…

### Monitoring Profit Factor

Profit Factor is something by default considering sufficient amount of trades to be calculated. It is obtained by dividing all profits to the all losses of the trading system. That is easy. If profit factor would be higher than 1 our trading system would be profitable. The rest are just details. We can define profit factor level when we consider the Research system is profitable and sufficiently robust to deploy Attacker system. As well as we can also stop this Attacker system in case Profit Factor of the Researcher system would drop below the certain profitability level. 

This method is better than previous as it may capitalise on successful system profit. We can decide now to only consider last trades only so to consider recent history of the system.

Overall, this course provide you with example of R code that can be used to supervise trading systems and take decision to switch on/off successful systems. Indeed code is elegantly written using *tidyverse* verbs and few *pipes*, it should be very easy to reproduce this code to understand what is there happening…

### What about Reinforcement Learning?

Exactly this concept was the main driver creating this course. For the Author it was priceless experience to study the concept of Action - Reward principle and apply that for trading. The idea is probably more hard to grasp without putting hands on on the subject however it’s very much worth it. And this is because the fact that principle can be applied to many different situations apart of trading.

In simple words Reinforcement Learning is something about continuously calculating probability of getting positive *Reward* provided some experience made on *Environment*. Once we have that estimate we can generate *Policy* of our our future actions. Trading is the ideal world for that. Reward - is our Profit or Loss, Environment - is all our trades we did. Policy is our decision to use or not use this particular trading system…

When it comes to details, it is always some details. In particular we can have some room for manoeuvre. For example we can specify how quick our system will learn, how much of the last experience it would consider etc. It is somehow similar to PID loop in Engineering but rather here we are dealing with data.

The greatest challenge in this particular case was around getting information for the model. It was about transforming information from our trades into the form digestible by the Reinforcement Learning Function in R. The proposed way is to use two steps approach:

1. Cumulative sum of profits is used when Researcher trading system is just deployed
2. Trading results of the Attacker system is later being used to re-train the model for our Attacker trading system
 
## It is not a holy grail but probably better…

In any case 

## Conclusion

If we would measure results of both supervising systems of our trading systems we would always come to the point to say that:

- good winning trading system will always be good and 
- poor lousy trading system will always be bad

All those supervised systems at the end will help you to limit your absolute amount of losses in case your trading systems will be loosing and ineffective.  There is still a chance that profitable trading system would be less profitable because of applied supervision.
 What is important is that it should... "Save Your Time and let Computer Do the Job"
