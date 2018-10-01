---
layout: post
title: Argument
date: 2018-09-07
tags: philosophy logic
---
An argument is a list of statements in some natural language (e.g. English) that are either true or false. The final statement is called the **conclusion** and should follow from the other statements, called **premises**.

<!--more-->

## Inference
Arguments can employ different types of reasoning, or inferences, to show why the premises (might) imply the conclusion. The primary types of inference used in philosophical arguments being deduction, induction, and abduction.

![arguments](https://upload.wikimedia.org/wikipedia/commons/c/c6/Argument_terminology_used_in_logic.png)

### Deduction
A deductive argument is one that uses logic to show that the premises *necessarily* imply the conclusion. As opposed to other types of arguments (like inductive and abductive ones) that reason about probable truths, deductive arguments are the only kind that can definitively *prove* a truth.

Because deductive arguments are based on logic they can be **formalized**, meaning that they can be proved and reasoned about via totally mechanical means. A formal argument can be proved from a finite set of rules.

<details>
<summary><strong>Validity</strong></summary>
An argument is **valid** if and only if the truth of its premises directly implies its conclusion. Symbolically this means the following must hold:

$$p_1\wedge p_2\wedge\cdots\wedge p_n\rightarrow q$$

*Where $p_1, p_2, \cdots, p_n$ is the argument's premises and $q$ is its conclusion.*

If an argument does not satisfy the above it is called **invalid** and cannot be sound.
<p></p>
</details>

<details>
<summary><strong>Soundness</strong></summary>
An argument is **sound** if and only if it is valid and all its premises are true. Symbolically this is:

$$p_1\wedge p_2\wedge\cdots\wedge p_n$$

*Where $p_1, p_2, \cdots, p_n$ is the argument's premises.*

Notice that these two conditions are sufficient for us to use the argument form *modus ponens*:

$$\begin{align}
&p_1\wedge p_2\wedge\cdots\wedge p_n\implies q\\
&p_1\wedge p_2\wedge\cdots\wedge p_n\\
\therefore\ &\hline{q}\\
\end{align}$$

If an argument does not satisfy the above it is called **unsound**. Good arguments ought to be sound.
</details>

### Induction
TODO

<details>
<summary><strong>Strength</strong></summary>
TODO
</details>

<details>
<summary><strong>Cogency</strong></summary>
TODO
</details>

### Abduction
TODO

## Extraction
Arguments in real life, and even academic discourse/papers, are not usually given as a list of statements. Instead they are given implicitly as a, hopefully, coherent paragraph or passage of reasoning.

As a result, before we can analyze the logic of the argument (like its validity if it's deductive or its strength if it's inductive) we must first **extract** it from the reasoning. This is not a concrete process and some liberty must be taken to represent what the author of the passage/paper might have implicitly meant to be in their argument. Premises added by interpretation are called **suppressed premises**.

Staying true to the source is paramount in a historical analysis of the ideas of past philosophers, but when engaging in a debate with another, it is good practice to assume the strongest argument of your interlocutor rather go through the formality of disproving them on a technicality or easily remedied premise.

*When told to extract an argument without being told what type of inference should be used, deduction is the most likely. This is simply because deduction is based on concrete, formal logic and thus is apt for rigorous analysis.*
