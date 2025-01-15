# 06
contare le parole
```python
a0 = 'programmazione dei calcolatori con laboratorio'
a1 = 'linguaggio di programmazione'
```
parola è un carattere alfabetico maiuscolo.
## implementazione
Ci serve un puntatore che conti le parole, se è una lettera allora smette di contare, se è uno spazio allora aumenta di uno. dobbiamo avere una variabile in e una out:
- se $c \in [a, z]$, allora sarei dentro una parola  
- se $c \not \in [a, z]$, allora non sono dentro una parola
bisogna iniziare dal carattere out, da qui si parte.
```python

def lettera(c):
	return c >= 'a' and c <= 'z'

def conta_parole(a):
	'''
	questa è una docstring
	Input: a una stringa
	Return: numero di parole nella stringa
	'''
	parole = 0
	in_parole = False
	
	for c in a0:
		if lettera(c):
			if not in_parola:
				parole += 1
				in_parola = True
	
		else:
			if in_parola:
				in_parola = False
	return parole

print(conta_parole(a0))
```
## funzione help
```python
help(len)
```
prende in input una funzione e ne ritorna la guida

```python
help(conta_parole)
```
però può prendere in input anche una funzione creata da noi e return la doc-string che abbiamo scritto noi
## complessità temporale

```python

def lettera(c):
	return c >= 'a' and c <= 'z'

def conta_parole(a):
	'''
	questa è una docstring
	Input: a una stringa
	Return: numero di parole nella stringa
	'''
	parole = 0
	in_parole = False
	
	for c in a0: #numero lineare di operazioni
		if lettera(c): # numero costante di operazioni c0
			if not in_parola: # c1 costante
				parole += 1 # c2 costante
				in_parola = True #c3 costante
	
		else:
			if in_parola: #c4 costante
				in_parola = False #c5 costante
	return parole

print(conta_parole(a0))
```
- costante significa che $\forall x: f(x) = y$, il tempo per creare y non cambia al cambiare di x, quindi per ogni input l'output ci metterà sempre lo stesso tempo, tipo, senza contare il for loop, la somma delle operazioni costanti è costante.
- lineare, significa che al crescere di x, cresce linearmente anche y. e le costanti di ordine inferiore nel calcolo della complessità perdono di importanza, in questo caso è il for loop è quello predominante, quindi è lineare
### studio di questa funzione
$n\cdot c + d$, più n cresce più d diventa irrilevante
$c\cdot n^2 + c'\cdot n + d$, possiamo ignorare c'e d perché $n^2$ sarà troppo più grande, oltre a ciò butto via le costanti moltiplicative $c$, perché è difficile calcolare la costante, perché abbiamo troppe condizioni da verificare e perché già ci vanifica il fatto che assumiamo che tutte le operazioni elementari valgano 1.
### O-grande
la notazione O-grande \[O()] serve per capire il costo temporale di un algoritmo, viene utilizzato il caso peggiore.
# 07
## ripresa O-grande
### definizione
$T(n) \in \text{O}(f(n))$ questo significa $T(n) \leq f(n)$ se $n \geq n_0$, per esempio: $T(n) = 6n + 4 \in \text{O}(n)$, quindi $T(n) \leq c\cdot n$, quindi deve esistere un valore di $c$ moltiplicato per n tale che sia maggiore della funzione. Ma se dovesse esistere anche $T(n) \geq c'n$, per $n \geq n_0$, allora avrò anche il $\theta$.
## foo
diciamo che n = dimensione dell'input e A = un algoritmo, allora T(n) è il tempo di calcolo o numero di operazioni da A con l'input dato.
Può essere come $T(n) = 2n^2 + \frac{n}{4} + 9$, oppure può essere una funzione definita a tratti.
### esempio
$T(n) = 2n^2 + \frac{n}{4} + 9$,in questo caso, prendiamo solo $n^2$, se questo è vero, allora: 
- $T(n) \in \text{O}(n^2)$ questa è vera.
- $T(n) \in \text{O}(n^3)$ è anche vera.
quindi la O(n) ci dice che una funzione cresce come $\text{O}n^2$ oppure al di sotto.
## $\theta$-notation
la $\theta$-notation ci dice non che una funzione cresce all'incirca, ma ci dice che cresce esattamente così, allora diciamo che $T(n) = \theta(n^2)$. perché $\theta$ è sia un limite inferiore che un limite superiore.
## built-in function ==in==
```python
for c in x:
```
$$
T(n)
\begin{cases}
i+1, & \text{dove $i$ t.c $x[i]=c$} \\
n & \text{se $c \not \in x$.}
\end{cases}
$$
nel caso peggiore T(n) = $\theta$(n), quindi posso dire che la complessità è lineare.
## cambiare carattere stringa
```python
a = 'programmazione'
a[0] = 'P'
```
questo è un errore, le stringhe in python sono immutabili, quindi bisogna creare una nuova stringa
```python
a = 'P' + a[1:]
print(a)
```
quindi se la strina è grande n, l'operazione costerà n.
## assegnazione multipla
```python
a, b = 10, 12
```
le variabili non devono essere maggiori delle assegnazioni o il contrario.
## tuple
```python
t = 10, 11, 12 #(10, 11, 12)
```
questo crea una tuple, può contenere ogni dato, anche le tuple stesse.
Tutte le operazioni che si possono fare sulle stringhe si possono fare sulle tuple. \[len(), slice, concatenare]
```python
print(len(t))
print(t[2])
print(t[::-1]) # creera una nuova tupla
print(2*t)
print(t+(1,2)) # creera una nuova tuple
```
le tuple non si possono cambiare.
```python
t = ('a', 'b', 'c')
x, y, z = t # spacchettamento
t = x, y, z # impacchettamento 
```
## liste
le liste sono come le tuple ma sono mutabili, tutte le operazioni sono valide: len, indicizzazione, slicing, iterazione, concatenazione, ripetizione, spacchettamento, ma anche cancellazione.
```python
a = [0, 'stringa', (1, 2)]
a[0] = '169'
print(a)
del(a[1])
print(a)
```
### aggiungere in coda
```python
a = []
a.append(100)
print(a)
a.append(200)
print(a)
```
si utilizza un metodo, `.append()`, la funzione append non restituisce nulla, non ha output (`None`), ma ha un effetto collaterale.
## esempio
```python
a = [('A', 2, 7),('B', 3, -1),('C', 0, 1),('D', -2, -2)]
r = 2.0
```
calcolare la distanza al più r da (O, 0, 0)
```python
b = []

for n, x, y in a:
	if x**2+y**2 <= r**2: # formula per trovare la distanza O(1)
		b.append(n) # tempo costante O(1)

print(b)
```
il costo temporale è $O(n)$. Append è stata integrata in modo da essere intelligente, non deve ogni volta che aggiunge un elemento fare una nuova lista.
$$
append
\begin{cases}
O(1) & \text{posso aggiungere}\\
O(n) & \text{devo aumentare spazio}
\end{cases}
$$
quindi, se eseguo una operazione costosa, sto tranquillo che per i prossimi n append, l'operazione costa 1, tradotto esce: $n + 1 + 1 + \dots + 1$, il costo è $n + n$ perché prima dai memoria, e poi per n volte la memoria appendi, quindi singolarmente, una $\frac{n+n}{n+1}$, costa $O(1)$.
# 08
```python
def trova_posizioni(a, v):
    '''
	Input: a una lista, v un valore
	Return: una lista di interi contenente le posizioni di v in a
	'''
    b = []
    for i in range(len(a)): #len(a) = O(1), ma il for = O(n)
        if a[i] == v: # O(1)
            b.append(i) #O(1)
	return b #O(1)

```
in questo caso il costo di questa operazione sarà il valore del $O(n)$ più grande. Un'altro modo per poter scrivere questa funzione con una list comprehension è:
```python
a = [1, 3, 4, 5, 2, 5, 7, 5, 3, 1, 3, 4]
v = 3
b = [i for i in range(len(a)) if a[i] == v]
```
## complessità temporale esercizio
Complessità temporale dell'esercizio precedente (lezione 3)
```python
b = ''
for x in a: # ha costo O(n)
	if x in 'aeiouAEIOU':
		b += '*' # qui si nasconde concatenazione, viene fatta la copia con +=
		# quindi ha cost O(n)
	elif x >= '0' and x <= '9':
		b += '#'
	else:
		b +=' '
print(a)
print(b)
```
in questo caso si sta nascondendo un ciclo for nascosto, infatti quando andiamo a fare `b += ' '` o qualunque altro tipo di concatenazione, si crea in realtà sempre una nuova lista. Descriviamolo sotto un profilo matematico:
$$
\sum_{i = 1}^{n} i = 1 + 2 + \dots + (n-1) + n
$$
questo implica che secondo la somma gaussiana si arriva alla formula:
$$
\frac{n(n+1)}{2} 
$$
quindi il costo del nostro algoritmico è quadratico, quindi $O(n^{2})$.
### miglioramento
```python
b = []
for x in a: # ha costo O(n)
	if x in 'aeiouAEIOU':
		b.append('*') # qui si nasconde concatenazione, copia lista +=
		# quindi ha cost O(n)
	elif x >= '0' and x <= '9':
		b.append('#')
	else:
		b.append(' ')
print(a)
print(b)
```
## .join()
serve per concatenare una lista con un separatore in mezzo, funziona mettendo il carattere da usare come separatore prima del punto, poi tra le parentesi mettere l'insieme di stringhe da concatenare.
```python
print(''.join(b)) #ha costo O(n)
```
## len(a)
serve per misurare la grandezza di un oggetto.
### sintassi
```python
len(value) #value non puo essere un inter
```
### funzionamento
per farlo va a vedere il metodo `__len__(self)`:
```python
class MyClass:
	def __len__(slef):
		return 42

obj = MyClass()
print(len(obj)) # output = 42
```
and stop, non ha altri parametri opzionali come print, 
## aliasing
```python
a = [1, 2, 4, 3, 5, 3]
b = a
```
qui quello che accade è che assegniamo ad `a` una lista, però a `b` non diamo una copia di `a`, ma diamo il riferimento ad `a`, quindi andando a modificare a andremo `b` modificare `a` e viceversa.
quindi quello che si può fare è:
```python
a = [1, 2, 4, 3, 5, 3]
b = a[:]
```
così da assegnare a `b` una copia di `a`, senza dare il suo riferimento
## esercizio
```python
def del_item(a, v):
	'''
	Input: a un alista, v un valre
	Return None

	Effetto collaterale: da a elimina tutte le occorrenze di v
	'''

	for i in range(len(a)): # errore, index out of range
		if a[i] == v:
			del(a[i])
```
praticamente quello che succede è che la funzione `range()` in `range(len(a))` prende in input un valore e creerà una sequenza di numeri che manterrà durante tutta la iterazione, proprio perché il `for i in range(len(a))` va a 0 fino a n-1, quindi quello che non è creare sequenze ogni volta, ma andare al prossimo numero della sequenza.
quindi bisogna fare:
```python
i = 0
while i < len(0):
	if a[i] == v:
		del(a[i]) # 0(n)
	else:
		i += 1
		
```
`del(a[i])` sposta di una posizione a sinistra, quindi nel caso peggiore dovrà fare n copie per n operazioni (se deve eliminare tutto)
# 09
la funzione ha i parametri e gli argomenti, i parametri o formal arguments possono avere qualsiasi nome, anche nomi di variabili definite nello stesso blocco di codice, perché hanno valenza solo nel blocco della funzione stessa.
```python
def foo(x, y): #paramentri o formal arguments
	return x + y

foo(1, 2) #argomenti o actual arguments
x, y = 2, 1
```
```python
def f(x):
	a = x+[0]*g(x) # x + [0]*g(x) concatena la lista x con tre 0 dentro la lista
	# x + [0, 0, 0]

def g(x):
	n = len(x)
	return n

L = [0, 1, 2]
n = f(L)
print(L)
```
## del istanze lista migliorata
Questa soluzione è sbagliata, perché non rispetta le specifiche, infatti ha un return questa funzione, ma non dovrebbe averla
```python
def del_item(a, v):
	b = []

	for x in a:
		if x != v:
			b.append(x)

	return b
```
soluzione corretta, ma non ancora efficiente, l'ultimo while ha costo quadrato.
```python
def del_item(v, a):
	b = []

	for x in a:
		if x != v:
			b.append(x)

	i = 0
	while i < len(b):
		a[i] = b[i]
		i += 1

	wile i < len(a):
		del(a[i])
```
mentre la soluzione corretta elimina gli ultimi elementi in fondo, proprio perché sono quelli che sono i numeri da eliminare:
```python
def del_item(v, a):
	b = []

	for x in a:
		if x != v:
			b.append(x)

	i = 0
	while i < len(b):
		a[i] = b[i]
		i += 1

	wile i < len(a):
		del(a[-1])
```
la lista di appoggio `b` occupa spazio tanto quanto la dimensione dell'input, a differenza della prima funzione che occupa spazio lineare proprio perché non ha strutture di appoggio.
La complessità spaziale occupata si misura solo con lo spazio supplementare, non con la grandezza dell'input, proprio perché quello non lo possiamo controllare ma solo analizzare.
# 10
```python
a = [('A', 6), ('B', -2), ('C', 0), ('D', 5), ('E', 3)]
# risultato *B*C**E*DA*
```
bisogna farlo senza usare memoria aggiuntiva e senza modificare gli input, perciò calcoliamo lx e rx degli estremi dell'intervallo
```python
lx = a[0][1]
for _, p in a: # '_' si usa per indicare una variabile muta, che non ci sreve
	if p <lx:
		lx = p
```
l'esito tra tuple è definito da posizione per posizione, viene usato il confronto lessico grafico
## confronto tra tuple o stringhe
```python
print((1, 3) < (1, 2))
```
se i numeri in posizione n sono uguali, allora va alla posizione n+1, però non possono confrontare tipi diverso di dati
```python
print(('A', 3) < (3, 2))
```
però se le tuple hanno dimensione diversa, se sono tutte uguali, allora la tuple con elementi minori sarà la più grande.
```python
print(("A", 3) < ("B", 2))      # False
print((2, 3) < (1, 2, 4))       # True
print((1, 2, 3) < (1, 2, 3, 4)) # True
```
## max
ci dice il massimo di una lista di numeri, è una funzione incorporata nel linguaggio.
```python
max([1, 2, 3, 0])
```
la funzione `max()` può avere anche il parametro, che è una funzione, `key=func`, attribuisce un valore ad ogni elemento della lista un valore che decidiamo noi al posto del valore di default.
### implementazione max()
il parametro delle funzioni incorporate delle funzioni min() e max() è lo stesso della funzione Max().
```python
def Max(a, key=None):
	'''
	Input: a una lista, key una funzione
	Output: e in a tale che key(e) = max(key(x) per x in a)
	se key == None, massimizza e, quindi funzione identità
	'''

	if key == None:
		key = identity

	r_max = a[0]
	v_max = key(a[0])

	for e in a:
		if key(e) > v_max:
			r_max, v_max = e, key(e)
	return v_max

def t1(e):
	return e[1]

print(Max(a))
print(Max(a, key=t1))
```
## problema iniziale
```python
def t1(e):
	return e[1]

a = [('A', 6), ('B', -2), ('C', 0), ('D', 5)]
lx = min(a, key=t1)[1]
rx = max(a, key=t1)[1]
```
 Qui sto dicendo che lx è uguale al minimo della chiave della funzione e, quindi \[1], quindi andrò a prendere solo gli elementi interi della funzione.
 Però mi restituisce una tuple, ma io voglio prendere solo l'elemento intero, quindi dopo aver preso la tupla max, vado adire di prendere l'elemento numero due della tupla.
 Quindi ho selezionato il max o min dell'intero ed ho assegnato a `lx` solo l'intero della tupla selezionata per il tipo intero.
```python
for x in range(lx, rx+1): # perché l'ulimo elemento non è incluso da range()
                          # quindi dobbiamo aggiungere 1 per includere anche 
                          # ('A', 6) in questo caso
    c = '*'
    for e, v in a:
        if x == v:
            c = e
    print(c, end= '')
print()
```
qui quello che accade è che stiamo dicendo che c è uguale al carattere `*`, e per ogni `e`, lettera nella tuple, `v` valore intero nella stringa, se il il numero nella serie generata da `range()` che parte da `lx` e finisce a `rx` è uguale a uno degli elementi interi dentro le tuple, `c = e`, quindi dentro `c` non ci sarà più il carattere `*` ma ci sarà il carattere individuato.
Altrimenti stamperemo semplicemente `*`.
# 11
