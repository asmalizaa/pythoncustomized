# Computer Programming and Python

Python has become one of the most popular programming languages in the world in recent years. It's used in everything from machine learning to building websites and software testing. It can be used by developers and non-developers alike.

Python is a computer programming language often used to build websites and software, automate tasks, and conduct data analysis. Python is a general-purpose language, meaning it can be used to create a variety of different programs and isn’t specialized for any specific problems. This versatility, along with its beginner-friendliness, has made it one of the most-used programming languages today.

Stack Overflow's 2022 Developer Survey revealed that Python is the fourth most popular programming language, with respondents saying that they use Python almost 50 percent of the time in their development work. Survey results also showed that Python is tied with Rust as the most-wanted technology, with 18% percent of developers who aren't using it already saying that they are interested in learning Python.

### What is Python used for?

Python is commonly used for developing websites and software, task automation, data analysis, and data visualization. Since it’s relatively easy to learn, Python has been adopted by many non-programmers such as accountants and scientists, for a variety of everyday tasks, like organizing finances.

"Writing programs is a very creative and rewarding activity,” says University of Michigan and Coursera instructor Charles R Severance in his book Python for Everybody. “You can write programs for many reasons, ranging from making your living to solving a difficult data analysis problem to having fun to helping someone else solve a problem."

What can you do with python? Some things include:
- Data analysis and machine learning
- Web development
- Automation or scripting
- Software testing and prototyping
- Everyday tasks

## 1.1 Understand fundamental terms and definitions

