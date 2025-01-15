I computer parlano in un linguaggio binario. Infatti rappresentano i numeri come 1 e 0, non in base 10 ma in base 2. Questo perché un numero è un concetto astratto e può avere più simboli: $(10)_{10} = (0101)_2 = (A)_{16}$ il pedice $10, 2. 16$ indicano la base, cioè quanti simboli vengono usati.
# codifiche posizionali
sono le codifiche decimali, binarie o con basi diverse, seguono lo stesso schema logico:
## logica dietro
abbiamo una variabile $b$ che rappresenta il numero di caratteri presenti (la base), quindi $b \in \mathbb{N}, b \geq 2$, ed un insieme $B$ di $b$ simboli, ognuno dei quali rappresenta un numero compreso tra $[0,(b-1)]$. Poi abbiamo una sequenza di simboli $\{x_{k-1} + x_{k-2} + \dots + x_1 + x_0\}$, dove ogni $x$ rappresenta uno dei possibili simboli $\in B$. Però ora bisogna far in modo che vengano anche rappresentate le grandezze, mi spiego meglio:
Il numero 1280 è dato da: $1(10^{3})+2(10^{2})+8(10^{1})+0(10^0)$, quindi quello che accade è che ogni numero viene prima moltiplicato per la base elevata alla posizione del numero stesso, quindi non basta scrivere questo: $\{x_{k-1} + x_{k-2} + \dots + x_1 + x_0\}$, perché sarebbe come fare $(1+2+8+0) \not = 1280$.
Allora serve modificare la nostra formula aggiungendo questo, e diventerebbe: $\{x_{k-1}b^{k-1} + x_{k-2}b^{k-2} + \dots + x_1b^{1} + x_0b^{0}\}$, così che possiamo descrivere quel comportamento la sopra.
# codifica complemento a 2
consiste nel poter rappresentare anche i numeri negativi, per farlo dobbiamo capire bene come funziona la notazione binaria:
il numero più a sinistra sarà grande il doppio rispetto a tutti i numeri messi insieme fino a lui, proprio perché è come se raddoppiassimo (visto che la base è 2). Quindi possiamo fare che i numeri che hanno 1 come primo termine siano negativi, mentre i numeri che hanno 0 siano positivi.
per esempio: |1|0|0|0| = -8, |0|0|0|1| = 1, infatti se facessimo -8 + 1, ci uscirebbe |1|0|0|1|, che sarebbe -7 in complemento a 2, perché bisogna prendere la cella più a sinistra e darle valore negativo, quindi (-8) e poi andare a sommare tutti i numeri positivi alla sua destra, quindi |1|0|0|0| + |0|0|0|1| = |1|0|0|1|, quindi -8 +1 = -7.
