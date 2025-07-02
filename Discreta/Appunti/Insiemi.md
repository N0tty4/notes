i
# Concetti fondamentali:
- Insieme
- Elemento
- Appartenenza all'insieme
## def
Un insieme è una collezione di oggetti $\in$ all'insieme
$$
\{1, 2, 3, 4\}
$$
1. Un insieme può essere elemento di un'altro insieme
   $\{1, 2, 3, 4, \{5, 6, 7\}, 8\}$
   
2. In un insieme non ci sono ripetizione:
   $\{1, 2, 3, 3, 4\}$ non è un insieme
   
3. l'ordine in un insieme non conta:
   $\{1, 2, 3\} = \{3, 1, 2\}$
## def
1. $A := \{...\}$ significa che per definizione A è uguale a quel insieme
2. $x\in A$ significa che $x$ appartiene ad $A$
3. $\emptyset = \{\}$ significa che l'insieme è vuoto
## Notazioni
1. $\mathbb{N} := \{0, 1, 2, 3, ...\}$ sono i numeri naturali
2. $\mathbb{P} := \{1, 2, 3, 4, ...\}$ sono i numeri positivi
3. $\mathbb{Z} := \{-1, 3, 0, -4, ...\}$ sono i numeri interi
4. $\mathbb{Q} := \{\frac{a}{b}: a, b \in \mathbb{Z}, b \not = 0\}$ 
5. $\mathbb{R} :=$ numeri reali
6. $\mathbb{C} :=$ numeri complessi 
## def
- $A := \{x:x \text{ ha } P\}$ (P è una proposizione)
- $A = B$ se tutti elementi $\in$ $A$ sono uguali agli elementi $\in$ $B$
- $A\subseteq B$ se tutti gli elementi di $A \in B$ 
- $A \subset B$ se tutti gli elementi di $A \in B$ e $A \not = B$ 
  Oss:
  - se $A \subseteq B$ e $B\subseteq A \iff A = B$ 
- $A\cap B$ prendono gli elementi in comune tra $A$ e $B$, $:= x \in A : x \in B$ 
- $A \cup B$ uniscono tutti gli elementi nell'insieme
## Prop:
- associativa:
	- $A \cup (B \cup C) = B \cup (A\cup C)$ 
	- $A \cap(B \cap C) = B \cap (A \cap C)$ 
- Transitiva:
	- se $A \subseteq B$ e $B \subseteq C$, allora $A \subseteq C$ 
- Distributiva:
	- $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$ 
	- $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$
