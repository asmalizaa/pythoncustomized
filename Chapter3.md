# Data Collections – Tuples, Dictionaries, Lists, and Strings

## 3.1 Collect and process data using lists

Lists are used to store multiple items in a single variable.

Lists are one of 4 built-in data types in Python used to store collections of data, the other 3 are Tuple, Set, and Dictionary, all with different qualities and usage.

Lists are created using square brackets.

```python
# This assigns a three-element list to x
x = [1, 2, 3]
```

- List items are ordered, changeable, and allow duplicate values.
- List items are indexed, the first item has index [0], the second item has index [1] etc.
- When we say that lists are ordered, it means that the items have a defined order, and that order will not change.
- If you add new items to a list, the new items will be placed at the end of the list.
- The list is changeable, meaning that we can change, add, and remove items in a list after it has been created.
- Since lists are indexed, lists can have items with the same value.

```python
fruits = ["apple", "banana", "cherry", "apple", "cherry"]
print(fruits)
```

To determine how many items a list has, use the len() function.

```python
# get the length/size of list
print(len(x))
```

List items can be of any data type

```python
list1 = ["apple", "banana", "cherry"]
list2 = [1, 5, 7, 9, 3]
list3 = [True, False, False]
```

A list can contain different data types.

```python
list1 = ["abc", 34, True, 40, "male"]
```

It is also possible to use the list() constructor when creating a new list.

```python
thislist = list(("apple", "banana", "cherry")) # note the double round-brackets
print(thislist)
```

If L is a list, the expression L [ start : stop : step ] returns the portion of the list from index start to index stop, at a step size step.

```python
x = ["first", "second", "third", "fourth"]
y = x[1:-1]
print(y)

y = x[0:3]
print(y)

y = x[-2:-1]
print(y)

print(x[:3])
print(x[2:])
```

Let's do some operations on the list.

```python
# modifying list
x = [1, 2, 3, 4]
x[1] = "two"
print(x)

# append
x[len(x) :] = [5, 6, 7]
print(x)

x[:0] = [-1, 0]  # append from front
x[1:-1] = []  # remove/clear

x = [1, 2, 3, 4]
y = [5, 6, 7]
x.append(y)  # [1, 2, 3, 4, [5, 6, 7]]
x.extend(y)  # [1, 2, 3, 4, 5, 6, 7]
x.insert(2, "hello")

del x[1]
x.remove(3)  # remove the first 3 value
x.reverse()
```

```python
# loop through items in list
fruits = ["apple", "banana", "cherry", "apple", "cherry"]

for item in fruits:
    print(item)
```

```python
>>> # Work with composite numbers only
>>> number = 8
>>> if not is_prime(number):
...     print(f"{number} is composite")
...
8 is composite
```

The copy() method returns a shallow copy of the list.

```python
# mixed list
prime_numbers = [2, 3, 5]

# copying a list
numbers = prime_numbers.copy()

print('Copied List:', numbers)

# Output: Copied List: [2, 3, 5]
```

We can also use the = operator to copy a list. For example

```python
old_list = [1, 2, 3]

# copy list using =
new_list = old_list

# add an element to list
new_list.append('a')

print('New List:', new_list)
print('Old List:', old_list)
```

Nested list.

```python
  
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
 
odd_numbers = []
for row in matrix:
    for element in row:
        if element % 2 != 0:
            odd_numbers.append(element)
 
print(odd_numbers)
```

## 3.2 Collect and process data using tuples

## 3.3 Collect and process data using dictionaries

## 3.4 Operate with strings
