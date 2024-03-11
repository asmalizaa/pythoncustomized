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
elif x > 5:
    y = 1
    z = 11
else:
    y = 0
    z = 10

print(x, y, z)
```

## 2.2  Perform different types of iterations
