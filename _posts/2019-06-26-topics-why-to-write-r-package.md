---
title: Why do I write an R package
excerpt: Sharing experience of building your first R package
date: 2019-06-26
author: vladdsm
categories:
  - topics
tags:
  - lazytrade
  - r package
  - Version Control
  - Open Source
---

## Making a last mile effort - submitting R package to CRAN

Recently I was looking into the process of creating a package and submiting that to the CRAN repository.
Honestly I found this experience both nice and challenging. In this short post (5 min read) I would like to share these experiences and hopefully to convince doing that one last extra mile!

### Why I decided to do that?

In the very beginning I never had an idea to write a package. However at the moment when I was looking into developing my dedicated Docker Container with my favorite packages this was quite a natural outcome.
The idea was to simply add all my functions to the package and submit that to CRAN. Of course by doing so it would bring few more advantages to students of the lazytrade project on Udemy:

* No need to 'source' function by modifying local directory
* More quality and reproducibility of code
* Opportunity to optimize code, add automatic tests for better quality
* Nice and neat documentation
* Public demonstration of capabilities around R / Data Science

### Few general tips about the process

* Start with one or two functions first and compile the package!
* Add data and examples, don't postpone this process
* Process is semi - manual so record your steps in the Readme file [for example](https://github.com/vzhomeexperiments/lazytrade/blob/master/README.md#notes-to-remind-myself-how-to-create-r-package) this file contains some code snippets and short description on how to add data, document datasets, make tests, etc
* Solve all the Errors, Warnings and Notes, don't postpone!
* Capture information in [Hadley's book](http://r-pkgs.had.co.nz/) or similar, but don't hesitate to 'google' for the answer. According my experience these books are not always updated to reflect recent tools and policies
* Learn about using R-Studio in Docker Container to test your package for example in my [Docker course](https://www.udemy.com/docker-containers-data-science-reproducible-research/?couponCode=DOCKERRR)
* Make sure to automate the process as much as possible including automated build and submission of the new versions

### Be ready for challenges!

Probably the hardest challenge is to be systematic and push yourself to return to your work!
This is probably a little warning check for those who would decide to add package to CRAN because process would require maintaining your code, fixing bugs and re-building the package every few months as R version evolves

## Conclusion

Writing an R package is somehow challenging process in the beginning but rewarding at the end. Main idea of this post is still to try this but start small and add more functions later!