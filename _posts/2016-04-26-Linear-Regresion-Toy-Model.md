---
layout: post
title: 
---

*Work in progress*

[Linear Regression](https://en.wikipedia.org/wiki/Linear_regression) is a simple tool for modelling the relationship 
between a scalar dependent variable and one or more explanatory variables, where this relationship is expressed as
a linear function of the explanatory variables. 
If the [model assumptions](http://www.statisticssolutions.com/assumptions-of-multiple-linear-regression/)
are met, it can predict an increase or decrease in the dependent variable based on the changes in the explanatory variables; e.g., for each $1 that I invest into the production budget of my future movie, how much will I earn on the movie's total gross? 
Answering a question like this is not an easy task. Naturally, we would ask the following questions: (i) What is the prediction power of our model? 
(ii) Can we trust the model's linear coefficients?
(iii) What features do we include/omit in our analysis? Could we perform any better, and if so, how does the final model look like?

[Box Office Mojo](http://www.boxofficemojo.com/)
is a great resource for movie industry data. The website is neatly organized, allowing one to extract different features about each movie, such as domestic total gross, production budget, release date, widest release theaters count, genre, runtime, rating of the movie, as well as information on the distributor, director, producer(s), actor(s), screenwriter(s), composer(s), cinematographer(s), etc. 
Because our question of interest is ``How much will I earn on a movie's (domestic) total gross if I invest $1 in its production budget?``, our dependent variable is set to be the domestic total gross and our explanatory variable is
production budget.
Let's see how we perform.

Box Office Mojo was founded in 1999. When we look at their number of records per year, we soon realize that there is a jump in the number of records around the year the company was founded. For our purposes, we decide to use only records with a release date of 1999 or a later date. Notice that the number of movies released varies by month. 
October-December have the most records, January-February have the least records.
![Box Office Mojo Records](/images/BoxOfficeMojo/actorproducer_count_vs_year+month.png)

We perform [ordinary least squares](https://en.wikipedia.org/wiki/Ordinary_least_squares) fit
and find that domestic total gross is estimated based on the production budget with a prediction power measured by 
R<sup>2</sup>=0.4.
[The interpretation](http://blog.minitab.com/blog/adventures-in-statistics/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit) 
one might use is that our model explains about 40% of the variation in our data, leaving the rest 60% unexplained.
This might seem a little worrisome, especially if we want to be sure how our $1 investment turns out.
However, predicting a human-related behavior is a tough job in general. In the absence of any other information, we conclude that this prediction is as good as we can get.

But wait, what about all the movie information on actors or producers? Afterall, I would love to see a movie with my favorite superhero (and I'm not listening to anyone's objections, sorry, no reviews yet). What about producer? Director? Movie quality should be related to the quality of those who produce it! 
It turns out that even by scoring the producers and actors, and including their qualities into our model, our predictions don't improve significantly. We can get up to R<sup>2</sup>=0.45. Weird..












