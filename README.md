# autograding

Place to share tips/tricks/best practices for autograding


## Python

Example to test that + operator was used in the add function:
```{python}
import inspect

def add(x,y):
    return x+y

assert "+" in inspect.getsource(add), "+ operator should be used"
```
