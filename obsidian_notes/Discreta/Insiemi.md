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
Siano A, B insiemi, Una funzione o applicazione o mappa$f(x)$ da A in B è una legge che associa $f : A \to B, \quad \forall a \in A, \, \exists! \, b \in B \quad \text{tale che} \quad f(a) = b$ è un sotto insieme di $A \times B : (a,b) \in f$.
## tipi di funzione:
sai $f:A \to B$
- iniettiva se $a_1 \not= a_2, f(a_1) \not= f(a_2), \forall a_1, a_2 \in A$   
- suriettiva se $\forall b \in B \exists a \in A: f(a) = b$ 
- biunivoca: se una funzione è suriettiva e iniettiva
## composizione
siano $A, B, C$ insiemi, e $f: A \to B \wedge g: B \to C$, la composizione è la funzione $g \text{o} f: A \to C$
$(g \text{o} f)(a) := g(f(a)) \forall a \in A$ 
###  funzione uguaglianza:
Due funzioni si dicono uguali se: siano $f,g: A \to B, \text{f e g sono uguali (scritto f=g) se} f(a) = g(a) \forall a \in A$
### definizione
1. $f$ e $g$ iniettive, allora $f$o$g$  è iniettiva  
2. $f$ e $g$ suriettiva, allora $f$o$g$  è suriettiva
3. $f$ e $g$ biunivoca, allora $f$o$g$  è biunivoca 
### funzione identità
sia A un insieme, la funzione Identità su A è la funzione $Id_A : A \to A$ ogni elemento è associato a se stesso. $Id_A(a) := a, \forall a \in A$  
### funzione inversa
siano A e B insiemi, e $f : A \to B$ . la funzione inversa di $f$ è $f^{-1} : B \to A$. Definito da $f^{-1}(b) :=  a$: la definizione formale è:  $f^{-1} := \{(a, b) \in B \times A: (a, b) \in f\}$ sono insiemi di coppie che sono sottoinsieme del prodotto cartesiano. $Id_a$ è biunivoco, quindi $Id_A^{-1} = Id_A$ 
### definizione
siano $f, g, h$ : $A \to A$ allora:
1. $f \circ (g \circ h) = (f \circ g) \circ h$ 
2. $f \circ Id_A = f = Id_A \circ f$
3. se f è biunivoca $f \circ f^{-1} = Id_A = f^{-1} \circ f$ 
## Esempi e Controesempi
- esempio: non dimostra
- controesempio: dimostra che non è sempre vero
### definizione
sia $f : A \to B$ e sia $S \subseteq A$ l'immagine di $S$ tramite $f$ è $f(S) :=\{f(a): a \in S\}$, quindi $f(S) \subseteq B$
## gruppo simmetrico
sia $a \in \mathbb{P}$, il gruppo simmetrico di rango m è: $S_n := \{f: [m] \to [m]: f \text{ biunivoca}\}$. le funzioni che vanno da $f_n$ ad $n$ sono biunivoche.
Gli elementi di $S_n$ si dicono permutazioni se $f \in S_n$ scriveremo $f = \{a_1, a_2, ..., a_n\}$ sequenza di $n$ numeri dove $a_1 := f(1), a_2 := f(2)$. 
#### esempio
$S_3 = \{123, 132, 213, 213, 312, 321}
## osservazione
siano $f, g \in S_n, f = \{a_1, \dots, a_n\}, g =\{b_1, \dots, b_n\}$, allora $f \circ g = ab_1, ab_2, \dots, n$
### esempio
$n = 7, f = \{2_1, 6_2, 1_3, 7_4, 4_5, 3_6, 5_7\}, g = \{6_1, 1_2, 7_3, 2_4, 4_5, 5_6, 3_7\}$  
$f \circ g = \{3, 2, 5, 6, 7, 4, 1\}$
qui quello che accade è che prendi l'indice e dici: "mettiamo al primo post l'elemento numero 2, poi mettiamo al secondo posta l'elemento numero 6", quindi l'indice indica il posto in cui va, il numero indica l'indice dell'altro insieme in cui va il numero.
$g \circ f = \{1, 5, 6, 3, 2, 7, 4\}$

