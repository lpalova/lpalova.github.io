---
layout: post
title: 
---

[Linear Regression](https://en.wikipedia.org/wiki/Linear_regression) is a simple tool for modelling the relationship 
between a scalar dependent variable and one or more explanatory variables, where this relationship is expressed as
a linear function of the explanatory variables. 
If the [model assumptions](http://www.statisticssolutions.com/assumptions-of-multiple-linear-regression/)
are met, it can predict an increase or decrease in the dependent variable based on the changes in the explanatory variables; e.g., for each $1 that I invest into the production budget of my future movie, how much will I earn on the movie's total gross? 
Answering a question like this is not an easy task. Naturally, we would ask: (i) What is the prediction power of our model? 
(ii) Can we trust the model's linear coefficient(s)?
(iii) What features do we include/omit in our analysis? Could we perform any better, and if so, how does the final model look like?

[Box Office Mojo](http://www.boxofficemojo.com/)
is a great resource for movie industry data. The website is neatly organized, allowing one to extract different features about movies, such as domestic total gross, production budget, release date, widest release theaters count, genre, runtime, rating of the movie, as well as information on the distributor, director, producer(s), actor(s), screenwriter(s), composer(s), cinematographer(s), etc. 
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
However, predicting a human-related behavior is a tough job. In the absence of any other information, we conclude that this prediction is as good as we can get.

Let's move one step forward and include more features into our simple model. Can we think about the movie quality being related to the players: actors, producers? 
It turns out that by scoring producers and actors based on their former movies, using a simple metric that favors 
former high gross revenues, we are able to improve our model's performance but not greatly. The R-squared increases to 0.45.
[The early predictions of movie success](http://link.springer.com/chapter/10.1007%2F978-3-319-16268-3_41) 
include features such as *who* plays or contributes to the movie, *what* is the movie about and *when* it will be released. Our simple linear regression toy model captures 
[the main trend](http://blog.minitab.com/blog/adventures-in-statistics/how-to-interpret-a-regression-model-with-low-r-squared-and-low-p-values)
of the
[relations](http://blog.minitab.com/blog/adventures-in-statistics/how-to-interpret-regression-analysis-results-p-values-and-coefficients)
of these predictors to the movie gross (higher rated producers/actors, production budget increase the movie's gross on average).
However, more sophisticated models are needed to
[design a decision support system with practical utilities](http://arxiv.org/pdf/1506.05382.pdf).

As an aside, we mention that as soon as we deviate from the early prediction nature of our algorithm and include features that are known closer to the movie release date or post-release features, like the number of opening theaters
(typically an expected high-performance movie will have a wider release),
or [movie rating](http://www.metacritic.com/),
the predictive power increases.

[Source code - simple linear regression](https://github.com/lpalova/Box-Office-Mojo---Analysis/tree/master/source-files).   
[Slide deck](https://docs.google.com/presentation/d/1GLkTnWRyj4v8bTs55frT6jBn3Vv_8z6fsjY_XuADVbY/edit#slide=id.g10f7417bd3_0_19) on some notions about the Box Office Mojo movie data and intro to linear least squares.













