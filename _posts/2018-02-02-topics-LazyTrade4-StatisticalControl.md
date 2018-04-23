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

In this blogpost [7 min read] I would like to explain the motivation behind the forth course of the series. 

This course is all about decision and continuous human-independent management of risks. There are a lot of courses and methods out there about how to develop, optimise and use Automated Trading Systems. However it is quite often that parameters for algorithmic trading systems are not working. Even after “backtesting” Market Type may change, there might be “overfit” during optimisation process so the robot will fail. Even though we may opt for exploiting robot to trade, robot that should be doing everything by itself, yet life shows that we [humans] are still need to be there and to decide to use this robot or not… 

At the end of this course you will learn to program your own decision and automate it. You will have a chance to use either *Profit Factor* or more advance principle of *Reinforcement Learning* for doing that. The final outcome of the course will consist in **creating a Robot which will supervise all other robots!** The concepts covered in this course will help you to:

* Set up *Automated Monitoring* for your Trading Systems
* Dynamically calculating *Profit Factors* of the Trading Systems and using it for decision making
* Using *Reinforcement Learning* algorithm to make more advanced decision support using RL Policy
* Stay more calm psychologically as you will have your own system that can manage your risks for you
* Learn by reproducing provided examples and further improve them (including Trading Robot)
* Getting organised by receiving a summary of trading robots performance and decide on robots maintenance
* Understand limitations of this method (no holy grail)

By the way, **This is not a trading advice!** so just relax and have a fun reading for the next 7 minutes!

## Why to use Statistical Methods to supervise your trades?

The theoretical section of the course introduces the 2 proposed methods and why we should do that in the first place. Once again it is all about risk management. The idea would be to deploy many different trading systems [on Demo trading account], or one system with different parameters, and then only use the most successful system(s) for trading. 

## How to use it?

Obviously one can decide to apply different methods of managing trading systems results:

- Stop trading system if lost more than X
- Trade if Profit Factor is more than Y for the N trades, stop Trading if Profit Factor is less than Z
- Apply Reinforcement Learning Policy estimating reward R for the decision D

Further below I would expand each concept in higher level detail. In order to better get the idea let me propose two actors:

* - *Researchers*. Researchers are the trading systems deployed on Demo Account that are not afraid of loosing. These are used to confirm hypothetical market inefficiency or the absence of those 

* - *Attackers* are exactly same trading systems as researchers but they are deployed on the different Demo Account. They mean to wait until the relevant decision comes. The goal is to keep those Trading systems to be as profitable as possible

### Stop Trading System if it’s lost more than X 

It is probably the simplest way to automate decision. We can just monitor how much system will win or lose since it’s deployed. This is also called PnL monitoring. If that PnL would exceed pre-defined amount then we stop using this trading system. However this method is not even explained nor implemented in the course and for a simple reason. Imagine we have a trading system. It’s super powerful, gained so much and then started to deteriorate. Nothing will secure our profits because this method will still be waiting for the pre-defined amount of loss to stop nowadays un-successful system…

### Monitoring Profit Factor

Profit Factor is something by default considering sufficient amount of trades to be calculated. It is obtained by dividing all profits to the all losses of the N closed orders of the trading system. That is easy. If profit factor would be higher than 1 our trading system would be profitable. The rest are just details. 

We can define profit factor level when we consider the Research system is profitable and sufficiently robust to deploy Attacker system. As well as we can stop this Attacker system in case Profit Factor of the Researcher system would drop below the certain profitability level. 

This method is better than previous as it may capitalise on successful system profit. We can decide now to only consider last trades only so to consider recent history of the system. Of course this method would assume our trading system would have sufficiently long winning or loosing streaks. One can decide the number of trades to consider in this logic. The fewer number selected the more risky but flexible this system will be. Opposite, if the trading system is generating many trades it would be possible to extend the number for the profit factor so the decision would be more reliable but slow to react to the changes

This course is providing an example of R code that can be used to supervise trading systems and take decision to switch on/off successful systems using Profit Factor monitoring. Indeed code is elegantly written using *tidyverse* verbs and few *pipes*, it should be very easy to reproduce this code and to understand what is there happening…

### What about Reinforcement Learning?

Exactly this concept was the main driver creating this course. For the Author it was priceless experience to study the concept of *Action - Reward* principle and apply that for trading. The idea is probably more hard to grasp without putting hands on to the subject however it’s very much worth it. And this is because the fact that principle can be applied to many different situations apart of trading. In fact this principle is used to teach computer to beat human in computer games…

In simple words Reinforcement Learning is something about continuously calculating probability of getting positive *Reward* provided some experience made on *Environment*. Once we have that estimate we can generate *Policy* of our our future actions. Trading is the ideal world for that. Reward - is our Profit or Loss, Environment - is all our trades we did. Policy is our decision to use or not use this particular trading system…

When it comes to details, it is always some details. In particular we can have some room for manoeuvre. For example we can specify how quick our system will learn, how much of the last experience it would consider etc. It is somehow similar to PID loop in Engineering but rather here we are dealing with data.

The greatest challenge in this particular case was around getting information for the model. It was about transforming information from our trades into the form digestible by the Reinforcement Learning Function in R. The proposed way is to use two steps approach:

1. Cumulative sum of profits is used when Researcher trading system is just deployed
2. Trading results of the Attacker system is later being used to re-train the model for our Attacker trading system

## Tell me when to optimise

Another simple idea of the course is to automate decision process to trigger Trading System maintenance. For example, our Researching system is absolutely poor and becoming even poorer. Of course we are not risking anything but there might be times when it would be worth to look at it. What about weekly or monthly summary about your systems? What about spending few hours on Saturday to have a look on those and check these systems out?
 
## It is not a holy grail but probably better…

If we would measure results of both supervising systems of our trading systems we would always come to the point to say that:

- good winning trading system will always be good and 
- poor lousy trading system will always be bad

All those supervised systems at the end will help you to limit your absolute amount of losses in case your trading systems will be loosing and ineffective.  There is still a chance that profitable trading system would be less profitable because of applied supervision. Once again it’s not a holy grail. It is very unlikely that totally un-profitable trading system would become profitable just by following this course

## Conclusion

Personally I would not use robots to trade unless I would know there would be a supervision layer active to monitor what is there going on. Automating that decision layer can be questionable as we are probably ready to risk expecting probable reward. However creating *Self-thinking* system is probably very lucrative for one simple reason - psychology of the trader… “faciant migliore potentis” / “Who do may try to make it better” - lat. And at the end of the day you can try to use this system in order to "Save Your Time and let Computer Do the Job"
