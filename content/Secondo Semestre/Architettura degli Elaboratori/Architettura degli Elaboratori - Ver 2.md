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

