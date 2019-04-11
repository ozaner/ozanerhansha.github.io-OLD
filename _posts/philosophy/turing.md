---
layout: post
title: On Turing's 'Computing Machinery and Intelligence'
date: 2019-02-09
tags: philosophy computer-science artificial-intelligence
---
#### Background
These are my thoughts, a summary, and possibly a bit more, on Alan Turing's seminal 1950 paper ["Computing Machinery and Intelligence"](http://phil415.pbworks.com/f/TuringComputing.pdf). Each section (denoted by §) of this post corresponds to the same titled section of the paper.

As a quick background, the paper was published in the philosophy journal *Mind* in 1950 and laid out a method of testing the 'intellectual capabilities' of a machine, the Turing test. The paper is a cornerstone of artificial intelligence, computer science, and the philosophy of the mind. Even further, the Turing test has become a mainstay of popular culture and science fiction.

## §1. The Imitation Game
Turing wastes no time in posing the question of interest: "Can machines think?" but then immediately points out that key to this question is the definition of 'machine' and 'think'. To avoid the murky issue of nailing down such definitions, Turing proposes an experiment called the *imitation game* or, as we know it today, the **Turing test**. The rules of the game are quite simple:

- There are two players A and B and an interrogator C.
- One of the two players is a computer and the other a human.
- It is the interrogator's job (also a human) to determine which of the two is the computer and which the human.
- To that end, the interrogator is able to communicate with A and B via text (a chatroom, teleprompter, etc.) and ask them any question they please.

It is with this Turing test that we can rephrase our initial question of "Can a machine think?" to the more unambiguous "Can a machine fool the interrogator into thinking it is a human?" Of course, this still leaves 'machine' undefined but Turing will address that in §3.

## §2. Critique of the New Problem
Here Turing explains that doing the test over text abstracts away the physical formalities of fooling a human to thinking a machine isn't a robot. Remember, we are concerned with the "intellectual capacities of a man" not the physical ones. Of course, the interrogator can question the player's physical aspects, but the player is under no obligation to tell the truth.

Another important point here is that there may be some game theoretic trickery going on with the test, leading to the best strategy for the computer *not* being to imitate a human. While this seems unlikely, we will simply assume that the computer's best strategy to be labeled a human by the interrogator is to imitate one.

## §3. The Machines concerned in the Game
It is in this paragraph that Turing addresses what constitutes a 'machine' that can take part in the imitation game. After mulling the possibility of simply rearing a human (maybe even in such a way as to have arisen from a single cell and not normal procreation), Turing restricts the kind of machine we will be focusing on to the **universal Turing machine** or, as he refers to it in the paper, the **digital computer**.

The reader may, at first glance, think this to be too limiting a restriction to our question, but they would be wrong. Indeed the mathematical idealization that is the universal Turing machine, realized by electronic digital computers, represents the most general of information manipulation. The very notion of computation is defined by them. Any 'thinking' machine one could come up with (that could be constructed) would *necessarily* be less than or equivalent to a Turing machine.

*In fact strictly less than, as the mathematical formulation of a Turing machine calls for a countably infinite amount of memory. That said, this distinction needn't concern us, as humans don't require a countably infinite amount of memory to function and Turing machine can only use a finite amount of memory at one time anyway.*

#### Regarding Machine Learning
Another interesting point Turing made when considering what machines would be applicable is:

> "...to allow the possibility than an engineer or team of engineers may construct a machine which works, but whose manner of operation cannot be satisfactorily described by its constructors because they have applied a method which is largely experimental."

To any computer scientist of the modern age, a single thought comes to mind when reading that passage: **machine learning**. In particular, artificial neural networks and deep learning. These relatively new, at least in practice, models of computation have proven to be able to tackle tasks 'classical AI' could never have hoped to accomplish. From diagnosing patients, writing poetry, composing music, and driving cars, there have been few domains untouched by the rise of machine learning in our society, and those few will invariably become even fewer. That Turing might even have had an inkling of such a possibility is incredible. Due to the nature of human intelligence, that is, an intelligence cobbled up by the random statistical processes of evolution and culture, techniques where we do not explicitly know/program our machines (a la machine learning) seem all but necessary to solve the Turing test.

