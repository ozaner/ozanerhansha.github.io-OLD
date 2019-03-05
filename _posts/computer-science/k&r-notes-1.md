---
layout: post
title: Notes on K&R - Ch. 1
date: 2019-06-03
tags: computer-science programming
---
My notes on Kernighan and Ritchie's *The C Programming Language*. Chapter 1 - A Tutorial Introduction

## Section 1.1
#### Example Program - hello.c
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=00_hello.c"></script>
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=01_hello2.c"></script>

```
hello, world
```

<!--more-->

#### Regarding the separation of compiled source code
Consider two functions A, B and their composition with the following time complexities:
- $O(A)=n!$
- $O(B)=n!$
- $O(A\circ B)=n$

If your source code only ever ran AB then a perfect compiler would return code that is simpler to run than either A or B, as neither function needs to run in its most general, and thus most complex, form. But if these functions were compiled separately, the compiler couldn't know this and would have to package the functions in their full inefficient form. This would avoid having multiple copies of the same code (e.g. the standard library) but it must mean that some efficiency is lost right?

Does the preprocessor deal with this? Are all programs independent when they run? They must be... so then is this not an issue? If so do we have copies of code everywhere?

[Thought came up when reading Pg. 1 - Paragraph 5]

#### Common Escape Sequences
 - `\n` - newline
 - `\t` - tab
 - `\b` - backspace
 - `\"` - double quote
 - `\\` - backslash

#### Exercise 1-1 - Error Messages
Omit certain parts of code to see what errors appear.
<details>
<summary><b>Remove <code>{</code></b></summary>
  <script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=02_hello{.c"></script>
  <script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=03_hello{.c output"></script>
</details>

<details>
<summary><b>Remove <code>}</code></b></summary>
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=04_hello}.c"></script>
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=05_hello}.c output"></script>
</details>

<details>
<summary><b>Remove <code>;</code></b></summary>
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=06_hello-semicolon.c"></script>
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=07_hello-semicolon.c output"></script>
</details>

<details>
<summary><b>Remove <code>"</code></b></summary>
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=08_hello-quotation.c"></script>
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=09_hello-quotation.c output"></script>
</details>

<details>
<summary><b>Remove <code>)</code> from <code>main()</code></b></summary>
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=10_hello).c"></script>

<!-- <pre><code>
hello.c: In function 'main':
hello.c:5:10: warning: missing terminating " character
   printf("hello, world\n);
          ^
hello.c:5:10: error: missing terminating " character
   printf("hello, world\n);
          ^~~~~~~~~~~~~~~~~
hello.c:6:1: error: expected expression before '}' token
 }
 ^
hello.c:5:10: error: expected ';' before '}' token
   printf("hello, world\n);
          ^
          ;
 }
 ~
</code></pre> -->

<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=11_hello).c output"></script>
</details>

#### Exercise 1-2 - Escape Sequence
What is the output of `\c` where `c` is a non-escape sequence character? It's just that character, for example:
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=12_escape-seq.c"></script>
```
c
```

## Section 1.2
#### Example Program - fahr.c
An example program displaying basic arithmetic, looping, and output in C.
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=13_fahr.c"></script>

```
0       -17
20      -6
40      4
60      15
80      26
100     37
120     48
140     60
160     71
180     82
200     93
220     104
240     115
260     126
280     137
300     148
```

#### Variables
Variables must be declared before use. The basic data types include:
- `char` - character (i.e a single byte)
- `short` - a short integer (typically 2 bytes)
- `int` - an integer (typically 4 bytes)
- `long` - a long integer (typically 8 bytes)
- `float` - single-precision floating point (4 bytes)
- `double` - double-precision floating point (8 bytes)

#### Integer Division
The division of integer types returns a truncated integer. That is, given two variables $a$ and $b$ of integer type, the statement `a/b` returns $\left\lfloor \frac{a}{b}\right\rfloor$. Here's an example:

<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=14_integer-division.c"></script>

```
21
```

#### The `printf` Function
`printf` can take in either just a string as its first argument, or a string followed by a number of variables. These variables will then be filled into the string wherever the characters `%d` (for integer types) or `%f` (for floating points) appear in the string. Appending an integer after the % but before the letter will *pad out* the value with whitespace. And adding a `.n` will limit floating points to only $n$ places after the decimal. Here's an example of all of these uses:
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=15_printf.c"></script>
```
no variables
5 is an integer value
2.130 is a float value
two values spaced apart: -18  40.20
```

#### Single Statement Scopes
When using a structure like `if`, `while`, or `for`, if the code to be executed in that structure consists of only one statement, it is acceptable to omit the brackets. That is to say the following code snippets are equivalent:
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=16_single-bracket.c"></script>

<details>
<summary><h4 class="inline">Exercise 1-3 - Table Heading</h4></summary>
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=17_fahr-heading.c"></script>

<pre><code>
  F         C
---------------
  0      -17.8
 20       -6.7
 40        4.4
 60       15.6
 80       26.7
100       37.8
120       48.9
140       60.0
160       71.1
180       82.2
200       93.3
220      104.4
240      115.6
260      126.7
280      137.8
300      148.9
</code></pre>
</details>

<details>
<summary><h4 class="inline">Exercise 1-4 - Celsius to Fahrenheit</h4></summary>
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=18_fahr-inverse.c"></script>

<pre><code>
  0       32.0
 20       68.0
 40      104.0
 60      140.0
 80      176.0
100      212.0
120      248.0
140      284.0
160      320.0
180      356.0
200      392.0
220      428.0
240      464.0
260      500.0
280      536.0
300      572.0
</code></pre>
</details>

## Section 1.3
#### `if`, `while`, and `for`
These programmatic structures work as expected. Here are some examples:
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=19_prog-structs.c"></script>

