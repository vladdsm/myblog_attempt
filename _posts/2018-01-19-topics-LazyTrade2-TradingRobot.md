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

This course will cover setting up your personal Trading Robot Template. At the end of this course you will have complete and ready to be used Trading System installed and active on your Home Computer. It will help you to:

* Programming environment
* Setting up Version Control Project
* Overview of robot functions
* How to customize to target market inefficiency
* Integrate robot with Decision Support System (start/stop trading system from external commands)
* Customize and record trades results
* You will be able to customize this Robot Template

By the way, **This is not a trading advice!** so just relax and have a fun reading for the next 5 minutes!

## Programming Environment

In this section of the course I mainly talk about using our Algorithmic Trading Environment. As usual this is just a brief theoretical section aiming to give you conceptual understanding. My goal was to give you a bigger picture of the entire thing, architecture of our Trading Environment and how you can orient in it.

## Adapting Robot Template

IN this section you will learn how to get the code, synchronize it easily and know how you can modify it to suit your purposes. We will mainly look to:

- Log trading results from the Trading Robot
- Reading external commands in the Trading Robot
- How to further modify trading strategy

Below I would shortly summarize the purpose of those

### Log Trading Results

It's all about setting a standard. All your trading robots will be able to record trading results in one place! That easy. You don't have to worry about it! You just know that when the trade will be completed the results will be stored. No databases - just simple csv file!

### Reading external commands in the Trading Robot

This is all about control. How can you just switch on/off your trading robot from external software? This we will learn in this lecture. Not only that. You will be able to virtually to anything to your trading robot. Even the weather forecast:)

### How to further modify it

The robot can and must be modified. Experiment, log changes and try different things. I just explain where. Simple recommendation is to make modular changes and use Version Control.

## Conclusion

Course is concluded by showing Demo test trading results. The results will be shown using our own Trading Journal [topic of the next course of the series]. That's because we will always want to be Lazy and... "Save Your Time and let Computer Do the Job"
