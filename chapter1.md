---
title       : Introduction to R
description : Introduction to R
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf


--- type:NormalExercise lang:r xp:100 skills:1 key:9227bbc889
## Welcome
Welcome to the short introductory tutorial for R. Here is how this tutorial works.
In the editor on the right you should type R code to solve the exercises. When you hit the 'Submit Answer' button, every line of code is interpreted and executed by R and you get a message whether or not your code was correct. The output of your R code is shown in the console in the lower right corner.

R makes use of the # sign to add comments, so that you and others can understand what the R code is about. Comments are not run as R code, so they will not influence your result. This is an indispensable feature for documentation. Use it to document what you do (code does) as much as you can.

You can also execute R commands straight in the console. This is a good way to experiment with R code, as your submission is not checked for correctness. There are two ways to do this. 1. Copy lines of code you need to execute from “script.R” field to “R Console” field and hit enter. 2. Highlight lines of code you need to execute in “script.R” and hit command+enter.

*** =instructions
- Calculate the sum of `1` and `2` in the editor on the right.
- Calculate the sum of `42` and `88` in the editor on the right.
*** =hint
Notice that R does not care much for spaces before and after operations.
Both operations above are executed without any problemes.

*** =pre_exercise_code
```{r}
# no pec

```

*** =sample_code
```{r}
#Calculate 1 + 2

#Calculate 42 + 88

```

*** =solution
```{r}
#Calculate 1 + 2
1 + 2

#Calculate 42 + 88
42+88
```

*** =sct
```{r}
test_output_contains("3",
                     incorrect_msg = "Did you print the sum of `1` and `2`?")
test_output_contains("130",
                     incorrect_msg = "Did you print the sum of `42` and `88`?")
success_msg("Nice job!")
```


--- type:NormalExercise lang:r xp:100 skills:1 key:59b6111ffa
## Arithmetics
Arithmetics in R is pretty straight forward (you probably guessed this from the previous examples). The operations have pretty much same signs as the same operations in Excel.

Study each example presented in the script. Make calculations with pen and paper (or mentally) for examples (f) and (g). Then execute the script and compare the results.

Notice that for the example (h) you have to write the script.

*** =instructions
- Add the sum of `8` and `7`.
- Substruct `4` from `7`.
- Multiply `4` per `5`.
- Devide `9` by `3`.
- Raise `7` to the power of `2`.
- Devide the sum of `5` and `7` by `3`
- Raise `3` to the power of the difference between `8` and `6`
- Multiply `5` by the sum of `6` and `-3`

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# (a) An addition
8+7

# (b) A subtraction
4-7

# (c) A multiplication
4*5

# (d) A division
9/3

# (e) An exponentiation
7^2

# (f) Devide the sum of 5 and 7 by 3
(5+7)/3

# (g) Raise 3 to the power of the difference between 8 and 6
3^(8-6)

# (h) Multiply 5 by the sum of 6 and -3

```

*** =solution
```{r}
# (a) An addition
8+7

# (b) A subtraction
4-7

# (c) A multiplication
4*5

# (d) A division
9/3

# (e) An exponentiation
7^2

# (f) Devide the sum of 5 and 7 by 3
(5+7)/3

# (g) Raise 3 to the power of the difference between 8 and 6
3^(8-6)

# (h) Multiply 5 by the sum of 6 and -3
5*(6-3)
```

*** =sct
```{r}
test_output_contains("15",
                     incorrect_msg = "Did you multiply `5` by the sum of `6` and `-3`?")
success_msg("Nice job!")
```


--- type:NormalExercise lang:r xp:100 skills:1 key:9a44f58c0a
## Variables
A basic concept in (statistical) programming is called a variable. We still have not talked about variables in our course, so without going into too much detail, for the moment think about variables as value holders.

A variable allows you to store a value (e.g. 4) or a set of values in R. You can then later use this variable's name to easily access the value or the object (like a set of values) that is stored within this variable.

You can use the command “=“ to assign values to variables. (Notice that in R there is an alternative and more widespread command “<-” for assignment operation. However, we will stick to “=” in this course).

After creating variables and signing values to them, you can perform arithmetic operations on them (and much more).

*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Define variable x and assign value 3 to it
x=3

# Print out the value of x into the console
x

# Define variable y and assign value 5 to it (you do it!)


# Define variable z using variables x and y
z=x*y

# Print the value out into the console
z

# Redefine value of variable z
z=x+y
z

# Redefine value of z once more
z=z*2
z

# Notice here that R uses the old value of z on the right side of the equation! This is a very useful feature.


# Define the variable myVar and assign the value z times x to it


# Print out to the console half of the variable myVar

```

*** =solution
```{r}
# Define variable x and ssign value 3 to it
x=3

# Print out the value of x into the console
x

# Define variable y and assign value 5 to it (you do it!)
y=5

# Define variable z using variables x and y
z=x*y

# Print the value out into the console
z

# Redefine value of variable z
z=x+y
z

# Redefine value of z once more
z=z*2
z
# Notice here that R uses the old value of z on the right side of the equation! This is a very useful feature.

# Define the variable myVar and assign the value z times x to it
myVar=z*x

# Print out to the console half of the variable myVar
myVar/2

```

*** =sct
```{r}
test_output_contains("24",
                     incorrect_msg = "Did you assign the value z times x to myVar?")

```

--- type:NormalExercise lang:r xp:100 skills:1 key:be86704fa3
## Data types
There are three basic data types in R.

1. numerics - these are values like 3 and 4.123 (Notice that R does not make distinction between integer (i.e. 3) and decimal (i.e. 4.123) values. This is different from Stata as we will see later in the course)

2. characters - these are textual (or string, particularly in Stata) values like “dog” and “cat”. Notice that we wrap these values in quotation marks to tell R what they are. Also keep in mind that R is case sensitive, so value “cat” is different from value “Cat”.

3. logical values - these are Booleans that take only two values TRUE and FALSE.

Notice that each data type calls for different types of operations. Also, R will not be able to handle operations combining data types in senseless manner (e.g. 3 + “cat”).

You can check the type of any variable using class(variable) command.

*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}

```

*** =solution
```{r}

```

*** =sct
```{r}

```


--- type:NormalExercise lang:r xp:100 skills:1 key:f0bfb6230f
## Vectors


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}

```

*** =solution
```{r}

```

*** =sct
```{r}

```


--- type:NormalExercise lang:r xp:100 skills:1 key:220118c6eb
## Factors


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}

```

*** =solution
```{r}

```

*** =sct
```{r}

```
