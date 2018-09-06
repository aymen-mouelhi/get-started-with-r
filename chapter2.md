---
title: Variables
description: 'A step by step guide to Variables'
---

## Introduction

```yaml
type: NormalExercise
key: e5aea4ac19
lang: r
xp: 100
skills: 1
```

This section will go through basic functions to handle variables. Toward the end we will also introduce a concept that combines variables together.

However, before getting into handling variables let’s recall factors.

Recall that factors handle categorical variables. Previously we’ve seen categories as string values. However, this is not necessary. Categories can also be numerical values.

`@instructions`
- You will need to use “levels” attribute for generating the order
- If it is not clear how to use levels within factor(), try to call R help by typing help(levels) directly into the console and running it

`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
# Define a numeric vector x
x=c(1,4,3,5,2,4,3,6,3,5,3,5,1,5,1,6,3,4,6)

# Create a factor vector (xFactor) from x and print it out
xFactor=factor(x)
xFactor
# Notice that levels are unordered

# We can create an ordered factor vector by simply specifying an argument "ordered" in function "factor"
xFactor2=factor(x, ordered=TRUE)
xFactor2
# Notice that we have not given R the instruction on how to order levels
# In such a situation R uses numerical order as a default

#[DIY] Create an ordered factor vector with levels ordered as follows 4<3<5<1<2<6 and print it out into console



# Sometimes you want to get rid of a certain variable from the memory of your computer.
# For this you can use "rm" function.
# For example to get rid of "xFactor2" you execute
rm(xFactor2)

# Sometimes it is useful to clear your workspace (drop all the variables and constructs that you have created).
# For this purpose you can use
rm(list=ls())
```

`@solution`
```{r}
# Define a numeric vector x
x=c(1,4,3,5,2,4,3,6,3,5,3,5,1,5,1,6,3,4,6)

# Create a factor vector (xFactor) from x and print it out
xFactor=factor(x)
xFactor
# Notice that levels are unordered

# We can create an ordered factor vector by simply specifying an argument "ordered" in function "factor"
xFactor2=factor(x, ordered=TRUE)
xFactor2
# Notice that we have not given R the instruction on how to order levels
# In such a situation R uses numerical order as a default

#[DIY] Create an ordered factor vector with levels ordered as follows 4<3<5<1<2<6 and print it out into console
xFactor3=factor(x, ordered=TRUE, levels=c(4,3,5,1,2,6))
xFactor3

# Sometimes you want to get rid of a certain variable from the memory of your computer.
# For this you can use "rm" function.
# For example to get rid of "xFactor2" you execute
rm(xFactor2)

# Sometimes it is useful to clear your workspace (drop all the variables and constructs that you have created).
# For this purpose you can use
rm(list=ls())
```

`@sct`
```{r}
#test_object("xFactor3")
success_msg("Nice job!")
```

---

## Summarizing

```yaml
type: NormalExercise
key: 499cf8673c
lang: r
xp: 100
skills: 1
```

Statistics is routinely dealing with long vectors (variables with lots of observations). Therefore, the first useful thing to do to study your data is to summarize it.

R’s “summary()” function is indispensable in this respect. However, you have to keep in mind that the same function produces very different type of output depending on what type of vector it is fed.

One particularly important type of summary is a frequency distribution. Absolute frequency distributions for discrete variables are easily produced by first factoring our variable and then summarizing it.

Notice that R’s useful function “as.factor()”. Using this shortcut we can produce frequency distributions without actually creating a new factor vector.

`@instructions`
- Use function summary() to see various types of output it generates
- Try to produce the solution to the last [DIY] in one line, remember you can nest the functions

`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
# Create a string vector
x=c("cat", "dog", "dog", "rabbit", "dog", "cat", "rabbit")

# Summarize vector x
summary(x)

# Create numeric vector (a discrete variable)
y=c(1,4,3,5,5,4,3,6,3,5,3,5,1,5,1,6,3,4,6)

#[DIY] Summarize y


# Create Boolian vector
z=c(FALSE, FALSE, TRUE, FALSE, TRUE, TRUE, TRUE)

#[DIY] Summarize z


# Create a new factor vector by factoring x
xFactor=factor(x)

#[DIY] Summarize xFactor


# Summarize a factor of y
summary(as.factor(y))

#[DIY] Summarize a factor (produce an absolute frequency distribution) of z

```

`@solution`
```{r}
# Create a string vector
x=c("cat", "dog", "dog", "rabbit", "dog", "cat", "rabbit")

# Summarize vector x
summary(x)

# Create numeric vector (a discrete variable)
y=c(1,4,3,5,5,4,3,6,3,5,3,5,1,5,1,6,3,4,6)

#[DIY] Summarize y
summary(y)

# Create Boolian vector
z=c(FALSE, FALSE, TRUE, FALSE, TRUE, TRUE, TRUE)

#[DIY] Summarize z
summary(z)

# Create a new factor vector by factoring x
xFactor=factor(x)

#[DIY] Summarize xFactor
summary(xFactor)

# Summarize a factor of y
summary(as.factor(y))

#[DIY] Summarize a factor (produce an absolute frequency distribution) of z
summary(as.factor(z))

```

`@sct`
```{r}
success_msg("Nice job!")
```

---

## Visualization

```yaml
type: NormalExercise
key: e66bff2891
lang: r
xp: 100
skills: 1
```

