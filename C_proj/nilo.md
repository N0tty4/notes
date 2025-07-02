# <unistd.h>
Provides access to the POSIX oprating system API.
Used for directly read from a file descriptor.

## read()
```c
ssize_t read(int fildes, void *buff, size_t nbyte);
```
- In size filedes you have three chiose:
    - STDIN_FILENO  = 0
    - STDOUT_FILENO = 1
    - STDERR_FILENO = 2
- Buff: is where to put what we are reading
- nbyte: size of buff
### difference between STDIN_FILENO and stdin

## canonical or cooked mode
è la modalità predefinita del terminale, gestita dal line discipline del sistema.
 IL terminale buffreizza l'input e lo fornisce al programma solo dopo aver premuto invio.

# <termios.h>
- tcgetattr(td, &t) used for read the current attributes into a struct `tremios`

- tcsetattr(fd, TCSAFLUSH, &t) used for write the new terminal attributes back.
    - TCANAW -> subito senza aspettare
      (terminal control set apply now)

    - TCSADRAIN -> dopo che il terminale ha critto l'output in coda
      (terminal control set aaply drain)

    - TCAFLUSH -> come TCSADRIN, ma cancella anche l'input non letto
      (terminal control set after output flush)

flags:
    - c_lfalg = "local flags"
    - c_iflag = "input flags"
    - c_oflag = "output flags"
    - c_cflag = "control flags"


# Local flag
`ECHO` (local flag)
- s 4bytes long (32 bits), defined as:00000000000000000000000000001000.
  so, with the (~) operator we have: 11111111111111111111111111110111 and the bit 
  in position 4 will be deactivated.

`ICANON` Input Canonical mode (local flag)
- l'imput è bufferizzato di default se attivo.
  Il programma puo leggere i dato solo se premi invio. 
- Quando è disattivato legge carattere per carattere, nessun buffering

`ISIG` Input Signal (local lfag)
- disabilita Ctrl-c, Ctrl-f e Ctrl-\

`IEXTEN` (local flag)
- disabilita ctrl-v


# Input flag
`XON` flow contro XON-XOFF (input flag)
- disabilita Ctrl-s e Ctrl-q che ferma e fa partire la trasmissione di dati

`ICRNL` Input carriage Return to New Line (input flag)
- transforma carriage '\r' in '\n', disattivandolo li trattera come cose singolo
`BRKINT` break integer
- disabilita segnali di break come ctrl-C

`ISTRIP` input strip
- abilita rimozione ottavo bit

`INPCK` Input parity check
- abilitare il controllo di parità
# Control flag
`CS8` character size (control flag)
- imposta la dimensione dei caratteri a 8 bit (1 byte per carattere)


# Output flag
`OPOST` Oputput Post Processing
- applica trasformazioni automatiche prima che venga inviato a terminale


# c_cc\[\] (control character)
- `VMIN` sets the minimum number of bytes of input needed before read() can return.
- `VTIME` sets the maximum amount of time to wait before read() returns.

# atexit() \<stdlib\>
è una funzione utilizzata quando dobbiamo uscire dal programma, eseguirà la funzione all'interno come ultima funzione.

# \<errno.h\>
è una libreria che definisce la variabile errno, che indica gli errori.

`EAGAIN` fa parte di `errno.h` e serve a dire che la operazione non può essere completata subito ma forse più tardi.

# \<ctype\>
`iscntrl()` tests whether a character is a control character, are non printable character that we don't
want to print (32-126) are all printable

