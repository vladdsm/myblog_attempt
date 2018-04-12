---
title: Lazy Trading Part 3 Set up your Trading Journal
excerpt: Learn Computer and Data Science through Algorithmic Trading
date: 2018-01-28
author: vladdsm
categories:
  - topics
  - lazy trading
tags:
  - algorithmic trading
  - Version Control
  - Decision Support System
  - R
  - Shiny
  - Trading Journal
  - MQL4
---

## Set up your Trading Journal

In this blogpost [5 min read] I would like to explain the motivation behind the third course of the series. 

This course will cover setting up your personal Trading Journal. At the end of this course you will have your own Trading Journal. It will be your local tool that you can use to verify your trading systems performance in minutes. It will help you to:

* Monitor trading systems over time
* Have an overview of all trading systems in the trading terminal
* See performance of particular trading system in the terminal
* Write your thoughts behind performances and possible improvements
* ... learn to program ShinyApps!

By the way, **This is not a trading advice!** so just relax and have a fun reading for the next 5 minutes!

## Shiny Basics & Data Grammar

This section introduces the tool. Basics and where to find relevant info. Few concepts about Data Visualization are also explained there

## Building trading journal

In this section you will learn how to get the code, synchronize it easily and know how you can modify it to suit your purposes. We will mainly look to:

- Write financial data assets to the file
- Basic overview of shiny app structure
- How to keep strategy text in front of us when we use journal
- Hot to add notes to the journal and keep them persistently stored in a file

Below I would shortly summarize the purpose of those

### Write financial data to file

This is needed simply to have an ability to visualize time-series price of the asset in our journal. We are using MQL4 Robot to do this. Things will be happening automatically as the data will be refreshed by our robot every 15 minutes

### ShinyApp structure

Idea of User Interface and Server scripts can be easily understood by anyone. More different is the notion of different reactions of shiny. This course should help you to get intuition on how they work by looking on the working example

### Visualize the Strategy text

This is all to keep things in one place! You see your results - you see your strategy. What do you need else?

### Adding notes 

Yes ability to add notes, comments, improvements is the trading journal characteristic. Not only you can add new but also see previous notes.

## Conclusion

What else you want to see in the trading journal? Well, the answer depend on every individual. This may include many things. For example upcoming Forex news events, current market type, may be relevant financial news... list can expand. What is important is that it should... "Save Your Time and let Computer Do the Job"