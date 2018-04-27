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

This course will cover setting up your personal Trading Journal. At the end of this course you will have your local tool that can be use to verify trading systems performance in minutes. It will help you to:

* Monitor trading systems over time
* Have an overview of all trading systems in the trading terminal
* See performance of particular trading system in the terminal
* Visually correlate price action of the asset to the trading results
* Write your thoughts behind performances and possible improvements
* ... learn to program ShinyApps [interactive tool to deploy Data Science Project]!

By the way, **This is not a trading advice!** so just relax and have a fun reading for the next 5 minutes!

## Shiny Basics & Data Grammar

This section introduces the tool. Basics and where to find relevant info. Few concepts about Data Visualisation are also explained there

## Building trading journal

In this section we will learn how to get the code, synchronise it easily and know how to modify it to suit our purposes. We will mainly look to:

- Write financial data assets to the file
- Basic overview of shiny app structure
- How to keep strategy text in front of us when we use journal
- Hot to add notes to the journal and keep them persistently stored in a file

Below I would shortly summarise the purpose of those

### Write financial data to file

This is needed simply to have an ability to visualise time-series price of the asset data in our journal. We are using MQL4 Robot to log the data to the simple file. Things will be happening automatically as the data will be refreshed by our robot every 15 minutes

### ShinyApp structure

Idea of User Interface and Server scripts can be easily understood by anyone. More different is the notion of different reactions of shiny. This course should help you to get intuition on how they work by looking on the working example.

A word of caution: Shiny App is hard to troubleshoot. The recommendation tip is to ‘comment’ some code that would help to debug piece of the code. Often helpful to store a sample R data object as an *.rds* object and store it inside of the repository. This way it would be much easy to maintain the code. For example after R/Library updates this may be very relevant…

### Visualise the Strategy text

This is all to keep things in one place! We see trading results - we see our Trading Strategy. Proposed method is to keep one file in which we write the key strategy elements. For example strategy entry/exit rules, targeted market inefficiency. Most importantly strategy ID code would be automatically matched with a magic number decoded ID. Please read description from the LazyTrade Part2 blog section *Magic Number Convention*

### Adding notes 

Yes ability to add notes, comments, improvements is the trading journal characteristic. Not only we can add new but also see previous notes. Interesting principle covered in this block is the ability to store/retrieve information from simple comma-separated files. Easy to manage and troubleshoot and no need of the bulky databases!

## Conclusion

What else one would want to see in the trading journal? Well, the answer depend on every individual. This may include many things. For example upcoming Forex news events, current market type, may be relevant financial news... list can be expanded as far as this Lazy Trading Series. What is important is that it should... "Save Your Time and let Computer Do the Job"