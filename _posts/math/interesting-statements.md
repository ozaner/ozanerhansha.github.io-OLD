## Cardinality
The universe of sets in ZFC is expressible in NBG as the following class $V$:

$$V=\{x\mid\left(\exists y\right) x\in y\}$$

The cardinality function $|\cdot|$ is a large function from the universe $V$ to the cardinal numbers:

$$|\cdot|:V\to\operatorname{Card}$$

Equinumerosity (equipollency) is a large relation on a class $V$:

$$x\#y\equiv \exists f:x\xrightarrow{\text{Bijection}} y$$

Equivalence classes of $\#$ are different than their representative cardinals:

$$[S]_ \#=\{x\mid x\# S\}$$

If we define the cardinality function's codomain to be the Ordinals instead of Cardinals:

$$|\cdot|:V\to\operatorname{Ord}$$

We can directly define cardinality as the smallest ordinal that is equinumerous with $S$:

$$|S|\equiv \inf\{x\in\operatorname{Ord}\mid x\#S\}$$

## Sequences
A sequence $f$ over $S$ is a function of the following form:

$$f:\alpha\in\operatorname{Ord}\to S$$

Bi-infinite sequences? Must allow sum of reverse order types (i.e. $\omega^* +\omega$). Opens the door to order types in general or at least total order types. Canonical representation of order types? Not that I've seen.

Could just throw out bi-infinite sequences. Call them functions from integers to a set.

How do we deal with the natural numbers embedded in the reals rather than ordinals? hyperreals?
