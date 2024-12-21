## definizioni
Un insieme è una collezione di oggetti detti elementi appartenenti all'insieme.
In matematica tutto è un insieme. i  3 concetti fondamentali sono:
- insieme
- elemento
- appartenenza 
### scrittura
- si scrive un insieme elencando gli elementi separando li da `,` in `{}`: $\{1, 4, 6, 7\}$ 
- \$A:=\{...\}$ Indice che l'insieme A per definizione è l'insieme a destra

## caratteristiche
1. Un insieme può contenere anche altri insiemi: $\{1, 3, \{1, 2\}, \{2, 4, 6\} \}$   
2. In  un insieme non ci devono essere ripetizioni : $\{1, 1, 2\}$ non è un insieme 
3. l'ordine di un insieme non conta: $\{1, 2, 3\}  = \{2, 1, 3\}$
## definizioni
1. $x \in A$ significa che x appartiene ad A (elemento di A)
2. $ø$ significa insieme vuoto = $\{\}$ 
3. $A:=\{x:p(x)\}$ `:` significano tale che, serve per definire le proprietà
### notazione
$\mathbb{N}:=\{0, 1, 2, 3, ecc...\}$
$\mathbb{P} := \{1, 2, 3, ecc...\}$
$\mathbb{N} := \{...,-2, -1, 0, 1, 2,  ...\}$
$\mathbb{Q} := \{\frac{a}{b}: a, b \in \mathbb{Z}\}$
$\mathbb{R} := numeri-reali\}$
$\mathbb{C} := numeri-complessi\}$
$[a] := \{1, 2, 3, ..., a\}$   

# 1.2 operazioni tra insiemi
## definizioni
1.  ==Uguaglianza:== 2 insiemi si definiscono uguali se hanno gli stessi elementi $A = B$
2.  ==Sottoinsiemi:==  A è un sottoinsieme di B se ogni elemento di A appartiene a B. si scrive $A \subseteq  B$ Inoltre $A=B \iff A \subseteq B \wedge B \subseteq A$ .
3.  ==Sottoinsiemi propri:== A è un `SOTTO ISIEME PROPRIO` di B, scriviamo che $A \subset B$: $A \subseteq B \wedge A \not= B$ 
4.  ==Intersezione:==  $A \cap B := \{x \in A \wedge x \in B\}$ 
 5. ==Unione:== $A \cup B :=\{x \in A \vee x \in B\}$ 
## proprietà
siano A, B, C insiemi:
- proprietà commutativa
  $A \cup B = B \cup A$ 
  $A \cap B = B \cap A$ 
- proprietà associativa
  $A \cup (B \cup C) = B \cup (A \cup C)$
  $A \cap (B \cap C) = B \cap (A \cap C)$
- proprietà distributiva
  $A \cap (B  \cup C) = (A \cup B) \cap (A \cup C)$
  $A \cup (B  \cap C) = (A \cap B) \cup (A \cap C)$ 
## definizioni
1. Complementare: è l'insieme universo senza quel insieme: $C_A := \{x \in U : x \not\in A$}. si può usare $A'$ per indicarlo
   ![[Drawing 2024-12-21 17.15.49.excalidraw.png]]

3. Differenza tra 2 insiemi: $A \setminus B := \{x \in A : x \not \in B\}$  
   ![[Differenza_insiemi.excalidraw.png]]
4. differenza simmetrica: $A \triangle B := (A \setminus B) \cup (B \setminus A)$
   ![[differenza_simmetrica.excalidraw.png]]   
5. l'insieme potenza di A $P(A)$ è l'insieme di tutti i sottoinsiemi di A: $P(A) := \{B: B \subseteq A\}$, si scrive anche $2^A$ . Per esempio : $P({1, 2})  = \{\emptyset, \{1\}, \{2\}, \{1,2\}\}$ 
## Tavole di verità
siano A, B, C insiemi, implica che ci sono 8 possibilità:
- $x \in A \vee x \not\in A$
- $x \in B \vee x \not\in B$ 
- $x \in C \vee x \not\in C$
$$
\begin{array}{|c|c|c|c|c|c|c|c|}
\hline
A & B & C & B \cap C & A \cup (B \cap C) & A \cup B & A \cup C & (A \cup B) \cap (A \cup C) \\
\hline
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 & 0 & 0 & 1 & 0 \\
0 & 1 & 0 & 0 & 0 & 1 & 0 & 0 \\
0 & 1 & 1 & 1 & 1 & 1 & 1 & 1 \\
1 & 0 & 0 & 0 & 1 & 1 & 1 & 1 \\
1 & 0 & 1 & 0 & 1 & 1 & 1 & 1 \\
1 & 1 & 0 & 0 & 1 & 1 & 1 & 1 \\
1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 \\
\hline
\end{array}
$$
con la tavola di verità possiamo vedere che i valori corrispondono quindi abbiamo dimostrato che effettivamente è verificata l'uguaglianza

## leggi di De Morgan
siano A e B insiemi, allora:
1. $(A \cup B)' = A' \cap B'$ 
2. $(A \cap B)' = A' \cup B'$
## Diagrammi di Venn
Rappresentano il modo in cui gli insiemi secondo le formule si vanno ad intrecciare ed il risultato derivante. Ad esempli $A \cap (B \cup C)$ 
![[example_venn.excalidraw.png]]
### Osservazione
- tavola di verità: dimostra ma non aiuta immaginazione
- diagramma di Venn: aiuta l'immaginazione ma non dimostra
- ragionamento: dimostra ma ha bisogno dell'immaginazione
## prodotto cartesiano di insiemi
Il prodotto cartesiano è: $A \times B := \{(a, b) : a \in A, b \in B\}$.
### proprietà
- $(1, 2) \not= (2,1)$ l'ordine conta
- $A \times (B \cap C) = (A \times B) \cap (A \times C)$ 
# 1.3 funzioni
Siano A, B insiemi, Una funzione $f(x)$ da A in B è una legge che associa $f : A \to B, \quad \forall a \in A, \, \exists! \, b \in B \quad \text{tale che} \quad f(a) = b$ 
