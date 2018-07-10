# autograding

Place to share tips/tricks/best practices for autograding

## R

### nbgrader with R
- [example/demo of nbgrader with R](https://github.com/ttimbers/nbgrader_r_demo)

### Hashing answers with R
Example of using hashing to hide correct answer from students:

Question 4.1. Use the function tolower to change all the words the following movie title to lower case text: "The House with a Clock in Its Walls" and assign the lower case text the name title

```{r}
import digest

# change movie title to lower case using tolower
### BEGIN SOLUTION
title <- tolower("The House with a Clock in Its Walls")
### END SOLUTION


test_that('Solution is correct', {
    expect_equal(digest(title), 'c76933115bc8095b2140c11556800725') # we hid the answer to the test here so you can't see it
})
print("Success!")
```

*note - if you are hashing data frames that are from the tidyverse, convert them back to base data frames using `as.data.frame` before hashing so that things work nicely across computers (different versions of tidyverse make slightly different tibble objects...)*

### Check that a specific function or operator was used in a function definition

Example to test that + operator was used in the add function:
```{r}
add <- function(a, b){
  return (a + b)
}

test_that('function should use + operator', {
  expect_that(grepl("+", body(add)[2]), is_true())
})
print("Success!")
```

## Python

### Hashing answers with Python
Example of using hashing to hide correct answer from students:

Exercise 0.1. Now write some code that converts the time 5 hours and 30 minutes to that time in seconds. In doing this make sure you:
  - create a variable called minutes_in_hour for the conversion factor of minutes to seconds
  - save the answer to a variable called seconds

```{python}
from hashlib import sha1

# convert 5 hours and 30 minutes to seconds
hours = 5
minutes = 30 

### BEGIN SOLUTION
minutes_in_hour = 60
seconds = (minutes*seconds_in_minutes) + (hours*minutes_in_hour*seconds_in_minutes)
### END SOLUTION

print(seconds)


assert sha1(str(seconds).encode('utf8')).hexdigest() == '10392a9ffe9156c31d2cc4c534a08cc43d76c2ad' # we hid the answer 
print("success!")

```

*note - I plan to write a wrapper function for `sha1(str(VARIABLE).encode('utf8')).hexdigest()` in Python so we can simplify this test*


### Check that a specific function or operator was used in a function definition

Example to test that + operator was used in the add function:
```{python}
import inspect

def add(x,y):
    return x+y

assert "+" in inspect.getsource(add), "+ operator should be used"
```
