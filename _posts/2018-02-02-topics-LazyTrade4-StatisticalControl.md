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
  - Trading Psychology
  - tidyverse
  - MQL4
---

## Statistical control of trades

In this blogpost [7 min read] I would like to explain the motivation behind the forth course of the series. 

This course is all about decision and continuous human-independent management of risks. There are a lot of courses and methods out there about how to develop, optimize and use Automated Trading Systems. However it is quite often that parameters for algorithmic trading systems are not working. Even after “backtesting” Market Type may change, there might be “overfit” during optimisation process so the robot will fail. Even though we may opt for exploiting robot that should be doing everything by itself, yet life shows that we [humans] are still need to be there and to decide to use this robot or not… 

At the end of this course we are going to learn to program our own risk management decision system. We will even make a demo-trading experiment to find what is better: *Profit Factor* Monitoring or more advanced *Reinforcement Learning* for doing that [further in the text **RL**]. The final outcome of the course will consist in **creating a Robot which will supervise all other robots!** The concepts covered in this course will help us to:

* Set up *Automated Monitoring* for multiple Trading Robots
* Dynamically calculating *Profit Factors* and using it for decision making
* Using *Reinforcement Learning* algorithm to dynamically generate decision support using RL Policy
* Stay more calm psychologically by using our own system that can manage risks automatically
* Learn by reproducing provided examples and further improve them (including Trading Robot)
* Getting organized by receiving a summary of trading robots performance and decide on robots maintenance
* Understand limitations of this method (no holy grail)

By the way, **This is not a trading advice!** so just relax and have a fun reading for the next 7 minutes!

## Why to use Statistical Methods to supervise your trades?

The theoretical section of the course introduces the 2 proposed methods and why we should do that in the first place. Once again it is all about risk management. The idea would be to deploy many different trading systems [on Demo trading account], or one system with different parameters, and then only use the most successful system(s) for trading. Whenever 'successful' system stops to be successful - it should be recognized as well

## How to use it?

Obviously one can decide to apply different methods of managing trading systems results:

- Stop trading system if lost more than X
- Trade if Profit Factor is more than Y for the N trades, stop Trading if Profit Factor is less than Z
- Rely on Reinforcement Learning Policy that is predicting outcome of the decision D

Further below we would expand each concept in higher level detail. In order to better get the idea let us define the two actors:

* - *Researchers*. Researchers are the trading systems deployed on Demo Account that are used just to confirm hypothetical market inefficiency or the absence of those. These trading systems would have possibility to open multiple orders with minimum allowed risk. [Learn Fast - Fail Fast]

* - *Attackers* are exactly same trading systems as Researchers but they are deployed on the different Demo Account. They meant to wait until the relevant decision comes and exploit it. The goal is to keep using only most profitable Trading systems. These trading systems would be allowed to open only 1 order at the time and use more advanced Money management policy [e.g. 1% per trade] to maximize profit. There are of course still some chances to fail

### Stop Trading System if it’s lost more than X 

It is probably the simplest way to automate decision. We can just monitor how much system will win or lose since it’s deployed. This is also called PnL monitoring. If that PnL would exceed pre-defined amount then we stop using this trading system. However this method is not even explained nor implemented in the course and for a simple reason. Imagine we have a trading system. It’s super powerful, gained so much and then started to deteriorate. Nothing will secure our profits because this method will still be waiting for the pre-defined amount of loss to stop nowadays un-successful system…

### Monitoring Profit Factor

Profit Factor is something by default considering sufficient amount of trades to be calculated. It is obtained by dividing all profits to the all losses of the N closed orders of the trading system. If profit factor would be higher than 1 our trading system would be profitable.

We can define profit factor level when we consider the Research system is profitable and sufficiently robust [level Y] to deploy Attacker system. We can also stop this Attacker system in case Profit Factor of the Researcher system would drop below the certain profitability level [level Z]. **Note that Y > Z**. For example, Y can be 2.0 and Z can be 1.4.

