- Rules of logic specify meaning mathematical statement.
- Logic is the basis of mathematical reasoning.
- To understand mathematics we must understand the proof, because once a statement, it begin a theorem. A collection of theorem on a topic is what we know about the topic.
- Proofs are used to verify if a computer produce the correct output.
# 1.1 proposition logic
## 1.1.1 introduction
rules of logic give meaning to mathematical statements,used to distinguish between valid and invalid argument.
## 1.1.2 Proposition
A proposition is a `Declarative sentence` that is either true or false.
Can Use letter to denote proposition variables (sentential variable), with letter that denote numerical variables $p, q, r, s$.
- if the value of preposition is true, is denoted by `T`
- if is false we use `F`
Proposition cannot expressed in simpler proposition -> `atomic proposition`
The aria that deals with proposition is called `Propositional logic`.
### new Proposition
New proposition are created by combining propositions with `logical operators` for create `compound propositions`.
- ==negation==:
	- $\lnot p$ means the negation of our statement $p$
	- the truth value of this negation is the opposite of $p$

| $p$ | $\lnot p$ |
| --- | --------- |
| T   | F         |
| T   | F         |
| F   | T         |
| F   | T         |
- ==conjunction==:
	- $p \land q$ read as "p and q"
	- is true when both are true
	
| $p$ | $q$ | $p \land q$ |
| --- | --- | ----------- |
| T   | T   | T           |
| T   | F   | F           |
| F   | T   | F           |
| F   | F   | F           |
- ==disjunction==:
	- $p \lor q$ read as "p or q"
	- Is true when one of the two is true

| $p$ | $q$ | $p \lor q$ |
| --- | --- | ---------- |
| T   | T   | T          |
| T   | F   | T          |
| F   | T   | T          |
| F   | F   | F          |
- ==exclusive or==:
	- $p \oplus q$ read as "p xor q"
	- is true when only one of the propositions are true

| $p$ | $q$ | $p \oplus q$ |
| --- | --- | ------------ |
| T   | T   | F            |
| T   | F   | T            |
| F   | T   | T            |
| F   | F   | F            |
## 1.1.3 Conditional Statements
let $p$ and $q$ be propositions. The conditional statement $p\implies q$ is the implications.
- p is the Hypothesis
- q is the Conclusion
- is false when the hypothesis is true and conclusion is false.
- asserts that q is true on the condition that p holds.

| $p$ | $q$ | $p \implies q$ |
| --- | --- | -------------- |
| T   | T   | T              |
| T   | F   | F              |
| F   | T   | T              |
| F   | F   | T              |
### converse, contrapositive, inverse
let be the proposition $p \implies q$ our statement
- ==converse==:
	- is $q \implies p$ 
- ==contrapositive==:
	- is $\lnot q \implies \lnot p$ (only have have the same truth value)
- ==inverse:
	- is $\lnot p \implies \lnot q$  (equivalent to converse)
- ==Biconditional==:
	- is the proposition "$p$ if and only if $q$"
	- is $p \iff q$, that is equal to $(p \implies q) \land (q \implies p)$

| $p$ | $q$ | $p \iff q$ |
| --- | --- | ---------- |
| T   | T   | T          |
| T   | F   | F          |
| F   | T   | F          |
| F   | F   | T          |
## 1.1.4 Truth table of Compound Propositions
is used for resolve a compound proposition and see his solution:

| $p$ | $q$ | $\lnot q$ | $p \lor \lnot q$ | $p \land q$ | $(p \lor \lnot q) \implies (p \land q)$ |
| --- | --- | --------- | ---------------- | ----------- | --------------------------------------- |
| T   | T   | F         | T                | T           | T                                       |
| T   | F   | T         | T                | F           | F                                       |
| F   | T   | F         | F                | F           | T                                       |
| F   | F   | T         | T                | F           | F                                       |
## 1.1.5 precedence of logical operators
Usually are used parenthesis for specify the order in which are defined logical operators.
- $\lnot$ is the first to be applied
- $p \land q$ second to be applied
- $p \lor q$ third to be applied
- $p \implies q$ forth to be applied
- $p \iff q$ fifth to be applied
# Applications of propositional logic 1.2
Human language is often ambiguous or imprecise. Translating sentences into compound statements removes the ambiguity.
- example 1:
	- "You can access the Internet from campus only if you are a computer science major or you are not a freshman."
	- now we can say that
		- $\text{You can access internet from campus} := a$
		- $\text{You are a computer science major} := c$
		- $\text{You are a freshman} := f$
	- so now the sentence is: $a \implies (c \lor \lnot f)$
- example 2:
	- "you cannot ride the roller coaster if you are under 4 feet tall, unless you are older than 16 years"
	- now we can rearrange in "if you are under 4 feet and you are younger than 16 years then you cannot ride the roller coaster"
		- $\text{you are under 4 feet} := p$
		- $\text{you are older than 16 years} := q$
		- $\text{You can ride the roller coaster} := r$
	- $(p \land \lnot q) \implies \lnot r$
## 1.2.3 system specifications
Translating from Human language into logical is essential for specify both hardware and software.
```
System specification from human language -> logical language
```
- example 1:
	- "The automated reply cannot be sent when the file system is full"
		- $\text{the automated replay can be sent} := p$
		- $\text{when the file system is full} := q$
		- $q \implies \lnot p$ 
System specification should be consistent, not contain conflicting requirements that derive a contradiction.
```
No consistent -> no system satisfies all specifications
```
## 1.2.6 Logic Circuits
Propositional logic can be applied to the design of hardware. In fact complicated digital circuits can be constructed from `NOT, AND, OR` gates.
# 1.3 Propositional equivalences
A compound proposition that is ever true is called ==Tautology==, if is always false is called ==Contradiction==. else is called ==Contingency==
## 1.3.5 Satisfiability
A compound proposition 
$$

$$