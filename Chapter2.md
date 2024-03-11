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

