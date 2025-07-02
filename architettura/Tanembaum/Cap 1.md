- **Calcolatore digitale**: macchina che svolge compiti con istruzioni.
- **Programma**: istruzioni per compiere un compito.
## intro
Computer:
- esegue piccolo insieme di istruzioni semplici, in cui tutti i programmi devono essere convertiti. 
- Raramente sono più complesse di:
	- sommare due numeri
	- controllare se un numero vale zero
	- copiare dati da una memoria all'altra
- **linguaggio macchina**: insieme di tali istruzioni 
- combinandosi riescono a svolgere compiti più complessi.
- Per esigenza si costruirono livelli di astrazioni su di essi, per gestire complessità, così da avere **livelli di astrazione**. 
# Approccio strutturale
Per parlare con il linguaggio macchina **L0**, si possono definire due strade:
1. **Traduzione**, costruire un linguaggio **L1**, che poi con un programma traduce ogni istruzione da L1 a L0. Crea un nuovo file contente il linguaggio
2. **Interpretazione**, scrivere programma in L0 che accetta come input programmi in L1, esaminando una istruzione per volta e sostituendo sul momento con L0. Non crea nuovo file contente linguaggio.
## Macchine virtuali
- per il linguaggio L1 costruire una macchina M1, però costerebbe troppo, ma si usa software che traduce.
- linguaggio L1 non troppo diverso da L0, quindi per avere dei linguaggi al livello più umano bisogna creare una macchina virtuale M2 che accetti il linguaggio L2 che non deve essere troppo diverso da L1. Questo processo può continuare in maniera indefinita.
- Questo si intende per livelli di astrazione; un computer a $n$ livelli può essere visto come $n$ macchine virtuali.
## Macchine multi livello
ad esempio prendiamo una macchina costruita a sei livelli:
0. **hardware**: i circuiti che eseguono il programma, porte (gate) logiche, come per esempio OR o AND, le quali combinate danno vita ai registri, CPU ecc...
1. **Livello di micro architettura**: composlta da un gruppo di registri, una **ALU** (arithmetic Logic Unit), i quali sono connessi da un **percorso dati**. In alcune macchine tale percorso è controllato dal **micro programma** mentre in altri direttamente dal hardware.
2. **Instruction set architecture**: definito anche con l'acronimo di **ISA** è un insieme di istruzioni che vengono interpretati dal micro programma o dai circuiti elettronici.
3. **Livello macchina del sistema operativo** ha parte delle istruzioni del livello 2 ma può eseguire più programmi alla volta e aggiunge istruzioni sue, le istruzioni livello sono interpretate direttamente dal microcodice oppure dal hardware, mentre quelle del livello 3 dal sistema operativo.
4. **Assemblatore** Da questo sistema in su si risolvono problemi applicativi per programmatori medi, ora può essere anche tradotto il codice. I linguaggi dei livelli sottostanti sono numerici, ora possono essere anche letterali. Il programma che effettua la traduzione è l'assemblatore.
5. consiste di linguaggi chiamati **ad alto livello** definiti per essere usati dai programmatori.
### architettura
Insieme dei tipi di dati, operazioni e funzionalità di ciascun livello.
### architettura degli elaborati
studio di come progettare le parti di un computer, la parte implementativa.
## evoluzione macchine multi livello
- I primi linguaggi furono scritti in puro linguaggio macchina, i circuiti più i componenti di I/O formano **Hardware**, mentre i codici scritti formano il **software**.
- Nel corso del tempo hardware e software diventano logicamente equivalenti, parti hardware possono diventare software e vice versa.
### evoluzione sistema operativo
Intorno 1960 cercò ridurre quantità di tempo sprecata automatizzando il lavoro dell'operatore, Programma chiamato **sistema operativo** era tenuto sempre nel computer. Nel corso del tempo si aggiunsero nuove funzionalità finché non si andò a creare un nuovo livello con istruzioni più complesse (sopratutto di input e output), che divennero le **chiamate di sistema**.
### migrazione funzionalità verso microcodice
Quando videro che era possibili aggiungere funzionalità senza aggiungere hardware (estendendo microprogramma) decisero di ampliarlo.
Come per esempio:
1. accedere calcoli con array
2. funzioni di ri-locazione
3. sistemi di interrupt 
4. sospendere un programma e partire uno nuovo
5. elaborazione file, audio e video
### eliminazione microprogramma
Con il tempo si capì che:
- ridurre utilizzo microprogramma
- diminuire insieme di istruzioni
- far fare istruzioni al hardware
avrebbe velocizzato il computer.
# Pietre miliari nell' architettura
- Gen 0: meccanici
- Gen 1: Valvole (1945-1955)
	ad esempio Colossus creato da Alan Turing.
	Oltre a ciò ci fu anche la macchina di Von Neumann che era composta da:
	- unità di logica aritmetica (ALU)
	- unità di controllo (CU)
	- memoria centrale 
	- Input (in)
	- Output (out)
- Gen 2: Transistor (1955-1965)
	- con scoperta transistor costruiti 2 pc basati su tecnologia **TX-0** e **PDp-8** che introducono il BUS 
- Gen 3: Circuiti integrati(1965-1980)
	- circuiti integrati su silicio permisero realizzare su unico chip molti transistors.
- Gen 4: integrazione a grandissima scala (1980 - ?)
	- Con tecnologia **VLSI** premise inserire milioni di transistors, 
- Gen 5: Computer a basso consume e invisibili, inventati primi Personal Computer. 
# Tipologie di computer
Con avanzare tempo si inserirono più transistors, **Legge di Moore** dice che raddoppiano ogni 18 mesi. Però raggiunto limite miniaturizzazione. 
## classificazione:
- Dispositivi usa e getta:
	- vita utile breve, come cartoline happy birthday. Scoperta più importate sono chip **RFID** (Radio frequency identification), a 128 bit che contengono piccolo radiotrasmettitore. Il funzionamento è il seguente: ricevono segnale radio abbastanza allungo per ricaricarsi, per poi ritrasmettere il loro codice identificativo. Si differiscono in attivi e passivi (a seconda se sono alimentati o no) e ad alte o basse frequenza.
- Micro-controllori:
	- integrano CPU, memoria e interfacce, usati in elettrodomestici, progettati per scopi precisi con alte prestazioni e basso costo.
- Dispositivi mobili e da gioco:
	- macchine potenti ma con limitate possibilità di espansione hardware o software specifiche per giocarci.
- Personal computer:
	- Desktop e portatili, offrono elevate prestazioni e sono molto versatili.
- Server:
	- spesso potenti rispetto ai pc dotate di mono o multi processore, dotato di molta memoria e connessioni di reti veloci.
- mainframe:
	- enormi pc con capacità di I/O elevate, usati in ambiti con gran di volumi di dati
- Cluster:
	- consistono in più server connessi tra di loro, da non confondere con i data center che è il luogo che li ospita.
# Esempi famiglie di computer
