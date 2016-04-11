---
layout: post
title: 
---

*Work in progress*

# MTA Turnstile Data

MTA has publicly available [datasets](http://web.mta.info/developers/turnstile.html) on the activity of their turnstiles. The data is recorded weekly. Each observation consists of a timestamp, a unique identifier of a turnstile device (such as a station name, line name, area, and subunit channel position), the cumulative entry and exit register values for a device and a few other features.

Through analysis of the collected data in a certain time interval, we are identifying the most frequent train stations and the busiest times on a given day of an average week (Monday, Tuesday, .. Sunday). As expected, the commuter hub stations such as 42St - Grand Central, 34St - Herald Square, 42St - Times Square, or 34St - Penn Station show most turnstile activity. Our goal here is to find other frequent commuter stations that might not be easily identified based on simple transit patterns or other common sense assumptions.

![Top 20 Stations by total entries](images/MTA/entries/top_20_entries_lines_stations.png)
![Top 20 Stations by total exits](images/MTA/exits/top_20_exits_lines_stations.png)

The two figures above show the top 20 stations in terms of most entries and exits. Notice that a station is uniquely identified by station name and line name. For example, 86th street on Upper East Side is ''86 ST, 456''. Similarly, Penn Station, New York is characterized by three turnstile groups: ''34ST-PENN STA, ACE'', ''34ST-PENN STA, 123ACE'', and ''34ST-PENN STA, 123''. The ambiguity of 34ST-Penn Station notation is unfortunate here. However, most stations are identified uniquely by using the station and line name rule. A closer analysis, where we count all subway lines per station, shows that ''34ST-PENN STA'' is the number one hub for commuters, followed by ''42ST-GRD CNTRL'' (Grand Central Station) and ''34ST-HERALD SQ''.



If we exclude ... , ... , .. and ... from our analysis, and plot the most frequent MTA stations again, we notice that ... is number 1 station, followed by ... and ... .
The entries and exits figures below show ...

Fig. entries, Fig. exits -- excluding obvious stops such as Penn, 42nd, Grand Central.


In order to get a feeling for how the turnstile traffic looks for an average week, we created heatmaps that shows the number of entries/exits as a function of day and a 4-hour time block. For example, a 04:00:00 block shows the number of entries/exits in the midnight (00:00:00) to 4am time window. Similarly, a 20:00:00 block shows the number of entries/exits in the 4pm (16:00:00) to 8pm (20:00:00) time window, that is, it generally captures the afternoon peak traffic hours.

The figures below show traffic entries/exit patterns for Penn Station, .. . We compare them to two other stations: ... and ... .
Describe.

Our preliminary analysis of the data shows rich patterns in the MTA commute, and allows us to draw conclusions ..
App next steps.






<!--![_config.yml]({{ site.baseurl }}/images/config.png)-->

<!--The easiest way to make your first post is to edit this one. Go into /_posts/ and update the Hello World markdown file. For more instructions head over to the [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.-->