Reference : (https://www.geeksforgeeks.org/difference-between-compiler-and-interpreter/)

The Compiler and Interpreter, both have similar works to perform. Interpreters and Compilers convert the Source Code (HLL) to Machine Code (understandable by Computer). In general, computer programs exist in High-Level Language that a human being can easily understand. But computers cannot understand the same high-level language, so for computers, we have to convert them into machine language and make them readable for computers. In this article, we are going to see the differences between them.

### Compiler

The Compiler is a translator which takes input i.e., High-Level Language, and produces an output of low-level language i.e. machine or assembly language. The work of a Compiler is to transform the codes written in the programming language into machine code (format of 0s and 1s) so that computers can understand.

- A compiler is more intelligent than an assembler it checks all kinds of limits, ranges, errors, etc.
- But its program run time is more and occupies a larger part of memory. It has a slow speed because a compiler goes through the entire program and then translates the entire program into machine codes.

#### Roles of a Compiler

For Converting the code written in a high-level language into machine-level language so that computers can easily understand, we use a compiler. Converts basically convert high-level language to intermediate assembly language by a compiler and then assembled into machine code by an assembler.

![image](https://github.com/asmalizaa/pythoncustomized/assets/23090837/608160c0-e851-45b0-8b85-8d5b82e2c740)

#### Advantages of Compiler

- Compiled code runs faster in comparison to Interpreted code.
- Compilers help in improving the security of Applications.
- As Compilers give Debugging tools, which help in fixing errors easily.

#### Disadvantages of Compiler

- The compiler can catch only syntax errors and some semantic errors.
- Compilation can take more time in the case of bulky code.

### Interpreter

An Interpreter is a program that translates a programming language into a comprehensible language. The interpreter converts high-level language to an intermediate language. It contains pre-compiled code, source code, etc.

- It translates only one statement of the program at a time.
- Interpreters, more often than not are smaller than compilers.

#### Role of an Interpreter

The simple role of an interpreter is to translate the material into a target language. An Interpreter works line by line on a code. It also converts high-level language to machine language.

![image](https://github.com/asmalizaa/pythoncustomized/assets/23090837/0542ea02-9406-4f98-b9f2-56d68ab18655)

#### Advantages of Interpreter

- Programs written in an Interpreted language are easier to debug.
- Interpreters allow the management of memory automatically, which reduces memory error risks.
- Interpreted Language is more flexible than a Compiled language.

#### Disadvantages of Interpreter

- The interpreter can run only the corresponding Interpreted program.
- Interpreted code runs slower in comparison to Compiled code.

### Difference Between Compiler and Interpreter

<table>
  <tr><th>Compiler</th><th>Interpreter</th></tr>
  <tr>
    <td>Steps of Programming:

- Program Creation.
- Analysis of language by the compiler and throws errors in case of any incorrect statement.
- In case of no error, the Compiler converts the source code to Machine Code.
- Linking of various code files into a runnable program.
- Finally runs a Program.</td>
 <td>Steps of Programming:

- Program Creation.
- Linking of files or generation of Machine Code is not required by Interpreter.
- Execution of source statements one by one.
</td></tr>
<tr><td>The compiler saves the Machine Language in form of Machine Code on disks.</td><td>The Interpreter does not save the Machine Language.</td></tr>
<tr><td>Compiled codes run faster than Interpreter.</td><td>Interpreted codes run slower than Compiler.</td></tr>
<tr><td>Linking-Loading Model is the basic working model of the Compiler.</td><td>The Interpretation Model is the basic working model of the Interpreter.</td></tr>
<tr><td>The compiler generates an output in the form of (.exe).</td><td>The interpreter does not generate any output.</td></tr>
<tr><td>Any change in the source program after the compilation requires recompiling the entire code.</td><td>Any change in the source program during the translation does not require retranslation of the entire code.</td></tr>
<tr><td>Errors are displayed in Compiler after Compiling together at the current time.</td><td>Errors are displayed in every single line.</td></tr>
<tr><td>The compiler can see code upfront which helps in running the code faster because of performing Optimization.</td><td>The Interpreter works by line working of Code, that’s why Optimization is a little slower compared to Compilers.</td></tr>
<tr><td>It does not require source code for later execution.</td><td>It requires source code for later execution.</td></tr>
<tr><td>Execution of the program takes place only after the whole program is compiled.</td><td>Execution of the program happens after every line is checked or evaluated.</td></tr>
<tr><td>Compilers more often take a large amount of time for analyzing the source code.</td><td>In comparison, Interpreters take less time for analyzing the source code.</td></tr>
<tr><td>CPU utilization is more in the case of a Compiler.</td><td>CPU utilization is less in the case of a Interpreter.</td></tr>
<tr><td>The use of Compilers mostly happens in Production Environment.</td><td>The use of Interpreters is mostly in Programming and Development Environments.</td></tr>
<tr><td>Object code is permanently saved for future use.</td><td>No object code is saved for future use.</td></tr>
<tr><td>C, C++, C#, etc are programming languages that are compiler-based.</td><td>Python, Ruby, Perl, SNOBOL, MATLAB, etc are programming languages that are interpreter-based.</td></tr>
</table>

## Activity: Hello World Program

```python
# display "Hello World!" to output
print("Hello World!")
print("Hello World!")
print("Hello World!")
```

```python
# this program declares a variable x that store a number
x = 7
print(x + 10)   # display 17
```

```python
x = 10

# check the data type using builtin function type()
print(type(x))  # output: <class 'int'>

# use concatenator + to append and 
# use builtin function str() to convert int to str
print("Number x is " + str(x))  # output: Number x is 10
```

```python
# store string value 10 to x then check the type
x = "10"
print(type(x))  # output: <class 'str'>

# convert string x to integer
x = int(x)
print(type(x))  # output: <class 'int'>
```

```python
# set the 'end' property of print function
print("hello", end="--")    # output: hello--world
```

### Lexis, Syntax and Semantics

Reference: (https://www.baeldung.com/cs/lexicon-vs-syntax-vs-semantics)

As for a natural language, programming languages use a set of words considered valid. Moreover, a programming language specifies rules of how to dispose of these words in a source code. In such a way, programming languages must be able to judge if the written code represents valid and logical statements.

A programming language lexicon, syntax, and semantics provide information for programmers on how to express and correctly execute multiple operations in their source codes.

**Lexis**

Lexis is from the Greek word lexis which means 'word'. Lexis is a term in the English language that refers to the words of a language. A family of other words are related to this base word:

- Lexicology is the study of lexis (or lexical items).
- Lexicon is a collection of words, a bit like a dictionary.
- Lexicalisation is the process of adding or changing words in a lexicon.
- A lexeme is a basic unit of word meaning, or the “root word”. For example, eats, ate, eaten, and eating come from one lexeme, eat.

In short, a language lexicon includes the complete set of available terms. Practically, we can see the lexicon as a dictionary. This dictionary contains every word used and recognized by the language speakers.

**Syntax**

A language syntax, in turn, represents the possible ways that we can put words from the lexicon together. So, talking about syntax is talking about well-defined rules to create sentences in a given language.

- It refers to the rules and regulations for writing any statement in a programming language like C/C++.
- It does not have to do anything with the meaning of the statement.
- A statement is syntactically valid if it follows all the rules.
- It is related to the grammar and structure of the language.

**Semantics**

The semantics of a language, in turn, indicates if a sentence has a concrete representation for those who hear or read it.

- It refers to the meaning associated with the statement in a programming language.
- It is all about the meaning of the statement which interprets the program easily.
- Errors are handled at runtime.

### The Organization of Programming Languages

Similar to natural languages, learning a programming language includes understanding its formal structures and organization.

So, summarily, the lexicon of a programming language presents the reserved list of words adopted by it. These words, in turn, are what we use to code commands and create data structures.

The words written by a programmer are known as lexemes. Lexemes, however, are matched with a predefined pattern and thus identified as a token of the programming language (we call this lexical analysis). Let’s see a simple pseudocode example:

![image](https://github.com/asmalizaa/pythoncustomized/assets/23090837/4f7c40b7-6939-4d7a-a02e-0d2bf44b4f52)

**Furthermore, we also have a specific lexicon related to a particular program (source code).** So, besides the standard reserved words list from the programming language, the program lexicon include other words exclusively defined for it, such as variable and function names.

However, executing commands, creating data structures, and using generic coding resources typically demand not only one word but a bunch of them. **In such a way, the rules to correctly use the available words to achieve coding objectives form what we know as the programming language syntax.**

If a programming statement is lexically and semantically valid, we can compile/interpret it. But, if it is not semantically valid, we can have unexpected or wrong behaviors during the program execution.

In practice, the syntax analysis process a derivation tree with the tokens identified in the lexical analysis. Let’s see an example:

![image](https://github.com/asmalizaa/pythoncustomized/assets/23090837/7cd800e2-4275-45dc-bee1-bdb60f88b9e7)

**Semantics in a programming language indicates what practically does or not make sense in the context of a given source code.**

Some usual semantic errors are, for example, using an uninitialized variable in arithmetic expressions or adding an operation immediately after a return operation in a function.

It is important to note that the number and format of words and rules in the lexicon, syntax, and semantics can vary from one programming language to another. It depends on several technical aspects of these languages, such as being a language statically or dynamically typed.

## 1.2 Understand Python's logic and structure

Reference: (https://www.programmingonlinehelp.com/understand-pythons-logic-and-structure/)

Python, renowned for its readability and simplicity, captivates programmers with its logical structure. In this exploration, we’ll unravel the essence of Python’s logic and structure by dissecting keywords, understanding instructions, appreciating the significance of indentation, and acknowledging the role of comments.

1. **Keywords: Unlocking Python’s Vocabulary**

   - **Definition**: Keywords are reserved words in Python with predefined meanings. They form the backbone of Python’s syntax, shaping the logic and flow of the code.
   - **Examples**: "if," "else," "for," "while," and "def."
   - **Significance**: Keywords introduce structure and specificity to the code, guiding the interpreter on how to execute instructions.
  
2. **Instructions: Building the Script’s Narrative**

   - **Definition**: Instructions in Python are individual lines or blocks of code that carry out specific operations. They dictate the sequence of actions performed by the program.
   - **Examples**: Variable assignments, function calls, conditional statements, and loops.
   - **Significance**: Instructions bring the script to life, executing tasks and achieving the desired outcomes based on the defined logic.

3. **Indentation: The Silent Architect of Python Code**

   - **Definition**: Indentation refers to the consistent use of whitespace (usually spaces or tabs) to structure code blocks. Unlike many programming languages that use braces, Python relies on indentation for readability and scope definition.
   - **Examples**: Indentation is crucial in blocks like loops, conditionals, and function definitions.
   - **Significance**: Indentation not only enforces clean and readable code but also determines the scope of statements, eliminating the need for explicit block delimiters.
  
4. **Comments: Adding Context to the Code**

   - **Definition**: Comments in Python are annotations within the code that are ignored during execution. They provide explanatory notes, making the code more understandable for developers.
   - **Examples**: Single-line comments using “#” and multi-line comments enclosed in triple quotes.
   - **Significance**: Comments enhance code comprehension, serving as documentation for future reference or collaboration among developers.

### Incorporating Logic and Structure in Python Code

- **Guided by Keywords**: Utilize keywords to structure your code logically. "if" and "else" keywords guide the flow based on conditions, while "for" and "while" keywords control iteration.
- **Following Instruction Flow**: Develop a clear sequence of instructions. Assign variables, call functions, and implement conditional statements and loops strategically to achieve the desired logic.
- **Maintaining Indentation Precision**: Embrace consistent indentation to ensure clarity and accuracy. Let indentation define code blocks, aiding both human readability and correct execution.
- **Clarifying with Comments**: Use comments judiciously to provide insights into the rationale behind code decisions. Explain complex sections or flag potential improvements to foster collaboration.

## 1.3 Introduce literals and variables into code and use different numeral systems

Reference: (https://www.programmingonlinehelp.com/introduce-literals-and-variables-into-code-and-use-different-numeral-systems/)

When delving into code, incorporating literals and variables is essential. Understanding different numeral systems, including binary and hexadecimal, is crucial. 

### Booleans: The Binary Stars of Logic

- Meet Booleans, the binary stars of logic in Python.
- Named after the brilliant mathematician George Boole, these truth values, "True" or "False," play a pivotal role in decision-making within your code.
- Think of them as the guiding lights steering the flow of execution based on conditions.
- In the cosmic realm of an "if" statement, your code block springs to life if the condition is "True"; otherwise, it gracefully glides into the "else" block.
- Booleans are the unsung heroes behind logical operations, empowering you to craft dynamic and responsive programs that adapt seamlessly to changing scenarios.

```python
# define a boolean variable
x = True
print(x, type(x))   # output: True <class 'bool'>

# assign string value 'True' to x
x = "True"
print(x, type(x))   # output: True <class 'str'>
```

### Integers and Floating-Point Numbers: The Building Blocks of Mathematics

- Now, let’s explore the numerical wonders of Python – integers and floating-point numbers.
- Integers, those trusty whole numbers without decimals, provide a precise way to quantify quantities in your code.
- On the flip side, floating-point numbers bring flexibility to the table, gracefully accommodating decimals and even scientific notation.
- Whether you’re tallying apples or navigating complex mathematical models, Python’s knack for handling integers and floating-point numbers empowers you to tackle a wide array of challenges with numerical finesse.

```python
# define variables to store integer and floating-point number
number = 10
print(number, type(number)) # output: 10 <class 'int'>

price = 10.99
print(price, type(price))   # output: 10.99 <class 'float'>

# convert/cast float to int
result = int(price)
print(result, type(result)) # output: 10 <class 'int'>

# cast int to float
result = float(result)
print(result, type(result)) # output: 10.0 <class 'float'>
```

### Scientific Notation: Bridging the Macro and Microcosms

- Enter the realm of scientific notation – a sleek feature in Python that effortlessly bridges the macro and microcosms of numerical representation.
- Imagine expressing vast or minuscule numbers with ease, condensing those seemingly endless zeros into a sleek and manageable format.
- This capability proves to be a game-changer in scientific and engineering applications, where precision and readability take center stage.
- Python’s embrace of scientific notation not only elevates the clarity of your code but also simplifies the communication of complex numerical values, making your computations both accessible and comprehensible.

```python
# scientific notation
value = "{:e}".format(0.000001234)
print(value)    # output: 1.234000e-06
print(value, type(value))   # output: 1.234000e-06 <class 'str'>
```

### Strings: The Poetic Verses of Code

- Strings, the eloquent storytellers in Python’s repertoire, are sequences of characters enclosed in quotes.
- Whether you’re dealing with text, manipulating user inputs, or constructing intricate narratives within your code, strings provide the canvas for expression.
- Python’s versatility with strings extends to various operations, such as concatenation, slicing, and formatting, making them a cornerstone for representing textual information in a dynamic and engaging manner.

```python
# format string output
firstname = "John"
lastname = "Smith"

# output: John Smith
print(firstname, lastname)  

# use string format, all these will output: John Smith
print("{} {}".format(firstname, lastname))      
print("{0} {1}".format(firstname, lastname))
print("{1} {0}".format(firstname, lastname))
print("{} {}".format(123, 456))     # output: 123 456
```

```python
name = "John Smith"
age = 20

# all of these will output Name: John Smith Age: 20
print("Name: " + name + " Age: " + str(age))
print("Name:", name, "Age:", age)
print("Name: {} Age: {}".format(name, age))
print("Name: %s Age: %s" % (name, age))
```

```python
# string in python can be defined using both single and double quotes
first = 'hello world'
second = "hello world"

print(first, type(first))   # output: hello world <class 'str'>
print(second, type(second)) # output: hello world <class 'str'>

message = 'John says "Hello World!"'
print(message)  # output: John says "Hello World!"

message = "John says 'Hello World!'"
print(message)  # output: John says 'Hello World!'
```

```python
# tripple single-quotes and double-quotes
msg = '''
Dear John, 

    How are you?

Jane
'''
print(msg)

John = "test"

msg = """
Dear John, 

    How are you?

Jane
"""
print(msg)
```

### Numeral Systems: Unraveling the Digits

- Python’s support for multiple numeral systems opens a doorway to a diverse world of representation.
- The binary system, using '0b' as a prefix, deals with zeros and ones, ideal for low-level computations and understanding computer architecture.
- Octal, with the '0o' prefix, is a base-8 system that occasionally surfaces in specific contexts.
- The familiar decimal system, our everyday numbering system, provides the standard representation. Lastly, the hexadecimal system, marked by '0x,' introduces letters A-F to represent values beyond 9.
- Understanding these numeral systems enriches a programmer’s toolkit, allowing them to communicate effectively in different mathematical languages.

```python
# define a variable age and assign value 17
age = 17

# print age to output
print(age)

# numbers
print(5 + 2 - 3 * 2)
print(5 / 2)	# floating 2.5
print(5 / 2.0)	# also floating 2.5
print(5 // 2)	# integer result 2
print(3000000000)	# a large number
print(3000000000 * 3)
print(3000000000 * 3.0)
print(2.0e-8)	# scientific
```

### Variables: Containers for the Code Treasure

- As we transition to the realm of data storage, variables emerge as the reliable containers for storing and manipulating data values.
- By assigning values to variables, programmers create placeholders that can be referenced and modified throughout the code.
- Variables empower code to be dynamic, allowing for efficient data management and manipulation.
- The flexibility they provide is a testament to Python’s user-friendly approach, enabling programmers to create expressive and adaptable scripts.

```python
# define a variable name and assign value "John"
name = "John"

# display name to output
print(name)

# define a variable age and assign value 17
age = 17

# print age to output
print(age)

# Hello John, you are 17 years old
print("Hello " + name + ", you are " + str(age) + " years old")
```

### Naming Conventions: The Art of Clarity

- In the symphony of Python code, naming conventions play the role of musical notes, contributing to the clarity and readability of the composition.
- Following PEP-8 recommendations, Python’s style guide, ensures a harmonious and consistent coding experience.
- Descriptive and concise variable names enhance code comprehension, acting as signposts for fellow programmers navigating the codebase.
- Best practices include using lowercase with underscores for variable names, avoiding single-letter names (except for iterators), and maintaining a consistent style throughout the code.
- Adhering to naming conventions transforms code into a readable and collaborative piece of art

### Implementing PEP-8 Recommendations: The Aesthetics of Code

- The PEP-8 guide, akin to an art curator for Python code, offers recommendations for maintaining a visually pleasing and consistent code style.
- Proper indentation, using 4 spaces per level, creates a readable structure that reflects the logic of the code.
- Limiting line lengths to 79 characters for code and 72 for docstrings prevents code from sprawling into an unreadable mess.
- Introducing whitespace judiciously and following import organization guidelines adds to the overall aesthetics.
- By aligning with PEP-8, programmers contribute to an elegant and collaborative codebase, where the visual appeal is as important as the functional brilliance.

## 1.4 Choose operators and data types adequate to the problem

### Python Data Types

In programming, data type is an important concept.

Variables can store data of different types, and different types can do different things.

Python has the following data types built-in by default, in these categories:

<table>
  <tr><th>Category</th><th>Built-in Data Types</th></tr>
  <tr><td>Text Type</td><td>str</td></tr>
  <tr><td>Numeric Types</td><td>int, float, complex</td></tr>
  <tr><td>Sequence Types</td><td>list, tuple, range</td></tr>
  <tr><td>Mapping Type</td><td>dict</td></tr>
  <tr><td>Set Types</td><td>set, frozenset</td></tr>
  <tr><td>Boolean Type</td><td>bool</td></tr>
  <tr><td>Binary Types</td><td>bytes, bytearray, memoryview</td></tr>
  <tr><td>None Type</td><td>NoneType</td></tr>
</table>

**Getting the Data Type**

You can get the data type of any object by using the type() function:

```python
x = 5
print(type(x))
```

**Setting the Data Type**

In Python, the data type is set when you assign a value to a variable:

```python
x = "Hello World"  # str
x = 20  # int
x = 20.5  # float
x = ["apple", "banana", "cherry"]  # list
```

**Setting the Specific Data Type**

If you want to specify the data type, you can use the following constructor functions:

```python
x = str("Hello World")
x = int(20)
x = float(20.5)
x = list(("apple", "banana", "cherry"))
```

### Python Operators

Operators are used to perform operations on variables and values.

In the example below, we use the + operator to add together two values:

```python
print(10 + 5)
```

Python divides the operators in the following groups:

- Arithmetic operators
- Assignment operators
- Comparison operators
- Logical operators
- Identity operators
- Membership operators
- Bitwise operators

**Python Arithmetic Operators**

Arithmetic operators are used with numeric values to perform common mathematical operations:

<table>
  <tr><th>Operator</th><th>Name</th><th>Example</th></tr>
  <tr><td>+</td><td>Addition</td><td>x + y</td></tr>
  <tr><td>-</td><td>Subtraction</td><td>x - y</td></tr>
  <tr><td>*</td><td>Multiplication</td><td>x * y</td></tr>
  <tr><td>/</td><td>Division</td><td>x / y</td></tr>
  <tr><td>%</td><td>Modulus</td><td>x % y</td></tr>
  <tr><td>**</td><td>Exponentiation</td><td>x ** y</td></tr>
  <tr><td>//</td><td>Floor Division</td><td>x // y</td></tr>
</table>

**Python Assignment Operators**

Assignment operators are used to assign values to variables:

<table>
  <tr><th>Operator</th><th>Example</th><th>Same As</th></tr>
  <tr><td>=</td><td>x = 5</td><td>x = 5</td></tr>
  <tr><td>+=</td><td>x += 3</td><td>x = x + 3</td></tr>
  <tr><td>-=</td><td>x -= 3</td><td>x = x - 3</td></tr>
  <tr><td>*=</td><td>x *= 3</td><td>x = x * 3</td></tr>
  <tr><td>/=</td><td>x /= 3</td><td>x = x / 3</td></tr>
  <tr><td>%=</td><td>x %= 3</td><td>x = x % 3</td></tr>
  <tr><td>//=</td><td>x //= 3</td><td>x = x // 3</td></tr>
  <tr><td>**=</td><td>x **= 3</td><td>x = x ** 3</td></tr>
  <tr><td>&=</td><td>x &= 3</td><td>x = x & 3</td></tr>
  <tr><td>|=</td><td>x |= 3</td><td>x = x | 3</td></tr>
  <tr><td>^=</td><td>x ^= 3</td><td>x = x ^ 3</td></tr>
  <tr><td>>>=</td><td>x >>= 3</td><td>x = x >> 3</td></tr>
  <tr><td><<=</td><td>x <<= 3</td><td>x = x << 3</td></tr>
</table>

**Python Comparison Operators**

Comparison operators are used to compare two values:

<table>
  <tr><th>Operator</th><th>Name</th><th>Example</th></tr>
  <tr><td>==</td><td>Equal</td><td>x == y</td></tr>
  <tr><td>!=</td><td>Not equal</td><td>x != y</td></tr>
  <tr><td>></td><td>Greater than</td><td>x > y</td></tr>
  <tr><td><</td><td>Less than</td><td>x < y</td></tr>
  <tr><td>>=</td><td>Greater than or equal to</td><td>x >= y</td></tr>
  <tr><td><=</td><td>Less than or equal to</td><td>x <= y</td></tr>
</table>

**Python Logical Operators**

Logical operators are used to combine conditional statements:

<table>
  <tr><th>Operator</th><th>Description</th><th>Example</th></tr>
  <tr><td>and</td><td>Returns True if both statements are true</td><td>x <5 and x < 10</td></tr>
  <tr><td>or</td><td>Returns True if one of the statements is true</td><td>x < 5 or x < 4</td></tr>
  <tr><td>not</td><td>Reverse the result, returns False if the result is true</td><td>not(x < 5 and x < 10)</td></tr>
</table>

**Python Membership Operators**

Membership operators are used to test if a sequence is presented in an object:

<table>
  <tr><th>Operator</th><th>Description</th><th>Example</th></tr>
  <tr><td>in</td><td>Returns True if a sequence with the specified value is present in the object</td><td>x in y</td></tr>
  <tr><td>not in</td><td>Returns True if a sequence with the specified value is not present in the object	</td><td>x not in y</td></tr>
</table>

**Python Bitwise Operators**

Bitwise operators are used to compare (binary) numbers:

<table>
  <tr><th>Operator</th><th>Name</th><th>Description<th>Example</th></tr>
  <tr><td>&</td><td>AND</td><td>Sets each bit to 1 if both bits are 1</td><td>x & y</td></tr>
  <tr><td>|</td><td>OR</td><td>Sets each bit to 1 if one of two bits is 1</td><td>x | y</td></tr>
  <tr><td>^</td><td>XOR</td><td>Sets each bit to 1 if only one of two bits is 1</td><td>x ^ y</td></tr>
  <tr><td>~</td><td>NOT</td><td>Inverts all the bits</td><td>~x</td></tr>
  <tr><td><<</td><td>Zero fill left shift</td><td>Shift left by pushing zeros in from the right and let the leftmost bits fall off</td><td>x << 2</td></tr>
  <tr><td>>></td><td>Signed right shift</td><td>Shift right by pushing copies of the leftmost bit in from the left, and let the rightmost bits fall off</td><td>x >> 2</td></tr>
</table>

**Operator Precedence**

Operator precedence describes the order in which operations are performed. 

```python
print((6 + 3) - (6 + 3))
print(100 + 5 * 3)
```

The precedence order is described in the table below, starting with the highest precedence at the top:

<table>
  <tr><th>Operator</th><th>Description</th></tr>
  <tr><td>()</td><td>Parentheses</td></tr>
  <tr><td>**</td><td>Exponentiation</td></tr>
  <tr><td>+x -x ~x</td><td>Unary plus, unary minus, and bitwise NOT</td></tr>
  <tr><td>* / // %</td><td>Multiplication, division, floor division, and modulus</td></tr>
  <tr><td>+ -</td><td>Addition and subtraction</td></tr>
  <tr><td><< >></td><td>Bitwise left and right shifts</td></tr>
  <tr><td>&</td><td>Bitwise AND</td></tr>
  <tr><td>^</td><td>Bitwise XOR</td></tr>
  <tr><td>|</td><td>Bitwise OR</td></tr>
  <tr><td>== != > >= < <= is is not in not in</td><td>Comparisons, identity, and membership operators	
</td></tr>
  <tr><td>not</td><td>Logical NOT</td></tr>
  <tr><td>and</td><td>Logical AND</td></tr>
  <tr><td>or</td><td>Logical OR</td></tr>
</table>

If two operators have the same precedence, the expression is evaluated from left to right.

```python
print(5 + 4 - 7 + 3)
```

## 1.5 Perform input/output console operations

### The print() and input() functions

Let’s explore how to perform input and output operations in Python.

**Reading Input From the Keyboard**

To obtain data from the user via the keyboard, you can use the built-in function input(). It allows the user to type in a line of input, which is then returned as a string. Here’s how it works:

```python
# Example 1: Basic input
user_input = input()
print("You entered:", user_input)

# Example 2: Input with a prompt
name = input("What is your name? ")
print("Hello,", name)

# Example 3: Converting input to a numeric type
number = int(input("Enter a number: "))
print("Your number plus 100 is:", number + 100)
```

Remember that input() always returns a string. If you need a numeric type (like an integer), you can convert the string using int(), float(), or complex().

**Displaying Output to the Console**

To output text to the console, use the print() function. You can display strings, variables, or any other data you want. Here are some examples:

```python
# Example 4: Basic output
print("Hello, world!")

# Example 5: Output with variables
name = "Alice"
age = 30
print(f"{name} is {age} years old.")

# Example 6: Formatting output
pi = 3.14159
print(f"Approximate value of pi: {pi:.2f}")
```

In the last example, we use an f-string to format the output with two decimal places for the value of pi.

### The sep= and end= keyword parameters

Reference: (https://www.studytonight.com/post/the-sep-and-end-parameters-in-python-print-statement)

The end parameter in Print is used to append any string at the end of the output of the print statement in python while the sep parameter is used to format the strings that need to be printed on the console and add a separator between strings.

**The end parameter**

The end parameter is used to append any string at the end of the output of the print statement in python.

By default, the print the method ends with a new line. This means there is no need to explicitly specify the parameter end as '\n'. Programmers with a background in C/C++ may find this interesting.

Let us look at how changing the value of the end parameter changes the contents of the print statement onscreen.

The below example demonstrates that passing '\n' or not specifying the end parameter both yield the same result. Execute 2 lines of code at a time to see the result.

```python
print("Studytonight",)
print("is awesome")

print("Studytonight", end= "\n")
print("is awesome")
```

On the other hand, passing the whitespace to the end parameter indicates that the end character has to be identified by whitespace and not a new line (which is the default).

```python
print("Studytonight", end=' ')
print("is awesome")
```

The below example shows that any value can be passed to the end parameter and based on the content in the print statement, the end value gets displayed.

```python
print("Hi", end=' Studytonight ')
print("you are awesome")
```

**The sep parameter**

Sometimes, we may wish to print multiple values in a Python program in a readable manner. This is when the argument sep comes to play. The arguments passed to the program can be separated by different values. The default value for sep is whitespace. The sep parameter is primarily used to format the strings that need to be printed on the console and add a separator between strings to be printed. This feature was newly introduced in Python 3 version.

The below example shows that passing the sep parameter as whitespace or not passing the sep at all doesn't make a difference. Execute every line of code to see the result.

```python
print("Study", "tonight")
print("Study", "tonight", sep = ' ')
```

The below example shows different values that are passed to the sep parameter.

```python
print("Study", "tonight", sep = '')
print("Study", "tonight", sep = ' & ')
```

The sep parameter, used in conjunction with the end parameter is generally used in production code to print data in a readable fashion.

```python
print("Studytonight","has","been","created","for", sep = " _ ", end=" _STUDENTS")
```

**The int() and float() function**

Reference: (https://medium.com/@onifadeay/understanding-pythons-int-and-float-functions-handling-numbers-and-strings-a04f724ee1d2)

Two essential functions that assist in this endeavor are int() and float().

- Converting Numbers to Integers

  The int() function in Python is primarily used to convert numerical values, such as integers and floats, to integers. It truncates any decimal portion, providing only the whole number. Here’s an example:

  ```python
  number = 7.9
  integer_number = int(number)
  print(integer_number) # Output: 7
  ```

  In this case, the float value 7.9 is converted to an integer, resulting in 7. The int() function is useful when you need to discard any decimal places and work solely with whole numbers.

- Converting Numbers to Floats

  Conversely, the float() function allows you to convert numerical values to floating-point numbers. This function is particularly handy when performing calculations that involve decimal values. Consider the following example:

  ```python
  number = 4
  float_number = float(number)
  print(float_number) # Output: 4.0
  ```

  In this example, the integer 4 is converted to a float, resulting in 4.0. This conversion ensures that the number retains its decimal precision, which is essential for accurate calculations involving fractions.

- Converting Strings to Integers or Floats

  Both int() and float() functions can also be used to convert strings representing numeric values into their corresponding data types. However, it is important to ensure that the string contains only valid numeric characters; otherwise, errors can occur. Consider the following examples:

  ```python
  number_str = "123"
  integer_number = int(number_str)
  print(integer_number) # Output: 123
  float_str = "3.14"
  float_number = float(float_str)
  print(float_number) # Output: 3.14
  ```

  In the above code snippets, the strings 123 and 3.14 are successfully converted to integers and floats, respectively. This functionality becomes invaluable when working with user inputs provided as strings and needing to perform numerical computations.

- The Decimal Number Pitfall

  While the int() function can convert strings to integers and the float() function can handle floats, it’s important to note that int() cannot directly convert a string representation of a decimal number. For instance, attempting to convert the string 3.5 to an integer will result in a `ValueError`. Instead, you should use the float() function to convert the string to a float data type.

  ```python
  decimal_str = "3.5"
  integer_number = int(decimal_str) # Raises ValueError
  float_number = float(decimal_str)
  print(float_number) # Output: 3.5
  ```

  In the above example, an attempt to use int() to convert the string 3.5 will raise a `ValueError` since the conversion from a decimal string to an integer is not valid. However, using float() successfully converts the string to a float, allowing for the accurate representation of the decimal value.
