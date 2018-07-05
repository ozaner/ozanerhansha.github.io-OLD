---
layout: post
title: Letter Case and Computing
date: 2018-06-30
tags: computer-science
---
## What is Letter Case?
Letter case refers to whether a letter is **uppercase**/capitalized (*A*) or **lowercase** (*a*). There are different styles of writing words and sentences with different conventions of where to capitalize letters and where not to.

The topic of letter case is a detailed one, involving the history and linguistics of different languages, their grammars, and of printed word itself. This post will touch upon letter case styles in general writing, but will mostly focus on the use of case styles on the internet, in programming, and computing in general. Specifically in English.

<!--more-->

## Writing/Typing
### This is sentence case.
This is the standard letter case used in the English language. The beginning of sentences are capitalized along with proper nouns (i.e names, places, days of the week, etc.). Each sentence ends with some punctuation (ex *.*, *?*, *!*).

Here's an example:
> The quick brown fox jumps over the lazy dog.

You'd see this case when reading anything somewhat formal, like emails, a person's/company's website, text documents, academic papers, etc.

### This is Title Case
This is the case used when typing out titles. Title case has all words capitalized barring a limited subset that are deemed *common* (unless they are the first word, in which case they are capitalized). That includes words like *or*, *but*, *if*, *the*, *in*, etc.

Here's an example:
> The Quick Brown Fox Jumps over the Lazy Dog

Academic papers, emails (think subject line), music, videogames and just about any media or document has a title. Its important to note that there is no agreement on what exactly the subset of words not capitalized in title case is. That said, all titles more or less follow the same pattern of capitalization.

### ALL CAPS
Writing in all uppercase letter, or all caps as it is more commonly known, is taken to convey yelling when typed out, especially when texting or commenting on the internet. That said, all caps is also used in titles and headlines in order to make the text stand out more.

Here's what it looks like:

> THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG!

Typing in all caps can be done by holding down the `SHIFT` key while typing or, more commonly, by simply turning on the `CAPS LOCK` key. Smartphone keyboards also have similar functionality with caps lock being activated by double tapping the shift key, for example. Acronyms are written in all caps (NATO, USA, ASAP) unless the acronym has had enough usage to become a fully fledged word like *radar* (**ra**dio **d**etection **a**nd **r**anging) or *laser* (**l**ight **a**mplification by **s**timulated **e**mission of **r**adiation)

### all lowercase
All lowercase is typically used when writing something informally and quickly, such as a text message or an internet comment (if the commenter isn't particularly concerned with the comment's presentation). This is because the message is not worth the extra effort of pressing the `SHIFT` key (especially on smartphone keyboards). File extensions are also conventionally all lowercase.

Here's what it looks like:

> the quick brown fox jumps over the lazy dog

Since the use of all lowercase is one of convenience, text written in it is not usually punctuated unless necessary to convey intent. (you hate him. vs. you hate him?)

That said, this case may soon die out as some mobile keyboards, for example Google's GBoard for Android, automatically capitalize the first letter in sentences as well as in proper nouns. This essentially makes typing in sentence case the default.

## Computing/Programming
For many languages, it is best practice to use different type cases to differentiate variables, methods, classes, functions, and other identifiers from each other, as well as provide useful metadata on said identifiers. Their use in languages is almost never mandatory and instead serve to promote readability and uniformity in code.

Virtually all programming languages do not allow whitespace in identifier names. As such, the three main programming type cases do not make use of spaces and instead use other means of **delimiting**, or telling apart, words. It is also important to note that these naming conventions don't just utilize different type cases for different identifiers, but also uppercase and lowercase variations of those type cases.

### CamelCase
Camel case has the first letter of every word in the phrase/identifier capitalized. And so capitalization serves as camel case's delimiter. Lower camel case has the first letter of the first word in the identifier lowercased while upper camel case does not:

>UpperCamelCase

>lowerCamelCase

Used in
- Class names in Java (upper)
- Class names in Python (upper)
- Method names in Java (lower)
- Variables names in Java (lower)

### snake_case
Snake case delimits words using underscores ( _ ). And like the others, There are uppercase and lowercase variants:
>Upper_Snake_Case

>lower_snake_case

Unlike camel case, snake case is not delimited by the capitalization of letters. As such it is possible to make use of a third variant with all capital letters:
>CAPITAL_SNAKE_CASE

This case is commonly used for naming attributes on computers, like files or usernames, where space characters cannot be processed. Snake case is essentially the default type case used when spaces are unavailable.

Used in
- Constants in Java (upper)
- Constants in Python (upper)
- Variables in Python (lower)
- Functions and classes in the C & C++ Standard Library (lower)

### kebab-case & Train-Case
Kebab case is similar to snake case, as well as used in similar situations, with its only difference being the use of hyphens (-) to delimit words rather than underscores:
>Upper-Kebab-Case

*Upper kebab case is also known as train case*

>lower-kebab-case

>CAPITAL-KEBAB-CASE

Used in
- CSS Classes (lower)
- URLs (lower)

## Other
### StUdLyCaPs
Studly caps has letters randomly capitalized and may or may not include spaces to delimit words. Its use is associated with sarcasm and parodying other type cases.

>tHeqUIckBrOwNFOxjuMpsOvERtHeLazYdOg

Below is variation of Studly caps where spaces are used to delimit words. This makes the message more readable while still retaining its sarcastic tone:

>tHe qUIck BrOwN FOx juMps OvER tHe lAzYdOg

Indeed this is the same case used in the [mocking Spongebob meme](http://knowyourmeme.com/memes/mocking-spongebob) that was popular around 2017.
