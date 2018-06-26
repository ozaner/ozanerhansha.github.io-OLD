---
layout: post
title: On the Origin of "Hello, World!"
date: 2018-06-25
tags: computer-science
---
<!-- - [What is "Hello, World!"?](#what-is-hello-world)
- [History](#history)
  - [A Tutorial Introduction to the Language B](#a-tutorial-introduction-to-the-language-b)
  - [Programming in C: A Tutorial](#programming-in-c-a-tutorial)
  - [The C Programming Language](#the-c-programming-language)
  - [Side note on BCPL](#side-note-on-bcpl)
- [Examples](#examples) -->

## What is "Hello, World!"?
When learning to program for the first time, students are often instructed to write a program that outputs the string `"Hello, World!"` in order to test out their programming environment.

Over the years, introducing the topic of programming with this example has become a tradition amongst computer science teachers. As such, "Hello, World!" is often the first program most people write.

<!--more-->

## History
Why and how outputting the string "Hello, World!" became the quintessential beginner program is a matter of interest for both computer scientists and historians alike due to the prevalence of this practice amongst computer scientists today.

In summary, this program was created and first used by Professor Brian Kernighan when documenting both the B and C programming languages during his time at Bell Labs. Below I give the 3 instances in which it appears in his work.

### A Tutorial Introduction to the Language B
**B** is a programming language developed at Bell Labs around 1969 and is a simplified successor to **BCPL**. It was in 1972 that Kernighan was tasked with writing a manual for using B that was to be used internally at Bell Labs. This memorandum, [*A Tutorial Introduction to the Language B*](https://www.bell-labs.com/usr/dmr/www/bintro.html), is the first documented instance of "Hello, World!" in all of programming cannon.

The program appears in section *7 -- External Variables* in the following form to demonstrate the piecing together of several `char` variables:
~~~ b
main( ) {
  extrn a, b, c;
  putchar(a); putchar(b); putchar(c); putchar(’!*n’);
}

a ’hell’;
b ’o, w’;
c ’orld’;
~~~

It appears again in the next section *8 -- Functions* to demonstrate the composition of functions:
~~~ b
main( ) {
  extrn a,b,c,d;
  put2char(a,b) ;
  put2char(c,d) ;
}

put2char(x,y) {
  putchar(x);
  putchar(y);
}

a ’hell’; b ’o, w’; c ’orld’; d ’!*n’;
~~~

### Programming in C: A Tutorial
The next instance of "Hello, World!" appeared in another internal memorandum at Bell Labs titled [*Programming in C: A Tutorial*](https://www.bell-labs.com/usr/dmr/www/ctut.pdf). The document was again authored by Prof. Kernighan and was for the programming language **C**, developed from 1969 to 1973 by Dennis Ritchie.

The program is the first code seen in the document, appearing in section *2 -- A Simple C Program*:
~~~ c
main( ) {
        printf("hello, world");
}
~~~

### The C Programming Language
While the above two instances of "Hello, World!" were the first, it wasn't until Kernighan and Ritchie published their famous book *The C Programming Language* in 1978 that the example program would catch on. It first appears in section *1.1 -- Getting Started*:
~~~ c
#include <stdio.h>

main()
{
    printf("hello, world\n");
}
~~~
*The `include` statement in the first line was added to the second edition of the book and is not present in the first.*

It then appears again in the same section but split up to demonstarte the use of the `\n` escape sequence:

~~~ c
#include <stdio.h>

main()
{
    printf("hello, ");
    printf("world");
    printf("\n");
}
~~~
*Again, the first edition doesn't include the `include` statement.*

Indeed the book, often abbreviated K&R for its authors, remains a cornerstone of programming literature even today. It should be no surprise then, that the practice of using "Hello, World!" as a test program for beginners would originate from it.

#### Side note on BCPL
Several sources on the internet claim that Prof. Kernighan first wrote the "Hello, World!" program in his documentation of the Basic Combined Programming Language (BCPL) at Bell Labs before he wrote it for the B tutorial. This however is untrue. Unsure myself of whether the first documented use of "Hello, World!" was in BCPL or B, I emailed Prof. Kernighan and he confirmed it:

  > I have never written a line of BCPL, so I definitely never wrote a hello world example for BCPL documentation. As best I can recall, the original example was for the internal B manual that I wrote at Bell Labs...

## Examples
Below are 4 examples of "Hello, World!" programs in Java, Python, C++, and Brainfuck respectively. You can find many more examples for different languages at the [Hello World Collection](http://helloworldcollection.de) website.

#### Java
~~~ java
public class HelloWorld {
  public static void main(String[] args) {
    System.out.println("Hello, World!")
  }
}
~~~
Java is a class based, object oriented language. Because of this we must first define a `HelloWorld` object class with a `main()` method. Here we can call the `println()` method to output the string `"Hello, World!"`.

#### Python
~~~ python
print("Hello, World!")
~~~
Python is a scripting language so programs are simply a set of commands run from top to bottom. As such, it's "Hello, World!" program contains no boilerplate code and is simply a `print()` statement.

#### C++
~~~ c++
#include <iostream>

int main() {
    std::cout << "Hello, World!";
    return 0;
}
~~~
All C++ programs start by executing the `main()` function. Here we can print out the desired string to the *standard character output device* `std::cout`.

#### Brainfuck
~~~ brainfuck
++++++++[>++++[>++>+++>+++>+<<<<-]>+>+>->>+[<]<-]>>.>---.
+++++++..+++.>>.<-.<.+++.------.--------.>>+.>++.
~~~
*See [here](https://en.wikipedia.org/wiki/Brainfuck#Hello_World!) for a commented version of this program.*

Brainfuck is an esoteric programming language whose sole purpose is to be obfuscated and difficult to program in. As such, writing a "Hello World!" program in it (and other esoteric languages) is a show of programmatical prowess rather than inexperience.

<!-- #### C#
~~~ C#
using System;

internal static class HelloWorld {
    private static void Main() {
        Console.WriteLine("Hello, world!");
    }
}
~~~

#### Prolog
~~~ Prolog
main:- write('Hello, world!'),nl.
~~~ -->
