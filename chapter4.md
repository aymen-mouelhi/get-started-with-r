---
title: 'Regression Analysis'
description: 'Regression Analysis'
---

## Introduction

```yaml
type: NormalExercise
key: 59e698bbd4
lang: r
xp: 100
skills: 1
```

Regression analysis is a workhorse of the inferential statistics. It allows us to take first steps into modelling certain variables by using information available to us.

This is also a method of supervised machine learning, which means that it is necessary to have some information about the variable that we are actually modelling.

In a nutshel, regression analysis will help us predict a value of one variable by having information about other variables.

For example, we could use somebody’s grade in statistics course to predict his/her grade in a different course.

In this section we will be using mtcars dataset that we have been also using before.

Refresh your memory about the dataset by completing tasks on your right.

`@instructions`
- use function head() to display first few observations of the dataset.
- use function summary() to display summary characteristics of a given variable.
- do not forget to refer to your dataset in the name of the variable you are interested in.

`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
#load data
a=data.frame(mtcars)

#[DIY] visualize first few observations of the dataset


#[DIY] summarize variable "mpg"


#[DIY] summarize variable "cyl"
```

`@solution`
```{r}
#load data
a=data.frame(mtcars)

#[DIY] visualize first few observations of the dataset
head(a)

#[DIY] summarize variable "mpg"
summary(a$mpg)

#[DIY] summarize variable "cyl"
summary(a$cyl)
```

`@sct`
```{r}
success_msg("Nice job!")
```

---

## Linear Regression

```yaml
type: NormalExercise
key: 3113397a2a
lang: r
xp: 100
skills: 1
```

The simplest sort of the regression is a linear Ordinary Least Squares (OLS) regression. This is the method that tries to fit the straight line into your two-dimensional scatter plot data such that this line (predicted values) has the lowest possible squared errors compared to actual values (which we observe in our data — hence, supervised learning).

In its simplest form we will try to predict the values of one variable (in this case mpg) by looking at the values of another variable (in this case cyl).

Linear regression can be run by using function lm(). Of course, in R you can create an object which would hold your “regression object” that can be visualised at later point.

The left-hand-side variable is our dependent variable. While the right-hand-side variable is referred to as an independent variable.

The output specifies coefficients for the fitted line (intercept, and the slope of the line) as well as many other feature of the model. The most important of these values are:
- R-squared, that takes values between 0 and 1 and measures the fit of the model. Or, in other word, how much variation in our dependent variable can be explained by the variation in independent variable. Or, how accurately we can predict the value of the left-hand-side variable by looking at the value of the right-hand-side variable.
- p-value (or in this output “Pr(>|t|)”) of each of the coefficient, which represents the p-value of the test with the null hypothesis of the actual coefficient being zero (with an alternative hypothesis of it not being zero). Recall that p-value measures the size of the error that we will be making if we rejected our null hypothesis in favour of the alternative. Therefore, low p-value (less than 0.05) means that the likelihood of making an error if we claim that the slope of the line is different from zero (in other words, that our independent variable can predict our independent variable) is very small. Notice that the number 6.11e-10 is extremely small: it basically is 6.11 divided by 1 followed by 10 zeros (so, basically 0.000000000611).

We can generate the scatter plot of our data in R. We can, afterwards, fit in the regression line to better visualise the relationship.

`@instructions`
- Notice that you do not need to use a$ in front of your variables in function lm() as you are specifying the dataset to use.
- Notice that plot() function in R first takes the variable that you want to measure on x-axis, and then the variable to be measured on y-axis. Which is of course different for the regression, where the variable to model always have to go first and will be visualised on y-axis.

`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
#load data
a=data.frame(mtcars)

#create an object holding the (linear) regression model
model1 = lm(mpg ~ cyl, data=a)

#displaying the regression results
summary(model1)

#plotting the data
with(a, plot(cyl, mpg))

#adding the regression line to the plot
abline(model1)

#[DIY] create an object "model2" that would hold the regression of "wt" on "drat"


#[DIY] display the regression results of model2

```

