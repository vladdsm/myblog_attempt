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



## DRAFT 

## Summary

This little article [~7 min read] describes the idea of using Artificial Intelligence to identify problems. Problems in manufacturing where you have a lot of time-series data that are coming from multiple machines or processes. Article should give you insights on how to transform basic time-series data into the signal to alert human on potential problems.

## Why to bother?

Few month ago I went to Bern city centre. I went there with a purpose to visit a [place](http://www.einstein-bern.ch/index.php?lang=en) where **Albert Einstein** was living more than hundred years ago. Believe me, this place is very hard to find! It's so much hidden around fancy shops and caffee's. The museum is very small and depicting just few years of the life of the later famous scientist. My attention however, was brought not to the famous formula, not the fact that Einstein had bad times with languages. I was shocked with the fact how determine he was to solve problems. He took 1.5 years to solve just one problem. I had a very simple thought: "What if the Einstein had computing power we have today?"..."What if he could combine it with that genious?"... I went back home and was determined to think how it's possible to use computing power to solve problems? But then I quickly realized that the first thing I should do is different. I need to find the problem I will want to solve first. I tried to research the subject and found several approaches on using computational power to identify problems

## What is the problem?

In order to find a problem you need to know it's definition. In my view **problem is when the object new state deviate from original state AND this new state is something un-desirable**. In order to turn this into math we need to quantify *Object State* as something measurable. This *metric* can be result of the process that has a business relevance. For example this can be resulting throughput, delivery time, sales values, quality score, satisfaction levels... 

But when the deviation starts? How to find this magic threshold without explicit setting of parameters? How can we at least suggest this state to the human to later decide if it's *undesirable* or not?

## Ideas from Problem Solving

Here came an idea about using logical thinking from *Problem Solving*. This brings us the assumption that any change in property over time potentially can lead to the problem. For example let's take a generic manufacturing process. In case the machine stopped working the first thing we must check is to verify what we did shortly before this failure occurred? We have a first hint: **monitor change**. 

Let's continue our discussion on what problem solving can bring to us? It will also add another dimension by asking: "Is there are another process or system(s) that might have a problem but not having it?". More over this logical approach will ask you to find what are the differences between properties of these processes or systems. Hence we have second hint: **Compare objects**! The advantage we can have is that manufacturing process rarely has only one line or process. There are very often multiple same processes or machines that are running in parallel...

## Combining power of logic and computers

Obvously, the next idea was to see what strategies can we exploit to *augment problem identification* using Artificial Intelligence?

## Unsupervised Machine Learning *kmeans*

Starting from the second hint about *Comparing objects* that should behave similarly. We can use pattern recognition techniques. Using popular algorithm **kmeans** we can arrange our data in the way that our observations from several similar processes or machines are splitted into classes. The fact that this data splits into classes (*normality* and *anormality*) can already highlight the problem. For example in this image we can see group of observations that have been classfied differently versus the majority of other observations. 

<img src ="https://raw.githubusercontent.com/vladdsm/myblog_attempt/master/images/plotarbitrary.png">

This will help human to interpret the result and ultimately highlight the problem.

We can use this model to automatically pass new observations through our model and classify them again and again...

Comparing objects may be tricky however. What if there is very little difference between them? Algorithm will still to split data into classes... however we have another powerfull option...

## Deep Learning Autoencoders

What if we have no other option but to monitor change. Suppose we have serviced our equipment bringing it to the perfect state. Important process parameters of this equipment right after service can be collected and used to (sorry for the long definition) *Build a Deep Neural Network model using CPUs Builds a feed-forward multilayer artificial neural network on an H2OFrame*. We will train this model on our *perfect state* data example. For example the model [AI] can learn patterns in this **ECG** dataset. For the better clarify 3D image was generated using `plotly` library in `R`: 

<img src="https://raw.githubusercontent.com/vzhomeexperiments/detect-anomaly/Lecture25-DeepLearning/h2o_datasets/train.png" >

This is how the 'AI' would see it:

<img src ="https://raw.githubusercontent.com/vzhomeexperiments/detect-anomaly/Lecture25-DeepLearning/h2o_datasets/predict.png" >

*Think about it as yourself trying to memorise the landscape on the picture for a few seconds. Then you try to make the drawing on paper using your memory. You will capture some details if they are simple, overal idea, but probably will have a difficult time to remember everything, right?*

We will run our process further and sooner or later it will start to deviate. But, our process data will be continously 'passed' through our model. As soon as the error coming from the model will exceed given threshold - we will immediately get the alert! This is how *MSE* metric would look like as soon as you pass data with *Anomaly*:

<img src = "https://raw.githubusercontent.com/vzhomeexperiments/detect-anomaly/Lecture25-DeepLearning/h2o_datasets/MSE.png">

*Suppose you just seen a landscape with a forest and a river and memorised it in your memory. Now you get another landscape picture with a forest and a **frozen** river. Boom - you will notice that something is different right?*

## Conclusion

These simple ideas were impemented in the course that describes the entire process in a very detail and even provide you a tool to deploy this anomaly detection technique in a real production environment. 

p.s. if you were so kind to read up to the end, get the discounted [coupon](https://www.udemy.com/identify-problems-with-ai-case-study/?couponCode=AI-DETECT-PROBLEM) for this course for a special symbolic price of 10USD. Offer will be valid until 2017-12-09

## Final thanks

Here I should say thanks for my family (and git*) to allowing me to spend few time to creating this course :)

_* git allowed me to create course on the go while travelling for work
