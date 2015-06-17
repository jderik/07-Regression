# 07 Regression - Quiz 3

####Q01 : Consider the mtcars data set. Fit a model with mpg as the outcome that includes number of cylinders as a factor variable and weight as confounder. Give the adjusted estimate for the expected change in mpg comparing 8 cylinders to 4.

data(mtcars)
fit <- lm(mpg ~ factor(cyl) + wt, data = mtcars)
summary(fit)

#####Ans : factor(cyl)8  -6.0709

####Q02 : Consider the mtcars data set. Fit a model with mpg as the outcome that includes number of cylinders as a factor variable and weight as a possible confounding variable. Compare the effect of 8 versus 4 cylinders on mpg for the adjusted and unadjusted by weight models. Here, adjusted means including the weight variable as a term in the regression model and unadjusted means the model without weight included. What can be said about the effect comparing 8 and 4 cylinders after looking at models with and without weight included?.

fit_withweight<-lm(mpg ~ factor(cyl) + wt, mtcars)
summary(fit_withweight)$coef

                          Estimate Std. Error   t value     Pr(>|t|)
            (Intercept)  33.990794  1.8877934 18.005569 6.257246e-17
            factor(cyl)6 -4.255582  1.3860728 -3.070244 4.717834e-03
            factor(cyl)8 -6.070860  1.6522878 -3.674214 9.991893e-04
          wt             -3.205613  0.7538957 -4.252065 2.130435e-04

fit_noweight <- lm(mpg ~ factor(cyl), mtcars)
summary(fit_noweight)$coef

                             Estimate Std. Error   t value     Pr(>|t|)
              (Intercept)   26.663636  0.9718008 27.437347 2.688358e-22
              factor(cyl)6  -6.920779  1.5583482 -4.441099 1.194696e-04
              factor(cyl)8 -11.563636  1.2986235 -8.904534 8.568209e-10

#####Ans : Holding weight constant, cylinder appears to have less of an impact on mpg than if weight is disregarded.

####Q03 : Consider the mtcars data set. Fit a model with mpg as the outcome that considers number of cylinders as a factor variable and weight as confounder. Now fit a second model with mpg as the outcome model that considers the interaction between number of cylinders (as a factor variable) and weight. Give the P-value for the likelihood ratio test comparing the two models and suggest a model using 0.05 as a type I error rate significance benchmark.

fit1 <- lm(mpg ~ factor(cyl) + wt, data = mtcars)
fit2 <- lm(mpg ~ factor(cyl) + wt + interaction(cyl, wt), data = mtcars)

###### Use ANOVA ; A NULL Hypothesis indicates both models are the same.
checker <- anova(fit1, fit2)
checker$Pr

###### NA 0.08358536

#####Ans : The P-value is larger than 0.05. So, according to our criterion, we would fail to reject, which suggests that the interaction terms may not be necessary.

####Q04 : Consider the mtcars data set. Fit a model with mpg as the outcome that includes number of cylinders as a factor variable and weight inlcuded in the model as
lm(mpg ~ I(wt * 0.5) + factor(cyl), data = mtcars)
How is the wt coefficient interpretted?

fit4<-lm(mpg ~ I(wt * 0.5) + factor(cyl), data = mtcars)
summary(fit4)

#####Ans : The estimated expected change in MPG per one ton increase in weight for a specific number of cylinders (4, 6, 8).

####Q05 : Consider the following data set
x <- c(0.586, 0.166, -0.042, -0.614, 11.72)
y <- c(0.549, -0.026, -0.127, -0.751, 1.344)
Give the hat diagonal for the most influential point

fit5 <- lm(y ~ x)

*Two alternatives
###### 1
hatvalues(fit5)  #

            1         2         3         4         5 
        0.2286650 0.2438146 0.2525027 0.2804443 0.9945734 

###### ITEM 5 -> 0.9945734

###### 2

lm.influence(fit5)

####### ITEM hat[5]5 -> 0.9945734

#####Ans : 0.9945734 


####Q06 : Consider the following data set
x <- c(0.586, 0.166, -0.042, -0.614, 11.72)
y <- c(0.549, -0.026, -0.127, -0.751, 1.344)
Give the slope dfbeta for the point with the highest hat value.


#####Ans : 