`@solution`
```{r}
#load data
a=data.frame(mtcars)

#create an object holding the (linear) regression model
model1 = lm(mpg ~ cyl, data=a)

#displaying the regression results
summary(model1)

#plotting the data
with(a, plot(cyl, mpg))

#adding the regression line to the plot
abline(model1)

#[DIY] create an object "model2" that would hold the regression of "wt" on "drat"
model2 = lm(drat ~ wt, data=a)

#[DIY] display the regression results of model2
summary(model2)
```

`@sct`
```{r}
success_msg("Nice job!")
```

---

## Multivariate Linear Regression

```yaml
type: NormalExercise
key: 8aa017f043
lang: r
xp: 100
skills: 1
```

In previous chapter we have tried to predict the value of one variable by using the information about the other variable.

In principle there is no reason why we might want to use the information in only one variable to model our variable of interest. Maybe the grade of a student in a particular class can be predicted better if we use some other information together with his/her grade in the statistics class?

Multivariate linear regression allows us to do just that. With a simple line of code we can specify a multiple independent variables that could help us predict our dependent variable. (Notice that using linear regression we cannot model multiple dependent variables at the same time. So, only one left-hand-side variable at a time).

Notice that adding independent variables to the regression might change coefficients associated to right-hand-side variables that were already in the model, as well as R-squared of the model. For example, by taking into account the information in variable “wt” together with the information in variable “cyl” to predict variable “mpg” allows us to increase the predictive power of the model from 79% to 83% (see R-square).

`@instructions`
- notice that as we are using several independent variables, visualisation of the regression line on the scatter plot does not make much sense.
- notice that the p-value of the “cyl” variable also changes if we also include “wt” in the model.

`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
#load data
a=data.frame(mtcars)

#regress variariables "cyl" and "wt" on "mpg"
model1=lm(mpg ~ cyl + wt, data=a)

#visualize the output of the regression
summary(model1)

#[DIY] add another dependent variable "hp" to the regression performed above


#[DIY]visualize the output of the new regression


#produce the scaterplot of the relation between "mpg" and "cyl"
with(a, plot(cyl, mpg))

#[DIY] add the regression line from our model2 estimation to the plot


#[DIY] in one line of code, visualize the output of a linear regression
#with "mpg" as a dependent variable and "cyl", "qsec", "gear" and "carb" as independent variables

```

`@solution`
```{r}
#load data
a=data.frame(mtcars)

#regress variariables "cyl" and "wt" on "mpg"
model1=lm(mpg ~ cyl + wt, data=a)

#visualize the output of the regression
summary(model1)

#[DIY] add another dependent variable "hp" to the regression performed above
model2=lm(mpg ~ cyl + wt + hp, data=a)

#[DIY]visualize the output of the new regression
summary(model2)

#produce the scaterplot of the relation between "mpg" and "cyl"
with(a, plot(cyl, mpg))

#[DIY] add the regression line from our model2 estimation to the plot
abline(model2)

#[DIY] in one line of code, visualize the output of a linear regression
#with "mpg" as a dependent variable and "cyl", "qsec", "gear" and "carb" as independent variables
summary(lm(mpg~cyl+qsec+gear+carb, data=a))
```

`@sct`
```{r}
success_msg("Nice job!")
```

---

## Logistic Regression

```yaml
type: NormalExercise
key: 6b7ee380ea
lang: r
xp: 100
skills: 1
```

Linear regression is a great tool for first steps in exploring the data. However, it might not be the best tool to model certain variables.

For example, if we are modelling a variable that represents a market share of the company on the market, using linear regression might be problematic. If the slope of the line is not zero, linear regression could easily predict that certain firms would have 140% of the market share, or -40% of the market share. This is, clearly, not reasonable.

Therefore, for modelling share variables we might have to use different approach.

