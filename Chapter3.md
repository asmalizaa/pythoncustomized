# Data Collections – Tuples, Dictionaries, Lists, and Strings

## 3.1 Collect and process data using lists

List is an ordered collection (sequence) of values, defined using comma-separated values in a pair of square brackets. List in python is mutable (it can be modified - add, update, delete).

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

Sorting list.

```python
# in-place sorting (change the list)
x = [3, 8, 4, 0, 2, 1]
x.sort()

# make copy then sort
x = [2, 4, 1, 3]
y = x[:]
y.sort()

# strings
x = ["Life", "Is", "Enchanting"]
x.sort()

# list of list
x = [[3, 5], [2, 9], [2, 3], [4, 1], [3, 2]]
x.sort()
print(x)

# sort by the second element
x.sort(key=lambda x : x[1])
print(x)

# sorted
x = (4, 3, 1, 2)
y = sorted(x)

z = sorted(x, reverse=True)
```

## 3.2 Collect and process data using tuples

Tuple is very similar to list, that is a sequence of comma-separated values defined in a pair of brackets. Tuple is immutable i.e. it cannot be modified (readonly).

```python
# start with a list, and then convert to tuple using python builtin function
nums = [1, 2, 3, 4, 5]
nums_tup = tuple(nums)

# display the data
print("nums: {}, type: {}, size: {}".format(nums, type(nums), len(nums)))
print("nums_tup: {}, type: {}, size: {}".format(nums_tup, type(nums_tup), len(nums_tup)))
```

```python
# define a tuple using a pair of brackets
days = ('monday', 'tuesday', 'wednesday', 'thursday', 'friday')
print("days: {}, type: {}, size: {}".format(days, type(days), len(days)))

# read a single value from tuple
print('first value in days: {}'.format(days[0]))
print('last value in days: {}'.format(days[-1]))

# tuple is immutable - cannot update value
# days[0] = 'sunday'  # TypeError

# but you can reassign tuple
days = days + days
print("days: {}, type: {}, size: {}".format(days, type(days), len(days)))

# initialization/reassignment
days = days * 2
print("days: {}, type: {}, size: {}".format(days, type(days), len(days)))

# count the occurences/frequencies
print("'monday' appeared {} times in days".format(days.count('monday')))

# check index of value in tuple
first_friday_index = days.index('friday')
print("the first 'friday' occured at position {}".format(first_friday_index))

# how to sort values in tuple?
# 1. convert to list
days_list = list(days)
print("\ndays_list: {}, type: {}, size: {}".format(days_list, type(days_list), len(days_list)))

# 2. sort the list
days_list.sort()
print("\ndays_list: {}, type: {}, size: {}".format(days_list, type(days_list), len(days_list)))

# 3. convert back to tuple
days = tuple(days_list)
print("\ndays: {}, type: {}, size: {}".format(days, type(days), len(days)))
```

```python
days = ('monday', 'tuesday', 'wednesday', 'thursday', 'friday')
days = days * 2
print("\ndays: {}, type: {}, size: {}".format(days, type(days), len(days)))

# can do slicing on tuple
days_sliced = days[ : 7]
print("\ndays_sliced: {}, type: {}, size: {}".format(days_sliced, type(days_sliced), len(days_sliced)))

# python builtin functions min() and max()
print("\nmin value: {}".format(min(days_sliced)))
print("max value: {}\n".format(max(days_sliced)))

# in operator - to check if value is existed
print('monday' in days_sliced)
print('sunday' in days_sliced)

# not operator
print('monday' not in days_sliced)
print('sunday' not in days_sliced)
```

```python
# quick check
# how to sort values in tuple

cats = ("Snow", "Stitch", "Chewy", "Luke", "Han")
cats_sorted = sorted(cats)
print(cats)
print(cats_sorted)
```

## 3.3 Collect and process data using dictionaries

Dictionary is an ordered collection of key-value pairs, defined within a pair of curly-brackets {}. Key can be anything ie. numbers, string, object etc. Key must be unique and point to one value. Dictionary is mutable.

```python
# define a dictionary
myusers = { 'carl' : 40, 'alan' : 40, 'bob' : 38, 'danny' : 39 }
print(myusers)

# check the type and length
print("type: {}".format(type(myusers)))
print("length: {}".format(len(myusers)))

# retrieve a value from dictionary - using the key
print('value for {} is {}'.format('carl', myusers['carl']))
print('value for {} is {}'.format('bob', myusers['bob']))

# add new pair
myusers['james'] = 41
print(myusers)

# try add new pair using existing key
myusers['james'] = 29
print(myusers)

# get value by key
# print('value for {} is {}'.format('bob', myusers['bobs']))  # KeyError

# use get() instead
result = myusers.get('bobs', 'Not found')
print(result)

result = myusers.get('bob', 'Not found')
print(result)

# create a shallow copy
myusers_copy = myusers.copy()

# remove pair from dictionary
del myusers_copy['bob']
print("myusers_copy: {}".format(myusers_copy))
print("myusers: {}".format(myusers))

# clear dictionary
myusers.clear()
print("myusers: {}".format(myusers))
```

Other operations on dictionary
- keys() : return all keys in dictionary
- values() : return all values in dictionary
- items() : return all pair of key-value in dictionary
- in operator : to check for existence

```python
myusers = { 'carl' : 40, 'alan' : 40, 'bob' : 38, 'danny' : 39 }
print(myusers)

# add new pair to dictionary
myusers['james'] = 37

# keys() example
thekeys = myusers.keys()
print(thekeys)

# try access the first key
# 1. convert dict_key to list using python builtin function list()
keylist = list(thekeys)
# 2. use index to access individual key
print("first key: {}".format(keylist[0]))

# check if key is existed, if yes then do nothing, else add new key-value pair
if 'james' not in keylist :
    myusers['james'] = 27
print(myusers)
```

### Activity

1. Display value pointed to by the third key.

   ```python
   myusers = { 'carl' : 40, 'alan' : 40, 'bob' : 38, 'danny' : 39 }
   ```

2. Find the key for value '99'

   ```python
   myresults = { 'Java' : 100, 'Python' : 99, 'Perl' : 98, 'PHP' : 97 }
   ```

3. Write a program to do word counting.

   ```python
   sample_string = "To be or not to be"
   ```
## 3.4 Operate with strings
