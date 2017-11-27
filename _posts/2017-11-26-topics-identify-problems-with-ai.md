---
title: Identify Problems with Artificial Intelligence
excerpt: Bring your Complex Problem Solving Skills to a new level
categories: 
 - topics
tags:
 - featured
 - industry
 - artificial intelligence
 - kmeans
 - deep learning
 - autoencoder
date: 2017-11-26 16:18
---

## DRAFT 

## Summary

This little article describes the idea of using AI to identify problems. Problems in manufacturing where you have a lot of time-series data that are coming from multiple machines or processes. It gives an insights on how to transform basic SQL data on the server into the valuable information to alert human on the problems.

## Pre-face

Few month ago I went to Bern city centre. I went there with a purpose to visit a place where **Albert Einstein** was living more than hundred years ago. Believe me this place is very hard to find! It's so much hidden around fancy shops and caffee's. The museum is very small and depicting few years of the life of the later famous scientist. My attention however, was brought not to the famous formula, not the fact that he had not been good at math or languages. I was shocked with the fact how determine he was to solve problems. He took 1.5 years to solve just one problem. I had a very simple thought: "What if the guy had computing power we have today?"..."What if he could combine it with that genious?"... I went back home and was determined to think how it's possible to use computing power to solve problems. But then I quickly realized that the first thing I should do is different. I need to find the problem I want to solve first. I tried to research the subject and found several approaches on using computational power to identify a problems

## What is the problem?

In order to find a problem you need to know what is the problem? I was probably influenced by Kepner Treqoe approach that says that problem is when the object has deviation from normal state. Fine with that. Object can be a state of the object or process. It can be a result of the process that has a business importance. This can be resulting throughput, delivery time, sales values, quality score, satisfaction levels... 

## Combining power of logic and computers

But when the deviation starts? How to find this magic threshold without explicit setting of parameters? 

## Ideas from Problem Solving

Here came an idea about using logical thinking from *Problem solving methodology*. This brings us the assumption that any change in property over time potentially can lead to the problem. For example let's take a generic manufacturing process. In case the machine stopped working the first thing we must check is to verify what we did shortly before this failure occurred? We have a first hint: **monitor change**. 

Let's continue our discussion on what problem solving can bring to us? It will also add another dimension by asking: "Is there are another process or system(s) that might have a problem but not having it?". More over this logical approach will ask you to find what are the differences between properties of these processes or systems. Hence we have second hint: **Compare objects**

Obvously, the next idea was to see what strategies can we exploit to *automate* problem identification using Artificial Intelligence

## Unsupervised Machine Learning *kmeans*

Starting from the second hint about *Comparing objects* that should behave similarly. We can use pattern recognition techniques. Using popular algorithm **kmeans** we can arrange our data in the way that our observations are splitted into classes. This can already highlight the problem. For example in this image we can see group of observations that have been classfied differently versus the majority of other observations. This will help human to interpret the result and ultimately highlight the problem.

We can use this model to automatically pass new observations through our model and classify them again and again. Comparing objects may be tricky however. What if there is very little difference between them? Algorithm will still to split data into classes

... however we have another option...

## Deep Learning Autoencoders

What if we have no other option but to monitor change. Suppose we have serviced our equipment. Important process parameters of this equipment can be collected and used to (sorry for the long definition) Build a Deep Neural Network model using CPUs Builds a feed-forward multilayer artificial neural network on an H2OFrame. We will train this model on our *perfect* example. The model will learn patterns in this dataset. The image below will show what the actual data may look like and how the 'AI' would see it.

Think about it as yourself trying to memorise the landscape on the picture for a few seconds. Then you try to make the drawing on paper using your memory. Similar, right?

We will run our process further and sooner or later it will start to deviate. But, our process data will be continously 'passed' through our model. As soon as the error coming from the model will exceed given threshold - we will immediately get the alert!

Suppose you just seen a landscape with a forest and a river and memorised it in your memory. Now you get another landscape picture with a forest and a *frozen* river. Boom - you will notice that something is different right?

## Conclusion

These simple ideas were impemented in the course on the time-series data coming from several objects that should behave similarly.

## Final thanks

Here I should say thanks for my family (and git*) to allowing me to spend few time to creating this course :)

_* git allowed me to create course on the go while travelling for work
