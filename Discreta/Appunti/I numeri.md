# Principio di induzione
in matematica esistono tre modi per dimostrare che $A \implies B$:
1. dimostrazione diretta
2. per assurdo
3. per induzione.
## principio di induzione
Sia $P(n), n \in \mathbb{P}$,
- se $P(1)$ è vera
- dimostrare $P(n) \implies P(n+1)$ è vero $\forall n \in \mathbb{P}$
# Principio del buon ordinamento
il "WOP" dice che sia 
$$
S \subseteq \mathbb{P}, s \not = \emptyset \implies \exists n \in S : n \leq x, \forall x \in S
$$
# Numeri complessi
definiti come $\mathbb{C} := \{a + ib: a, b \in \mathbb{R}\}$ dove $i = \sqrt{-1}, i^2 = -1$.
Sia $z \in \mathbb{C}, z = a + ib$.
Possiamo immaginarla come le coordinate nel piano di Gauss, dove la $ib$ è l'asse immaginari.
## def:
- $a$ è la parte reale di $z$
- $b$ è la parte immaginaria di $z$
- $i$ è la unita immaginaria
- il complesso coniugato di $z$ è $\overline{z} := a - ib$
## operazioni
siano $w, z \in \mathbb{C}$, dove $w = a + ib, z = c + id$ 
- somma:
	- $w + z := (a+c) + i(b+d)$
	- $z_1 = 1 + 3i, z_2 = 1-i \implies z_1 + z_2 = 1 + 1 +3i - i = 2+2i$ 
- prodotto:
	- $w \cdot z := (a+ ib)(c + id) = ac + iad + icb -bd$
	  basta moltiplicare termine per termine e ricordarsi che $i^2$ = -1
- Divisione:
	- bisogna moltiplicare e dividere il denominatore in modo da ottenere $A^2-B^2 = (A-B)(A+B)$  
	- $\frac{a+bi}{c+di} = \frac{a+bi}{c+di}\frac{c-di}{c-di} = \frac{ac-adi+bci-bdi^2}{c^2-(di)^2} = \frac{ac + bd}{c^2+d^2} + \frac{bc-ad}{c^2+d^2}i$
## coordinate polari
al posto di scrivere in coordinate cartesiane, possiamo sfruttare l'angolo e la lunghezza del segmento che connette il punto all'origine.
- $\rho = \sqrt{a^2 + b^2}$, e si definisce anche modulo di $z$ e si scrive $||z||$ 
- $\theta = \arctan(\frac{b}{a})$ se b > 0, altrimenti $\theta = \arctan(\frac{b}{a}) + \frac{\pi}{2}$ per b < 0 
- a = $\rho \cdot \cos(\theta)$
- b = $\rho \cdot \sin(\theta)$
# Numeri primi e composti
siano $a, b \in \mathbb{R}$
- si dice che $a$ è un divisore di $b$ (oppure $b$ è un multiplo di $a$), scritto $a|b$ se $\frac{b}{a} \in \mathbb{Z}$
	- $a|b \implies a \leq b$  
	- $a|b$ e $b|c \implies a|c$  
	- $a|b$ e $a|c \implies a|(bx + cy), \forall a, y \in \mathbb{Z}$
sia $a \in \mathbb{P}$
- $a$ è primo se $b|a \implies b = 1$, oppure $b = a$ e $a \geq 2$. altrimenti è composto
## numeri coprimi
Siano $a, b \in \mathbb{R}$, si definiscono coprimi se $c|a$ e $c|b \implies c = \pm1$
- ad esempio 9 10 lo sono perché i divisori di 9 sono: $\{1, 3, 9\}$ mentre i divisori di 10 sono $\{1, 2, 5, 10\}$, ed in comune hanno solo 1.
- teorema
	- sai $n \in \mathbb{P}, n \geq 2$, allora $n$ è un prodotto di primi
	- $\exists k \in \mathbb{N}$
	- $p_1, p_2, ..., p_k \in \mathbb{P}$, primi
	- tali che: n = $p_1 \cdot p_2 \cdot ... \cdot p_k$ 
- teorema
	- esistono infiniti numeri primi
- definizione
	- sai $n \in \mathbb{P}$ $n$ si dice perfetto se la somma dei suoi divisori propri, (per i divisori $\not = n$) è uguale a $n$
# algoritmo euclideo