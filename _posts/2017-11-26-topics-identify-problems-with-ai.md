---
title: Identify Problems with Artificial Intelligence
excerpt: Bring your Complex Problem Solving Skills to a new level
categories: 
 - topics 
date: 2017-11-26
author: vladdsm
background-image: predict.png
tags:
  - featured
  - h2o
  - kmeans
  - Deep Learning
  - Anomaly Detection
---

## Summary

This little article [~7 min read] describes the idea of using Artificial Intelligence to **identify** problems. Problems in manufacturing where you have a lot of time-series data that are coming from multiple machines or processes. Article should give you insights on how to transform basic time-series data into the signal to alert human on potential problems.

## Why to bother?

Few month ago I went to Bern city centre. I went there with a purpose to visit a [place](http://www.einstein-bern.ch/index.php?lang=en) where **Albert Einstein** was living more than hundred years ago. Believe me, this place is very hard to find! It's so much hidden around fancy shops and caffee's. The museum is very small and depicting just few years of the life of the later famous scientist. My attention however, was brought not to the famous formula, not the fact that Einstein had bad times with languages. I was shocked with the fact how determine he was to solve problems. He took 1.5 years to solve just one problem. I had a very simple thought: "What if the Einstein had computing power we have today?"..."What if he could combine it with that genious?"... I went back home and was determined to think how it's possible to use computing power to solve problems? But then I quickly realized that the first thing I should do is different. I need to find the problem I will want to solve first. I researched the subject and found several approaches on using computational power to identify problems

## What is the problem?

In order to find a problem you need to know it's definition. In my view **problem is when the object new state deviate from original state AND this new state is something un-desirable**. In order to turn this into Math we need to quantify *Object State* as something measurable. This *metric* can be result of the process that has a business relevance. For example this can be resulting throughput, delivery time, sales values, quality score, satisfaction levels... 

But when the deviation starts? How to find this magic threshold without explicit setting of parameters? How can we at least suggest this state to the human to later decide if it's *undesirable* or not?

## Ideas from Problem Solving

Here came an idea about using logical thinking from *Problem Solving*. This logic will force us to ask: "Is there are another process or system(s) that might have a problem but not having it?". More over this logical approach will ask you to find what are the differences between properties of these processes or systems. Hence we have a first hint: **Compare objects**! The advantage we can have is that manufacturing process rarely has only one line or process. There are very often multiple same processes or machines that are running in parallel. We can have an advantage to monitor data from several lines and compare them

Let's continue our discussion on what problem solving can bring to us? It asks us to verify what has happened with the object before it broke. It points out strong assumption that any change in property over time is a potential cause of the problem. For example let's take a generic manufacturing process. In case the machine stopped working the first thing we must check is to verify what we did shortly before this failure occurred? We have a first hint: **monitor change**. 

## Combining power of logic and computers

Obvously, the next idea was to see what strategies can we exploit to *augment problem identification* using Artificial Intelligence?

## Unsupervised Machine Learning *kmeans*

Let's start *Comparing objects* that should behave similarly. We can use pattern recognition techniques. For example algorithm **kmeans** can arrange our data in the way that our observations from several similar processes or machines are splitted into classes. The fact that this data splits into classes (*normality* and *anormality*) can already highlight the problem. For example in this image we can see group of observations that have been classfied differently versus the majority of other observations. As a reminder - this depicts 4 exact same machines and shown parameter must be the same!

<img src ="https://raw.githubusercontent.com/vladdsm/myblog_attempt/master/images/plotarbitrary.png" alt="speakom"   />

Solely this image will help human to interpret the result and ultimately highlight the problem. We can use this model to automatically pass new observations through our model and classify them again and again. No complex modelling or *big data* is involved...

Comparing objects may be tricky. What if there is very little difference between them? Algorithm will still split data into classes... however we have another powerfull option...

## Deep Learning Autoencoders

What if we have no other option but to monitor change. Suppose we have serviced our equipment bringing it to the perfect state. Important process parameters of this equipment can be collected right after service. Data can be used to ... (sorry for the long definition) *Build a Deep Neural Network model using CPUs Builds a feed-forward multilayer artificial neural network on an H2OFrame*. We will train this model on our *perfect state* data example. For example the model [AI] can learn patterns in this **ECG** dataset. For the better clarify 3D image of the dataset will be generated using `plotly` library in `R`: 

<img src="https://raw.githubusercontent.com/vzhomeexperiments/detect-anomaly/Lecture25-DeepLearning/h2o_datasets/train.png" >

Once the model was trained on this dataset we will test it on new dataset where 3 anomalous records were added [highlighted by red arrow]

<img src ="https://raw.githubusercontent.com/vladdsm/myblog_attempt/master/images/test.png" >

This is how the 'AI would see' new dataset where three new rows have an anomaly:

<img src ="https://raw.githubusercontent.com/vladdsm/myblog_attempt/master/images/predict.png" >

The last three rows will in fact generate different responce. The Mean Square Error coming from the model will exceed given threshold - we will immediately get the alert! This is how *MSE* metric would look like as soon as you pass data with *Anomaly*:

<img src = "https://raw.githubusercontent.com/vzhomeexperiments/detect-anomaly/Lecture25-DeepLearning/h2o_datasets/MSE.png">

This concept is very powerful as it can help to build **Predictive Maintenance** dashboard solely from monitored parameter by monitoring *MSE* metric over time

## Conclusion

Identifying problems automatically is probably a wish of every manufacturer. This article just described some ideas on using *Artificial intelligence* together with logical approach coming from *Problem Solving* in order to take an advantage of:

- comparing similar objects that should behave similarly
- monitoring object state over time

## Postscriptum

These simple ideas were impemented in the course that describes the entire process in a very detail and even provide you a working application **ShinyApp** to deploy this anomaly detection techniques or better understand the method. Feel free to check it out inside the [works](https://vladdsm.github.io/myblog_attempt/works/) section of this site!

## Final thanks

Here I should say thanks for my family (and git*) to allowing me to spend some time to creating this course :)

_* git allowed me to create course on the go while travelling for work
