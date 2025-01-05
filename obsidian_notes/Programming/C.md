# array
gli array sono fissi in C perché è definita durante la compilazione, in fatti è detta allocazione statica.
```C
int main() {
	arr[5] = {1, 2, 3, 4, 5};
}
```
# allocazione dinamica
durante l'esecuzione del programma viene deciso la dimensione dell'array. Gestire input esterni.
Se ne occupa il nostro sistema operativa attraverso certe chiamate. Ritorna l'indirizzo del primo byte allocato. Per farlo bisogna usare la libreria `<stdlib.h>`, per farlo bisogna usare un tipo di dato chiamato puntatore.
```C
#include<stdio.h>
#inlcude<stdio.h>
int main() {
	int *p;
	int f = 3;
	p = &f // soto assegnando la variabile a un puntatore
	printf("%f, %f\n", f, *p);
}
```
`p` è un puntatore a un indirizzo di una variabile `int`, con`&` assegno l'indirizzo di memoria delle variabili alla memoria.
### malloc()
serve per allocare memoria. sizeof() serve per verificare la grandezza di una variabile, infatti da architettura a architettura cambia. %p si utilizza per indicare il valore della memoria del puntatore.
```C
#include<stdio.h>
#inlcude<stdio.h>
int main() {
	int f = 3;
	p = &f // soto assegnando la variabile a un puntatore
	p = malloc(sizeof(float));
	printf("%lu, %p", sizeof(int), p);
	*p = 0 // così sto dicendo che il valore dentro la cella di memoria è 0
}
```
però possiamo allocare anche più celle di memorie collegate, come gli array
```C
#incldue<stdio.h>
#include<stdlib.h>
int main() {
	int *p = malloc(2*sizeof(int));
	*p = 12;
	*(p+1)= 13;
}
```
con questa scrittura `*(p+1)` sto usando l'aritmetica dei puntatori per andare alla prossima cela di memoria del mio array dinamico, che però può essere fatto anche da `p[1]`, come per gli array.
### free()
se vedi inizialmente `p = &f` p era assegnata a una variabile che poi è stata riassegnata con malloc(). quindi abbiamo perso la possibilità di poter accedere ancora a quella memoria. 
Per poterlo fare bisogna usare la funzione `free()`, così da restituire memoria al sistema operativo.
```C
#incldue<stdio.h>
#include<stdlib.h>
int main() {
	int *p = malloc(2*sizeof(int));
	if (p == NULL) {
		return -1
	}
	free(p)
}
```
qui invece dobbiamo verifica se il puntatore p è stato assegnato o meno a quella cella della memoria.
### array e puntatori
```C
float *crea_array_di_float(int n, float v) {
	float a[n];
	for(int i=0; i < n; i++) {
		a[i] = v;
	}
	return a;
}
```
infatti quando ritorniamo in nome dell'array non stiamo dando altro che il puntatore alla memoria per quel array.
però è ==SBAGLIATA== perché viene restituito l'indirizzo in una variabile che non contiene più niente dentro, perché fuori dalla funzione sparisce il contenuto. Infatti bisogna fare
```C
#include <stdio.h>
#inlclude <stdlib.h>
int main() {
	float *crea_array_di_float(int n, float v) {
		float *a = malloc(n*sizeof(float));
		if(a == NULL) {
		return -1
		}
		
		for(int i=0; i < n; i++) {
			a[i] = v;
		}
		return a;
	}
}
```
Attenzione, se faccio `sizeof(a)` non mi ritorna la dimensione dell'array, ma la dimensione del puntatore, quindi non bisogna confondersi. Se usata su un array statico, ritorna il numero di byte occupato dell'array.

