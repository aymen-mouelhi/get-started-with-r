---
title       : Hypotheses Testing
description : Discover Hypotheses Testing
--- type:NormalExercise lang:r xp:100 skills:1 key:b74f291bf2
## Introduction
In this section we will cover hypothesis testing.

We will cover two types of tests:
- proportion tests (z-test)
- mean tests (t-tests)

R is flexible enough to allow its user specify various characteristics for tests (e.g. null hypothesis, alternative hypothesis, confidence level).

Before going into details let’s load the data from the system.

Recall how to calculate mean and standard error of variables contained in the dataset.

*** =instructions
- You can also use function tail() to visualise a portion of your dataset
- Do not forget to use $ to refer to a variable in a particular dataset
- If you do not remember commands for calculating mean or standard deviation in R — Google!

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
#define an object a and assign the data on cars (from the system)
a=data.frame(mtcars)

#visualize a part of the dataset to get the feeling of what we are dealing with
head(a)

#[DIY] calculate the mean of variable "disp"


#[DIY] calculate the standard deviation of variable "disp"


#you can also calculate means of all (numeric) variables in your dataframe with one command
colMeans(a)

```

*** =solution
```{r}
#define an object a and assign the data on cars (from the system)
a=data.frame(mtcars)

#visualize a part of the dataset to get the feeling of what we are dealing with
head(a)

#[DIY] calculate the mean of variable "disp"
mean(a$disp)

#[DIY] calculate the standard deviation of variable "disp"
sd(a$disp)

#you can also calculate means of all (numeric) variables in your dataframe with one command
colMeans(a)
```

*** =sct
```{r}

```



--- type:NormalExercise lang:r xp:100 skills:1 key:e85395300f
## z-test

Z-test is a test for the proportions. In other words this is a statistical test that helps us evaluate our beliefs about certain proportions in the population based on the sample at hand.

This can help us answer the questions like:
- is the proportion of female students at SKEMA equal to 0.5.
- is the proportion of smokers in France equal to 0.15.

If you recall the lecture, for conducting Z-test you do not need much calculations on your sample data. The only thing you need to know is the proportion of observations that qualify to belong to the sub-sample you are interested in (e.g. a “female SKEMA student”, or a “French smoker” in examples above).

In the simplest example involving the data at hand, we can ask the question whether the share of cars with variable “am” being equal to 0 is equal to 50%.

Function used for z-testing is binom.test(). It requires three arguments
x - number of qualified observations in our data (19 in our case)
n - number of total observations (32 in our case)
p - the null hypothesis on the share of qualified data (0.5 in our case)

Output of the test gives rich information about the test:
- It specifies the alternative hypothesis (this is a default option, we can adjust this in next chapter)
- It specifies the confidence level and interval
- It also gives us the proportion that we observed in our sample data

Most importantly it gives us the p-value of the test.

This value can be understood as the probability that we are making a mistake if we reject our null hypothesis in favour of the alternative one. In this case this probability is 38% which is very high (anything above 10% is high), which would prompt us to conclude that we do not have enough statistical evidence to claim that the share of cars with am=0 was not 50% in the population!


*** =instructions
- Use table() function to display the frequency distribution of the desired variable in order to calculate the value of x
- Test whether the share of cars with the number of cylinders less than 6 is equal to 0.6
- What is your conclusion about the test on number of cylinders?
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
#define an object a and assign the data on cars (from the system)
a=data.frame(mtcars)

#display the frequency distribution of "am" variable
table(a$am)

#given that frequency distribution says there are 19 observations where "am=0" we run the test
binom.test(x=19, n=32, p=0.5)

#[DIY] calculate how many cars in our dataset have less than 6 cilinders


#[DIY] test whether we have enough statistical evidence to claim that the share of cars with less than 6 cilinders is not 60%

```

