Strings form a vector space?

Similarities
- Addition + is just concatenation
- Scalar multiplication . is just repeated concatenation with itself.
- Addition is associative
- Identity element is empty string
- Scalar multiplication compatible with field multiplication
- Distributivity of scalar multiplication with respect to field addition
- (a+b)v = av+bv

Caveats
- Underlying 'field' is only the natural numbers (times 0 gives the empty string.) Not a field just a ring.
- Addition is commutative
- Distributivity of scalar multiplication with respect to vector addition
- c(v+u) != cv+cu

Let's call a set of objects, called **strings**, with an underlying ring that satisfies the above properties be called a **String Space**.

Certainly the set of strings of any character set form a string space with the natural numbers. The set of all finite sequences with elements from a set S form a string space. i.e. the following is a string space:

$$\left(\bigcup_{n\in\mathbb N} S^n,\mathbb N\right)$$

Note that the finite polynomials are also a string space.

#### Non natural string spaces
What about string spaces whose underlying ring isn't the naturals? Well an immediate thought that comes to mind is transfinite sequences. Indeed, the ordinal numbers form a ring under ordinal addition multiplication. And if you don't like class sized rings, our underlying ring could be any limit ordinal.

#### Restriction on String spaces
Note that normal modules over rings and vector spaces are NOT string spaces. because to qualify as a string space your addition cannot be communitive and your scalar multiplication cannot distribute over vector addition. These properties take the stringiness out of string space.

With these limitations, what can we say about string spaces?





#### HOld on
wait scratch all of that these arent rings. we need the integers to amek them rings. but thats ok because negative scalrla multiplcationworks on wtrings too jsut reverse thenm. even repeects distrbutivity.

but now what abuot ordinals? negative ordinals? interesting novel applications of this concept. ordinal types? the assocaited ordinal type with each oefindal  number? a forward version, a backward one and a two way one? but then add them in different ways. a new calculus of ordinal integers. 2 dimensional essentially. reprsetned bya  tuple of ordinal numbers.