```C
#include <stdio.h>
#include <stdlib.h>
int main() {
	float v[10] = {0, 1, 2};
	float *w = copia_array_di_float(v, sizeof(v)/sizeof(float))
}
```
gli altri elementi saranno tutti 0. Però cosa accade se passo l'array ad un'altra funzione:
```C
#include <stdio.h>
#include <stdlib.h>

int try_array_out(int *a, int n){
	printf("%d\n", sizeof(a)/sizeof(float));
}
```
questo ci darà sempre 2 perché `*a` è un puntatore, quindi, secondo la nostra architettura, avrà sempre una misura fissa, che divisa per la misura del float, farà sempre una costante.
## realloc()
```C
int main() {
	float *a = malloc(10*sizeof(float));
	a = realloc(a, 11*sizeof(float));
}
```
serve per aumentare/diminuire la grandezza di una memoria. Prende l'indirizzo della struttura e la nuova dimensione. In caso di successo ritorna l'indirizzo della memoria allocata.
Non è detto che sia la stessa. Infatti verifica che sia possibile allungare la memoria. ci sono 3 casi:
1. Il primo è che ci sia spazio a destra, allunga la memoria e fine
2. il secondo è che non c'è spazio a destra, allora cerca un nuovo spazio nella memoria abbastanza grande, per poi andare a copiare.
3. l'ultimo è nel caso in cui non c'è spazio, ritorna `None`. Il caso peggiore è `O(n)`, altrimenti `O(1)`.  
se il `ptr == NULL` allora il comportamento sarà di una malloc.
### osservazione
```C
#include <stdio.h>
#include <stdlib.h>
int main() {
	int m = 100;
	int n = 1;
	a = malloc(1*sizeof(float));
	a[0] = 10;

	for(i = 0; i < n; i++) {
		n++;
		a = realloc(a, n*sizeof(float));
		a[n-1] = n;
	}	 
}
```
qui ad esempio il costo medio è lineare, mentre il costo nel caso peggiore è $n^2$, perché nel caso peggiore la funzione `realloc()` deve prendere tutti gli elementi e ricopiarli n volte per n posti della memoria.
Quello che posso fare è aggiungere più memoria per i futuri append. Quindi quello che posso fare è raddoppiare la grandezza della memoria ogni volta che finisce.
```C

```
# structure 
è un tipo di dato che possiamo definire noi, è un contenitore che contiene dati che sono raggruppati un unico dato. Con `typedef` possiamo creare un alias per la nostra structure.
## append
qui possiamo vedere come si può andare a creare e manipolare un nuovo dato chiamato `list`  infatti nella lista abbiamo un puntatore che serve come punto di inizio per accedere alla nostra lista, poi la capacità e il numero di elementi.
```C
#include <stdio.h>
#include <stdlib.h>

struct list{	
	float *a;
	int c; // capacità
	int n; // numero di elementi
}
typedef struct list list
```
invece qui abbiamo i riferimenti alle funzioni per poterle usare anche nella funzione main che sta sopra.
```C
list init();
list append(list, float);
```
Nella funzione main abbiamo prima creato una lista `l1` alla quale diamo il return della funzione `init()` che serve per creare il primo nodo. poi andiamo a chiamare le varie funzioni `append()` per creare spazio e per aggiungere lementi.
```C
int main() {
    list l1 = init();
    l1 = append(l1, 3.12);
    l1 = append(l1, 3.14);
    l1 = append(l1, 4.14);
    l1 = append(l1, 5.14);
    l1 = append(l1, 6.14);
    l1 = append(l1, 7.14);
    l1 = append(l1, 8.14);
    l1 = append(l1, 9.14);
    l1 = append(l1, 16.14);

    for (int i = 0; i < l1.size; i++) {
        printf("%f, %d, %d\n", l1.element[i], l1.size, l1.capacity);
    }
}
```
La funzione init serve per creare il primo nodo dove andare a concatenare i vari elementi, infatti è inizializzata con `NULL, 0, 0`.
```C
list init() {
    list l1 = {NULL, 0, 0};
    return l1;
}
```
La funzione append prima vede se la capacità è uguale alla dimensione dell'array, se così fosse allora controlla se la capacità è uguale a 0, se così fosse ritorna 2, altrimenti raddoppia la capacità.
Poi al puntatore `l1.element` da il puntatore alla memoria che è grande la capacità che prima è stata raddoppiata.
poi aggiunge `l1.element[l1.size]` il valore, quindi alla ultima posizione precedente, per  poi andare ad aumentare la size. alla fine ritorna la lista.
```C
list append(list l1, float value) {
    if (l1.capacity == l1.size) {
        l1.capacity = (l1.capacity == 0) ? 2 : l1.capacity*2;
        l1.element = realloc(l1.element, l1.capacity*sizeof(float));
    }
    l1.element[l1.size] = value;
    l1.size++;
    return l1;
}
```
# stringa
è una sequenza di caratteri che termina con un carattere speciale. è memorizzata in un array fino al carattere speciale `\0`.
```C
#inlcide <stdio.h>

int main() {
    char a[] = "una stringa";
    // psazio per tutti i carateri ed anche \0
	printf("%s\n", a);

	printf("%d\n", sizeof(a));
	a[3] = '\0';
	printf("%f\n", a);
}
 ```
 Determinare la grandezza di un astringa, basta iterare gli elementi finché non raggiunge il `\0`. 
