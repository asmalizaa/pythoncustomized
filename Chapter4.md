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

**A function can returns a value.**

```python
def getmessage(user) :
    return "Hello, good morning {}!".format(user)

getmessage("John")

---
'Hello, good morning John!'
```

**Python None Keyword**

None is used to define a null value or Null object in Python. It is not the same as an empty string, a False, or a zero. It is a data type of the class NoneType object. 

Python None is the function returns when there are no return statements.

```python
def check_return():
	pass
print(check_return())

---
None
```

Declaring a variable as None.

```python
var = None

# checking it's value
if var is None:
	print("var has a value of None")
else:
	print("var has a value")

---
var has a value of None
```

**Recursion in Python**

The term Recursion can be defined as the process of defining something in terms of itself. In simple words, it is a process in which a function calls itself directly or indirectly.

Advantages of using recursion
- A complicated function can be split down into smaller sub-problems utilizing recursion.
- Sequence creation is simpler through recursion than utilizing any nested iteration.
- Recursive functions render the code look simple and effective.

Disadvantages of using recursio
- A lot of memory and time is taken through recursive calls which makes it expensive for use.
- Recursive functions are challenging to debug.
- The reasoning behind recursion can sometimes be tough to think through.

**Syntax**
![image](https://github.com/asmalizaa/pythoncustomized/assets/23090837/f2684d47-86b1-4f66-aa93-52205ca19398)

```python
# Program to print the fibonacci series upto n_terms

# Recursive function
def recursive_fibonacci(n):
if n <= 1:
	return n
else:
	return(recursive_fibonacci(n-1) + recursive_fibonacci(n-2))

n_terms = 10

# check if the number of terms is valid
if n_terms <= 0:
print("Invalid input ! Please input a positive value")
else:
print("Fibonacci series:")
for i in range(n_terms):
	print(recursive_fibonacci(i))

---
Fibonacci series:
0
1
1
2
3
5
8
13
21
34
```

## 4.2 Organize interaction between the function and its environment

There is always a little confusion among budding developers between a parameter and an argument, this article focuses to clarify the difference between them and help you to use them effectively.

**Parameters**

A parameter is the variable defined within the parentheses during function definition. Simply they are written when we declare a function. 

```python
# Here a,b are the parameters 
def sum(a,b): 
print(a+b) 
	
sum(1,2)

---
3
```

**Arguments**

An argument is a value that is passed to a function when it is called. It might be a variable, value or object passed to a function or method as input. They are written when we are calling the function.

```python
def sum(a,b): 
print(a+b) 
	
# Here the values 1,2 are arguments 
sum(1,2) 

---
3
```

**Types of arguments in python**

Python functions can contain two types of arguments:
- Positional Arguments

  Positional Arguments are needed to be included in proper order i.e the first argument is always listed first when the function is called, second argument needs to be called second and so on.

  ```python
  def person_name(first_name,second_name):
      print(first_name+second_name)

      # First name is Ram placed first
      # Second name is Babu place second
      person_name("Ram","Babu")

  ---
  RamBabu
  ```

- Keyword Arguments

  Keyword Arguments is an argument passed to a function or method which is preceded by a keyword and an equal to sign. The order of keyword argument with respect to another keyword argument does not matter because the values are being explicitly assigned.

  ```python
  def person_name(first_name,second_name):
      print(first_name+second_name)

      # Here we are explicitly assigning the values
      person_name(second_name="Babu",first_name="Ram")

  ---
  RamBabu
  ```

**Function that takes parameters**

```python
# define function to greet a user
def greetuser(user) :
    print("Hello, good morning {}!".format(user))

greetuser("John")
greetuser("Bob")

---
Hello, good morning John!
Hello, good morning Bob!
```

```python
# function that calculate factorial
# this function takes 1 parameter
def fact(n) :
    """ return the factorial of the given number """
    r = 1
    while n > 0 :
        r = r * n
        n = n - 1
    return r

print("factorial of {} is {}".format(3, fact(3)))
print("factorial of {} is {}".format(4, fact(4)))

---
factorial of 3 is 6
factorial of 4 is 24
```

```python
# function that takes 2 parameters
def power(x, y) :
    r = 1
    while y > 0 :
        r = r * x
        y = y - 1
    return r

print("{} to the power of {} is {}".format(2, 3, power(2, 3)))
print("{} to the power of {} is {}".format(3, 3, power(3, 3)))

---
2 to the power of 3 is 8
3 to the power of 3 is 27
```

```python
# define function that takes 3 parameters
# make 2 of the parameters optional (default parameter)
def display(name, email = "user@example.com", message = "Hello World!") :
    print("Name: {}, Email: {}, Message: {}".format(name, email, message))

display("John", "john@example.com", "Good morning!")
display("John", "john@example.com")
display("Bob", "bob@example.com", "Today is a good day")
display("Bob", "bob@example.com")
display("Sarah")

---
Name: John, Email: john@example.com, Message: Good morning!
Name: John, Email: john@example.com, Message: Hello World!
Name: Bob, Email: bob@example.com, Message: Today is a good day
Name: Bob, Email: bob@example.com, Message: Hello World!
Name: Sarah, Email: user@example.com, Message: Hello World!
```

```python
# define another function that takes 3 parameters: string, integer, boolean
# parameter sequence is important
def getinformation(name, number, flag = False) :
    print("name: {}".format(name))
    print("number x 2: {}".format(int(number) * 2))
    print("flag: {}".format(flag))

getinformation("david", 12, True)

# named parameters
getinformation(number = 12, name = "david", flag = True)
getinformation(flag=False, name="alan", number=9)

# default parameter
getinformation("william", 18)

---
name: david
number x 2: 24
flag: True
name: david
number x 2: 24
flag: True
name: alan
number x 2: 18
flag: False
name: william
number x 2: 36
flag: False
```

```python
# function with default parameters
def fun1(a = 1, b = 2, c = 3) :
    print("a: {} b: {} c: {}".format(a, b, c))

fun1()
fun1(6)
fun1(6, 7)
fun1(6, 7, 8)
fun1(a=10, c=30)
fun1(c=100)
fun1(b=200)

---
a: 1 b: 2 c: 3
a: 6 b: 2 c: 3
a: 6 b: 7 c: 3
a: 6 b: 7 c: 8
a: 10 b: 2 c: 30
a: 1 b: 2 c: 100
a: 1 b: 200 c: 3
```

```python
# print() takes variable number of arguments
print(1)
print(1, 2)
print(1, 2, 3, 4, 5)
print("hello")
print("hello", 100, True)
print()

---
1
1 2
1 2 3 4 5
hello
hello 100 True
```

**Function that takes a variable number of arguments**

```python
def calculate(*numbers) :
    total = 0
    # print(numbers, type(numbers))
    # check if numbers is empty or not
    if len(numbers) == 0 :
        print("no parameters")
    else :
        # do calculation here
        for n in numbers :
            # check the type
            if type(n) is int :
                total += n
            else :
                print(n)
        print("total: {}".format(total))

calculate(1)
calculate(1, 2)
calculate(3, 4, 5, 6)
calculate()
calculate("hello", 10, 20)
calculate("hello", 10, "world", 20, True)

---
total: 1
total: 3
total: 18
no parameters
hello
total: 30
hello
world
True
total: 30
```

```python
# the first 2 parameters are required
# the rest will be assigned to varargs
def fun2(value, name, *numbers) :
    print(value)
    print(name)
    print(numbers)

fun2(1, "alan")
fun2(1, 2, 3, 4, 5)

---
1
alan
()
1
2
(3, 4, 5)
```

Indefinite number of arguments.

```python
# x and y are required parameters
# other will get/store parameters as dictionary
def example_fun(x, y, **other) :
    print(x, y, other)
    print("x: {0}, y: {1}, keys in 'other': {2}".format(x, y, list(other.keys())))
    
    other_total = 0
    for k in other.keys() :
        other_total += other[k]
    print("The total of values in other is {}".format(other_total))

example_fun(1, 2, foo = 3, bar = 4)
example_fun(5, 6, a = 1, b = 2, c = 3, d = 4)

---
1 2 {'foo': 3, 'bar': 4}
x: 1, y: 2, keys in 'other': ['foo', 'bar']
The total of values in other is 7
5 6 {'a': 1, 'b': 2, 'c': 3, 'd': 4}
x: 5, y: 6, keys in 'other': ['a', 'b', 'c', 'd']
The total of values in other is 10
```

Mutable objects as arguments.

```python
def fun3(n, list1, list2) :
    list1.append(3)
    list2 = [4, 5, 6]
    n = n + 1
    # no return from this function

# define variables
x = 5
y = [1, 2]
z = [10, 20]
print("before: x = {} y = {} z = {}".format(x, y, z))

# call function and pass parameters
fun3(x, y, z)
print("after: x = {} y = {} z = {}".format(x, y, z))

---
before: x = 5 y = [1, 2] z = [10, 20]
after: x = 5 y = [1, 2, 3] z = [10, 20]
```

**Function as parameter**

You are going to define a function and assign it to a variable, then use this variable to call a function and pass it as parameter.

```python
def f_to_k(tempf) :
    return 273.15 + (tempf - 32) * 5 / 9

def c_to_k(tempc) :
    return 273.15 + tempc

print("{}F is {:.3f}K".format(100, f_to_k(100)))
print("{}C is {:.3f}K".format(27, c_to_k(27)))

---
100F is 310.928K
27C is 300.150K
```

```python
# assign function to variable
fun_ftok = f_to_k
fun_ctok = c_to_k

# call the function using variable
result = fun_ftok(150)
print("result: {:.3f}".format(result))

result = fun_ctok(28)
print("result: {:.3f}".format(result))

---
result: 338.706
result: 301.150
```

```python
# place the variables in a list or tuple or dictionary
temp_converter = { 'ftok' : fun_ftok, 'ctok' : fun_ctok }
print(temp_converter)

# call the function using the key
print("{:.3f}".format(temp_converter['ftok'](150)))
print("{:.3f}".format(temp_converter['ctok'](28)))

---
{'ftok': <function f_to_k at 0x0000019642412CA0>, 'ctok': <function c_to_k at 0x0000019642412D40>}
338.706
301.150
```

**Lambda Expressions**

A lambda function is a small anonymous function.

A lambda function can take any number of arguments, but can only have one expression.

```python
# use lambda instead
# lambda is a syntax to do inline anonymous function definition
temp_converter_lambda = { 'ftoklambda' : lambda tempf : 273.15 + (tempf - 32) * 5 / 9, 
                            'ctoklambda' : lambda tempc : 273.15 + tempc }

print("{:.3f}".format(temp_converter_lambda['ftoklambda'](150)))
print("{:.3f}".format(temp_converter_lambda['ctoklambda'](28)))

---
338.706
301.150
```

**Variable Scopes**

- local : variable defined within a function block, it only available within function
- global : variable defined outside function block, available anywhere within program

```python
email = "john@example.com"  # global

print(email)    # get global

def showemail() :
    email = "bob@example.com"   # local
    print(email)    # get local

print(email)    # get global
showemail()
print(email)    # get global

---
john@example.com
john@example.com
bob@example.com
john@example.com
```

```python
name = "john"

def showname(name) :
    # changes only affect the local copy of name
    name = "bob"
    print(name)

print(name)
showname(name)
print(name)

---
john
bob
john
```

```python
title = "python"

print(title)

def showtitle() :
    global title    # access the global variable
    title = "java"  # no longer a local variable, but instead will modify global variable
    print(title)

print(title)
showtitle()
print(title)    # value updated

---
python
python
java
java
```


## 4.3  Python Built-In Exceptions Hierarchy

## 4.4 Basics of Python Exception Handling
