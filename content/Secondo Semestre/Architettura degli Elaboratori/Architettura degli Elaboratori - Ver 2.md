# Istruzioni, Assemblatore e Compilatore

Per comunicare con un computer abbiamo bisogno di inviare dei segnali elettrici, questo corrisponde all'azione di far passare corrente in un componente oppure no.
In questo modo diventa molto semplice usare il **sistema numerico binario** per rappresentare con 1 il passaggio di corrente e con il 0 il non passaggio.

A seconda della progettazione della sua progettazione ogni componente reagisce in base alle sequenze di 0 ed 1 che riceve, queste sequenze prendono il nome di **istruzioni** e possono essere interpretate come _comandi_ o come dei veri e propri _numeri_.

Inizialmente si comunicava con i computer inserendo manualmente ogni sequenza di numeri binari (_bit_) ma successivamente vennero creati gli **assemblatori** ovvero dei programmi in grado di convertire delle notazioni più vicini al nostro linguaggio in effettive istruzioni.
Questo linguaggio viene detto **Linguaggio Assembler**.

Del codice scritto in assembly risulta comunque difficile da interpretare velocemente e per questo nacquero linguaggio sempre più vicini al nostro chiamati **linguaggi ad alto livello**, questi vengono **interpretati** da un **compilatore** che traduce questo codice in linguaggio assembly che a sua volta viene convertito in linguaggio macchina (bit di 0 e 1) da un assemblatore.

![[Pasted image 20240316180006.png]]

# Architettura di Von Neumann, CPU e Memorie

L'esempio più semplice di architettura di un computer è **l'architettura di Von Neumann** secondo la quale un computer è costituito da 4 elementi:

- **Central Processing Unit (CPU)**: Esegue tutte le istruzioni che compongono un processo, ovvero un programma caricato in memoria.
  Questa a sua volta si divide in 3 elementi:
	  - *Control Unit (CU)*: Coordina le operazioni
	  - *Arithmetic Logic Unit (ALU)*: Svolge operazioni logiche e matematiche
	  - *Registri*: Piccole memorie interne per dati temporanei
- **Memoria**: Serve a memorizzare istruzioni e dati
- **Input / Output**: Comunicare con l'esterno
- **Bus di sistema**: Un canale che mette in comunicazione tutti i componenti,  questo si divide in 3 sottocanali ognuno con funzioni specifiche:
	  - *Control Bus*: Coordinazione fra i componenti
	  - *Addres Bus*: Indirizzi delle istruzioni da eseguire
	  - *Data Bus*: Scambio di dati

![[Pasted image 20240316180839.png]]

---

I primi modelli di computer erano in grado di eseguire soltanto un processo alla volta, adesso abbiamo dei sistemi di **parallelismo** che ci permettono di gestire più processi in contemporanea.
Questo metodo prende il nome di **scheduling** e consiste nel sospendere temporaneamente l'esecuzione di un processo ed eseguire le istruzioni di un secondo processo, grazie alla rapidità della CPU ci sembrerà di star eseguendo più programmi nello stesso momento.
Infatti per ogni istruzione il processore deve svolgere 3 fasi:

- **Fetch**: Lettura dell'istruzione successiva
- **Decode**: Decodifica dell'operazione da compiere
- **Execute**: Esecuzione

L'architettura di Von Neumann prevede che un programma prima di venire eseguito venga caricato in memoria e quando questo succede il programma prende il nome di **processo**.

# L'architettura MIPS 2000

Possiamo individuare due tipologie principali di architetture di calcolatori:

**Architettura CISC:**
- Complex Instruction Set Computer
- Istruzioni di dimensione variabile, per effettuare il fetch della prossima istruzione dobbiamo prima decodificarla
- Operazioni effettuate in memoria, necessitiamo di molti accessi a quest'ultima
- Pochi registri interni
- Modi di indirizzamento più complessi che rischiano di creare conflitti tra le istruzioni

**Architettura RISC:**
- Reduced Instruction Set Computer
- Istruzioni di dimensione fissa
- Operazioni svolte dalla ALU e solo tra registri
- Molti registri interni
- Modi di indirizzamento più semplici dato che le istruzioni hanno lunghezza fissa

Le architetture di tipo CISC sono più complesse ma ottimali per scopi specifici mentre le RISC sono più semplici ma per scopi generici.
L'architettura **MIPS** rientra nelle RISC

- Word con dimensione fissa da 32 bit
- Spazio di indirizzamento di $2^{30}$ word
- Memoria indicizzata al byte (8 bit) quindi dato un indirizzo di memoria $t$ per accedere al successivo dovremo andare al $t+4$
- I numeri vengono salvati in [[Complemento a 2]] su 32 bit
- Dotata di 3 microprocessori:
	- _CPU principale_ dotata di ALU e 32 registri, svolge le istruzioni
	- _Coprocessore 0_ gestione delle "trap" (eccezioni...)
	- _Coprocessore 1_ esegue i calcoli in virgola mobile
