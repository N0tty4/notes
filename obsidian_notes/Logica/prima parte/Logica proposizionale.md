# introduzione
Il linguaggio naturale è ambiguo, quindi ci serve un linguaggio non ambiguo. A questo ci serve la logica proposizionale, ossia la logica che studia le proposizioni (enunciati semplici che possono essere $T$ o $F$ ) e le loro relazioni.
# lettere proposizionali 
Sono le variabili booleane, possono assumere valori $F$ o $T$, e le indichiamo con le lettere $s, p, q , r, \dots$ 
## connettivi
A partire dalle lettere proposizionali possiamo costruire delle formule più complesse con i connettivi, che sono:
- And, or e il not sono i più usati, $\neg$ rende vero il false e false il vero, $\land$ è vero quando entrambe sono vere, $\lor$ è falso quando entrambe sono false.
$$
\begin{array}{|c|c|c|c|c|}
\hline
p & q & \neg p & p \land q & p \lor q \\
\hline
T & T & F & T & T \\
T & F & F & F & T \\
F & T & T & F & T \\
F & F & T & F & F \\
\hline
\end{array}
$$
- poi anche implicazione $\implies$ e equivalenza $\leftrightarrow$:
$$
\begin{array}{|c|c||c|c|}
\hline
p & q & p \implies q & p \iff q \\
\hline\hline
T & T & T & T \\
T & F & F & F \\
F & T & T & F \\
F & F & T & T \\
\hline
\end{array}
$$
## formule ben formate
non tutte le possibili combinazione sono interpretabili, tipo $\neg p \lor q \leftrightarrow$ non è corretta, quindi bisogna stabilire cosa è una formula ben formata:
1. se $f$ è una f.b.f, allora anche $\neg f$ lo è
2. se $f$ e $g$ sono f.b.f, allora che $f \circ g$ è una f.b.f, con $\circ$ indichiamo un connettivo.
3. nient'altro lo è
### considerazione
se $\forall$ f.b.f $\exists$ una interpretazione, allora $\forall$ interpretazione $\exists$ almeno una f.b.f.
per trovarle bisogna identificare quando è true e quando è false, per poi andare a unire con un $\lor$ tutte le combinazioni che sono $T$.
## costanti
le costanti sono delle variabili booleane che sono o sempre vere o sempre false
- $p \land f = f$, $p \land t = t$
- $p \lor f = p$, $p \lor t = t$ 
- $t \lor f = t$, $t \land f = f$
## interdipendenza dei connettivi
non tutti i connettivi sono essenziali, molti sono usati per rappresentare delle tabelle di verità che si possono esprimere con formule più complesse, tipo
- $p \implies q$ si può esprimere come $\neg p \lor q$ 
- $p \leftrightarrow q$ come $(p \implies q) \land (q \implies p)$ e come $(p \land q) \lor (\neg p \land \neg q)$ 
quindi tutto si può riportare a $\neg$ e $\lor$
### esercizi:
1. scrivere $p \land q$ in termini di $\neg$ e $\to$:
   $\neg(p \to \neg q)$ 
2. scrivere $\equiv$ in termini di $\land$ e $\to$:
   $(p \to q) \land (q \to p)$
3. scrivere $\lor$ con $\to$:
   

### nor e nand
 il nor è la negazione dell' or e il nand è la negazione dell' and:
$$
\begin{array}{|c|c||c|c||c|c|}
\hline
p & q & p \lor q & \neg(p \lor q) & p \land q & \neg(p \land q) \\
\hline\hline
T & T & T & F & T & F \\
T & F & T & F & F & T \\
F & T & T & F & F & T \\
F & F & F & T & F & T \\
\hline
\end{array}
$$
possono essere usati per rappresentare tutti i connettivi logici:
- $\neg p = p \downarrow q$ 
- $p \lor q = \neg(p \downarrow q) = (p \downarrow p) \downarrow (p \downarrow q)$
la stessa cosa vale il nand
# tautologie, contingenze e contraddizioni
le tautologie sono tutte quelle formule che sono sempre vere: $\neg(p \lor q) \implies (\neg p \land \neg q)$ 
$$
\begin{array}{|c|c||c|c|c|c|}
\hline
p & q & p \lor q & \neg(p \lor q) & \neg p \land \neg q & \neg(p \lor q) \implies (\neg p \land \neg q) \\
\hline\hline
T & T & T & F & F & T \\
T & F & T & F & F & T \\
F & T & T & F & F & T \\
F & F & F & T & T & T \\
\hline
\end{array}
$$