This method is better than previous as it may capitalize on successful system profit. We can decide now to only consider last trades only so to consider recent history of the system. One can decide the number of trades to consider in this logic. The fewer number selected the more risky but flexible this system will be. Opposite, if the trading system is generating many trades it would be possible to extend the number for the profit factor so the decision would be more reliable but slow to react to the changes

This course is providing an example of R code that can be used to supervise trading systems and take decision to switch on/off successful systems using Profit Factor monitoring. Indeed code is elegantly written using *tidyverse* verbs and few *pipes*, it should be very easy to reproduce this code and to understand what is there happening…

### What about Reinforcement Learning?

Exactly this concept was the main driver creating this course. For the Author it was priceless experience to study the concept of *Action - Reward* principle and apply that for trading. 

The idea is probably more hard to grasp without putting hands on to the subject however it’s very much worth it. And this is because the fact that principle can be applied to many different situations apart of trading. In fact this principle is used to teach computer to beat human in computer games… Not mentioning that RL can be applied to supervise performance of deployed models [more on that in my further projects]... One would of course argue that completed trades are not the **Markov Process** however for the sake of learning let’s not debate and try to imagine that it is!

In simple words Reinforcement Learning is something about continuously calculating probability of getting positive *Reward* provided some experience made on *Environment*. Once we have that estimate we can generate *Policy* of our future actions. Trading is the ideal world for that. Reward - is our Profit or Loss, Environment - is all our trades we did. Policy is our decision to use or not use this particular trading system…

When it comes to practical implementation, it is always about details. For example we can specify how quick our system will learn, which strategic reward will be considered for short or longer term, how much of the last experience it would consider etc. It is somehow similar to PID loop in Engineering but rather here we are dealing with data and coefficients are called *alpha*, *gamma* and *epsilon*. Good news is that our code will help us to set the best parameters by checking all possible outcomes of the model to maximize the output.

### Important assumption

Of course this method would assume our trading system would have sufficiently long winning or loosing periods.

## Tell me when to optimize

Another simple idea of the course is to automate decision process to trigger Trading System maintenance. For example, our Researching system is not working as expected. What about weekly or monthly summary about such systems? This will allow to plan few hours to optimize those systems
 
## Demo trading experiment

During this course dedicated 'demo-trading experiment' was conducted to see how it would work in practice. It was possible to see how both methods were working to reach the goal - perform automatic risk management of 36 trading robots over a period of 5 weeks:

### No risk management in Terminal 1

* Profit factor 1.02
* Total Trades 1088

<img src ="https://raw.githubusercontent.com/vladdsm/myblog_attempt/master/images/T1.gif" alt="speakom"   />

### Monitoring of profit factor in Terminal 3

* Profit factor 1.04
* Total Trades 80

<img src ="https://raw.githubusercontent.com/vladdsm/myblog_attempt/master/images/T3.gif" alt="speakom"   />

### Using RL in Terminal 4

* Profit factor 1.23
* Total Trades 118

<img src ="https://raw.githubusercontent.com/vladdsm/myblog_attempt/master/images/T4.gif" alt="speakom"   />

 
## It is not a holy grail but probably better…

Few points to summarize:

- good winning trading system will always be good and 
- poor lousy trading system will always be bad
- RL is allowing to help with psychology of the Algorithmic Trader by using another robot capable to ‘self-organise’ Trading Systems into clusters and maximize the total output

## Conclusion

Personally I would not use robots to trade or Data Science models unless I would know there would be a supervision layer active to monitor what is there going on. 

Creating *Self-thinking* smart systems is very lucrative because it helps to "Save Your Time and let Computer Do the Job"

## p.s. “faciant migliore potentis”

If I remember well and wrote that correct this can be translated from Latin as “Who do may try to make it better” … feel free to use and improve provided examples to reach better results!