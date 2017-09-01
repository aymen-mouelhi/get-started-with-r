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