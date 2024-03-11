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
