---
layout: post
title: 
---

Predicting damages or injures caused by a severe event is a key part of [risk modeling software](https://en.wikipedia.org/wiki/Catastrophe_modeling).
The [software](https://en.wikipedia.org/wiki/HAZUS) 
[calculates](http://www.oasislmf.org/) [(financial) impacts of catastrophes before they occur](http://www.air-worldwide.com/Models/About-Catastrophe-Modeling/).
Typically, the input consists of an event generation and exposure data. 
Damage is then estimated for each affected exposure.
Insured loss is evaluated based on policy conditions and the damage estimation.

In general, [quantitative risk assessment](https://en.wikipedia.org/wiki/Risk_assessment)
requires calculations of two components of risk: 
the magnitude of the potential loss, and the probability that the loss will occur.
Here I focus my attention on the former and analyze 
[NOAA's storm events database](http://www.ncdc.noaa.gov/stormevents/ftp.jsp).
The database consists of individual storm observations described by features, including event type, timestamp (beginning and
end of a storm event), latitude and longitude, state, number of injuries and deaths, property and crops damage,
range and azimuth (if applicable) and others.
The data comes from the National Weather Service. [The National Weather service receives their information from a variety of sources: county, local, state and federal law enforcement and emergency management officials, skywarn spotters, NWS damage surveys, newspaper clipping services, the insurance industry and the general public, among others.](http://www.ncdc.noaa.gov/stormevents/faq.jsp)

Event types vary from wind (such as 
strong wind, thunderstorm wind) and storm (including blizzard, hail, rain), 
tornadoes (including [waterspout](https://en.wikipedia.org/wiki/Waterspout)),
hurricanes (including tropical storms and depressions), floods (and landslides), to events such as fires (heat), 
tsunami (tide) or winter weather (cold, avalanche, snow).
Here I categorize all storm events into the eight categories, and apply an algorithm
to test accuracy of the chosen categorization scheme.
I find an average 83% accuracy with a [random forest classifier](http://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html).
 There are overlaps among the different categories (such as storm and wind, or 
tsunami and flood), however, 
a categorization like this condenses vast amount of different labels
 into a more organized labeling scheme.

Let's explore the past twenty years of the dataset. The following plot shows average annual number of events of a given event type across the US (left), as well the average annual property damage (inflation adjusted) 
(center and right) as a function of the year. 
<!-- ![Count_property_vs_year](/images/Storms/stormcount_propertyyear.png =250x)-->
<img src="/images/Storms/stormcount_propertyyear.png" width="1000" height="180" />   
Notice a few peaks: 
[2005 Atlantic Hurricane Season](https://en.wikipedia.org/wiki/2005_Atlantic_hurricane_season),
[2008 several](http://www.weather.gov/lot/2011blizzard) [storm](http://www.spc.noaa.gov/exper/archive/event.php?date=20110427) 
[and wind events](http://www.srh.noaa.gov/oun/?n=events-20110614),
[2012 warmest year in US](http://www.climatecentral.org/news/noaa-2012-was-warmest-and-second-most-extreme-year-on-record-15436).

Although the number of storm events stays relatively unchanged, there are much wider variations in average property damage
(similarly crops damage, or number of injuries/deaths) as a function of time. 
Catastrophic events, such as [2005 Katrina](https://en.wikipedia.org/wiki/Hurricane_Katrina)
or [2008 Hurricane season](https://en.wikipedia.org/wiki/2008_Atlantic_hurricane_season),
lead to large insured and uninsured property loss and number of injuries/deaths
compared to other storm events even within the same event type.

Here I predict the amount of property damage based on a few storm-related features,
including (beginning) latitude,
longitude of the event, event type and season, among others.
The most difficult task is to separate low property damage events (say, zero property damage events) 
from high property damage events (say, nonzero property damage events).
I find that the two groups are present with an almost equal weight in the NOAA's storm event dataset.
Again, by employing a random forest algorithm with an adjusted probability threshold value I classify the nonzero damage events with a high precision rate. Furthermore, a continuous regression on the labeled nonzero propery damage events leads to the Rsquared score of about 0.22.
<!-- Learning curve-->
Notice that a similar analysis on the number of injuries or deaths is fundamentaly more difficult to accomplish,
mostly because of very unbalanced data; 
the majority of reported events results in no injuries/deaths, with a few outsiders representing catastrophic events.

Lastly, I created a 
[simple predictor app](http://ec2-54-173-233-196.compute-1.amazonaws.com/map_predictor/)
that predicts the amount of damage to be the median annual damage per state per event type 
based on events between years 1996 and 2012.   
<img src="/images/Storms/simple_predictor_app.png" width="450" height="250" />

[Slide deck](https://docs.google.com/presentation/d/1uSIFORCHXLeSqNanSpRr9VIMAkclPoNNYD00efeqypg/edit#slide=id.g10f7417bd3_0_19) and [source code](https://github.com/lpalova/Storm-Events-Classification).














