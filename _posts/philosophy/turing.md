---
layout: post
title: On Turing's 'Computing Machinery and Intelligence'
date: 2019-02-09
tags: philosophy computer-science
---
These are my thoughts (and possibly a bit more) on Alan Turing's 1950 paper *Computing Machinery and Intelligence*.

## §1. The Imitation Game
Turing wastes no time in posing the question of interest: "Can machines think?" but then immediately points out that key to this question is the definition of 'machine' and 'think'. To avoid the murky issue of nailing down such definitions, Turing proposes an experiment called the *imitation game* or, as we know it today, the **Turing test**. The rules of the game are quite simple:

- There are two players A and B and an interrogator C.
- One of the two players is a computer and the other a human.
- It is the interrogator's job (also a human) to determine which of the two is the computer and which the human.
- To that end, the interrogator is able to communicate with A and B via text (a chatroom, teleprompter, etc.) and ask them any question they please.

It is with this Turing test that we can rephrase our initial question of "Can a machine think?" to the more unambiguous "Can a machine fool the interrogator into thinking it is a human?" Of course, this still leaves 'machine' undefined but Turing will address that in part 3.

## §2. Critique of the New Problem
Here Turing explains that doing the test over text abstracts away the physical formalities of fooling a human to thinking a machine isn't a robot. Remember, we are concerned with the "intellectual capacities of a man" not the physical ones. Of course the interrogator can question the players physical aspects but the player is under no obligation to tell the truth.

Another important point here is that there may be some game theoretic trickery going on with the test leading to the best strategy for the computer *not* being to imitate a human. While this seems unlikely, we will simply assume that the computer's best strategy to be labeled a human by the interrogator is to imitate one.

## §3. The Machines concerned in the Game
After mulling the possibility of simply rearing a human (maybe even in such a way as to have arisen from a single cell and not normal procreation), Turing restricts the kind of 'machine' we will be focusing on to the **universal Turing machine** or, as he refers to it in the paper, the **digital computer**.

The reader may, at first glance, think this to be too limiting a restriction to our question, but they would be wrong. Indeed the mathematical idealization that is the Turing machine, realized by electronic digital computers, represents the most general of information manipulation. The very notion of computation is defined by them. Any 'thinking' machine one could come up with (that could be constructed) would *necessarily* be less than or equivalent to a Turing machine.

#### Regarding Machine Learning
Another interesting point Turing made when considering what machines would be applicable is:

> "...to allow the possibility than an engineer or team of engineers may construct a machine which works, but whose manner of operation cannot be satisfactorily described by its constructors because they have applied a method which is largely experimental."

To any computer scientist of the modern age, a single thought comes to mind when reading that passage: **machine learning**. In particular, artificial neural networks and deep learning. These relatively new, at least in practice, models of computation have proven to be able to tackle tasks 'classical AI' could never have hoped to accomplish. From diagnosing patients, writing poetry, composing music, and driving cars, there have been few domains untouched by the rise of machine learning in our society, and those few will invariably become even fewer. That Turing might even have had an inkling of such a possibility is awe-inspiring to say the least. Indeed, if we are ever to solve the Turing test, machine learning will most likely play the biggest role.

#### Regarding Quantum Computers
Since Turing has written this paper an even more general model of computation has been discovered, namely the **quantum Turing machine**. This model of computation is concerned with the manipulation of quantum information. And unless some reality shattering new physics is discovered, it would appear that this is the most general notion of computation in the universe (more on that below).

That said, while quantum computers *are* more general than classical ones, they still cannot compute anything a classical one can't (in theory). The only difference between them is that quantum computers can solve a particular subset of problems (called BQP) faster than any classical computer.

Why I put 'in theory' in parenthesis above is because while the difference between quantum and classical is one of efficiency and not of computability, it is the case that algorithms that would take longer than the lifespan of the universe to run on a classical computer could run in a tractable time on a quantum one. That said, while this *quantum speedup* is real and has a real world implications on what problems humanity could possibly solve, that speedup is most likely not necessary for solving the Turing test. Even if it was we can just as well prepend 'quantum' to all instances of 'computer' in the paper and continue without a worry.

#### Regarding the Computation of the Universe
Even further, I'd argue that all things in the universe are computable. Indeed, quantum physics has shown us that there are only 2 types of events that can occur in the universe: 1) the *deterministic* unitary transformation of a quantum system and 2) the *indeterministic* collapse of these quantum systems described only by probabilities. This is exactly what a quantum algorithm is: a sequence of unitary transforms and measurements (i.e. collapses). It would stand to reason, then, that all real world phenomena are computable, that is describable via some algorithm, even thought itself (unless you believe that it is something immaterial and thus not bound by the laws of physics).

All that said, this is probably overkill for our goal of simply imitating human conversation. Putting aside the fact that such a program is mathematically guaranteed to exist, I think the answer to the more interesting question of whether humans can empirically create such a program is a resounding "most likely".

## §4. Digital Computers
