---
title: How Machine Learning May Take Real Estate to 'The Next Level'
layout: post
author: tmanjson
post-image: /assets/images/blogimages/figs-10-06/cityscape.jpeg
description: An overview of machine learning methods currently being used in the real estate industry and their possible roles in the future.
tags:
- Machine learning
- Real estate
- Variable selection
---

### Introduction
Machine learning (ML) has come somewhat recently into the field of investments and real estate as a tool that buyers and sellers can use to evaluate and predict prices, volatility, and a number of other factors. While most experts recognize the usefulness of such technology, it is not yet fully understood what all can be done with machine learning and what its effect will be on the real estate market in the future.

This post is meant as an overview of how machine learning is currently being used in the real estate market, and assess how it will influence the market in the future. I will look at the following three topics:
1. Variables used for property valuation.
2. Favorite methods and models in the field currently.
3. The future of the real estate industry with ML/AI

### Housing Market Influences

![influences](/assets/images/blogimages/figs-10-06/housing_influences.jpeg)

One of the key potential uses for artificial intelligence and machine learning in the real estate industry is the valuation of properties. **Property valuation** is the practice of assessing a property’s potential value. Valuation can be performed by looking at a number of variables and determining how much profit can be gained from a property within a given timeframe. It is often used by real estate organizations and individuals as part of an investment decision-making process. As the use of ML is still relatively new in the field of real estate, there remains the question of which factors ought to be taken into account when building an ML model for property valuation. In this section, I will look at different variables that have been used for such valuation and what researchers have found are important factors to consider.
##### Micro-variables
Ado et al. (2020) reported that, of the studies they surveyed, the majority of ML models for property valuation had been performed using **micro-variables**, or local and small-scale factors that influence property value. Such variables may include:
* availability of real estate within a given area
* location of a property
* prices within a certain radius of the property in question
* number of rooms
* square ft., -etc.

Of the 26 different studies surveyed in the article by Ado et al., the study performed by Morano et al. (2015) resulted in the highest R² score, indicating the prediction model with the least error. However, besides this specific study, the other studies examining only micro-variables did not perform as well as other criteria, with only 23% of the studies reaching an R² score of over 90%. Morano et al. also point out that although their model was well fit, their sample size was relatively small, and that further research would be necessary for greater understanding of the market. *These findings suggest that more factors than just micro-variables may be necessary to produce a consistently accurate ML model for valuation.*
##### Macro-variables
Other variables to take into account for real estate valuation are macro-variables. **Macro-variables** are large scale events or influences that affect the economy or housing market as a whole. These may include:
* GDP
* National/international laws
* Global events,etc.

Renigier-Bilozor and Wiśniewski (2013), Constantinescu (2019), and others each performed macro-variable-focused studies, finding prediction models that were mostly accurate, yet either failed to account for different time frames or were not applicable to different countries and regions. (Constantinescu found that while GDP and credit were a good measure of real estate prices for the most part, there were times in which they did not account for all trends in the real estate market. This failure was most obvious in the 2005 recession, as the global average housing market spiked while the GDP did not.) This suggests that macro-variables alone cannot be relied upon to accurately make predictions all the time either.  *Thus we see that, like models focused only on micro-variables, those models that only took macro-variables into account also failed to follow the market accurately all the time.*

It may therefore stand to reason that an accurate prediction model must take both the macro and micro into consideration in order to reliably predict property values in any given location. Kabaivanov and Markovska (2021) suggest three key factors to take into account when analyzing the housing market:
* global influences (or macro-variables)
* local factors
* individual property characteristics

Ado et al. (2020) conclude their study with a similar claim, stating that a *blend of macro and micro variables is necessary for accurate analysis.* These positions are upheld even by those studies which focused exclusively on either macro or micro variables. Renigier-Bilozor and Wiśniewski (2013), Constantinescu (2019), and Morano et al. (2015) each concluded their studies expressing the need for both large and small scale data to take into account.

Further research may focus on which variables of the two categories are consistently most important. It may also be concluded that there is no one set of variables best suited for every property, and that different variables ought to be considered for different locations, or when using various ML modeling techniques. Whatever the case, much progress has been, and will yet be made towards greater and more reliable property valuation in the coming years. In the following section, I will discuss some of the more popular methods of modeling that have been used in the real estate industry to date.


### ML Algorithm Methods

![ML](/assets/images/blogimages/figs-10-06/ML.png)

As there is still much being done to improve machine learning methods and practices in nearly every field, there is little doubt that techniques and ideas will continue developing in the future. There is much to take into account while attempting to analyze the housing market. However, there are some methods that have been suggested that may help individual home investors and professional real-estate organizations alike.