Humans digest visual information much faster than numeric information. Therefore, sometimes it is desirable to plot the frequency distributions.

Plotting frequency distributions in R is very easy, as long as we are concerned with categorical variables.

We need a bit more care when it comes to continuous (numeric) variables.

`@instructions`
- Remember to transform your numeric vector into factors
- Use arrows below the plots to navigate between multiple plots you might have created

`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
# Create a string vector
x=c("cat", "dog", "dog", "rabbit", "dog", "cat", "rabbit")

# Plot the frequency distribution of x
plot(as.factor(x))

# Create numeric vector (a discrete variable)
y=c(1,4,3,5,5,6,3,6,3,5,3,5,1,5,1,6,3,4,6)

#[DIY] Plot the frequency distribution of y


# You can use "hist()" function to do the same
hist(y)

# However, ploting factor of a cariable makes sense only in certain cases
# Create a numeric vector of a continuous variable
z=c(2.1,3,4.2,8,4.1,7,14,13.3,15.2,19.2,5.8,6,4.1,8.9,14.5,16.7,3.1,1.4,2.3,5.1)

#[DIY] Plot and compare frequency distributions with both "plot(as.factor())" and "hist()" functions



# If we do not pass any argument, "hist()" function chooses (equal) bin sizes automatically
# But we can also specify the number (of equal) bin sizes
hist(z, breaks=9)

# Moreover, we can even make bins of varied size if we pass specific break points
hist(z, breaks=c(0,1,2,3,5,7,10,15,20))
```

`@solution`
```{r}
# Create a string vector
x=c("cat", "dog", "dog", "rabbit", "dog", "cat", "rabbit")

# Plot the frequency distribution of x
plot(as.factor(x))

# Create numeric vector (a discrete variable)
y=c(1,4,3,5,5,6,3,6,3,5,3,5,1,5,1,6,3,4,6)

#[DIY] Plot the frequency distribution of y
plot(as.factor(y))

# You can use "hist()" function to do the same
hist(y)

# However, ploting factor of a cariable makes sense only in certain cases
# Create a numeric vector of a continuous variable
z=c(2.1,3,4.2,8,4.1,7,14,13.3,15.2,19.2,5.8,6,4.1,8.9,14.5,16.7,3.1,1.4,2.3,5.1)

#[DIY] Plot and compare frequency distributions with both "plot(as.factor())" and "hist()" functions
plot(as.factor(z))
hist(z)

# If we do not pass any argument, "hist()" function chooses (equal) bin sizes automatically
# But we can also specify the number (of equal) bin sizes
hist(z, breaks=9)

# Moreover, we can even make bins of varied size if we pass specific break points
hist(z, breaks=c(0,1,2,3,5,7,10,15,20))
```

`@sct`
```{r}
success_msg("Nice job!")

```

---

## Data frames

```yaml
type: NormalExercise
key: df58e8b202
lang: r
xp: 100
skills: 1
```

As you remember (I hope) you cannot store information of different data types in the same vector. However, you can combine vectors holding data of various types into a data frame.

Fata frame is a central concept in R. This is how we can hold large data sets into the memory of our machines.

Most of the times datasets are very large to examine in its entirety. Therefore, in order to familiarize ourselves with the structure of the data, we can display only first few observations by using “head()” function.

Data frame binds together information about different variables. We can call out these separate variables (as vectors) by using “$” sign. Once we have done this, we can handle this variable as a vector (and perform any analysis we have already covered, or will cover in the future).

We can add and remove variables to any data frame (make sure not to try to combine vectors of different length — different number of variables).

`@instructions`
- Notice that our dataset is just a regular object in R. We know how to print out the values contained in the object.
- Recall that any operation on the vector is performed separately on every component
- Printing out several observations allows us to see every variable contained in the dataset

`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
# R has a number of built in datasets. mtcars is one of them.
# We can create an object to hold our data
x=mtcars

# We can examine a part (several top observations) of the dataset
head(x)

# We can also examine several observations at the bottom of the dataset
tail(x)

#[DIY] We can also print out the whole data set into the console


# We can refer to a variable "wt" in data frame "x" as
x$wt
# This gives us a vector that we can manipulate

#[DIY] Create a vector y whose components are squares of variable wt in dataframe x


# Now we can add this variable y to our data frame
x$wtSquare=y

#[DIY] Examine that we have in fact expanded our datafreme by one variable by the use of "head()" function


# We can also drop some variables from our data frame. For this we have to use "NULL" designation
x$qsec=NULL
```

`@solution`
```{r}
# R has a number of built in datasets. mtcars is one of them.
# We can create an object to hold our data
x=mtcars

# We can examine a part (several top observations) of the dataset
head(x)

# We can also examine several observations at the bottom of the dataset
tail(x)

#[DIY] We can also print out the whole data set into the console
x

# We can refer to a variable "wt" in data frame "x" as
x$wt
# This gives us a vector that we can manipulate

#[DIY] Create a vector y whose components are squares of variable wt in dataframe x
y=x$wt^2

# Now we can add this variable y to our data frame
x$wtSquare=y

#[DIY] Examine that we have in fact expanded our datafreme by one variable by the use of "head()" function
head(x)

# We can also drop some variables from our data frame. For this we have to use "NULL" designation
x$qsec=NULL
```

`@sct`
```{r}
success_msg("Nice job!")

```
