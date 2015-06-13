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


#####Ans :# lwr: 18.99098

####4.Question 4 : Refer to the previous question. Read the help file for mtcars. What is the weight coefficient interpreted as?

#####Ans : The estimated expected change in mpg per 1,000 lb increase in weight.

####5.Question 5 : Consider again the mtcars data set and a linear regression model with mpg as predicted by weight (1,000 lbs). A new car is coming weighing 3000 pounds. Construct a 95% prediction interval for its mpg. What is the upper endpoint?

data(mtcars)

predict(fit, data.frame(x=mean(3000/1000)), interval="prediction")

#####Ans : upr: 27.57355

####6.Question 6 : Consider again the mtcars data set and a linear regression model with mpg as predicted by weight (in 1,000 lbs). A “short” ton is defined as 2,000 lbs. Construct a 95% confidence interval for the expected change in mpg per 1 short ton increase in weight. Give the lower endpoint.

data(mtcars)

x2<-mtcars$wt/2
y2<-mtcars$mpg

fit2<-lm(y2~x2)
SUMM<-summary(fit2)$coefficients

mean1<-SUMM[2,1]    

std_err<-SUMM[2,2] 

deg_freedom<-fit2$df


*this is just a plot for depiction
par(mfrow=c(1,2))

plot(x,y)

abline(fit,col="blue")

plot(x2,y2)

abline(fit2,col="red")

mean1 + c(-1,1) * qt(0.975,df=deg_freedom) * std_err   #Ans is -12.97262
#####Ans : -12.97262


####7.Question 7 :If my X from a linear regression is measured in centimeters and I convert it to meters what would happen to the slope coefficient?

This can be tested with the above formulas

x3<-mtcars$wt/100
y3<-mtcars$mpg
fit3<-lm(y3~x3)

The coefficient "estimate" (slope) is -5.3445 for summary(fit).It is -534.447 for summary(fit3).

#####Ans :It would get multiplied by 100.

####8.Question 8 :I have an outcome, Y, and a predictor, X and fit a linear regression model with Y=β0+β1X+ϵ to obtain β^0 and β^1. What would be the consequence to the subsequent slope and intercept if I were to refit the model with a new regressor, X+c for some constant, c?


#####Ans :The new intercept would be β^0−cβ^1

####9.Question 9 :Refer back to the mtcars data set with mpg as an outcome and weight (wt) as the predictor. About what is the ratio of the the sum of the squared errors, ∑ni=1(Yi−Y^i)2 when comparing a model with just an intercept (denominator) to the model with the intercept and slope (numerator)?


#####Ans : 
#### DONT KNOW WHAT THIS QUESTION MEANS

####10.Question 10 : Do the residuals always have to sum to 0 in linear regression?
#####Ans :  If an intercept is included, then they will sum to 0.
