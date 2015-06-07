## 07 Regression - Quiz 1

####1.Question 1 : Consider the data set given below

x <- c(0.18, -1.54, 0.42, 0.95)
And weights given by

w <- c(2, 1, 3, 1)
Give the value of μ that minimizes the least squares equation ∑ni=1wi(xi−μ)2


Z <- sum(x*w) / sum(w)
sqsum <- sum(w*(x-Z)^2)
c(Z, sqsum)


#####Ans : [1] 0.1471429 3.7165429


####2.Question 2 : Consider the following data set

x <- c(0.8, 0.47, 0.51, 0.73, 0.36, 0.58, 0.57, 0.85, 0.44, 0.42)
y <- c(1.39, 0.72, 1.55, 0.48, 1.19, -1.59, 1.23, -0.65, 1.49, 0.05)
Fit the regression through the origin and get the slope treating y as the outcome and x as the regressor. 
(Hint, do not center the data since we want regression through the origin, not through the means of the data.)

fit<- lm( y ~ x - 1 )
summary(fit)
fit$coefficient
#####Ans :  # 0.8263


####3.Question 3 : Do data(mtcars) from the datasets package and fit the regression model 
with mpg as the outcome and weight as the predictor. Give the slope coefficient.

data(mtcars)
head(mtcars)
fit <- lm(mpg ~ wt, mtcars)
summary(fit) 
fit$coefficient
#####Ans :  # -5.3445

####4.Question 4 :Consider data with an outcome (Y) and a predictor (X). 
The standard deviation of the predictor is one half that of the outcome. The correlation between the two variables is .5. 
What value would the slope coefficient for the regression model with Y as the outcome and X as the predictor?

sX <- 1/2
sY <- 1
cor <- .5
cor * sY / sX

#####Ans : [1] 1

####5.Question 5 : Students were given two hard tests and scores were normalized to have empirical mean 0 and variance 1. 
The correlation between the scores on the two tests was 0.4. 
What would be the expected score on Quiz 2 for a student who had a normalized score of 1.5 on Quiz 1?



