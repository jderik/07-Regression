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




#####Ans : 










