---
layout: post
title: 
---

*Work in progress*

## Storm Events Classification

<!-- App simple predictor -->

Predicting damages or injures caused by a severe event is a key part of [risk modeling software](https://en.wikipedia.org/wiki/Catastrophe_modeling).
The [software](https://en.wikipedia.org/wiki/HAZUS) 
[calculates](http://www.oasislmf.org/) [(financial) impacts of catastrophes before they occur](http://www.air-worldwide.com/Models/About-Catastrophe-Modeling/).
Typically, the input consists of an event generation and exposure data. 
Damage is then estimated for each affected exposure.
Insured loss is evaluated based on policy conditions and the damage estimation.

In general, [quantitative risk assessment](https://en.wikipedia.org/wiki/Risk_assessment)
requires calculations of two components of risk: 
the magnitude of the potential loss, and the probability that the loss will occur.
Here we focus our attention on the former and analyze 
[NOAA's storm events database](http://www.ncdc.noaa.gov/stormevents/ftp.jsp).
The database consists of individual storm observations described by features including Event Type, Timestamp (beginning and
end of a storm event), Latitude and Longitude, State, Number of Injuries and Deaths, Property and Crops Damage,
Range and Azimuth (if applicable) and others.
The data comes from the National Weather Service. [The National Weather service receives their information from a variety of sources: county, local, state and federal law enforcement and emergency management officials, skywarn spotters, NWS damage surveys, newspaper clipping services, the insurance industry and the general public, among others.](http://www.ncdc.noaa.gov/stormevents/faq.jsp)

First, we look at the event type. Event types vary from wind (such as 
strong wind, thunderstorm wind) and storm (including blizzard, hail, rain), 
tornadoes (including waterspout), hurricanes (including tropical storms and depressions), floods (and landslides), to events such as fires (heat), 
tsunami (waves) or winter weather (cold, avalanche, snow).
We categorize all storm events into the eight categories, and apply an algorithm
to test accuracy of our chosen categorization scheme.
We find an average 83% accuracy with a [random forest classifier](http://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html).
We expect overlaps among the different categories (such as storm and wind, or 
tsunami and flood), however, 
a categorization like this condenses vast amount of different labels
 into more organized labels.

Let's explore the past twenty years of the dataset. 
In the following, we plot the average number of events of a given type across the US
as a function of year.
![Count_vs_year](/images/Storms/stormcountyear.png)
We notice a few peaks: 2005 is a well known [Atlantic Hurricane Season](),
....

We also plot the average property damage (adjusted for inflation) 
per event type across the US as a function of year.
![Property_vs_year](/images/Storms/stormpropertyyear.png)
Although the number of storm events stays relatively unchanged, 
we see much wider varriations 


Storm categories are characterized by EVENT_TYPE feature in the NOAA datasets. 
A closer look at the datasets reveals that many different EVENT_TYPEs are used, including descriptions such as .. vs. ...
In order to categorize storms, we decide to bin the different events into eight 
categories: Storm, Wind, ...
By 




