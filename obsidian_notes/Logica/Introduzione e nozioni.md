# ragionamento
partendo da delle premessi si giunge a delle conclusioni, sopratutto per dimostrare affermazioni.
in particolare ce ne sono 2: per assurdo e per induzione
## per assurdo
significa prendere vera la negazione di un affermazione $P$, quindi $\neg P$, per poi andare a trovare l'assurdo che può avere diverse forme:
- che sia vera e falsa,
- che non possa essere ne vera ne false
- che $Q$ è falsa ma anche $\neg Q$ è falsa
- ...
### definizioni
1. funzione iniettiva se: $\forall x, y \in A, x_1 \not= x_2 \implies f(x_1) \not= f(x_2)$ 
2. funzione suriettiva se: $\forall x \in A, \exists y \in B: y = f(x)$ 
3. funzione biunivoca se è iniettiva e suriettiva.
1. se $f$ è iniettiva, allora $|A| \leq |B|$ 
2. se $f$ è suriettiva, allora $|A| \geq |B|$ 
2. se $f$ è biunivoca, allora $|A| = |B|$ 
la grandezza di un insieme si definisce cardinalità.

### teorema di Cantor
il teorema di Cantor si interroga sulla esistenza tra il numero di elementi di $\mathbb{N}$ e l'insieme potenza $P(\mathbb{N})$, quindi un numero associato a un sottoinsieme di $\mathbb{N}$, quindi $\forall n \in \mathbb{N}, \exists A_n \subseteq \mathbb{N}$.
Per farlo da una definizione per assurdo, e dice che deve essere biunivoca, quindi $|A| = |B|$, devono avere la stessa cardinalità. Per farlo usa la dimostrazione per assurdo:
#### dimostrazione
supponiamo che esista, quindi $0 \to \{\emptyset\}$, $1 \to \{1\}$,  $3 \to \{1, 2\}$, ecc...
okk. ora che abbiamo definito questo particolare, dobbiamo definire l'insieme preso da Cantor:
- $C = \{n \in \mathbb{N} : n \not \in A_n\}$, quindi $n$ non deve stare nell' insieme a cui è mappato.
- però siccome $C$ è un sottoinsieme, deve essere mappato con un numero $k$, quindi $k := C$ 
- ma quindi il numero k appartiene o no a questo insieme?, se sì, allora per definizione k non dovrebbe appartenerci perché C non contiene gli indici degli insiemi che contengono se stessi.
- se invece C non contiene k, allora C deve contenere k, perché k non è contenuto in C.
- E questo crea l'assurdo che è contenuto e non
## dimostrazione per induzione
la dimostrazione per induzione si basa sul fatto che per dimostrare una ipotesi matematica possiamo partire dal caso base $P(n_0)$, che sarebbe il primo valore della sequenza, e poi constatare se è vero per $P(n+1)$.
### esempio
prendiamo la funzione $n^2 +3n + 5$ è dispari $\forall n \geq 0$. 
questa si dimostra così:
- PB: $0 + 0 + 5 \implies$ dispari, quindi il passo base è verificato
- PI:
$$
\begin{aligned}
&(n+1)^2 + 3(n+1) + 5 = \\
&n^2 + 2n + 1 + 3n + 3 + 5 =\\
&n^2 + 3n + 5 + 2n + 4 =\\
&n^2 + 3n + 5 + 2(n+2)=\\
\end{aligned}
$$
perciò la prima parte $n^2 + 3n + 5$ è dispari per definizione e  $2(n+2)$  è sempre pari, quindi il tutto sarà sempre dispari.


