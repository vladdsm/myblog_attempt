---
title: Lazy Trading Part 5 Reading News and Sentiment Analysis in Forex
excerpt: Learn Computer and Data Science through Algorithmic Trading
date: 2018-03-03
author: vladdsm
categories:
  - topics
  - lazy trading
tags:
  - algorithmic trading
  - Web scrapping
  - Macroeconomic Forex News
  - Forex Calendar
  - qdap
  - rvest	
  - Sentiment Analysis
  - Version Control
  - Decision Support System
  - MQL4
---

## Read News and Sentiment Analysis in Forex

In this blogpost [5 min read] I would like to explain the motivation behind the fifth course of the series. 

The title of the course may be misleading. It is not about an algorithm to decode speech of the Prime Ministers or Central Banks heads in real time and generate trading decisions. No, it is about more simple things and ideas. First is to automatically detect presence of certain disruptive events in the Financial world like elections, key Forex news releases etc. Second it’s about studying polarity score or sentiment of the News headers and trying to correlate that to Financial Markets. Latter idea is probably very naive to be used for trading rather it can only be considered as a Social Research. Nevertheless this course would provide you value around those topics:

* Learn to perform web harvesting or scrapping to gather information from the Internet using R and rvest package
* Be able to automatically disable your trading systems in case matched Macroeconomic news are detected
* Learn to perform Polarity Scoring sentiment analysis of the text
* Perform descriptive analysis of the Polarity Scoring of the News headers from 3 english speaking countries US, UK, CA (I have a separate course about automated translation as well)
* Get the example of trading robot (use at your own risk) to define explore and test the trading idea
* Answer the question: “Are we bombarded by the bad news?” 

By the way, **This is not a trading advice!** so just relax and have a fun reading for the next 5 minutes!

## Know when macroeconomic news are released?

In case our trading system is not designed to capture sudden volatility it may be a good reason to avoid trading on certain days. Decision to do so is out of scope of this course. What the scope is is how to automate this process and to stop trading systems when certain event is going to occur.

## How do we do that?

This technique is relatively easy to achieve once you know a bit R. The idea is to follow few simple steps:

1. Generate url corresponding to the web page containing relevant information (for specific day)
2. Use *rvest* package to get the webpage content
3. Extract relevant columns from the table using html tags
4. Combine everything into the data frame object
5. Match every row in the table to the corresponding event
6. Depending on the result generate file containing relevant information
7. Use it inside Trading Robot

## Web as the data source for decision

Still, there would be always attempts to use AI to derive trading decision. Once again this course is not aiming that high. We are not here to generate trading decision using complex NLP modelling. More simple idea linked to Social Trading is being used instead 
 
## Are we bombarded by bad news?

In this course we are answering this question. 

A little challenge to the fellow reader: Please open any news aggregator of your preference. There would probably be 20 - 30 articles. Starting from politics moving to economy, sport, etc. Please try to classify these news according to simple grade: Good, Neutral, Negative. It is very likely that overall amount of news with negative score would prevail.

Now why does that matter? How can it be relevant? Well the idea (author assumption) is that news sentiment does matter and affecting society. The assumption of the author is that people who will read the good news in the morning will go to work being more happy. They will have higher productivity and produce more goods, services. There is much higher chance the happy scientist would invent something new, isn’t it??? 

## Social Research and trading idea

So using packages *rvest* and *qdap* we can read news headers from the news aggregator of several countries. 

Thanks to qdap library we can calculate overall sentiment of every news header. Software is using pre-defined library of classified words and output the score being positive if it’s more than 0 and vice versa negative sentiment will return value below zero.

Thanks to this analysis we can easily get average sentiment values from the entire country. This is the result of what you can see after 1 month of collecting this data:


If we subtract absolute values from one country to another country we will get this graph:



Notice that sometimes the difference is quite high. This is physically meaning that there was good news in one country and bad news in another country. Or, bad news in one country and very bad news in another country…  

## Conclusion

At the moment of writing this blog the research is still going on. What is clear so far is that majority of the news sentiment are negative. There are only few days when positive news do prevail. However why not to be about this and try to change that! Can we all influence this situation to make it opposite? Can we make it the way around so the good news would prevail? Perhaps then we will live in the better place?!