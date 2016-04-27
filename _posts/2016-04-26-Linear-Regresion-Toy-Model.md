---
layout: post
title: 
---

[Linear Regression](https://en.wikipedia.org/wiki/Linear_regression) is a simple tool for modelling the relationship 
between a scalar dependent variable and one or more explanatory variables, where this relationship is expressed as
a linear function of the explanatory variables. 
If the [model assumptions](http://www.statisticssolutions.com/assumptions-of-multiple-linear-regression/)
are met, it can predict an increase or decrease in the dependent variable based on the changes in the explanatory variables; e.g., for each $1 that I invest into the production budget of my future movie, how much will I earn on the movie's total gross? 
Answering a question like this is not an easy task. Naturally, we would ask the following questions: (i) What is the prediction power of our model? 
(ii) Can we trust the model's linear coefficient(s)?
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
R-squared=0.4.
[The interpretation](http://blog.minitab.com/blog/adventures-in-statistics/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit) 
one might use is that our model explains about 40% of the variation in our data, leaving the rest 60% unexplained.
This might seem a little worrisome, especially if we want to be sure how our $1 investment turns out.
However, predicting a human-related behavior is a tough job in general. In the absence of any other information, we conclude that this prediction is as good as we can get.

But wait, what about all the movie information on actors or producers? Afterall, I would love to see a movie with my favorite superhero (and I'm not listening to anyone's objections, sorry, no reviews yet). What about producer? Director? Movie quality should be related to the quality of those who produce it! 
It turns out that even by scoring the producers and actors, and including their qualities into the model, our predictions don't improve significantly. The R-squared is about 0.45. 
On the other hand, as soon as we allow to account for information that is more predictive in its nature, such as
count of theaters (typically an expected high-performance movie will be released in more theaters) or 
[movie rating](http://www.metacritic.com/),
the predictive power increases.

Let's move away from the prediction power for a moment, and let's focus our attention on the model itself.
The significant coefficients, the linear coefficients for ``production budget``, ``actors score`` and ``producer score``, still represent the mean change in the response for one unit of change in the predictor while holding other predictors in the model constant. This said, our estimator is still the best linear unbiased estimator (for the set of chosen features),
and this type of information is valuable.
We find that our best model's linear coeficients are about 0.8, 0.2 and 0.1 for the 
``production budget``, ``producer score`` and ``actor score``, resp. 
Loosely speaking, the mean change in the ``domestic total gross`` per $1 investment in the ``production budget`` is 
about $0.8, per $1 of the producer score (higher score means producing more revenue for past movies) 
is about $0.2, and per $1 of the actors score (looking only at the best performing actor per movie) 
is about $0.1.
To recap: 
[the linear coefficients still estimate the trend while R-squared represents the scatter around the regression line](http://blog.minitab.com/blog/adventures-in-statistics/how-to-interpret-a-regression-model-with-low-r-squared-and-low-p-values).
It's not clear a priori how to improve the prediction power, given the nature of movies data,
without accounting for close-to release or post-release features, like the number of opening theaters or pre-sale tickets, or movie reviews.

[Source code](https://github.com/lpalova/Box-Office-Mojo---Analysis/tree/master/source-files)    
[Presentation](https://docs.google.com/presentation/d/1GLkTnWRyj4v8bTs55frT6jBn3Vv_8z6fsjY_XuADVbY/edit#slide=id.g10f7417bd3_0_19)