*** =solution
```{r}
#define an object a and assign the data on cars (from the system)
a=data.frame(mtcars)

#display the frequency distribution of "am" variable
table(a$am)

#given that frequency distribution says there are 19 observations where "am=0" we run the test
binom.test(x=19, n=32, p=0.5)

#[DIY] calculate how many cars in our dataset have less than 6 cilinders
table(a$cyl)

#[DIY] test whether we have enough statistical evidence to claim that the share of cars with less than 6 cilinders is not 60%
binom.test(x=11, n=32, p=0.6)
```

*** =sct
```{r}

```

--- type:NormalExercise lang:r xp:100 skills:1 key:8985b8add6
## Alternative hypothesis

In the previous chapter we have not specified the alternative hypothesis. Instead, R automatically performed a two-sided test. This is a default option.

We can, of course, specify the alternative hypothesis we want to work this.

This is imply an additional argument in our binom.test() function. This argument is “alternative”, and takes three values “two.sided”, “less” and “greater”.

On the right you see the same test from last chapter executed twice. First without specifying alternative hypothesis. Then with the specification. This clearly makes no difference.

However, if we want to perform a one-sided test checking whether we have any statistical evidence that the share of am=0 cars is less than 0.5, we have to specify the argument alternative="less”. 

Notice that in this case the p-value is 89% which means that we do not find statistically significant evidence to reject our null hypothesis in favour of the alternative.

*** =instructions
- Simply change the value of the “alternative” in order to test whether the share of am=0 cars is more than 0.5.
- What is the conclusion from this test?
- When testing for the share of the less than 6 cylinder cars, do not forget to first calculate the number of such cars in our dataset, by using table()
- 

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
#define an object a and assign the data on cars (from the system)
a=data.frame(mtcars)

#perform the test without alternative specification
binom.test(x=19, n=32, p=0.5)

#perform the same test with specifying "two sided" as an alternative hypothesis
binom.test(x=19, n=32, p=0.5, alternative="two.sided")

#perform the test checking whether the share of am=0 cars is less than 0.5
binom.test(x=19, n=32, p=0.5, alternative="less")

#[DIY] perform the test checking whether the share of am=0 cars is greater than 0.5


#[DIY] perform the test checking whether the share of cars with less than 6 cylinders is greater than 20%


```

*** =solution
```{r}
#define an object a and assign the data on cars (from the system)
a=data.frame(mtcars)

#perform the test without alternative specification
binom.test(x=19, n=32, p=0.5)

#perform the same test with specifying "two sided" as an alternative hypothesis
binom.test(x=19, n=32, p=0.5, alternative="two.sided")

#perform the test checking whether the share of am=0 cars is less than 0.5
binom.test(x=19, n=32, p=0.5, alternative="less")

#[DIY] perform the test checking whether the share of am=0 cars is greater than 0.5
binom.test(x=19, n=32, p=0.5, alternative="greater")

#[DIY] perform the test checking whether the share of cars with less than 6 cylinders is greater than 20%
table(a$cyl)
binom.test(x=11, n=32, p=0.2, alternative="greater")
```

*** =sct
```{r}

