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

corr <- 0.4
quiz1 <- 1.5
quiz2 <- quiz1*corr*1 + 0
quiz2

#####Ans : [1] 0.6

####6.Question 6 : Consider the data given by the following
x <- c(8.58, 10.46, 9.01, 9.64, 8.86)
What is the value of the first measurement if x were normalized (to have mean 0 and variance 1)?
***********
x <- c(8.58, 10.46, 9.01, 9.64, 8.86)
(x[1] - mean(x))/sd(x)

#####Ans : [1] -0.9718658

####7.Question 7 : Consider the following data set (used above as well). What is the intercept for fitting the model with x as the predictor and y as the outcome?

x <- c(0.8, 0.47, 0.51, 0.73, 0.36, 0.58, 0.57, 0.85, 0.44, 0.42)
y <- c(1.39, 0.72, 1.55, 0.48, 1.19, -1.59, 1.23, -0.65, 1.49, 0.05)
***************************
fit <- lm(y ~ x)
summary(fit)
fit$coefficient

#####Ans : 1.567

####8.Question 8 : You know that both the predictor and response have mean 0. What can be said about the intercept when you fit a linear regression?

#####Ans : 0

####9.Question 9 : Consider the data given by

x <- c(0.8, 0.47, 0.51, 0.73, 0.36, 0.58, 0.57, 0.85, 0.44, 0.42)
What value minimizes the sum of the squared distances between these points and itself?

mean(x)

#####Ans : [1] 0.573

####10.Question 10 : Let the slope having fit Y as the outcome and X as the predictor be denoted as β1. Let the slope from fitting X as the outcome and Y as the predictor be denoted as γ1. Suppose that you divide β1 by γ1; in other words consider β1/γ1. What is this ratio always equal to?

b1 <- cor(x,y)*sd(y)/sd(x)  ##slope having fit Y as the outcome and X as the predictor

a1 <- cor(x,y)*sd(x)/sd(y)  ##slope from fitting X as the outcome and Y as the predictor

b1/a1

This is equal to 

#####Ans : var(y)/var(x)
