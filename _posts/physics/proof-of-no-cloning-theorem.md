---
layout: post
title: Proof of the No Cloning Theorem
date: 2018-07-13
tags: quantum-physics quantum-computing
---
The no-cloning theorem states that no quantum state can be perfectly copied. Meaning nothing can be perfectly copied as all things are composed of particles.

While this has larger physical and even philosophical ramifications, its most direct impact is on the field of quantum computing. Unlike classical computing where bits can be copied and sent at will, qubits are unique and cannot be cloned.

We simply have to show that it is impossible to clone, that is create two identical copies, of a given quantum particle. To do this we must establish two principles:

<!--more-->

1. Quantum mechanics is formulated as a vector space, specifically a Hilbert space, with quantum particles being the vectors. As such, all transformations of quantum states (so anything that can physically happen to a particle) must be **linear** and thus can be represented as a matrix.

2. While quantum mechanics is probabilistic in nature, all the different outcomes of measuring a quantum particle/system must sum to $1$ (the particle must be *something*). This is referred to as the *unitary property* and means that only **unitary matrices** are valid quantum transformations.

Thus, to prove the no-cloning theorem, we must show that there exists no complex valued unitary matrix that can take an arbitrary qubit.
