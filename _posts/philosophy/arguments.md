---
layout: post
title: Arguments
date: 2018-09-07
tags: philosophy logic
---
An argument is a list of statements in some natural language (e.g. English) that are either true or false. The final statement is called the **conclusion** and should follow from the other statements, called **premises**.

The above is a description of the non-formal arguments found in philosophy. A formal argument (or *proof*) is one in which the statements are propositions in a formal language, like FOL or ZFC, and is more prevalent in mathematics. This post will focus on non-formal arguments.

<!--more-->

## Inference
Arguments can employ different types of reasoning, or inferences, to show why the premises (might) imply the conclusion. There are many different kinds of systems of inference. Some produce conclusions that are partially uncertain, i.e. only probable, as opposed to being decisive or **truth-bearing** like other types of inference. The types of inference systems used in philosophical arguments can be broadly divided into two types: deductive and inductive. Below is a chart of how these arguments can be classified based on their 'correctness':

![arguments](https://upload.wikimedia.org/wikipedia/commons/c/c6/Argument_terminology_used_in_logic.png)

### Deduction
A deductive argument is one that uses logic to show that the premises *necessarily* imply the conclusion. As opposed to other types of arguments (like inductive and abductive ones) that reason about probable truths, deductive arguments are the only kind that can definitively *prove* a statement. It is no surprise then, that deduction is the prototypical type of inference used in arguments. The two most vital properties a deductive argument can have are **validity** and **soundness**:

<details>
<summary><strong>Validity</strong></summary>
An argument is <b>valid</b> if and only if the truth of its premises <i>logically</i> imply its conclusion. Formally this means the following must hold:

$$p_1\wedge p_2\wedge\cdots\wedge p_n\rightarrow q$$

<i>Where $p_1, p_2, \cdots, p_n$ are the premises of the argument and $q$ is its conclusion.</i><p></p>

If an argument does not satisfy the above it is called <b>invalid</b> and cannot be sound.
<p></p>
</details>

<details>
<summary><strong>Soundness</strong></summary>
An argument is <b>sound</b> if and only if it is valid and all its premises are true. Formally the latter is:

$$p_1\wedge p_2\wedge\cdots\wedge p_n$$

<i>Where $p_1, p_2, \cdots, p_n$ are the argument's premises.</i><p></p>

Notice that these two conditions are sufficient for us to use the argument form <i>modus ponens</i>:

$$\begin{align}
&(p_1\wedge p_2\wedge\cdots\wedge p_n)\implies q\\
&p_1\wedge p_2\wedge\cdots\wedge p_n\\
\therefore\ &\hline{q}\\
\end{align}$$

If an argument does not satisfy the above it is called **unsound**. Good arguments ought to be sound.<p></p>
</details><p></p>

Because deductive arguments are based on logic they can be **formalized**, meaning that they can be proved and reasoned about via totally mechanical means (à la FOL) after being put in a logical form. That said, deductive arguments are different from full on logical proofs in that the atomic statements present in the premises and conclusion are expressed in a natural language.

Thus only the validity of a deductive argument can be proved. The truth of the premises (and thus the soundness of the argument) must be established with reasoning and justification, unlike a proof whose premises can be proven axiomatically.

This makes the goal of deduction (and really all arguments) to split up a controversial conclusion into a collection of accepted premises and show that the latter logically implies the former.

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

## Extracting Arguments
Arguments in real life, and even in academic discourse/papers, are not usually given as a numbered list of premises. Instead they are given implicitly as a, hopefully, coherent paragraph or passage of reasoning.

As a result, before we can analyze the logic of the argument (like its validity if it's deductive or its strength if it's inductive) we must first **extract** it from the reasoning. This is not a concrete process and some liberty must be taken to represent what the author of the passage/paper might have implicitly meant to be in their argument. Premises added by interpretation to keep the argument valid are called **suppressed premises**.

Staying true to the source is paramount in a historical analysis of the ideas of past philosophers. However, when engaging in a debate with another, it is good practice to assume the strongest version of your interlocutor's argument rather than go through the formality of disproving them on a technicality or easily remedied premise. We call this **charitable interpretation** and abiding by it produces more productive and interesting debates.

<!-- *When told to extract an argument without being told what type of inference should be used, deduction is the most likely. This is simply because deduction is based on concrete, formal logic and thus is apt for rigorous analysis.* -->

## Argument Forms and Fallacies
