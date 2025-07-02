Discrete mathematics devoted study discrete structures for represent discrete objects.
# Sets
Sets are the fundamental discrete structure, used to group objects together.
## def
A set is an ==unordered collection== of distinct objects, called ==elements== of the set. A set is said to contain its elements.
- $a \in A :=$ a is an element of A
- $a \not \in A :=$ a is not an element of A
## represent a set
there are several ways to describe a set:
- list al members of a set between braces, called ==roster method==: $\{1, 2, 3, 4\}$
- use ==set builder== notation, general form is $\{x | x \text{ has properties P}\}$
## intervals
used for represent an interval inside a set:
- $[a, b] = \{x | a \leq x \leq b\}$
- $[a, b[ = \{x | a \leq x < b\}$
- $...$ 
### remark
The concept of ==datatype==, or ==type== in computer science is built upon the concept of a set. ==datatype== ==type== is the name of a set.
For example ==boolean== is the name of the set $\{0, 1\}$.
## equality of sets
Two sets are equal if and only if they have the same elements.
Therefore: if $A$ and $B$ are sets then $A$ and $B$ are ==equal== if and only if $(\forall x)(x \in A \iff x \in B)$.
- $\{1, 2, 3, 5, \} = \{5, 3, 1, 2\} = \{1, 1, 3, 3, 5, 2\}$
## empty set
is denoted with $\emptyset$, it means that has no elements, to not confuse with $\{\emptyset\}$
because it is a ==singleton set== (set with only one element).
## 2.1.2 Venn diagrams
is a way to represent graphically sets using Venn diagrams.
The ==universal set== $U$ is represented by a rectangle. Inside the rectangle the geometric figures are used to represent sets.
## 2.1.3 Subsets
The set $A$ is a ==subset== of $B$, and $B$ is a ==superset== of $A$ if and only if every element of $A$ is also an elemento of $B$.
- $A \subseteq B$ to indicate $A$ is subset of $B$
- $B \supseteq A$ to indicate $B$ is superset of $A$
$$
\forall x(x \in A \implies x \in B)
$$
$$
\sum_{k=1}^{n}{k^2}
$$
$$
\int_{0}^{b}2x^2 = 2 \int_{0}^{b}x^2 = \frac{2}{3}x^2
$$