- 32 registri:
  ![[Screenshot 2024-03-16 alle 18.58.38.png]]

# Linguaggio Assembly MIPS

Le istruzioni che possiamo dare alla CPU nell'architettura MIPS hanno una **struttura molto semplice** ovvero:

> \<operazione\> \<destinazione\>, \<sorgenti\>, \<argomenti\>

Un esempio pratico che possiamo fare è l'operazione di somma fra due registri:

```assembly
add $s0, $t0, $t1
```

Questa istruzione non fa altro che leggere i valori nei registri $t1 e $t0, sommarli e scrivere il risultato nel registro $s0.

> [!info] Struttura
> È importante ricordare che questa struttura è una generalizzazione e non viene rispettata da tutte le istruzioni.

Infatti anche se le istruzioni hanno **strutture diverse** per noi umani quando vengono lette ed interpretate dall'assemblatore queste vengono **convertite in word** da lunghezza fissa di **32 bit** (linguaggio macchina).
La disposizione di questi 32 bit determina quindi il tipo di istruzione e tutto quello che deve fare il calcolatore, abbiamo 3 tipologie di istruzioni:

## Istruzioni R-Type (tipo registro)

Questa tipologia di istruzioni accede a valori presenti nei registri e **NON** ha bisogno quindi di **accedere alla memoria**, viene utilizzata per svolgere **operazioni** **logiche** ed **aritmetiche**

![[Diagramma senza titolo (1).jpg]]

- **Opcode (OP)**: Indica la categoria dell'istruzione
- **First Register (RS)**: Indica il primo registro sorgente
- **Second Register (RT)**: Indica il secondo registro sorgente
- **Destination Register (RD)**: Indica il registro dove verrà scritto il risultato
- **Shift Amount (SHAMT)**: Indica la quantità di bit da shiftare
- **Function Code (FUNCT)**: Possiamo vederlo come un'estensione dell'opcode infatti questo ci indica l'operazione specifica da eseguire all'interno della categoria indicata dall'opcode

## Istruzioni I-Type (tipo immediato)

Questa struttura viene utilizzata per le operazioni di **load** e **store** ma anche per effettuare **salti condizionati**

![[itype.jpg]]

- **Opcode (OP)**: Viene indicata l'operazione di tipo immediato da svolgere
- **First Register (RS)**: Indica il registro sorgente
- **Destination Register (RT)**: Indica il registro dove verrà scritto il risultato dell'operazione
- **Immediate**: Viene indicato il valore costante da utilizzare nell'operazione (ad esempio una somma).

## Istruzioni J-Type (tipo jump)

Questa struttura viene utilizzata per effettuare **salti non condizionati**

![[jtype.jpg]]

- **Opcode (OP)**: Viene indicata l'operazione di salto non condizionato
- **Address**: Contiene l'indirizzo dove effettuare il jump, è importante ricordare che siccome la memoria è indicizzata al byte e non seguendo le word, quindi se voglio andare avanti di un'istruzione devo andare avanti di 32 bit (4 byte).
  Quindi ad esempio se accedo all'indirizzo 2500, in realtà sto entrando all'indirizzo 10.000 (2500 * 4).

> [!info] Differenza dei salti
> - **Salti Condizionati**: vengono effettuati solo se si verificano determinate condizioni
> - **Salti non Condizionati**: l'istruzione viene eseguita indipendentemente da altri fattori


# Organizzazione della memoria

La memoria nell'architettura MIPS 2000 è indicizzata al byte e come abbiamo già visto ogni word è composta da 4 byte.
Per avere in testa un'idea più chiara di come è fatta la memoria possiamo vederla come una tabella composta da **4 colonne** dove ciascuna di queste indica **un byte** e $2^{30}$ righe dove ogni **riga indica una word**.
Ad ogni byte è associato un **indirizz**o che per comodità è rappresentato da **8 cifre esadecimali**, infatti ogni cifra esadecimale è formata da 4 bit quindi 8 * 4 = 32 bit

![[Pasted image 20240317182517.png]]

Quindi possiamo dire che il _k-esimo_ byte si troverà all'indirizzo $k-1$ dato che contiamo anche lo 0 mentre la _j-esima_ word si trova all'indirizzo $4\cdot(j-1)$.

In linguaggio assembly per leggere il contenuto di una word presente in memoria si utilizza questa istruzione:

```assembly
<offset>($indirizzo)
```

