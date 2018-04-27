---
title: Lazy Trading Part 1 Set up your Home Trading Environment
excerpt: Learn Computer and Data Science through Algorithmic Trading
date: 2018-01-18
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

## Home Trading Environment

In this blogpost [5 min read] I would like to explain the motivation behind the first course of the series. 

This course will cover setting up your personal robust *Home Trading Environment*. At the end of this course students will have complete and ready to be used Trading System installed and active on the Home Computer. It will help to:

* Choose hardware
* Prepare and install needed software
* Establish Version Control for different Trading Strategies and tools
* Outline the Bigger Strategy of the Trader
* Set up Development, Test and Production Trading Environments
* Establish your own Decision Support System
* Making the entire system more robust to external factors

By the way, **This is not a trading advice!** so just relax and have a fun reading for the next 5 minutes!

## Hardware

In this section of the course we mainly talk about using Windows PC at Home or Virtual Private Server (VPS). Personally I am using just PC Windows leaving that working 24/7 with Monitors OFF when not in use. My personal recommendation is to choose VPS only when physical access to machine is not possible: e.g. frequent travelling, no space, not enough funds to pay for hardware, etc…

What I believe is also important is to insure risk-response in case there is a power-off situations. So in this course we are making sure to cover that point

## Software

The 3 key softwares are mainly used:

- MT4
- R/R-Studio
- Github for Desktop

Below is the short purpose summary of those

### MT4

This is a trading platform. Windows based, relatively easy to use and there is no need of any course for that. Probably the only value of the course is in the proposed strategy of using these terminals. In fact, entire method to apply this strategy is provided. For example how to combine development, test and production? How to insure everything you develop on one Terminal can be easily transferred to the rest of them once ready, how not to get lost in the performed steps?!

### R/R-Studio

Since I knew *R* I was always impressed that it can do almost anything! But the real great thing is that it's bringing so much understanding in what is going on. Nevertheless primary purpose of *R* is in creation of structured *Decision Support System*. This system meant to be automated and bring *supervisory layer* above the trading platforms.

In these courses Decision Support System is actually a key for the student to practice their skills. But not only practice by copying proposed ideas. In fact almost anything can be build on top of that! One can try to build crazy algorithms to detect certain patterns to join and aggregate data from different sources and so on. In author opinion however focus should be made on thinking what area of Decision Support system you should be developed in order to later re-use the code in relevant fields on the activities. At work or in Academia.

### Github for Desktop

Version Control is something every lazy person must use. This is something that helps not to loose track of what was created and not to be frustrated in case something went wrong and we want to go back. But it's hard to remember these commands! Besides not everybody is  professional programmer geek to perform these operations. Why do we need typing those boring commands git-commit-clone-push-master, etc?? Easiest way is to use GUI software for that!

Proposal of the course is to keep all project elements as Folders in the Version Control repositories. Each of the repositories should deliver some function. Either it is a Function library for the MQL4 Robots or R repository for one element of the Decision Support System. Obviously not everything is fully automated. Sometimes it's necessary to run batch script to synchronise particular folders of Trading Terminals. Only when we need to push ready to deploy Trading Robot to all trading Terminals

## Conclusion

Trading is something that should be compared with Marathon not Sprint. This course is just about preparing to the marathon. There is not even a single trade made. It's all just about preparing and planning the way to reach the finish. The finish is when you can "Save Your Time and let Computer Do the Job"
