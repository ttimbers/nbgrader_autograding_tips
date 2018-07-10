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

## Python

### Check that a specific function or operator was used in a function definition

Example to test that + operator was used in the add function:
```{python}
import inspect

def add(x,y):
    return x+y

assert "+" in inspect.getsource(add), "+ operator should be used"
```