```C
int str_len(char *a) {
	int c = 0;
	while(a[c] != '\0') {
		c++;
	}
	return c;
} 
```
Però se `a = NULL`, quale è la lunghezza della stringa? Non esiste a[0], quindi ho un segmentation fault. Però non è un problema perché ci dovrà essere `\0`, quindi la stringa vuota non può essere `NULL`. 
## strcpy()
è una funzione che prende in input la stringa da copiare, la stringa destinazione, e ritorna il puntatore alla stringa destinazione. La strina di destinazione deve essere sufficientemente grande per la stringa sorgente.
```C
#include <stdio.h>
#include <string.h>

int main() {
	char a[] = "una stringa";
	char b0[1000];
	char *b1;
	strcpy(b0, a);

	b1 = malloc(sizeof(char)*(strlen(a)+1));
	strcpy(b1, a);
	printf("%s = %d", b1, strlen(b1));
}
```
## come testare se una stringa è uguale all'altra
`a` e `b0` sono diversi come array, ma uguali come stringhe, dimensioni diverse ma stesso contenuto.
Fare `a == b` è un errore perché non fa altro che confrontare i puntatori.
```C
int str_cmp(char *a, char *b) {
	// a e b 2 stringhe, -1 se a precede b, +1 se b precede a, 
	// 0 se a e b sono uguali

	int i = 0;
	while ( i < strlen(a) && i < strlen(b) && a[i] == b[i]) {
		i++;
	}

	if (i == strlen(a)) {
		if (i < strlen(b)) { // tempo quadratico perché strlen
			return -1        // calcola per ogni while. Da risolvere.
		else
			return 0;
		}
	}
	if ( i == strlen(b)) {
		return +1;
	}
}
```
## rendere lista indipendente dal tipo
```C
#include<stdio.h>
#include<stdlib.h>

int main() {
	
}
```
tutti gli elementi dell'array deve avere la stessa dimensione perché l'indicizzazione è più veloce. se conosco il la posizione del primo elemento e conosco il tipo, allora posso accedere agli altri elementi semplicemente aggiungendo il numero di elementi per la lunghezza.
$$\&(a[i])= a + i \times \text{sizeof(element)}$$
Quindi quello che posso fare è usare i puntatori. Così che i dati potranno essere sparpagliati in memoria, nell' array metteremo solo i puntatori e il tipo del puntatore, così da poter accedere al dato. 
$$
a \to [\text{tipo}, \text{ptr}]
$$
```C
#include <stdio.h>
#include <stdlib.h>

typedef struct elemento {
    char tipo;
    void *dato;  // usato per indicare un place holder per essere convertito
} elemento;

typedef struct lista {
    elemento *a;
    int capacity;
    int size;
}lista;
```
il  tipo di puntatore void serve come place holder nel mentre che gli andiamo a definire un tipo, così da renderlo generico e per far valere la aritmetica dei puntatori.
Per esempio un `char *ptr` e andiamo a fare `ptr +1` punterà al prossimo byte.