# define
```c
#define CTRL_KEY(k) ((k) & 0x1f)
```
Il valore di 0x1f è: (31)_{10} e (0001 1111)_{2}, è una maschera bitwase che tiene solo
i 5 bit più bassi di un carattere. facendo ad esempio (


# escape sequence
```c
"\x1b[2J"
```
start with \[\x1b\] (the escape character) followed by a '\[' character. It instruct to the terminal to do various text formatting task. for example `2J` erase compliantly the terminal. 
(VT100 escape sequence) \[\x1b\] = \[\x1B\] = \[\033\]

```c
"\x1b[12;34H"
```
is only 3 bytes long, uses `H` to position the cursor. 
`H` takes 2 arguments: row and column number a which to position the cursor, for example it will
put our cursor on 12 rows and 34 column.

```C
"\x1b[?25l"
"\x1b[?25h"
```
- `?25l` e il parametro per il controllo del cursore
- `l` serve a nasconderlo
- `h` serve a mostrarlo
# Windows size
## \<sys/ioctl.h>
- fornisce l'interfaccia per la funzione `ioctl()`, usata per controllare dispositivi hardware e software.

- `tcgettattr() e tcsetattr()` sono wrapper di ioctl()

- for get the size of the terminal you cal call ioctl() with `TIOCGWINSZ` which means (Terminal Input/Output Control Get Window Size)

- `ioctl()` place the number of columns wide and the number of rows high the terminal is into the given winsize struct, on failed return -1.
## hard way windows size
prove fallback method for getting the window size. Position the cursor at the bottom-right of the screen, then use escape sequences that let us query the position of the cursor.
(query means interrogare per estrarre informazioni).

```C
int getCursorPosition(int *rows, int *cols) {
	char buf[32];
	unsigned int i = 0;

	// 6n used for ask the cursor position;
	if(write(STDOUT_FILENO, "\x1b[6n", 4) != 4) return -1;

	while (i < sizeof(buf) -1) {
		if (read(STDIN_FILENO, &buf[i], 1) != 1) break;
		if (buf[i] == 'R') break;
		i++;
	}
	buf[i] = '\0';

	if (buf[0] != '\x1b' || buf[1] != '[') return -1;
	if (sscanf(&buf[2], "%d;%d", rows, cols) != 2) return -1;
	return 0;

}

int getWindowSize(int *rows, int *cols) {
	// create a struct ws
	struct winsize ws;

	// ioctl used for control ardware and software
	// apply the len of rows and cols into ws.
	// control first if icotl work, after if provided a true value
	if (ioctl(STDOUT_FILENO, TIOCGWINSZ, &ws) == -1 || ws.ws_col == 0) {

		// 999C adn 999B used for set the cursor on bottop right
		if (write(STDOUT_FILENO, "\x1b[999C\x1b[999B", 12) != 12) return -1;

		// for observe result of our esacape before die()
		return getCursorPosition(rows, cols);
		return -1;
	} else {
		*cols = ws.ws_col;
		*rows = ws.ws_row;
		return 0;
	}
}

```

- tutto parte da `getWindowSize`, se la funzione `ioctl()` fallisce allora abbiamo un meccanismo di fallback:

- prima spostiamo il cursore in basso a destra con `\x1b[999C\x1b[999B`, poi andiamo a richiedere la posizione del nostro cursore.

- `GetCursorPosition` va a scrivere dentro il terminale la posizione del cursore con `\x1b[6n` (una query), la quale scrive nello `STDIN_FILENo O`. poi con il while va a leggere dal terminale un byte alla volta per immagazzinarlo nel buffer finché `buf[i]` non è diverso da 'R'. poi si va a sostituire R con `\0`.
- se il la prima posizione del buffer è diversa da `\x1b` o la seconda è diversa da `[`, allora return -1
- poi con `sscanf` vede quale formato nella stringa ha la form `%d;%d` per poi metterla dentro `rows` e `cols

# Draw Rows
```C
void editorDrawRows(struct abuf *ab) {
	int y;
	for (y = 0; y < E.screenrows; y++) {

		// if we are at 1/3 of rows
		if (y == E.screenrows / 3) {
			char welcome[128];

			// return the len of what we print inside the welcome message
			int welcomelen = snprintf(welcome, sizeof(welcome),
							 "kilo editor -- version %s", KILO_VERSION);

			if (welcomelen > E.screencols) welcomelen = E.screencols;
			int padding = (E.screencols - welcomelen) /2 ;
			if (padding) {
				abAppend(ab, "~", 1);
				padding--;
			}
			while (padding--) abAppend(ab, " ", 1);
			abAppend(ab, welcome, welcomelen);
		}
		else {
			abAppend(ab, "~", 1);
		}

		abAppend(ab, "\x1b[K", 3);
		if (y < E.screenrows -1) {
			abAppend(ab, "\r\n", 2);
		}
	}
}
```

In uno `switch`, tutti i `case` condividono lo stesso **scope**. Quando dichiari una variabile in un `case` senza le parentesi graffe, quella variabile esiste per tutto lo switch, ma viene inizializzata solo quando quel `case` specifico viene eseguito.
```C
switch (c) {
    case PAGE_UP:
        int times = 10;  // Dichiarazione nel case PAGE_UP
        break;
    case PAGE_DOWN:
        int times = E.screenrows;  // ridichiarazione della stessa variabile!
        break;
}
```

Le parentesi graffe `{}` creano un nuovo scope locale:
```C
switch (c) {
    case PAGE_UP:
    {
        int times = 10;  // Scope locale al blocco PAGE_UP
        // ...
    }
    break;
    
    case PAGE_DOWN:
    {
        int times = E.screenrows;  // Scope locale al blocco PAGE_DOWN - OK!
        // ...
    }
    break;
}
```