##### Time-series Models
One method experts often use to track data that depends on the date or time is a **“time-series model”**. These can be used to account for shared characteristics between similar time frames (same month of different years, same day of different weeks, etc.). Yu et al. (2020) suggest one such model for price forecasting, using a quadratic smoothing model, (helpful with non-linear trends), that periodically updates its estimation of ongoing trends so as to remain current in price prediction. Constantinescu (2019) also found that using a time varying matrix of coefficients for different variables involved in the housing market increased forecasting accuracy above other methods he used. The use of time-series models such as these is fairly common in property value forecasting, although Graczyk et al. (2010) found in their study that any model using additive regression, (a nonparametric method used in time-series as well as other models), helped reduce prediction error. They also concluded that no one type of model reliably outdid all others every time. It can therefore simply be stated that time-series models are often preferred for property value forecasting.

##### Artificial Neural Networks
Another method that is popular amongst experts in machine learning is the use of neural networks. **Artificial neural networks** (ANN) are not prediction models like time-series models. Rather, they are data processing methods used in ML inspired by the process of animal brains. Neurons in the ANN interact with one another and adapt with the input of new data. The ANN then comes up with some designated output, which may be a value or even a prediction model, like the time-series. ANNs are used in property valuation because they can respond to ongoing data, and create robust models.

Su et al. (2021) found that neural networks are the most popular ML method used for property valuation. Thus, we can see that neural networks play a prevalent role in modern real estate valuation. They are the preferred ML computing system of the majority of researchers in the field, and will likely remain so for some time.

In this section I have highlighted the more popular methods used for property valuation. There are certainly other methods and models used. Spatial clustering models, sentiment analysis, and ensemble learning using genetic algorithms have also been used by experts. *However, the majority of studies I have researched testify to the usefulness and accuracy of time-series models and ANN data processing.* These methods will almost assuredly continue to be relevant in the future as the use of machine learning in real estate is further developed.


### Future of ML/AI in Real Estate

![future](/assets/images/blogimages/figs-10-06/future.jpeg)

Finally, we look towards the future of artificial intelligence in the real estate industry.

According to Souza et al. (2021), the real estate industry is in the early stages of embracing the innovations of artificial intelligence and ML. Souza et al. state that real estate organizations will need to make radical changes to their structure and work model in order to adapt to the new technology. They point to tech companies such as Apple, with its focus on developing hardware and software that caters to customer demands, as the business model that real estate groups should strive for. Rather than simply expanding geographically to find property options, real estate organizations should learn to use AI/ML to more accurately cater to customer needs. *This will help these organizations expand their portfolio of property types, rather than having to focus on a single element of the real estate sector.*

Su et al. (2021) point to fragmented data as being a common problem faced in the use of ML in real estate. Inaccurate or missing data is a problem in machine learning, because it teaches the algorithm poorly. Su et al. therefore propose **building information modeling** (BIM) as a solution to the gaps in data. BIM is a growing data sharing technology that allows different professionals in the field of construction to share data. Through it, engineers, architects, designers, operators and others can share information easily and thus provide more accurate data. Using this approach to data collection should allow ML algorithms to more accurately and effectively make property valuation predictions.

They suggest that these changes are a part of the real estate industry’s evolution towards the trend of Industry 4.0. **Industry 4.0** refers to the “fourth great industrial revolution” that many claim is happening today, moving industry towards automation and smart machines. Starr et al. (2021) and Jamil et. al. (2020) also insist on the real estate industry’s emergence into “Real Estate 4.0”, stating that *changes occurring in the field will push the industry to adapt with increasing speed, and allow for more environmentally friendly construction.*

While various sources focus on different changes to be made by real estate organizations, these changes are not necessarily mutually exclusive. A company may restructure its work model in order to respond to a customer’s needs while also incorporating BIM technology in order to improve the effectiveness of ML property valuation methods. While the exact nature of the changes to be seen in the real estate industry are uncertain, there is surely a need for the development of AI and ML processes.


### Conclusion
In conclusion, there are a number of uses for artificial intelligence and machine learning in the real estate industry. With the use of such technology being so new in the real estate industry, there is still much to be learned about which practices are most effective. Here are my biggest take-aways:

* A blend of macro and micro-variables need to be taken into account for property valuation.
* Time-series models and artificial neural networks are current favorites for modeling and ML methods.
* The future of the industry most likely includes automation, greater information networks, and greater efficiency.

The potential uses for machine learning in the real estate industry are numerous and revolutionary to the field. While there is still much to be learned, the progress made so far is encouraging, and has already sparked major change. Whatever the future of the real estate industry will be, it will doubtlessly include machine learning systems and techniques.
