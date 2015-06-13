# 07 Regression - Quiz 2

####1.Question 1 : Consider the following data with x as the predictor and y as as the outcome.
x <- c(0.61, 0.93, 0.83, 0.35, 0.54, 0.16, 0.91, 0.62, 0.62)
y <- c(0.67, 0.84, 0.6, 0.18, 0.85, 0.47, 1.1, 0.65, 0.36)
Give a P-value for the two sided hypothesis test of whether β1 from a linear regression model is 0 or not.

fit <- lm(y~x)
summary(fit) ## THis gives p value


#####Ans :  p-value: 0.05296

####2.Question 2 : Consider the previous problem, give the estimate of the residual standard deviation.

The summaryabove gives the following 

#####Ans :  Residual standard error: 0.223 on 7 degrees of freedom

####3.Question 3 :In the mtcars data set, fit a linear regression model of weight (predictor) on mpg (outcome). 
Get a 95% confidence interval for the expected mpg at the average weight. What is the lower endpoint?

data(mtcars)

summary(mtcars)

x<-mtcars$wt
y<-mtcars$mpg

fit<-lm(y ~ x)
predict(fit,data.frame(x=mean(x)), interval="confidence")
# lwr: 0.4597867

#####Ans :# lwr: 18.99098



