#### Regarding Quantum Computers
Since Turing has written this paper an even more general model of computation has been discovered, namely the **quantum Turing machine**. This model of computation is concerned with the manipulation of quantum information. And unless some reality shattering new physics is discovered, it would appear that this is the most general notion of computation in the universe (more on that below).

That said, while quantum computers *are* more general than classical ones, they still cannot compute anything a classical one can't (in theory). The only difference between them is that quantum computers can solve a particular subset of problems (called BQP) faster than any classical computer.

Why I put 'in theory' in parenthesis above is because while the difference between quantum and classical is one of efficiency and not of computability, it is the case that algorithms that would take longer than the lifespan of the universe to run on a classical computer could run in a tractable time on a quantum one. That said, while this *quantum speedup* is real and has a real world implications on what problems humanity could possibly solve, that speedup is most likely not necessary for solving the Turing test. Even if it was we can just as well prepend 'quantum' to all instances of 'computer' in the paper and continue without a worry.

#### Regarding the Computation of the Universe
Even further, I'd argue that all things in the universe are computable. Indeed, quantum physics has shown us that there are only 2 types of events that can occur in the universe: 1) the *deterministic* unitary transformation of a quantum system and 2) the *indeterministic* collapse of these quantum systems described only by probabilities. This is exactly what a quantum algorithm is: a sequence of unitary transforms and measurements (i.e. collapses). It would stand to reason then that all real world phenomena are computable, that is, describable via some algorithm, even thought itself (unless you believe that it is something immaterial and thus not bound by the laws of physics).

All that said, this is probably overkill for our goal of simply imitating human conversation. Putting aside the fact that such a program is mathematically guaranteed to exist, I think the answer to the more interesting question of whether humans can empirically create such a program is a resounding "most likely".

## §4. Digital Computers
Here Turing, sparing the reader the details, describes how a digital computer works using a simplified von Neumann model, i.e. using the concepts of store, executive unit, and control as well as conditionals and looping. The instructions such a machine could perform are very simple ones: write a 0 here, multiply these two numbers and store the result here, if there is a 1 here jump to this instruction, etc. I too will spare you the details as I don't feel it necessary to reiterate the rudiments of computing's foundations.

A key take away he makes is that anything a computer can do a human could do as well, just much more slowly. Also of note, Turing briefly defines **programming**:
> "To 'programme a machine to carry out the operation A' means to put the appropriate instruction table into the machine so that it will do A."

Indeed the programming we do today on our machines is, in a mathematically formal sense, equivalent to setting up the instruction table of a Turing machine.

In the next paragraph, Turing briefly touches on the notion of probabilistic Turing machines. That is, Turing machines that can generate random numbers. This is something a normal, deterministic Turing machine cannot do. Such machines are more general models of computation than plain old Turing machines but, as I've mentioned before, are a subset of the even more general quantum Turing machine. As such, they really don't have any bearing on the rest of the paper.