The most straight forward of the methods available for these kinds of models is the generalised linear model, which makes sure that values of the predicted variable are confined to the interval between zero and one.

Logistic regression is one of the most widespread applications of the generalised linear models.

`@instructions`
- compare the outputs of the two models on the right (both modelling mpgShare by use of cyl and wt): the standard linear regression and the logistic regression.
- notice that logistic regression does not have R-squared statistics. Instead other indicator (AIC) is used to evaluate the goodness of fit.

`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
#load data
a=data.frame(mtcars)

#create a new variable mpgShare (which will be a part of our dataset "a") and will
#take a value of "mpg" divided by the highest value of "mpg" found in the dataset
a$mpgShare=a$mpg/max(a$mpg)

#[DIY] run a linear regression, modeling the value of mpgShare
# with variables "cyl" and "wt" 
model1=

#visualize the output of the above regression
summary(model1)

#Run a logistic regression, modeling the value of mpgShare
# with variables "cyl" and "wt" 
model2 = glm(mpgShare~cyl+wt,data=a,family=binomial(link="logit"))

#[DIY] visualize the output of the above regression

```

`@solution`
```{r}
#load data
a=data.frame(mtcars)

#create a new variable mpgShare (which will be a part of our dataset "a") and will
#take a value of "mpg" divided by the highest value of "mpg" found in the dataset
a$mpgShare=a$mpg/max(a$mpg)

#[DIY] run a linear regression, modeling the value of mpgShare
# with variables "cyl" and "wt" 
model1 = lm(mpgShare~cyl+wt, data=a)

#visualize the output of the above regression
summary(model1)

#Run a logistic regression, modeling the value of mpgShare
# with variables "cyl" and "wt" 
model2 = glm(mpgShare~cyl+wt,data=a,family=binomial(link="logit"))

#[DIY] visualize the output of the above regression
summary(model2)
```

`@sct`
```{r}
success_msg("Nice job!")
```

---

## Poisson Regression

```yaml
type: NormalExercise
key: aeb5a73e17
lang: r
xp: 100
skills: 1
```

Linear regression might not be the best tool to model certain (other than shares) types of data. For example, is we are modelling count data (e.g. number of times a consumer has visited a particular website), OLS might predict that this number is -3. This is not possible, clearly.

Other types of generalised linear models take into account of the count nature of the data.

The most widespread of such models are Poisson models. The syntax of this model is similar to that of the logistic model (as both are part of the generalised linear regression model family).

`@instructions`
- compare the output of the two models on the right (both modelling gear by use of mpg): the standard linear regression and the Poisson regression.
- notice that Poisson regression does not have R-squared statistics. Instead it has AIC similar to the logistic regression.
- run help(glm) in your RStudio (or right here in DataCamp) and study the displayed documentation carefully. This is a very powerful and simple-to-use family of regression models.

`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
#load data
a=data.frame(mtcars)

#[DIY] run a linear regression, modeling "gear" with "mpg"
# (i.e. regress "mpg" on "gear")
model1=

#[DIY] visualize the output of the model1 above


#Run a Poisson regression, modeling "gear" with "mpg"
# (i.e. regress "mpg" on "gear" by using a Poisson model)
model2 = glm(gear~mpg, data=a, family=poisson(link="log"))

#[DIY] visualize the output of the model2 above

```

`@solution`
```{r}
#load data
a=data.frame(mtcars)

#[DIY] run a linear regression, modeling "gear" with "mpg"
# (i.e. regress "mpg" on "gear")
model1 = lm(gear~mpg, data=a)

#[DIY] visualize the output of the model1 above
summary(model1)

#Run a Poisson regression, modeling "gear" with "mpg"
# (i.e. regress "mpg" on "gear" by using a Poisson model)
model2 = glm(gear~mpg, data=a, family=poisson(link="log"))

#[DIY] visualize the output of the model2 above
summary(model2)
```

`@sct`
```{r}
success_msg("Nice job!")
```