Poi abbiamo la struttura lista, la quale serve per creare le la nostra lista che conterrà il puntatore all'array della lista, la sua capacità e la dimensione.

```C
lista init();
lista append(lista, elemento);
void prntlst(lista);

int main() {
}

lista init() {
    lista lista_vuota = {NULL, 0, 0};
    return lista_vuota;
}
```
queste sono le definizioni delle varie funzioni che andremo a creare e la funzione `init()` che serve a creare un nuova lista.

```C
lista append(lista l1, elemento e) {
    if (l1.capacity == l1.size) {
        l1.capacity = l1.capacity == 0 ? 2 : l1.capacity*2;
        l1.a = realloc(l1.a, l1.capacity*sizeof(e));
    }
    l1.a[l1.size] = e;
    l1.size++;

    return l1;
}
```
La funzione `append()` funziona in maniera classica solo che ci mettiamo un `elemento`. dove andiamo a fare un $\text{capacity }\times 2$ ogni volta che finisce lo spazio ed andiamo ad inserire l'elemento.

```C
void prntlst(lista l1) {
    int i;

    for(i = 0; i < l1.size; i++) {
        switch(l1.a[i].tipo) {
            case 'i':
                printf("%d\n", *((int*)l1.a[i].dato));
                break;

            case 'f':
                printf("%f\n", *((float*)l1.a[i].dato));
                break;

            case 's':
                printf("%s\n",((char*)l1.a[i].dato));
                break;
        }
    }
}
```
la funzione di stampa della lista funziona che: finché la variabile `i` è minore di `l1.size`, va a comparare con lo switch se il `char` che rappresenta il tipo dell'elemento contenuto è uguale a, se sì usa quel tipo di stampa, se no passa al prossimo caso.

```C
elemento intero(int d) {
	elemento e ={'i', NULL};
	e.dato = malloc(sizeof(int));
	*((int*)e.dato) = d;
	return e;
}
```
questa funzione serve per andare ad inserire un elemento. prima l'elemento `e` viene creato, poi gli viene assegnato il tipo `i` e il puntatore da place holder `NULL`, poi a `e.dato` viene allocata memoria per il tipo di dato `int` e alla fine a quel spazio di memoria viene assegnato il valore dato in input e viene ritornato l'elemento.

```C
elemento fpoint(float d) {
	elemento e ={'f', NULL};
	e.dato = malloc(sizeof(float));
	*((float*)e.dato) = d;
	return e;
}
```
stessa cosa di `int` ma per le i `float`

```C
elemento stringa(char *d) {
	elemento e ={'s', NULL};
	e.dato = d;
	return e;
}
```
mentre le stringhe non hanno bisogno di allocazione della memoria perché sono già di base dei puntatori.

```C
lista pop(lista l1) {
    if(l1.size > 0) {
        if(l1.size < l1.capacity/4) {
            l1.capacity = l1.capacity/2;
            l1.a = realloc(l1.a, sizeof(lista)*l1.capacity);
        }
        if(l1.a[l1.size-1].tipo != 's') {
            free(l1.a[l1.size-1].dato);
        }
    }
    return l1;
    
}
```

## scanf()
```C
int main() {
	flaot f;
	scanf("%f", %f);
}
```
serve per avere degli input, la funzione ritorna il numero di conversioni eseguite con successo. Ritorna 1 se è giusto, altrimenti 0. La stringa della scanf descrive il formato al quale si dovrebbe attenere l'input.

```C
int main() {

	flaot f0, f1;
	printf("digita 2 numeri nel formato \"(%%f, \%%f)\")");
	tmp = scanf("(%f,%f)", &f0, &f1);

	if (tmp == 1) {
		printf("%f * %f = %f\n", f0, f1, f0*f1);
	}
	else {
		printf("formato errato\n");
	}
}
```
quando andremo ad eseguire la nostra funzione main() dovremo dare come input `(3.14,4.32)`, perché questo è il formato che gli ho dato.