```


--- type:NormalExercise lang:r xp:100 skills:1 key:dcb16d6637
## t-test

t-test is the test on the mean of the variable. Using this test we will be able gain information in order to answer questions like:

- is the average income of French household different from 50k Euros?
- is the average grade of SKEMA students above 14?

And all this, of course, based on the sample of the data.

For this we will use a different data, data on characteristics of iris flowers.

The function to perform t-test is t.test(). The syntax of this function is very similar to that of binom.test().

Except that now, instead of calculating the number of observations qualifying of the test by hand (which we did in case of z-test), we can pass the variable we want to test to the function t.test().

Also, we do not need to specify the number of observations (as variable itself informs R about this).

Of course, the null hypothesis in this case is “mu” (population mean), rather than “p” (proportion).

The output of the function is also similar to that of the output of binom.test().

You can use the same argument of “alternative” to specify the alternative hypothesis.

You can also specify the confidence interval (if you want it to be different from 95%, which is the default option).

*** =instructions
- Notice how confidence interval widens as you increase your requirement on the prevision of the test - conf.level=0.99.
- Make sure to say out loud (or write down) the conclusion after every test you perform!
- Notice that last [DIY] asks you to test for a different variable that previous tasks!
- 

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
#define an object b and assign the data on characteristics of iris flower (from the system)
b=data.frame(iris)

#test whether we have signifficant evidence to claim that sepal length of iris is different from 5.6 cantimeters
t.test(b$Sepal.Length, mu=5.6)

#[DIY] test whether we have signifficant evidence to claim that sepal length of iris is grater than 5.6 cantimeters


#test, with 99% confidence, whether sepal length of iris is different from 5.6 cantimeters
t.test(b$Sepal.Length, mu=5.6, conf.level=0.99)

#[DIY]test, with 90% confidence, whether petal length of iris is less than 4.3 cantimeters

```

*** =solution
```{r}
#define an object b and assign the data on characteristics of iris flower (from the system)
b=data.frame(iris)

#test whether we have signifficant evidence to claim that sepal length of iris is different from 5.6 cantimeters
t.test(b$Sepal.Length, mu=5.6)

#[DIY] test whether we have signifficant evidence to claim that sepal length of iris is grater than 5.6 cantimeters
t.test(b$Sepal.Length, mu=5.6, alternative="greater")

#test, with 99% confidence, whether sepal length of iris is different from 5.6 cantimeters
t.test(b$Sepal.Length, mu=5.6, conf.level=0.99)

#[DIY]test, with 90% confidence, whether petal length of iris is less than 4.3 cantimeters
t.test(b$Petal.Length, mu=4.3, alternative="less", conf.level=0.9)
```

*** =sct
```{r}

```



--- type:NormalExercise lang:r xp:100 skills:1 key:5cbe2ef243
## Two sample t-test

t-test can be used to compare characteristics of two independent samples.

This methodology can be used to get insight into questions like:
- Is the income of French population high than income of German population?
- Is the average resting heart rate of a sprinter lower than the average resting heart rate of a long-distance runner?

For this exercise we will need to have the information on the same variable for two unrelated samples.

In our case we could compare characteristics of two different species of iris. Say, setosa and versicolor.

We could compare petal length, sepal length, petal width or sepal width.

*** =instructions
- Notice that 2.2e-16 is a very small number. It’s a 0.[15 zeros]22.
- Notice that we can also use alternative hypothesis and confidence interval arguments in this case
- Notice that null hypothesis always involves the equality! So, when you are comparing means, the null hypothesis is that means of the two samples are equal to one another

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
#define an object b and assign the data on characteristics of iris flower (from the system)
b=data.frame(iris)

#create two other objects that would hold subsets of our dataset
b1=b[which(b$Species=='setosa'), ]
b2=b[which(b$Species=='versicolor'), ]

#test whether the petal length of setosa iris is different from the petal length of the versicolor iris
t.test(b1$Petal.Length,b2$Petal.Length)

#[DIY] test with 90% confidence, whether the petal length of the setosa iris is greater than the petal length of the versicolor iris

```

*** =solution
```{r}
#define an object b and assign the data on characteristics of iris flower (from the system)
b=data.frame(iris)

#create two other objects that would hold subsets of our dataset
b1=b[which(b$Species=='setosa'), ]
b2=b[which(b$Species=='versicolor'), ]

#test whether the petal length of setosa iris is different from the petal length of the versicolor iris
t.test(b1$Petal.Length,b2$Petal.Length)

#[DIY] test with 90% confidence, whether the petal length of the setosa iris is greater than the petal length of the versicolor iris
t.test(b1$Petal.Length,b2$Petal.Length, alternative="greater", conf.level=0.9)
```

*** =sct
```{r}

```
