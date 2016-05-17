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
Physical damage is then estimated for each affected exposure.
Insured loss is evaluated based on policy conditions and the damage estimation.

In general, [quantitative risk assessment](https://en.wikipedia.org/wiki/Risk_assessment)
requires calculations of two components of risk: 
the magnitude of the potential loss, and the probability that the loss will occur.
Here we focus our attention on the former and analyze 
[NOAA's storm events database](http://www.ncdc.noaa.gov/stormevents/ftp.jsp).
The database consists of individual storm observations described by features including Event Type, Timestamp (beginning and
end of a storm event), Latitude and Longitude, State, Number of Injuries and Deaths, Property and Crops Damage,
Range and Azimuth (if applicable) and others.
The data comes from the National Weather Service. [The National Weather service receives their information from a variety of sources, which include but are not limited to: county, state and federal emergency management officials, local law enforcement officials, skywarn spotters, NWS damage surveys, newspaper clipping services, the insurance industry and the general public, among others.](http://www.ncdc.noaa.gov/stormevents/faq.jsp).

Storm categories are characterized by EVENT_TYPE feature in the NOAA datasets. 
A closer look at the datasets reveals that many different EVENT_TYPEs are used, including descriptions such as .. vs. ...
In order to categorize storms, we decide to bin the different events into eight 
categories: Storm, Wind, ...
By 



Note:

NOAA has publicly available [datasets]()
on storm events.
The data is collected from various sources, including ...

![86th street exits](/images/MTA/exits/heatmap_72 ST, 123.png)
