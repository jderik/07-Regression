# 07 Regression - Quiz 4

####Q01 : Consider the space shuttle data ?shuttle in the MASS library. 
Consider modeling the use of the autolander as the outcome (variable name use). 
Fit a logistic regression model with autolander (variable auto) use (labeled as "auto" 1) versus not (0) 
as predicted by wind sign (variable wind). Give the estimated odds ratio for autolander use comparing head winds,
labeled as "head" in the variable headwind (numerator) to tail winds (denominator).


#####Ans : 


####Q02 : Consider the previous problem. Give the estimated odds ratio for autolander 
use comparing head winds (numerator) to tail winds (denominator) adjusting for wind strength from the variable magn.


#####Ans : 


####Q03 : If you fit a logistic regression model to a binary variable, for example use of the autolander, 
then fit a logistic regression model for one minus the outcome (not using the autolander) what happens to the coefficients?

#####Ans : The coefficients reverse their signs.

####Q04 : Consider the insect spray data InsectSprays. Fit a Poisson model using spray as a factor level. 
Report the estimated relative rate comapring spray A (numerator) to spray B (denominator).


#####Ans :

####Q05 : Consider a Poisson glm with an offset, t. So, for example, a model of the form glm(count ~ x + offset(t), 
family = poisson) where x is a factor variable comparing a treatment (1) to a control (0) and t is the natural log of a monitoring 
time. What is impact of the coefficient for x if we fit the model glm(count ~ x + offset(t2), family = poisson) 
where t2 <- log(10) + t? In other words, what happens to the coefficients if we change the units of the offset variable. 
(Note, adding log(10) on the log scale is multiplying by 10 on the original scale.)


#####Ans :

####Q06 : Consider the data

x <- -5:5

y <- c(5.12, 3.93, 2.67, 1.87, 0.52, 0.08, 0.93, 2.05, 2.54, 3.87, 4.97)

Using a knot point at 0, fit a linear model that looks like a hockey stick with two lines meeting at x=0. 
Include an intercept term, x and the knot point term. What is the estimated slope of the line after 0?


#####Ans :