### altro esempio
$n_5, f = \{3, 1, 4, 2, 5\}, g = \{5, 1, 3, 4, 2\}$
$f \circ g = \{5, 3, 4, 2, 1\}$ 
## osservazione
$f \in S_n, f = a_1, \dots a_n$, allora $f^{-1} = {b_1, \dots, b_n}$ dove b è la posizione d i $i$ in $n$ 
$\{a_1, \dots, a_n\} (\forall i = \{1, \dots, n\})$ 
### esempio
 $n = 7, f = \{2_1, 6_2, 1_3, 7_4, 4_5, 3_6, 5_7\} = f^{-1} = \{3, 1, 6, 5, 7, 2, 4\}$
 questo perché bisogna prendere gli indici dei numeri cambiarli con i numeri, quindi $2_1 \to 1_2$, e posizionare 1 in posizione 2, 3 in posizione 1 ecc... Questo è perché $f \circ f^{-1} = Id_A = f^{-1} \circ f$ :
 $f \circ f^{-1}=\{1, 2, 3, 4, 5, 6, 7\}$
# 1.4 relazioni
Siano A e B insiemi, una relazione binaria è un sottoinsieme, $A \times B : R \subseteq A \times B$. Per definizione $A \times B= \{(a, b): a \in A \land b \in B\}$. Con $a \not R b$ si indica che $(a, b)  \not \in R$.
### esempio
$A = \{1, 2, 3\}$  $b = \{0, 1, 2, 3, 4\}$. $A \times B= \{(1, 0),(1, 1), (1, 2),(1, 3),(1, 4),(2,0),(2,1),(2, 2), (2, 3), (2, 4),(3, 0),(3, 1),(3, 2), (3, 3), (3, 4)\}$
## relazione su un insieme
una relazione su un insieme A è una relazione $A R A$, 
### esempio
$R = \{(a, b)\}: \text{a è divisibile da b}\}$, $A = \{1, 2, 3, 4, 5, 6\}$
$R = \{(1,1),(1,2),(1,3),(1,4)(1,5),(1,6),(2,2),(2,4),(2,6),(3,3),(3,6),(4,4),(5,5),(6,6\}$
### osservazione
Noi sappiamo che una relazione $ARA \subseteq A \times A$, se A contiene n elementi, allora $A \times A$ contiene $n^2$ elementi. Per trovare tutti i possibili sottoinsiemi di $A \times A$, quindi l'insieme potenza di  $P(A \times A)$, quindi $2^{n^{2}}$, che sarebbe la sua cardinalità.
Quindi il numero di relazioni di $A \times A$ è $2^{n^{2}}$.  
## Tipi di relazioni
1. riflessiva
   una relazione R su un insieme A è chiamata riflessiva se $\forall a \in A, (a, a) \in R$
   ### esempio
   $A = \{1, 2, 3, 4\}$, 
   $R_1 = \{(1,1), (1, 2),(2,2),(2,3),(3,3),(3,4)\}$, è riflessiva perché contiene tutti i (n,n) 
   $R_2$ = $\{(1,1),(1,2),(2,1),(3,1),(4,4)\}$ non è riflessiva perché non contiene (3,3).
2. irriflessiva
   una relazione R su un insieme A è chiamata irriflessiva se $\forall a \in A, (a, a) \not \in R$ 
   ### esempio
   $A = \{1, 2, 3, 4\}$, 
   $R_2$ = $\{(1,2),(2,1),(3,1),\}$, non contiene $(1,1)$ o $(2,2)$ 
3. simmetrica
   una relazione R si definisce simmetrica su un insieme A se $\forall a, b \in A, (a,b) \in R\implies (b,a) \in R$
   ### esempio
   R =$\{(1,1),(2,1),(1,2),(2,2)\}$ è simmetrica
4. relazione transitiva
   una relazione R su un insieme A si chiama transitiva se $\forall a, b, c \in A, (a, b) \in R \land (b,c) \in R \implies (a, c) \in R$ 
   ### esempio