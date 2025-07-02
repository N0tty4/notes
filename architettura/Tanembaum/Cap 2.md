# introduzione
Un calcolatore è costituito da:
- Processori
- Memorie
- Periferiche
# Processori
La CPU ("Central process unity") è il cervello, ha la funzione di eseguire i programmi nella memoria principale.
I componenti sono connessi con il **BUS** (cavi paralleli connettono  componenti che trasmettono dati); possono essere esterni alla CPU o interni.
## componenti CPU
Composta da parti distinte:
- **Unità di controllo:**
  Si occupa di prelevare i dati e verificarne il tipo
- **Unità logico aritmetica:**
  esegue le operazioni
- **registri**:
  piccole celle di memoria ad alta velocità
### Registri:
  Piccole unità di memoria ad alta velocità, possono essere. Le più importanti sono:
  - **PC** (Program counter), che punta alla successiva istruzione
  - **IR** (Instruction Register), contente l'istruzione che si trova in fase di esecuzione.
Poi ci sono altri registri che sono generici o specializzati
## organizzazione della CPU
### data path di Von Neumann
è composta da dei registri (da 1 a 32), dalla ALU e da BUS che connettono i componenti tra di loro. Generalmente i registri vengono connessi alla ALU da due registri di input, che poi immettono i dati nella ALU che poi svolge i calcoli, però può variare la architettura.
### categorie istruzioni
- **registro-memoria:**
  si occupa di processi che devono andare a importare o esportare dati dalla memoria principale
- **registro-registro:**
  Si occupa di processi devono lavorare con dati direttamente nel registro, ad esempio i due registri di input della ALU, tale operazioni si definiscono come _ciclo del percorso dati_ e definisce il cuore delle CPU. I computer moderni hanno più ALU specializzate per compiti diversi.
## Esecuzione dell'istruzione
1. Prelevare successiva istruzione nel IR
2. Modificare PC che punta alla prossima istruzione
3. determinare tipo istruzione
4. se contiene dati in memoria determinare dove si trova
5. se necessario prelevare il dato per portarlo nella CPU
6. eseguire istruzione
7. tornare al punto 1.
Ci si riferisce come **ciclo esecutivo delle istruzioni**, oppure come **prelievo-decodifica-esecuzione**.
## famiglie di architetture
I primi calcolatori avevano architetture diverse per tipo di utilizzo, un computer di fascia bassa aveva meno istruzioni di quello di fascia bassa, però questo era un problema di compatibilità. Finché non sono nate le famiglie di architetture che avrebbero dovuto avere un' unica architettura ma varie e distinte interpretazioni, che avrebbero dovuto svolgere le stesse istruzioni.
Questo era possibile grazie all'interpretazione, le quali hanno il vantaggio di:
1. correggere errori o aggiungere istruzioni non presenti nel hardware
2. aggiungere istruzioni a costo minimo
3. possibilità di provare istruzioni complicate
Sopratutto perché all'epoca si usava l'ISA ed il microcodice, quindi risultava più vantaggioso, la quale era conservata nelle **Memorie di controllo**, che era di sola lettura. Per poi portare a eseguire le microistruzioni che erano istruzioni interpretate.
## CISC vs RISC
Sono degli acronimi per indicare il tipo di CPU:
- CISC
  Complex Instruction Set Computer, ed ha delle istruzioni più complesse e venivano interpretate, oggi invece vengono divise in microistruzioni per poi essere eseguite, ciò rallenta le istruzioni più complesse.
- RISC:
  Reduced Instruction Set Computer, è una tipologia di CPU che ha un insieme di istruzioni più piccolo che vengono eseguite direttamente dal hardware, così da togliere completamente il microcodice e l'interprete software.
### principi di progettazione dei calcolatori moderni
1. le istruzioni comuni devono essere eseguite dal hardware, ciò è rapportato anche nel CISC, dove quelle più complesse vengono suddivise in parti meno complesse e eseguite con microistruzioni.
2. **Cercare di iniziare ed eseguire più istruzioni al secondo**, così da velocizzare l'effettiva esecuzione del programma.
3. **Le istruzione devono essere facili da decodificare**
4. **Solo istruzioni Load e Store cambiano memoria**, perché cosi possono essere eseguite in parallelo con altre istruzioni, consente anche di dividere in piccoli passi le funzioni più complesse.
5. **Molti registri disponibili**, almeno 32, così da non dover memorizzare dati temporanei nella memoria.
## Parallelismo a livello di istruzione
Per poter avere macchine più veloci si può o aumentare il clock, oppure sfruttare il parallelismo così da ottenere risultati migliori a parità di clock.
Esistono 2 tipologie di forme:
1. livello di istruzione:
   sfruttato dalle singole istruzioni, così che elabora un maggior numero di esse al secondo
