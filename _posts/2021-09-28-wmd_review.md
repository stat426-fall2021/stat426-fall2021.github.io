---
title: "Statistical Genocide: A Review of Cathy O'Neil's Weapons of Math Destruction"
layout: post
author: joshegladwell
post-image: "https://miro.medium.com/max/942/1*H0yCBVZmZ1i3LoA1tUyAQQ.png"
description: A small-scale review of a large-scale book--Weapons of Math Destruction: How Big Data Increases Inequality and Threatens Democracy by Cathy O'Neil
tags:
- Book Review
- Data Science
- Data Science Ethics
- Weapons of Math Destruction
- Cathy O'Neil
---

![Book Cover](https://m.media-amazon.com/images/I/51SoudLYBaL.jpg)

# Introduction
A couple weeks ago during a lecture in Dr. Tass’s STAT 420 class this semester, she was discussing some of the ethics behind data science and mentioned Cathy O’Neil’s book, *Weapons of Math Destruction: How Big Data Increases Inequality and Threatens Democracy*. I was intrigued by the title and decided to check out the audiobook from my library app. For a while now I have been very interested in the societal roles of data science—how it can be used on a social level for either good or bad in the world we live in. Although I am still in the process of listening to the book, I will review the book by focusing on one particular chapter that I found to be very captivating. In doing so, my hope is that you will gain an idea of what O’Neil means by the phrase, “weapon of math destruction,” and be able to recognize them in your future work as data scientists.

# Background
The generic phrase, *weapon of mass destruction*, was first used [following the World War II bombing of Hiroshima](https://www.nytimes.com/1998/04/19/magazine/on-language-weapons-of-mass-destruction.html). This attack is estimated to have killed [one-fifth of the entire population of Hiroshima](https://www.atomicarchive.com/resources/documents/med/med_chp10.html). The phrase has since come to refer not only to atomic weapons, but also biological and chemical weapons—all of which have the potential to take millions of lives. It’s interesting that O’Neil adopts the same phraseology to describe the topic of this book. It speaks to the power she believes data menacingly holds over millions of people. To briefly explain, O’Neil defines weapons of math destruction (WMDs) essentially as algorithms or models that operate under the assumption that they are unbiased when in reality they are based on biased data, and therefore further perpetuate that bias. WMDs pop up in hiring metrics, teacher ratings, criminal proceedings, and many more everyday contexts. They take data that reflects systemic issues in society and spit out results consistent with that previously held issue. However, O’Neil argues, these models and algorithms are so dangerous because of how we treat them. We are inclined to believe that if something is machine then it has no bias. Bias is a human trait. After all, calculators don’t have bias. Simple computer programs don’t have bias. Computers will never choose to change mathematical truths or interpret code syntax differently. They do exactly what we tell them to do. Subsequently, we all subconsciously determine that the information we receive from an algorithm is tantamount to holy scripture. The problem, however, is that bias can in fact leak into our algorithms if we aren’t careful about ensuring that we feed it unbiased data.

![Photo of Cathy O'Neil](https://pbs.twimg.com/profile_images/1104749880717819905/4uj-gXMF.png)

*Photo of Cathy O'Neil, author of *Weapons of Math Destruction*. I love her hair. That hair is a weapon of math destruction.*



# A College Example
Based on that background on what a WMD is, I was fascinated with one chapter of this book in particular that delves into the WMD of the *U.S. News & World Report* college rankings. To briefly summarize—as a news outlet struggling to stay relevant in 1983, *U.S. News* decided to start publishing an annual rank of the best colleges across the United States in hopes to help inform prospective students of the best places to receive their bachelor’s degree from. The rankings hit the country by storm and a host of unintended consequences followed including inflated tuition costs, the collapse of student safety school plans, and misreporting of student data on the part of colleges. The most interesting consequence of the *U.S. News* college rankings to me, however, is the attempt to quantitatively build an algorithm that measures something so qualitative. To be specific, O'Neil outlines the main variables *U.S. News* uses in the algorithm:

* Incoming student test scores
* Acceptance rates
* Graduation rates
* Freshman retention
* Student to faculty ratio
* Alumni donations

O’Neil is quick to clarify that this in and of itself is not bad. The problem with using proxy data to represent something more abstract in this scenario is due to the large scale of the *U.S. News* rankings. Because so many colleges jockey for a good position in these rankings that monopolize the standards of what a good college is, it’s easy for the colleges to manipulate the proxy variables in arbitrary ways. This leads to an overall deemphasis on education quality, a superfluous emphasis on student admission variables such as acceptance rates, and a perpetuating cycle of colleges and students chasing arbitrary quotas while ignoring the actual motivators behind such quotas.

# Conclusion and Review
This example of a WMD in the *U.S. News* college rankings speaks to a larger theme that O’Neil explores in her book. While describing the system that *U.S. News* uses to evaluate the colleges, she subtly describes an algorithm as “an opinion formalized in code.” Sure, algorithms are powerful in their ability to determine what we read, see, and interact with. But their selection and weighing of variables are based on opinion. As citizens of a world driven by data and fueled by models and algorithms, we ought to remember that they still are not perfect. As future data scientists, we have a moral obligation to be responsible with the data we collect and the models we build. While our products will have the potential to vastly enrich life, they will also have the potential for mass destruction.

As I mentioned above, I am still in the process of listening to this book, but from what I have read so far I highly recommend it. As students of data science we are easily enamored with all of the problems big data can solve but don't give much attention to the problems it can cause. It is a must-read for any aspiring data scientist as it reminds us of the importance of being responsible with bias in data and models. It has also been fascinating to recognize examples of WMDs in the world. I would love to hear some examples in the comments of WMDs that you've noticed.

The book can be purchased [here](https://www.penguinrandomhouse.com/books/241363/weapons-of-math-destruction-by-cathy-oneil/).
