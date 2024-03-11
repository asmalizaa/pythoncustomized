# Control Flow – Conditional Blocks and Loops

## 2.1 Make decisions and branch the flow with the if instruction

### Conditional statements: if, if-else, if-elif, if-elif-else

In computer programming, the if statement is a conditional statement. It is used to execute a block of code only when a specific condition is met.

An if statement executes a block of code only if the specified condition is met.

**Syntax** <br/>
![image](https://github.com/asmalizaa/pythoncustomized/assets/23090837/84fc8381-c2e6-4ee7-b437-7224a361d897)

Here, if the condition of the if statement is:
- True - the body of the if statement executes.
- False - the body of the if statement is skipped from execution.

```python
x = 5

if x < 5:
    y = -1
    z = 5

print(x, y, z)
```

An if statement can have an optional else clause. The else statement executes if the condition in the if statement evaluates to False.

**Syntax**
![image](https://github.com/asmalizaa/pythoncustomized/assets/23090837/4511298a-888c-4c61-8c4d-4dd1a6b40e8d)

Here, if the condition inside the if statement evaluates to
- True - the body of if executes, and the body of else is skipped.
- False - the body of else executes, and the body of if is skipped

```python
x = 5

if x < 5:
    y = -1
    z = 5
else:
    y = 0
    z = 10

print(x, y, z)
```

### Multiple conditional statements 

The if...else statement is used to execute a block of code among two alternatives.

However, if we need to make a choice between more than two alternatives, we use the if...elif...else statement.

**Syntax**
![image](https://github.com/asmalizaa/pythoncustomized/assets/23090837/b67f4ab8-2b7d-497f-afec-57c782983b3b)

Here,
- if condition1 - This checks if condition1 is True. If it is, the program executes code block 1.
- elif condition2 - If condition1 is not True, the program checks condition2. If condition2 is True, it executes code block 2.
- else - If neither condition1 nor condition2 is True, the program defaults to executing code block 3.

```python
x = 5

if x < 5:
    y = -1
    z = 5
elif x > 5:
    y = 1
    z = 11
else:
    y = 0
    z = 10

print(x, y, z)
```

### Nesting conditional statements

It is possible to include an if statement inside another if statement. 

```python
number = 5

# outer if statement
if number >= 0:
    # inner if statement
    if number == 0:
      print('Number is 0')
    
    # inner else statement
    else:
        print('Number is positive')

# outer else statement
else:
    print('Number is negative')
```

## 2.2  Perform different types of iterations

### The pass instruction

In Python, the pass keyword is an entire statement in itself. This statement doesn’t do anything: it’s discarded during the byte-compile phase. But for a statement that does nothing, the Python pass statement is surprisingly useful.

To do nothing inside a suite, you can use Python’s special pass statement. This statement consists of only the single keyword pass. While you can use pass in many places in Python, it’s not always useful.

```python
>>> if 1 + 1 == 2:
...     print("math is ok")
...     pass
...     print("but this is to be expected")
...
math is ok
but this is to be expected
```

In this if statement, removing the pass statement would keep the functionality the same and make your code shorter. You might be wondering why the Python syntax includes a statement that tells the interpreter to do nothing. Couldn’t you achieve the same result by not writing a statement at all?

In some cases, explicitly telling Python to do nothing serves an important purpose. For example, because the pass statement doesn’t do anything, you can use it to fulfill the requirement that a suite include at least one statement:

```python
if 1 + 1 == 3:

  File "<stdin>", line 2

    ^
IndentationError: expected an indented block
```

Even if you don’t want to add any code inside the if block, an if block with no statement creates an empty suite, which is invalid Python syntax.

To fix this, you can use pass.

```python
>>> if 1 + 1 == 3:
...     pass
...
```

### The while Loop

With the while loop we can execute a set of statements as long as a condition is true.

```python
i = 1
while i < 6:
    print(i)
    i += 1
```

The while loop requires relevant variables to be ready, in this example we need to define an indexing variable, i, which we set to 1.

### Python For Loops

A for loop is used for iterating over a sequence (that is either a list, a tuple, a dictionary, a set, or a string).

This is less like the for keyword in other programming languages, and works more like an iterator method as found in other object-orientated programming languages.

With the for loop we can execute a set of statements, once for each item in a list, tuple, set etc.

```python
fruits = ["apple", "banana", "cherry"]
for x in fruits:
    print(x)
```

The for loop does not require an indexing variable to set beforehand.

### The break Statement

With the break statement we can stop the loop before it has looped through all the items.

```python
fruits = ["apple", "banana", "cherry"]
for x in fruits:
    print(x)
    if x == "banana":
        break
```

### The continue Statement

With the continue statement we can stop the current iteration of the loop, and continue with the next.

```python
fruits = ["apple", "banana", "cherry"]
for x in fruits:
    if x == "banana":
        continue
    print(x)
```

### The range() Function

To loop through a set of code a specified number of times, we can use the range() function,

The range() function returns a sequence of numbers, starting from 0 by default, and increments by 1 (by default), and ends at a specified number.

```python
for x in range(6):
    print(x)
```

The range() function defaults to 0 as a starting value, however it is possible to specify the starting value by adding a parameter: range(2, 6), which means values from 2 to 6 (but not including 6).

```python
for x in range(2, 6):
    print(x)
```

The range() function defaults to increment the sequence by 1, however it is possible to specify the increment value by adding a third parameter: range(2, 30, 3)

```python
for x in range(2, 30, 3):
    print(x)
```

### Else in For Loop

The else keyword in a for loop specifies a block of code to be executed when the loop is finished.

```python
for x in range(6):
    print(x)
else:
    print("Finally finished!")
```

### Nested Loops

A nested loop is a loop inside a loop.

The "inner loop" will be executed one time for each iteration of the "outer loop".

```python
adj = ["red", "big", "tasty"]
fruits = ["apple", "banana", "cherry"]

for x in adj:
    for y in fruits:
        print(x, y)
```

## Activity

1. Remove negative numbers from list.

   ```python
   x = [1, 3, 5, 0, -1, 3, -2]
   print("before: {} size: {}".format(x, len(x)))
   ```

2. Count negative numbers.

   ```python
   y = [[1, -1, 0], [2, 5, -9], [-2, -3, 0]]
   count = 0
   ```
   
