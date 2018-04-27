---
title: Lazy Trading Part 2 Set up your Trading Strategy Robot
excerpt: Learn Computer and Data Science through Algorithmic Trading
date: 2018-01-19
author: vladdsm
categories:
  - topics
  - lazy trading
tags:
  - algorithmic trading
  - Version Control
  - Decision Support System
  - MQL4
---

## Set up your Trading Strategy Robot

In this blogpost [5 min read] I would like to explain the motivation behind the second course of the series. 

This course will cover setting up your personal Trading Robot Template. At the end of this course we will have complete and ready to be used Trading System installed and active on Home Computer. It will help us to:

* Learn Programming environment
* Setting up Version Control Project
* Get the overview of robot functions
* Learn how to customise template to target market inefficiency
* Integrate robot with Decision Support System (start/stop trading system from external commands)
* Customise and record trades results

By the way, **This is not a trading advice!** so just relax and have a fun reading for the next 5 minutes!

## Programming Environment

In this section of the course we will mainly talk about using our Algorithmic Trading Environment. As usual this is just a brief theoretical section aiming to give conceptual understanding. The goal is to give a bigger picture of the entire thing, architecture of our Trading Environment and how we can orient in it.

## Adapting Robot Template

In this section we will learn how to get the code, easily synchronise it and know how to modify it to suit our purposes. We will mainly look to:

- Log trading results from the Trading Robot
- Reading external commands in the Trading Robot
- How to further modify trading strategy

Below is the short purpose summary of those

### Log Trading Results

It's all about setting a standard. All our trading robots will be able to record trading results in one place! That easy. We don't have to worry about it! You just know that when the trade will be completed the results will be stored. No databases - just simple csv file!

### Magic Number Convention

Even if we are too lazy to build an army of robots it would be still worth to define some rules, right? Why not to assign some known ID number for every single robot, for every single Terminal and every single chart? This standard will be very useful in further courses of the series. Concept is very simple to understand and works even better when printed! Below is the example of decoding Magic Number 8110101

- 8 ==> Year when strategy is developed e.g. 2018
- 1 ==> Terminal Type (1 - Demo Instant, etc)
- 1 ==> First digit of strategy ID
- 0 ==> Second digit of strategy ID
- 1 ==> Terminal number (1, 2, 3, 4 as Pre-Production, Development, etc)
- 0 ==> First digit of MT4 Chart
- 1 ==> Second digit of MT4 Chart (max 99 charts are possible)

In summary code 8110101 will mean that we are using strategy developed in year 2018, running on Demo account, strategy ID is 10. It is all running on Pre-Production terminal 1 on the first chart. That simple, isn’t it?

### Reading external commands in the Trading Robot

This is all about control. How can one just switch on/off the trading robot from external software? This we will learn in this lecture. Not only that. By using pre-defined and easily traceable method [via writing files] we will be able to virtually tell anything to our trading robots. Even the weather forecast:)

### How to further modify it?

The robot can and must be modified. Experiment, log changes and try different things. The course just explains where. Simple recommendation is to make modular changes and use Version Control to be able to come back.

## Conclusion

Course is concluded by showing Demo test trading results. The results will be shown using our own Trading Journal [topic of the next course of the series]. That's because we will always want to be Lazy and efficient as we love to say: … "Save Your Time and let Computer Do the Job"
