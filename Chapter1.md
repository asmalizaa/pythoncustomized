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

## Understand fundamental terms and definitions

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

## Understand python's logic and structure

Reference: (https://www.baeldung.com/cs/lexicon-vs-syntax-vs-semantics)

As for a natural language, programming languages use a set of words considered valid. Moreover, a programming language specifies rules of how to dispose of these words in a source code. In such a way, programming languages must be able to judge if the written code represents valid and logical statements.

### Lexis, Syntax and Semantics

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

## Introduce literals and variables into code and use different numeral systems

## Choose operators and data types adequate to the problem

## Perform input/output console operations