2. livello di processore:
   più CPU lavorano insieme su uno stesso compito.
### Pipelining
Collo di bottiglia maggiore è prelievo istruzioni dalla memoria. In passato si usava il prefetching.
#### prefetching
che consiste nella divisione in della esecuzione in due stadi:
1. prelievo delle informazioni (in un buffer di prefetch, che memorizzava le successive istruzioni del PC)
2. esecuzione effettiva.
In questo modo si poteva caricare le istruzioni successive in memoria, ma questo poteva creare un **prefetch miss**, caricando in memoria delle istruzioni che non sarebbero dovute avvenire: *if*, *for*, *while*.
```c
MOV AX, BX
ADD AX, 5
JMP 10  ; Salta all'istruzione 10
MUL AX, CX  ; (istruzione che non verrà eseguita)
SUB AX, 3
```
### Pipeline
Invece di dividere l'esecuzione in due fasi, la divide in tante piccole fasi, le quali possono essere eseguite in parallelo, dove ciascuna delle parti è gestite da un componente hardware dedicato.
Ad esempio, prendendo in esame una pipeline a 5 fasi si ha che:
1. S1
	- lavora sulla prima istruzione prelevandola dalla memoria (fetch dell'istruzione)
2. S2
	- decodifica l'istruzione 1
	- viene caricata l'istruzione 2 in S1
3. S3
	- preleva gli operandi per l'istruzione 1
	- S2 decodifica l'istruzione 2 
	- S1 preleva l'istruzione 3
4. S4 
	 - esegue l'istruzione 1
	 - S3 preleva gli operandi per l'istruzione 2
	 - S2 decodifica l'istruzione 3
	 - S1 preleva dalla memoria l'istruzione 4
5. S5
	- memorizza in memoria il risultato dell'istruzione 1
	- S4 esegue istruzione 2
	- S3 preleva gli operandi per l'istruzione 3
	- S2 decodifica l'istruzione 4
	- S1 preleva dalla memoria l'istruzione 5
#### latenza e larghezza di banda del processore
l'uso di pipeline bilancia 
- latenza (tempo istruzione impiega essere elaborata)
- la larghezza di banda del processore (MIPS della CPU)
Con un clock di $T$ ns e una pipeline a $n$ stadi, la latenza è di $T \cdot n$ ns. Visto che ad ogni giro di clock viene completato una istruzione, il numero di istruzione al secondo è di $10^9/T$. 
L'una è l'inversa dell'altra.
### Architetture superscalari
Possono esistere architetture con due pipeline, così da eseguire in parallelo due istruzioni, le quali hanno una singola unità di fetch che prende dalla memoria due distinte istruzioni e le inserisce nella pipeline, ognuna delle quali ha una ALU.
Affinché questo accada:
- non ci devono essere conflitti tra i processi.
- Ad occuparsi di ciò o è il compilatore o i conflitti sono individuati e risolti dal hardware specializzato.
Sono principalmente usate dalle macchine RISC.
Questo implica la duplicazione di hardware
Nei computer di fascia alta viene usato un approccio diverso, infatti ad unica pipeline vengono aggiunti più unità funzionali, le quali possono svolgere più compiti contemporaneamente.
## Parallelismo a livello di processore
Più un clock va veloce e più calore emette, in più non si può superare la velocità della luce, quindi a lungo andare bisogna progettare calcolatori con più CPU.
### Parallelismo sui dati
per eseguire degli algoritmi altamente regolari sono stati create due tipologie di processore: **SIMD**, **Vettoriali**. Il primo è visto come un calcolatore parallelo, il secondo come una estensione della CPU. Offre grande potenza di calcolo con risparmio di transistors poiché basta una sola CPU per controllare la macchina mentre gli altri sono in esecuzione sulla stessa istruzione.

| Categoria | Istruzioni | Dati     |
| --------- | ---------- | -------- |
| SISD      | Singola    | Singola  |
| SIMD      | Singola    | Multipli |
| MISD      | Multipla   | Singola  |
| MIMD      | Multipla   | Multipla |
#### Processore SIMD
Grande numero di processori identici che eseguono la stessa sequenza di istruzioni su insiemi diversi di dati. I processori singoli che li compone non sono delle CPU di per sé:
- non possono prendere decisioni autonomamente
- sono controllate tutte da un unico processore che le sincronizza
- sono identiche tra di loro.
#### Processore vettoriale
è un tipo di processore SIMD che ha un funzionamento diverso, infatti ha una unica unità funzionale che lavora con vettori e non con elementi singoli, carica nei _registri vettoriali_ tutti i dati da dover sommare e con una singola operazione somma tutti dati in questi registri. Tali registri vengono strutturati a pipeline.
### Multiprocessori
Sistema composta da più CPU, una memoria in comune e un BUS che le collega, Però sorge problema di coordinamento, poiché stanno sullo stesso BUS e hanno la memoria in comune, quindi soluzione può essere che ogni CPU ha la sua memoria privata e quella pubblica.
### Multicomputer
con più 256 processori difficile costruire Multiprocessori, quindi Idearono i Multicomputer, calcolatori interconnessi, comunicano tramite messaggi che possono attraversare anche più computer (grafi).
# Memoria principale
Il bit rappresenta l'unità della memoria, può avere valore di 0 o di 1, sono più affidabili poiché possono rappresentare alta o bassa corrente.
I bit si possono combinare per formare lettere o parole, e generalmente si usano potenze di 2 per la dimensione; in particolare $2^3$ bit sono un **byte**, quindi 8 bit.
## Indirizzi di memoria
- La memoria sono costituite da un numero di celle che hanno la stessa dimensione
- Ogni cella ha un numero identificativo, i quali vanno da $0$ a $n-1$.
- celle di $k$ bit hanno una possibile combinazione di $2^n$ possibilità
- Se un indirizzo ha $m$ bit, il massimo numero di celle indirizzabile è $2^m$ 
## ordinamento dei byte
possono essere numerati da sinistra a destro o da destra a sinistra
- Big-endian cioè da sinistra a destra
- Little-endian cioè da destra a sinistra
## codici correttori
Per proteggersi dagli errori, memorie usano codici di rilevazione e/o correzione. 
Vengono aggiunti bit extra nella memoria a ogni parola; ogni volta che viene aggiunta una parola si controllano questi bit.
- Parola in memoria sia di $m$ bit, ai quali vengono aggiunti r bit di controllo, quindi il risultato è $m = n + r$, chiamata **Parola di codice**.
- Date due parole, `10001001` e `10110001`, è possibile determinare per quante parole differiscono facendo lo _XOR_ e contare i bit = 1; tale valore è la **distanza di Hamming**.
- se tra due parole esiste una distanza di hamming pari a $d$, allora bisognerà fare $d$ errori per trasformare una parola in un'altra.

## memoria cache
Le CPU sono sempre più veloci, mentre le memorie sempre più capienti, questo crea troppa differenza di velocità nel andare a prendere le informazioni; Le soluzioni possibili sono 2:
- quando incontrano istruzione di prelievo dalla memoria le eseguono subito, se non fanno in tempo creano blocco momentaneo delle istruzioni
- Interprete non generare codice che usano informazioni prima che siano caricate, crea stallo software.
### cache
Quindi sono nate le memorie **cache**, che stanno nelle CPU, che mantengono le informazioni che vengono usate di più, se informazione non presente in cache, prende dalla memoria.
### Principio di località
Programmi non tendono accedere alla memoria casuale, se istruzione accede ad $A$, allora probabile che prossima istruzione accede in prossimità di $A$.
Programmi tendono a usare in piccoli intervalli la stessa frazione di informazioni.
#### tempo medio di accesso
- $k$ = numero di volte che una parola viene letta o scritta in un intervallo di tempo
- $c$ = tempo di accesso alla cache
- $m$ = tempo di accesso alla memoria centrale
- $h$ = frequenza di successo $= (k-1)/k$
$$\text{Tempo di accesso medio} = c+(1-h)m$$
### suddivisione memoria cache
la memoria centrale e la cache è divisa in blocchi di dimensione fissa, per le cache si chiama **linea di cache**. Infatti non carica solo una parola ma l'intera stringa ad essere caricate (la parola in questione e parte di memoria attorno ad essa tutte in una volta).
Esistono due modi per suddividere la memoria cache:
- fare un _cache unica_, più semplice
- creare una suddivisione in due parti (architettura Harvard), dove in una cache memorizza le istruzione e nell'altra i dati. Garantisce azioni in parallelo.
## assemblaggio e tipi di memoria
Vari chip sono montati su una singola scheda a circuiti stampati, essa è chiamata:
- **SIMM** (Single Inline Memory Module)
- **DIMM** (Double Inline Memory Module)
le DIMM sono le più diffuse, ad esempio una **DDR3** (Double Data Rate) è una DIMM, 
# Memoria secondaria
SI è deciso di dividere la memoria in gerarchie, dove la più alta è più veloce ma meno capiente la più bassa è meno veloce ma più capiente.
## gerarchie di memoria

| Gerarchia                      |
| :----------------------------- |
| Registri                       |
| Cache                          |
| Memoria centrale               |
| Disco magnetico o stato solido |
| Nastro / Disco ottico.         |
miniaturizzazione ha portato all'uso di bus seriali. 
## Dischi magnetici
fatto da una testina che si mouove trasversamlmente rispetto al disco. ha un solenoide e capisce se ce un valore magnetizzato uguale a 0 o a 1.
ogni tracia è divisa insetto ri di linghezaa fissa , tra settori adiacenti ce uno spazzio detto gap
- le tracce 
- ogni traccia è cositituita da un premabolo che permetti di sincronizzare delle testine prima di ini zarel alletture, contiene pertracce per errore.
- ogni dirve ha un ascheda deicata, (come una CPU) chiamata controllore del disce, corregge i dati ecc..., che la faccia funzionare.
### floppy disk
- primi dischi rimovibili 
- prima versione fisicamente flessibile (nome)
### hard disk magnetico
- dischi impilati in dei cilindri, ruotano sullo stesso asse. le permoarce dipendono da:
- tempo medio di seek (di ricerca)
- latenza rotazionale (momento di inerzia per partire)
- tempo di trasferimento
#### performance
tempo medio di seek è di 5 a 10 ms
ls latenza rotazionele dipende d
tempo di traspferminteo 
- densita lineare
- velocita di rotazione
tempo che spendiamo maggiormente è quello di seek e dalla latenza
### discki IDE
standard 
- IDE nell'EIDE, 
- i dischi EIDE consentivano 2 collegamenti, 
- successivamente nacque l'ATA
- SCSI (small computer system interface)
- SSD
- sled
- RAID
#### raid 0
dischi sempre della stessa natura e tipo, prendere strisce di memorizazzione e dividerle su più dischi, non è un vero raid, non esiste ridondanza.
#### raid livello 1
eisistono funzionamento raid 0 duplicati su più dischi, scirviamo in parallelo i dati.
#### raid livello 2
usa le parole binarie per decomporre le informazioni su vari dischi, con 7 bit possibile dividere un bit per disco
il throughput è alto perche le operazioni son oin parallelo
#### raid livello 3
versione semplificata del raid livello 2
#### raid livello 4
lavorano strice e non con dischi
#### raid livello 5
roiund-robin
### dischi stato solido
-memora flash non volatirle
- capacita di degrato nel tempo 
- prestazioni eccellenti, velocità traspferimento superiore
### CD-ROM
fattto polibicarbonato sul quale viene deposto stato alluminio riflettente, reicoperto vernice resistente, nel substrato si creavano delle valli o delle valli (pit o land)
### CD-Registrabili
potevano essere scritti una volta sola
- strato di pigmento
- contengono scanaltura che permetta di guidare il laser in fase di scrittura
- quandi il raggio laser colpisce pignmente lo mdifica una sola volta
### CD-riscrivibili
- al posto pigmento cera una lega ha due stati stabili (cristallo a morfo).
- il laser usava e direse intensita
- alta potenza
- postenza media
- bassa potenza
### DVD
porgettati simili ai CD ma piu innovativi, maggiore miniaturazazzione capcacita maggiore di capcacità, maggiore throughput
sono stati definiti 4 formati
1. single-side, single layer
2. single-side, dual layer

# dispostivi interni
## scheda madre
sche principale del computer ch e contiene la CPU, slot per la RAM, i bus, unico alloggiamento per tutti i componenti.
### bus interno 
- bus dati
	  trasmette informazioni tra componenti interne del cpui
- bus di controllo
	  segnali di controllo e sincrnizazzione utilizzati per stabili chi pyo trasmettere dati sul bus dati, per indicare il tipo di operzione la dimensione die dati trasmesssi, ecc. 
- bus indirizzi
	  specifica la posizione fisica di dove id dati devono essere letti o scritti.
## esempio lettura da disco
DMA è una tecnica che permette al controllore del disco di scrivere dati direttamente in memoira senza che la cpu intervenga nel processo
### interrput
forza la cpu a sospendere il programma corrente e avviare una procedura speciale (intrrupt handler), si arresta e poi ci pensa la CPU
procedurea si chiama ISR.
##
- Bus ISA
- Bus PCI
- Bus PCIe rete punto-putno con linee seriali capacita di inviare input
# dispositivi di input/output
come mouse, tastiera, stampante, 
## monitor lcd
## ram
## vram
## stampanti 
- ad impatto
- a matrice
- a getto di inchisotro
- stampanti al laser
## apparati per le telecomunicazioni
- DSL
- ADSL
# Codifica dei caratteri
## ascii e unicode