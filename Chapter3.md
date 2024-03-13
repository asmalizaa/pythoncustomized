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

## Activity

Given a list of employees, write a program to loop and extract data for each employee and display the output in a tabular/columns as below.

```
employees = ["1602:Albert:Lukas:Montgomery:Legal",
             "1602:Albert:Lukas:Montgomery:Legal",
             "1602:Albert:Lukas:Montgomery:Legal",
             "1601:Albert:Lukas:Montgomery:Legal",
             "3702:Albert:Lukas:Montgomery:Legal",
             "4730:Nadelle::Landale:Warehousing"]
```

Expected output.

```
ID    First                Middle               Last                 Department
--------------------------------------------------------------------------------
1602  Albert               Lukas                Montgomery           Legal
1602  Albert               Lukas                Montgomery           Legal
1602  Albert               Lukas                Montgomery           Legal
1601  Albert               Lukas                Montgomery           Legal
3702  Albert               Lukas                Montgomery           Legal
4730  Nadelle                                   Landale              Warehousing
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

```python
x = "Hello, World"

# extract the first character in x
print(x[0])
print(x[-1])    # the last character 
print(x[-3])
print(x[3])

# slicing - extract a subset of string
# syntax: strvarname[start_index:stop_index]
print(x[1:7])
print(x[:-1])
```

```python
# get the size/length of string including the spaces and special characters (\n, \t, etc)
# python builtin function len()
x = "Goodbye\n"
print(x)
print(x)

size = len(x)
print("size : {}".format(size))

x = "Goodbye"
size = len(x)
print("size : {}".format(size))
```

```python
# concatenate string values
x = "Hello " + "World"
print(x)

name = "John"
age = 20

# if non-string, then convert to string first
# python builtin function str()
print("Student " + name + " is " + str(age) + " years old.")

# repetition
print(name * 10)
print("-" * 20)
```

```python
# define strings using single and double quotes
str1 = 'A string can be defined using single quotes'
str2 = "A string can also be defined using double quotes"

# to display single or double quotes within string, use escape character
str3 = 'This string contains \'single-quotes\' characters'
str4 = "This string contains 'single-quotes' characters"
str5 = "This string contains \"double-quotes\" characters"
str6 = 'This string contains "double-quotes" characters'

print(str1)
print(str2)
print(str3)
print(str4)
print(str5)
print(str6)
```

```python
# use triple single or double quotes to define strings
str7 = '''Hello everyone! 

    Good morning...'''
str8 = 'Hello everyone!\n\n\tGood morning...'

print(str7)
print(str8)

str9 = """
Dear John,
    How are you doing? Hope to catch up soon.

    Sarah.
"""
str10 = "Dear John,\n\tHow are you doing? Hope to catch up soon.\n\n\tSarah."

print(str9)
print(str10)
```

### String Builtin Functions

- format() : format the string output
- lower() : convert string to lowercase
- upper() : convert everything to uppercase
- replace() : characters replacement
- find() : search from LHS (start)
- rfind() : search from RHS (end)
- strip() : remove trailing whitespaces from both LHS and RHS
- rstrip() : remove trailing whitespaces from RHS
- lstrip() : remove trailing whitespaces from LHS
- ljust() : left-justified (left-aligned)
- rjust() : right-justified (right-aligned)
- split() : tokenize string values, return an array of words
- join() : combine all string values, return a single string

```python
text = "The cat in the hat"

# split
items = text.split()

# use format to display results
print("text before split: {}".format(text))
print("text after split: {}".format(items))

# display individual token/item 
print("first item: {}".format(items[0]))
print("second item: {}".format(items[1]))
print("last item: {}".format(items[-1]))

# use len() to get the number of items
size = len(items)
print("there are {} items".format(size))

# join the items (token) by + character (delimiter)
result = '+'.join(items)
print("result after join: {}".format(result))

result = '-'.join([items[1], items[4]])
print("result after join: {}".format(result))
```

```python
text = "The cat in the hat"

# split
items = text.split()

# use format to display results
print("text before split: {}".format(text))
print("text after split: {}".format(items))

# display individual token/item 
print("first item: {}".format(items[0]))
print("second item: {}".format(items[1]))
print("last item: {}".format(items[-1]))

# use len() to get the number of items
size = len(items)
print("there are {} items".format(size))

# join the items (token) by + character (delimiter)
result = '+'.join(items)
print("result after join: {}".format(result))