Dove al posto di $indirizzo dobbiamo inserire un registro che contiene l'indirizzo di memoria da cui andremo a estrarre la word mentre al posto di offset inseriamo il numero di byte successivi a partire dall'indirizzo specificato.

_Esempio:_
Vogliamo accedere alla word presente all'indirizzo 3996 e anche alla sua successiva:

```assembly
li $t0, 3996
lw $t1, 0($t0)
lw $t1, 4($to)
```

- **li (load immediate)**: Abbiamo caricate nel registro $t0 il valore 3996
- **lw (load word)**: Abbiamo caricato l'intera word presente all'indirizzo presente in $t0 nel registro $t1.
  Nella riga successiva sempre con la stessa istruzione abbiamo caricato la word successiva all'indirizzo 3996 ovvero la 4000.

## Parti della memoria

Adesso che sappiamo come è organizzata la memoria possiamo vedere le sue parti principali

![[Pasted image 20240317184600.png|200]]

- **Stack**: Viene utilizzata per gestire le funzioni ovvero le sue variabili locali ma anche chiamate ricorsive, **non ha dimensione fissa** e può espandersi anche nel _free space_, per operare al suo interno utilizziamo il registro $sp **stack pointer**.
- **Dynamic Data (Heap)**: Contiene i dati dinamici che vengono creati durante l'esecuzione dei programmi, anche questa si può espandere nel _free space_.
- **Static Data**: Contiene tutti i dati statici dichiarati all'avvio del programma ovvero nella sezione _.data_ che vedremo in seguito, per gestire gli indirizzi in questa zona viene utilizzato il registro $gp **global pointer**.
- **Program Instructions**: Contiene le istruzioni del programma presenti nella sezione _.text_, all'interno di questa sezione opera il **Program Counter** ovvero il registro che contiene la posizione dell'istruzione successiva da eseguire.
- **Kernel Reserved**: Sezione di memoria riservata al kernel del sistema operativo alla quale noi programmatori non possiamo accedere, nel caso questo avvenisse si verificherebbe un'eccezione.

# Direttive Principali ed Esempi di Codice

Prima di iniziare a scrivere codice assembly è importante saper riconoscere quelle che sono le **direttive**, queste non sono vere e proprie istruzioni ma delle notazioni che verranno convertite dall'assemblatore in istruzioni più complesse.

Le principali sono queste:

![[Pasted image 20240317192028.png]]

Vediamo un esempio di codice molto banale per introdurre anche il concetto di **label** e poi andiamo a vedere un codice più articolato.

```assembly
.text

main:
	li $t0, 5          # Carichiamo 5 in $to
	li $t1, 0x10       # Carichiamo il valore esadecimale 0x10 in $t1
	add $s0, $t0, $t1  # Scriviamo in $s0 il valore $t0 + $t1
```

Quindi nel registro $s0 abbiamo scritto il valore 21 ovvero 5 + 16 (10 esadecimale).
La **label** è la scritta _main:_ presente prima del codice, questa funziona come da _segnalibro_ per l'assemblatore e possono essere inserite sia per indicare istruzioni o dati statici.

```assembly
.data

vettore: 10, 2, 0x12
stringa: "Ciao sono Alessio"
vettore_float: 10.3, 3.14

.text

main:
	la $s0, vettore     # Carico indirizzo del vettore in $s0
	lw $s1, 0($s0)      # 10 -> $s1
	lw $s2, 4($s0)      # 2 -> $s2
	lw $s3, 8($s0)      # 0x12 -> $s3
	add $t0, $s1, $s2   # $s1 + $s2 -> $t0
	sub $t0, $t0, $s3   # $t0 - $s3 -> $t0
```


> [!bug] Endianess
> I processori possono salvare e interpretare i byte nella memoria in diversi modi, due di questi formati sono:
> - **Big Endian**: Il byte più significativo viene salvato all'indirizzo più basso, quindi prima, mentre i byte meno significativi negli indirizzi successivi
> - **Little Endian**: Il byte più significativo viene salvato all'indirizzo più alto, quindi dopo, mentre i byte meno significativi vengono salvati negli indirizzi precedenti
> 
> ![[Pasted image 20240317223719.png|750]]
> 
> Nel simulatore MARS utilizziamo la notazione _little endian_ infatti se andiamo a vedere la rappresentazione ASCII delle stringhe che salviamo risulteranno invertite ogni 4 caratteri (byte)
> 
> ![[Screenshot 2024-03-17 alle 22.39.20 1.png]]
> 
> Per aggirare questa cosa dobbiamo leggere i byte uno alla volta o salvare direttamente la stringa invertita.

# Salti Condizionati e Salti Assoluti





