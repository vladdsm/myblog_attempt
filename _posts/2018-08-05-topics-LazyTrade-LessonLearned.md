---
title: Data Scientist Lessons Learned
excerpt: Re-iterate to improve your code and make it more robust!
date: 2018-08-05
author: vladdsm
background-image: code_roxygen.JPG
categories:
  - topics
tags:
  - Lessons Learned
  - Data Cleaning
  - algorithmic trading
  - Version Control
  - Decision Support System
  - MQL4
  - Udemy
  - Artificial Intelligence
  - eLearnings
  - Debugging
---

## Another lessons learned - do not be afraid of those mistakes to learn and improve!

Every developer, data scientist or researcher could face situations when something is not working as desired. Normal reaction in those cases is to go through the code, execute it line by line, check the output for errors. There are some challenges on this way and potentially reward is waiting just around the corner!

This blog post [5 min read] is discussing about those challenges. Main message is that mistakes and bugs are simply not possible to avoid from the first go. So the recommendations and tips are given how to re-iterate and finally turn them into rewards!

### Not satisfied? Keep experimenting with new ideas!

Sometimes the results of your code are not satisfactory. It might be like that right soon after start of your test or even after a month of two after code deployment. Good advised is to come back to the code with some plan like that:

* re-produce your work
* note the 'opportunities'
* check for bugs or mistakes, if they are not present implement some of opportunities
* re-start your test

Obviously make sure to follow objective KPI of the experiment and track changes. In any case it can be actually positive to be not satisfied. This can be a trigger to actually go and find the error or create new functionality for your project!

### Productivity tips - how to stop `code reviewing procrastination`

`Coding` is so un-natural for the human being. I have very often so high procrastination level to simply open and review the code again. It's incredible! Probably the main reason of this phenomenon is that developer would need to stress the brain to remember the code and literally 'place' the code into the brain! It is like to build a house inside of your brain. Visualizing the structure of your work, putting those functions to specific building blocks, starting to go through those functions from start to end and checking the outcomes of every module... A simple thought that this process will need to be repeated is bringing procrastination. Probably this procrastination level will exponentially increase according to the time of last code review!

Those are few tips one can use to 'step over' and 'enter' out of comfort zone:

#### Plan sufficient time for code review

Code review may take anything from few minutes or few hours. It might be very advisable to find a complete free day and focus on this work. Perhaps Saturday or Sunday morning may do the trick best. Knowing that there will be sufficient time to slowly start and having a chance to finish the job will help to take decision and finally sit to start your work

#### Watch a good movie day before

Switch your mind day before presumed work. Watch a nice movie that would move your mind completely away from coding. However two conditions. Let it be a story from start to end of approximately 2 hours. Find a movie you would like but chose from those not hard for the brain. Just make sure that it would be an interesting story but not something that would seed a message or influence your thoughts for too long time!

#### Motivate yourself with potential reward!

Say to yourself those positive things before you start:

* 'I will find that mistake that will make my project better'
* 'It would be a great achievement later on'
* 'I am on the right track'
* 'I will learn more new things because I will be experimenting'

#### Just start, review code from scratch!

Enter 'out-of-comfort-zone' by starting reviewing the code from scratch. This will help to recover the 'building blocks' in your brain 'operative memory'. In case your code is more complex and use functions follow the next advise

#### Keep data samples, commented code in functions, notes...

Keeping code in functions is probably the right approach, however it may be painful to debug them. There are three simple strategies that could be used:

* simply write notes in the code
* insert 'Roxygen scheleton' and write description of each argument
* always add commented code within your function to 'back-test' the code step by step within the function

Some of these tips could obviously be used for simple R scripts as well

#### Refresh your mind

Developer brain is like CPU! It needs two essential things:

* energy
* cooling

So make sure to start your work after having light breakfast or snack rich in carbohydrates. Cup of coffee or tea with a bit of a chocolate is something that will work. When the attention is lower the energy portion may be renewed. Drinking more water and some short physical exercise can help too.

Obviously cooling is something not to forget about. Taking a refreshing shower before start can be a good choice

### Data cleaning - once again... Making things Visual

I heard from one colleague that there are not only two things certain in live but three!

* taxes
* death
* and *bad data...*

Some typical examples:

#### Zero values

In several courses from the Lazy Trading series data is retrieved from MT4 platform by running a `for` loop. Technically there might be empty database and few particular data points will contain zero values. The best way is to always allow these cases however sometimes it's not possible. In case we could suspect to have them using this filter function may help to remove those:

`... %>% filter_all(any_vars(. != 0))`

In some cases those zero values may cause additional problems...

#### Outliers

Here is the example of such a case where data outliers on the label were detected:

<img src ="https://raw.githubusercontent.com/vladdsm/myblog_attempt/master/images/skewed_too_much.png" alt="speakom"   />

and here is how it should like:

<img src ="https://raw.githubusercontent.com/vladdsm/myblog_attempt/master/images/balanced.png" alt="speakom"   />

So use these simple functions like `summary(DataFrame)` and `hist(DataFrame$ColumnName)` to identify problem.

### Don't forget what you do, keep it as live test with logs!

Keeping diagnostics records generated during execution of your code is very good idea! It may seems adding some work but it will definitely pay off! Just quickly looking on the summary of results could make these two important gains:

* quick check of performance and generated value
* possible to automate checks
* possibility 'not to forget' about the project

Implementation can be very easy. It is sometimes just enough to save the resulting dataframe into `*.csv` or `*.rds` formats. For example, code below will write the resulting dataframe to the specific location:

`... %>% write_csv(path = paste0(path_LOG, Sys.Date(), "-", num_bars, "-",timeframe, "R", ".csv"))`

### Don't erase the mistakes, use Version Control!

Probably a final advise is about the discipline. It's all about pushing the limits and acknowledge mistakes. Write the mistakes down and check them into Version Control. Latter may help to return back into history to take potentially alternative project path but not start from scratch...

## Conclusion

Those tips are covering few ideas around coding, psychology of a developer and researcher. Once again the main message is that making and discovering mistakes can be actually very rewarding. It may be hard to overcome 'code-checking' procrastination but knowing and visualizing possible reward is certainly worth the effort!

Feel free to send your feedback if this would be ever helpful and make sense! 