result = '-'.join([items[1], items[4]])
print("result after join: {}".format(result))
```

```python
# whitespaces
text = "     The cat in the hat     "

print('|{}|'.format(text))
print('|{}|'.format(text.strip()))
print('|{}|'.format(text.lstrip()))
print('|{}|'.format(text.rstrip()))
```

```python
# special characters
text = "\t\tThe cat in the hat\t\n\n"

print('|{}|'.format(text))
print('|{}|'.format(text.strip()))
print('|{}|'.format(text.lstrip()))
print('|{}|'.format(text.rstrip()))
```

```python
x = "Mississippi"

# index, rindex
print(x.index('ss'))    # first ss
print(x.index('ss', 4)) # second ss
print(x.rindex('ss'))   # second ss

# find, rfind
print(x.find('ss'))
print(x.rfind('ss'))
print(x.find('ss', 4))
```

```python
x = "Mississippi"

# count
print("there are {} 'ss' in x".format(x.count('ss')))

# startswith, endswith
print("x starts with 'Miss': {}".format(x.startswith('Miss')))
print("x ends with 'pi': {}".format(x.endswith('pi')))
```

```python
# replace: this will return a new modified string
x = "Mississippi"

print(x.replace('ss', '+++'))
print(x)    # string is immutable, cannot be modified
```

```python
x = "Mississippi"
print("x before: {}".format(x))

# python builtin function list() - convert to list of values (characters)
xlist = list(x)
print("xlist: {}".format(xlist))
print("x after: {}".format(x))

# slicing
xlist[6:] = []  # remove all values in list starting index 6
print("xlist after slicing: {}".format(xlist))

# convert it back to string x
x = "".join(xlist)
print("x after: {}".format(x))
```

### String Formatting

```python
print("{0} is the {1} of {2}".format("Ambrosia", "food", "the gods"))
print("{1} is the {2} of {0}".format("Ambrosia", "food", "the gods"))
print("{} is the {} of {}\n".format("Ambrosia", "food", "the gods")) # same as first line

print("{{Ambrosia}} is the {0} of {1}\n".format("food", "the gods"))

# named parameters
print("{food} is the food of {user}\n".format(food="Ambrosia", user="the gods"))

# named parameters with list of values
print("{food} is the food of {user[0]}".format(food="Ambrosia", user=["the gods", "men", "others"]))
print("{food} is the food of {user[1]}".format(food="Ambrosia", user=["the gods", "men", "others"]))
print("{food} is the food of {user[2]}".format(food="Ambrosia", user=["the gods", "men", "others"]))
```

```python
# specify the placeholder's width
print("{0:10} is the food of gods".format('Ambrosia'))
print("{0:{1}} is the food of gods".format('Ambrosia', 10)) # pass width as parameter

# use named parameters
print("{food:{width}} is the food of gods".format(food='Ambrosia', width=10))

print("{0:>10} is the food of gods".format('Ambrosia')) # right-aligned

# fill empty spaces with &, right-aligned
print("{0:&>10} is the food of gods".format('Ambrosia'))
```

### Formatting Strings with %

Reference: (https://stackabuse.com/python-string-interpolation-with-the-percent-operator/)

```python
print("%s is the %s of %s" % ("Ambrosia", "food", "the gods"))

# you can also pass a list as parameter
x  = [1, 2, "three"]
print("The %s contains: %s" % ("x", x))
print("The first item in %s is %s" % ('x', x[0]))
```

```python
# using formatting sequences
print("pi value is %f" % 3.14149)

# 2 decimal points
print("pi value is %.2f" % 3.14149)

# width of placeholder
print("pi value is <%6.2f>" % 3.14149)

# left-aligned
print("pi value is <%-6.2f>" % 3.14149)
```

```python
# use dictionary to pass named parameters
num_dict = { 'e' : 2.718, 'pi' : 3.14159 }

print("%(pi).2f - %(pi).4f - %(e).2f - %(e).4f" % num_dict)
```

## Activity

Given list of employees, write a program to extract employee details and display the output as a table.

```python
employees = ["1080:Priscillia:Forbes:Shepard:Cleaning Services",
             "4382:Devan::Fielder:Public Relations",
             "6285:Grey::Collyer:Public Relations",
             "6201:Kierah::Battaile:Catering",
             "3702:Albert:Lukas:Montgomery:Legal",
             "4730:Nadelle::Landale:Warehousing"]
```

This time, add additional feature to allow user to sort the records.