le contraddizioni sono tutte quelle formule che sono sempre false: $p \land \neg p$
$$
\begin{array}{|c|c|c|}
\hline
p & \neg p & p \land \neg p \\
\hline
T & F & F \\
F & T & F \\
\hline
\end{array}
$$
## condizione necessarie e sufficiente
diciamo che $A$ è sufficiente affinché si verifichi $B$, oppure scritto così: $A \implies B$.
## sufficiente
nascere sul territorio degli USA è condizione sufficiente per avere la cittadinanza. quindi $\text{nascere sul territorio USA} \implies \text{cittadinanza USA}$ 
### attenzione
$\text{hai cittadinanza USA} \not \implies \text{sei nato negli USA}$, ad esempio Arnold Schwarzenegger non è nato in USA ma ha la cittadinanza.
### contronominale
$A \implies B$ è equivalente a $\neg B \implies \neg A$, quindi: se non hai la cittadinanza USA, allora non sei nato in USA
## necessaria
A è condizione necessaria affinché si verifichi B, allora se si è verificato B, allora si è verificato A.
- $B \implies A$
- se B allora A
- solo se A, allora B, significa che senza la condizione A non si può verificare B.
### contronominale
$B \implies A$ è equivalente a $\neg A \implies \neg B$
#### esempio
nascere sul territorio USA, è condizione necessaria per diventare presidente degli USA.
### osservazione
dire che A è necessario affinché si verifichi B, equivale a dire che B è sufficiente affinché si verifichi A
## necessaria e sufficiente
A è condizione necessaria e sufficiente affinché si verifichi B
- $B \implies A$ 
- $A \implies B$ 
queste 2 insieme portano a $A \iff B$ 
## tableaux 
Per verificare se una formula è una tautologia o no basta saper usare il metodo dei tableaux:
iniziamo dicendo che come abbiamo visto una f.b.f si può sempre ricondurre a una un $\land$ o a un $\lor$ di due formule. Tipo $f_1 \implies f_2 = \neg f_1 \lor f_2$, oppure $\neg (f_1 \implies f_2) = f_1 \land \neg f_2$.
da qui possiamo distinguere 2 casi: $\alpha$ e $\beta$ formule:
- le $\alpha$ formule sono quelle di tipo $\land$ e sono messe una sollo l'altra $\frac{\alpha_1}{\alpha_2}$ 
- le formule $\beta$ sono quelle formule che vengono divise in 2 rami $\beta$ = $\beta_1$ $\beta_2$ 
- $f_1 \iff f_2$ diventa $(f_1 \land f_2) \lor (\neg  f_1 \land \neg f_2)$ 
##### procedimento
innanzitutto partiamo dicendo che se$f$ è una tautologia, allora $\neg f$ è una contraddizione per definizione. Quindi basterà trovare un ramo che non si chiude per poter dire che esiste una forma in cui è vera. Quindi prima semplifichi finché non si ottengono tutti or e and, e poi si applica il procedimento con le $\beta$ formule e le $\alpha$ formule. dopo aver derivato tutti i rami, verificare se esistono le variabili nello stesso ramo che sono asserite e negate allo stesso tempo.
### Insiemi soddisfacibili e correttezza del metodo
Diciamo che $F$ è una formula `soddisfacibile` se esiste una interpretazione in cui è $T$ (solo se è una tautologia o una contingenza).
Diciamo che un insieme $S$ di formule è soddisfacibile, se esiste una interpretazione in cui tutte le formule di $S$ sono $T$.