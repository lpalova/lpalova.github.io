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
tsunami (tide) or winter weather (cold, avalanche, snow).
We categorize all storm events into the eight categories, and apply an algorithm
to test accuracy of our chosen categorization scheme.
We find an average 83% accuracy with a [random forest classifier](http://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html).
We expect overlaps among the different categories (such as storm and wind, or 
tsunami and flood), however, 
a categorization like this condenses vast amount of different labels
 into a more organized labeling scheme.

Let's explore the past twenty years of the dataset. The following plot shows the average number of events per year of a given type across the US (left), as well the average property damage (inflation adjusted) per year 
(center and right) as a function of year. 
![Count_property_vs_year](/images/Storms/stormcount_propertyyear.png)
We notice a few peaks: 
[2005 Atlantic Hurricane Season](https://en.wikipedia.org/wiki/2005_Atlantic_hurricane_season),
[2008 several](http://www.weather.gov/lot/2011blizzard) [storm](http://www.spc.noaa.gov/exper/archive/event.php?date=20110427) 
[and wind events](http://www.srh.noaa.gov/oun/?n=events-20110614),
[2012 warmest year in US](http://www.climatecentral.org/news/noaa-2012-was-warmest-and-second-most-extreme-year-on-record-15436).

Although the number of storm events stays relatively unchanged, we see a much wider varriations in average property damage
(similarly crops damage, or number of injuries/deaths). 
Catastrophic events such as [2005 Katrina](https://en.wikipedia.org/wiki/Hurricane_Katrina)
or [2008 Hurricane season](https://en.wikipedia.org/wiki/2008_Atlantic_hurricane_season)
lead to large insured and uninsured property loss and number of injuries/deaths
compared to other storm events (even within the same type).

Here we try to predict the amount of property damage based on several storm-related features, 
including (beginning) latitude,
longitude of the event, event type, season, among others.
The most difficult task is to separate low property damage events (say, zero property damage events) 
from high property damage events (say, nonzero property damage events).
Again, by employing a random forest algorithm with an adjusted probability threshold value we are able to 
classify the nonzero damage events with a high precision rate. Furthermore, a continuous regression on the labeled nonzero damage events leads to Rsquared of about 0.22.