After this, Turing notes that the notion of a 'digital computer' is not a new one, and goes back all the way to Charles Babbage and his plans for an [*Analytical Engine*](https://en.wikipedia.org/wiki/Analytical_Engine) in 1837. His computer, however, was unfortunately never realized as he failed garner sufficient funding. In particular there wasn't much of a need for digital computers back in the 1800s, especially compared to Turing's era of code breaking brought on by WWII.

Turing makes special note of that fact that, despite being totally mechanical rather than electrical like modern computers, the analytical engine is totally equivalent to any other digital computer. He does this because, apparently, some people attached special importance to the fact that both the human nervous system and digital computers are electrical. The existence of mechanical computers, then, rids us of any connection between the two based on some superstitious view of electricity. That said, it is no surprise that both nervous systems and computers use electricity as both systems require 'fast signaling' as Turing puts it.

## §5. Universality of Digital Computers
Here Turing tells us that Turing machines are **discrete state machines** and elaborates on this concept. An important point he makes is that, given the inputs and current state of such a machine, its future behavior is fully determined. He likens this to the Laplacian view that if one knew the current state of the entire universe, one could use classical mechanics to calculate the future (aka Laplace's demon). The difference here, Turing notes, is that constructing a finite state machine is a bit more practical then measuring the entire current state of the universe.

Another important point he makes is that these discrete states, as opposed to the regular continuous states we see in nature, is that they are resistant to small changes, i.e. they are not chaotic. Utilizing the Laplacian demon analogy, he notes that something as small as an electron being in a slightly different position might lead to radically different results in the calculation of the universe's future state (a phenomena commonly referred to as the butterfly effect).

Discrete state machines don't suffer from this problem as it is easy to distinguish their states from one another due to there being a finite (or in the case of Turing machines, countably infinite) number of them. An obvious example of this is the representation of 0 and 1 in digital computers as electrical voltages. Even if a voltage that was neither 0 nor 1 was registered, it could be reasonably assumed that the intended voltage is whatever is closer to either of the valid states ($0.3\approx0$, $0.9\approx1$).

*Of course, our modern view of physics does not allow for a Laplacian demon as, even if one got around the relativistic ambiguity of 'the current state of the universe', one would also have to contend with the fact that, on quantum scales, the universe and its laws are probablistic.*

Moving along, Turing now takes a quick detour to talk about the number of representable states in a contemporary (1950) digital computer. He uses the 'Manchester Machine', the first electronic stored-program computer and housed at the University of Manchester, as a measuring stick. It had 174,380 bits (~21.8 kb) of storage meaning it could represent $2^{174380}\approx10^{52500}$.

Despite this complexity, it should be possible to predict what this computer will do by simply having a copy of its instruction table and current state. And if a human can compute the future states of this machine:

>"There is no reason why this calculation should not be carried out by means of a digital computer. Provided it could be carried sufficiently quickly the digital computer could mimic the behavior of any discrete state machine."

And with this, Turing introduces us to the notion of a **universal Turing machine**. A Turing machine that can simulate any other Turing machine, even themselves. Digital computers, like the Manchester machine, are examples of these types of machines. Of course the effectiveness of this emulation will depend on what resources the emulator has at its disposal. There will always be an overhead to this sort of simulation, but not necessarily a prohibitively expensive one.

A useful consequences of this is that any computational task can be achieved with a single device with sufficient resources. There is no need, in principal, to create new and different computers for different tasks as they are all effectively equivalent.

*Indeed you can (naively) think of your desktop computer as a universal Turing machine, and the stored programs it runs as simulated Turing machines. No need to buy a powerpoint machine when its program code can be stored instead.*

Turing ends this section by simply restating the question posed in §3 "are there imaginable digital machines that can do well in the imitation game?" to the following, as he's shown, equivalent question:

> "Let us fix our attention on one particular digital computer $C$. Is it true that a by modifying this computer to have an adequate storage, suitably increasing its speed of action, and providing it with an appropriate programme, $C$ can be made to play satisfactorily the part of $A$ in the imitation game, the part of $B$ being taken by a man?"

We can see that the question is becoming more and more concrete. That said, I feel like the Turing machine description was sufficient.

## §6. Contrary Views on the Main Question
At this point Turing is finally done providing the necessary background in §3-§5 and can now proceed to the philosophical content of the paper.

This section is broken up into 7 parts, each detailing different objections one may have to Turing's claim that such a machine can exist and his defense against them. (maybe i didnt read it yet)??

## §7. Learning Machines
The beginnings of AI. some may say this passage is the start of AI (or at least computational based AI)

edit section 3 machine learing i think i interpreted that incorrectly.