## Insieme universo
Per non finire nel paradosso di Russel, si ha optato per pensare che tutti gli insiemi sono immersi in un insieme universo detto $U$.
### def
1. complementare di un insieme è $A' := \{x \in U : x \not \in A\}$
2. differenza tra insiemi $A \setminus B = \{ x \in A : x \not \in B\}$ 
3. Differenza simmetrica $\{(A \setminus B) \cup (B \setminus A)\}$
4. l'insieme potenza di $A$ è $2^A$, scritto come $P(A)$.
## Leggi di De Morgan's 
- $\overline{A \cup B} = \overline{A} \cap \overline{B}$ 
- $\overline{A \cap B} = \overline{A}\cup\overline{B}$
# Funzioni
$f:A \to B$ legge che associa ad ogni elemento di $A$ unico elemento di $B$. 
una funzione $f : A \to B$ è un sottoinsieme:
$$
\{f \subseteq A\times B : \forall a \in A, \exists!b \in B : (a, b) \in f\}
$$
in questo caso $f$ non è visto come una applicazione ma come l'insieme che ha al suo interno i valori $(a, b)$ i quali devono essere all'interno di $f$.
## def
- $f$ è iniettiva se $x_1 \not = x_2 \implies f(x_1) \not = f(x_2), \forall a_1, a_2 \in A$.
- $f$ è suriettiva se $\forall b \in B, \exists a \in A : b = f(a)$ 
- $f$ è biunivoca se è sia iniettiva che suriettiva.
## composizione
Siano $A, B, C$ degli insiemi, e $f: A \to B$ e $g : B \to C$.
La composizione di $f \circ g : A \to C$.
$$
(g \circ f)(a) = g(f(a)) ,\forall a \in A
$$
$g$ e $f$ sono uguali se: $f(a) = g(a), \forall a \in A$  
### proprietà
1. $f$ e $g$ iniettiva $\implies$ $g \circ f$ iniettiva
2. $f$ e $g$ suriettiva $\implies$ $g \circ f$ suriettiva
3. $f$ e $g$ biunivoca $\implies$ $g \circ f$ biunivoca
## funzione identità
è la funzione $Id_A : A \to A$ definita da
$$
Id_A(a) := a, \forall a \in A
$$
## funzione inversa
Sia $f : A \to B$, la funzione inversa sarebbe $f^{-1}: B \to A$, definita come $f(b) = a$, la quale deve essere biunivoca.
Formalmente si scriverebbe:
$$
f^{-1} := \{(b,a) \in B \times A : (a, b) \in f\}
$$
- $Id_A$ è biunivoca e $(Id_A)^{-1} = Id_A$
## prop
siano $f, g, h : A \to A$
1. $f \circ (g\circ h) = (f \circ g) \circ h$
2. $f\circ Id_A = f = Id_A \circ f$
3. se $f$ è biunivoca $\implies$ $f \circ f^{-1} = Id_A = f^{-1} \circ f$
# Esempi e controesempi
- Esempio: non dimostra
- controesempio: dimostra che non è sempre vero
## modi per dimostrare uguaglianza
1. tavola di verità
2. logica
# Prodotto cartesiano
siano $A, B$ insiemi, allora: $A \times B := \{(a, b): a \in A, b \in B\}$.
Oss:
- $(1, 2) \not = (2, 1)$
## prop
$A \times (B \cap C) = (A\times B) \cap (A \times C)$
# Definizioni
- L'immagine di $S$ tramite $f$ è $f(s):= {f(a): a \in S}$ 
- IL gruppo simmetrico di rango $n$ è $\{S_n := f:[n] \to [n]: \text{f biunivoca}\}$.
  Gli elementi di $S_n$ si dicono permutazioni e $n \in \mathbb{P}$.
  Se $f \in S_n$, scriviamo $f = a_1, a_2, ..., a_n$  dove $a_1 := f(1), a_2 := f(2), ...$  
# Relazioni
sia $A$ un insieme, Una relazione su $A$ è un sottoinsieme di $A \times A$. Se $(a, b) \in R$, allora scriveremo $aRb$, $(a, b \in A)$
## tipi di relazioni
1. Riflessiva se $(a, a) \in R,  \forall a \in A$
2. Simmetria se $\forall (a, b) \in R, (b, a) \in R, \forall a, b \in A$
3. Transitiva se $(a, b) \in R, (b, c) \in R \implies (a, c) \in R$
4. di equivalenza se è Riflessiva, Simmetrica, Transitiva
Oss:
- $R := A \times A$ è di equivalenza
- $R := \emptyset$ non è di equivalenza
## def
$R :=$ relazione di equivalenza su $A$ e sia $a \in A$.
La classe di equivalenza di $a$ è:
$$
[a]_R:={b\in A : aRb}
$$
Oss:
- $[a]_R \subseteq A$
- $[a]_R \not = \emptyset$ perché $a \in [a]_R$
### prop
Sia $R$ una relazione di equivalenza su $A$. Siano $a, b \in A$ allora può accadere:
- $[a]_R = [b]_R$ (coincidono)
- $[a]_R \cap [b]_R = \emptyset$ (vuota)  
Questo perché è una relazione di equivalenza quindi vale la transitività.
## def
Sia $A$ un insieme, una partizione di A è un insieme $\pi := \{B_1, ..., B_k\}$ t.c:
1. ogni insieme deve essere un sottoinsieme di A:
   $B_i \subseteq A, \forall i \in \{1, 2, ..., k\}$ 
2. I sottoinsiemi non devono esser vuoti:
   $B_i \not = \emptyset, \forall i \in [k]$
3. l'unione di tutti i sottoinsiemi deve fare A
   $\bigcup_{i=1}^{k}B_i=A$
4. tutti gli insiemi devono essere diversi tra di loro: $\forall i \not = j, B_i \cap = B_j = \emptyset$
## classi di equivalenza
sia $A$ un insieme e sia $R$ una relazione di equivalenza su A.
Allora le classi di equivalenza di $R$ sono un partizione di A