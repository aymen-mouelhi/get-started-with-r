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

*** =pre_exercise_code
```{r}
# no pec

```

*** =sample_code
```{r}
#Calculate 1 + 2
1 + 2

#Calculate 42 + 88
42+88

# Notice that R does not care much for spaces before and after operations.
# Both operations above are executed without any problems.
```

*** =solution
```{r}
#Calculate 1 + 2
1 + 2

#Calculate 42 + 88
42+88

# Notice that R does not care much for spaces before and after operations.
# Both operations above are executed without any problmes.

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
- Define variable y and assign value `5` to it
- Define the variable myVar and assign the value z times x to it
- Print out to the console half of the variable myVar
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
test_object("myVar")
test_output_contains("24",
                     incorrect_msg = "Did you assign the value z times x to myVar?")
success_msg("Nice job!")

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
# Define a numerical variable x and assign 3
x=3

# Define a string variable y and assign "cat"
y="cat"

# Define boolean z and assign FALSE
z=FALSE

# Add y to x
#x+y

# Check the type of x


# Define another string variable a and assign value "love"


# Combine variables y and a, as well as "jack"
paste(y, a, "jack")

# Create a new variable b and use paste function to assign to it "I love my cat"


# Print b into the console

```

*** =solution
```{r}
# Define a numerical variable x and assign 3
x=3

# Define a string variable y and assign "cat"
y="cat"

# Define boolean z and assign FALSE
z=FALSE

# Add y to x
x+y

# Check the type of x
class(x)

# Define another string variable a and assign value "love"
a="love"

# Combine variables y and a, as well as "jack"
paste(y, a, "jack")

# Create a new variable b and use paste function to assign to it "I love my cat"
b=paste("I", a, "my", y)

# Print b into the console
b
```

*** =sct
```{r}
test_error(incorrect_msg = "It seems like you added a numeric variable to a string variable")
success_msg("Nice job!")

```


--- type:NormalExercise lang:r xp:100 skills:1 key:f0bfb6230f
## Vectors

Vectors are very important as they allow us to handle multiple values all at once..

We can create vectors by using combine function c().

In correspondence with data types, we can have numeric, string or Boolean vectors.

Notice that you cannot combine different data types in the same vector!

We can call out any component of the vector by referring to it’s index/location in the vector. For example in vector x=[9, 8, 7, 6] 7 is in the third position, so we can call it out as x[3].

In R, applying (mathematical) operations on vectors results into the operation being applied to each component of the vector (rather than to the vector as a whole).

*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Create a numeric vector
numVector=c(1, 4, 5.7, 7)

# Create a string vector
strVector=c("a", "b", "cde")

# Create a Boolean vector
boolVector=c(FALSE, TRUE, TRUE, FALSE, FALSE)

# Create a new variable x and assign the third value in vector numVector, print it out
x=numVector[3]
x

# Combine number 1, string "a" and Boolean TRUE in a string y

# You did not get an error, but did R do what you wanted it to do? Print out the vector and examine
y

# Define a new vector z which contains squares of the components of vector numVector
z=numVector^2
z

# Redefine vector z so that it contains thirds of each of its current components


# Adjust the first component of vector z to be equal to 2

```

*** =solution
```{r}
# Create a numeric vector
numVector=c(1, 4, 5.7, 7)

# Create a string vector
strVector=c("a", "b", "cde")

# Create a Boolean vector
boolVector=c(FALSE, TRUE, TRUE, FALSE, FALSE)

# Create a new variable x and assign the third value in vector numVector, print it out
x=numVector[3]
x

# Combine number 1, string "a" and Boolean TRUE in a string y
y=c(1, "a", TRUE)
# You did not get an error, but did R do what you wanted it to do? Print out the vector and examine
y

# Define a new vector z which contains squares of the components of vector numVector
z=numVector^2
z

# Redefine vector z so that it contains thirds of each of its current components
z=z/3

# Adjust the first component of vector z to be equal to 2
z[1]=2

```

*** =sct
```{r}
success_msg("Nice job!")

```


--- type:NormalExercise lang:r xp:100 skills:1 key:220118c6eb
## Factors

We covered three types of data. However, there is one more important type of data structure in R — a factor. Factors are used to store data about categorical variables.

Categorical variables can take finite number of values. For example, if we have a variable that describes a day of the week for every workout you’ve had over last year, we know that this variable can only take seven distinct values (Monday, Tuesday, etc.).

The best way to save (and manipulate) such information is by using factors.

To create factors in R, you can use factor() function.

Factors in R use another notion of “levels”, which correspond to distinct occurrences (in the example above: Monday, Tuesday, etc.). Levels can be unordered (for example in case of gender there is no particular use for ordering) or ordered (for example in case of educational attainment we know that person who has a master’s degree has studied more than the person who only holds a high school diploma).

*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Create a string vector to stor gender of your friends and print out
x = c("Male", "Female", "Female", "Male", "Male")
x

# Convert the string vector x to a factor vector y and print out



# Create a string vector to hold your friends' highest educational attainment
edu=c("high school", "PhD", "bachelor", "masters", "masters")

# Transform this vector into an ordered factor and print it out
eduFactor=factor(edu, order=TRUE, levels=c("high school", "bachelor", "masters", "PhD"))


# We can compare ordered factors.
# Here we can compare whether your first friend has higher educattional attainment than your third friend
eduFactor[1]>eduFactor[3]

# This returns a Boolian value that we can also pass to another variable
z=eduFactor[1]>eduFactor[3]
z
```

*** =solution
```{r}
# Create a string vector to stor gender of your friends and print out
x = c("Male", "Female", "Female", "Male", "Male")
x

# Convert the string vector x to a factor vector y and print out
y=factor(x)
y

# Create a string vector to hold your friends' highest educational attainment
edu=c("high school", "PhD", "bachelor", "masters", "masters")

# Transform this vector into an ordered factor and print it out
eduFactor=factor(edu, order=TRUE, levels=c("high school", "bachelor", "masters", "PhD"))
eduFactor

# We can compare ordered factors.
# Here we can compare whether your first friend has higher educattional attainment than your third friend
eduFactor[1]>eduFactor[3]

# This returns a Boolian value that we can also pass to another variable
z=eduFactor[1]>eduFactor[3]
z
```

*** =sct
```{r}
success_msg("Nice job!")

```
