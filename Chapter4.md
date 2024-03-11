# Functions and Exceptions

## 4.1  Decompose the code using functions

A simple function in python basically a function that display (print) message only, does not take any input (parameter/argument) and also does not return any value (result).

```python
# define a simple function that display message
def greet() :
    print("Good morning everyone!")

# call greet() from here
greet()
```

```python
# call greet() from another code cell
greet()
greet()

for i in range(5) :
    greet()
```

A function can returns a value.

```python
def getmessage(user) :
    return "Hello, good morning {}!".format(user)

getmessage("John")

---
'Hello, good morning John!'
```

## 4.2 Organize interaction between the function and its environment

## 4.3  Python Built-In Exceptions Hierarchy

## 4.4 Basics of Python Exception Handling