```
1+1=2
*
**
***
****
*****
20      17      14      11      8       5       2
23 mod 3 = 2
```

<details>
<summary><h4 class="inline">Exercise 1-5 - Reverse Order</h4></summary>
This is the program from 300 to 0 degrees.
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=20_fahr-reverse.c"></script>

<pre><code>
300      148.9
280      137.8
260      126.7
240      115.6
220      104.4
200       93.3
180       82.2
160       71.1
140       60.0
120       48.9
100       37.8
 80       26.7
 60       15.6
 40        4.4
 20       -6.7
  0      -17.8
</code></pre>
</details>

## Section 1.4
#### Symbolic Constants
Instead of declaring a variable at the top of a program and treating it as a 'constant', we can instead define true constants in the form of **symbolic constants**. These are essentially macros defined (usually) at the top of a program. They replace all occurrences of themselves in the source code with whatever they represent, except when the name is imbedded in a string or another name (i.e. *bob* wont replace *bob*by). By convention they are written in all CAPS.

#### Example Program - fahr2.c
Taking into account the above features of C, namely for loops, symbolic constants, output formatting, and floating point casting, we can now write a more concise version of the `fahr.c` program like so:
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=21_fahr2.c"></script>

```
  0      -17.8
 20       -6.7
 40        4.4
 60       15.6
 80       26.7
100       37.8
120       48.9
140       60.0
160       71.1
180       82.2
200       93.3
220      104.4
240      115.6
260      126.7
280      137.8
300      148.9
```

## Section 1.5
#### Text Streams
C handles the input/output of text via **text streams**. These are sequences of characters split up by newlines `\n`. The `getchar()` function returns the *next input character* from the input text stream (usually the keyboard) and the `putchar(c)` function prints the given character `c` into the output text stream (usually the screen).

#### `EOF`
When the `getChar()` method has reached the end of a file (i.e. the input text stream) it returns a value unique from any other character denoted `EOF`. This value is an `int` defined by `<stdio.h>` and for this reason, we must use `int`s rather than `char`s to comb through an input stream in order to make proper use the `EOF` constant:
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=22_copystream.c"></script>

*Note that in the code sample above I redefined `EOF` to be `\n`. This is because `EOF` isn't meant to be written in the console where, you know, all these programs are being tested...*

```
> i am typing some text then pressing enter
i am typing some text then pressing enter
```

#### Assignment Return Value
In C, an assignment statement itself returns the value assigned. So the program above could be equivalently restated as:
<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=23_copystream2.c"></script>

<details>
<summary><h4 class="inline">Exercise 1-6 - Boolean Values</h4></summary>
The expression <code>getchar() != EOF</code> will always either evaluate to <code>1</code> or <code>0</code>. That is the behavior of the <code>!=</code> operator.
</details>

<details>
<summary><h4 class="inline">Exercise 1-7 - Value of <code>EOF</code></h4></summary>
<code>EOF</code> is a symbolic constant defined in <code>stdio.h</code>. It signifies that the end of a file has been reached. It's true value is some negative integer, usually implemented in compilers as <code>-1</code>.
</details>


#### Increment Operators
There are 4 increment operators:
|   | pre- | -post |
|---|------|-------|
| **+1** | ++x  | x++ |
| **-1** | --x  | x-- |

The `++` ones increment the value of by 1. They are equivalent to `x = x + 1`. The same is true for the `--` operators (i.e. `x = x - 1`). The technical part is whether the parity symbols are prepended or appended.

Prefixes mean the expression `++x` will equal $x+1$, that is the variable is updated *before* the expression returns a value. Post fixes mean the expression `x++` will equal $x$, that is the expression returns the value of the variable *then* updates it.

We can use the increment operator to easily count the number of characters in a file (or keyboard input):

<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=26_countchar.c"></script>

#### Null Statement
Making use of the for loop, we can also phrase the character counting program like so:

<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=27_countchar2.c"></script>

You'll notice that directly proceeding the `for` loop is a semicolon `;`. On its own, this is called the **null statement** and is added as C requires that `for` loops have a body. We could have written it on a separate line but having right after the `for` looks better.

<details>
<summary><h4 class="inline">Exercise 1-8 - Count Whitespace</code></h4></summary> The following is a program that counts the number of spaces, tabs and newlines in a file.

<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=28_countwhitespace.c"></script>
</details>

<details>
<summary><h4 class="inline">Exercise 1-9 - Remove Extra Whitespace</code></h4></summary> The following is a program removes extra spaces between words.

<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=29_removeextraspace.c"></script>
</details>

<details>
<summary><h4 class="inline">Exercise 1-10 - Remove Extra Whitespace</code></h4></summary> The following is a program replaces tabs with "\t", backspaces with "\b", and backslashes with "\\".

<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=30_visiblewhitespace.c"></script>
</details>

#### Word Counting
Putting together everything from this section, we can recreate a barebones version of the UNIX <code>wc</code> program that counts the number of words in a file:

<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=31_wc.c"></script>
</details>

<details>
<summary><h4 class="inline">Exercise 1-11 - Testing <code>wc</code> Whitespace</code></h4></summary> Effectively testing a program like <code>wc</code> means giving it many edge cases. Words that are separated by two spaces? Words separated by a combination of tabs, spaces, and newlines? An empty file? A file of only white space? And so on. If it passes those tests you can be reasonably sure that it works (at least for whatever situations you could think up).
</details>

<details>
<summary><h4 class="inline">Exercise 1-12 - 1 Word Per Line</code></h4></summary> The following is a program replaces tabs with "\t", backspaces with "\b", and backslashes with "\\".

<script src="https://gist.github.com/ozanerhansha/7711f26d4809a57ce7eeab2402e3f94c.js?file=32_oneperline.c"></script>
</details>