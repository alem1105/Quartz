# Bit, nibbles, byte
Un bit può assumere come valori 0 e 1 ed è un elemento di un insieme binario di simboli:
- **nibble**: 4 bit
- **byte**: 8 bit
Il bit più a sinistra prende il nome di **MSB (Most significant bit)** mentre quello più a destra si chiama **LSB (Least Significant Bit)**.

Utilizziamo soltanto 0 e 1 come valori perché la CPU è una **macchina sequenziale** quindi lavora con _stati, circuiti combinatori_  e _cicli di clock_.
Lavorando con soli 0 ed 1 possiamo facilmente tradurli in segnali elettrici per il nostro calcolatore, di solito infatti la macchina è sensibile ai fronti di salita del clock ovvero quando vale 1.

La sola velocità di clock non rende il nostro calcolatore veloce, ci sono anche altri fattori come ad esempio la memoria.

> [!NOTE] Legge di Amdhal
> ![[Screenshot 2024-03-05 alle 15.39.57.png]]
> Quindi è importante non solo migliorare la velocità del processore ma anche migliorare singolarmente un'istruzione che viene eseguita tante volte dal nostro programma.
> **Rendere veloci le situazioni comuni**

# Prestazioni
In generale il tempo di esecuzione di un programma dipende da:
- Numero di istruzioni del programma
- CPI (numero medio di clock per istruzione)
- Velocità di clock

![[Screenshot 2024-03-05 alle 15.59.44.png]]

# Architettura CISC e RISC
![[Pasted image 20240305160157.png]]

**Istruzioni complesse => molte più istruzioni. semplici ma che girano più velocemente.

## MIPS (Microprocessor without Interlocked Pipelined Stages)
Nel MIPS abbiamo 32 registri ($s0 - $s7; $zero; $sp; ecc...) che ci permettono un accesso veloce ai dati, gli operandi devono essere contenuti in registri per poter eseguire le operazioni.
Il registro $zero contiene tutti zeri mentre il registro $at viene riservato all'assemblatore per la gestione di costanti lunghe.

Abbiamo anche $2^{30}$ parole di memoria (Memoria[0],Memoria[4]...), infatti alla memoria si accede attraverso le istruzioni di trasferimento dati.
Il MIPS utilizza **l'indirizzamento al byte**, quindi due parole consecutive hanno indirizzi in memoria a una distanza di 4 byte (32bit / 8bit).
Nella memoria possiamo salvare strutture dati, vettori o il contenuto dei registri.

- **La memoria MIPS è indicizzata al byte (8 bit)**
- **Se sono all'indirizzo t e devo leggere la parola successiva incremento t+4, perchè una parola sono 4 byte ovvero 32 bit**

### Istruzioni in MIPS
![[Pasted image 20240305161411.png]]

Per lo istruzioni logiche abbiamo anche le loro versioni immediate:
![[Pasted image 20240305161512.png]]

Infine abbiamo le istruzioni di salto:
![[Pasted image 20240305161603.png]]
### Rappresentazione dell'istruzione (R-Type)
Abbiamo detto che ogni istruzione è formata da 32 bit, più nello specifico sono divise in questo modo:
![[Pasted image 20240305162644.png]]
- _opcode_ indica la tipologia di operazione (aritmetica, salto, ecc..) che stiamo andando a svolgere
- _rs, rt, rd_ indicano rispettivamente i primi due operandi e il registro di destinazione
- _shamt_ si usa nelle moltiplicazioni o divisioni, shift a destra divido per 2 mentre con uno shift a sinistra moltiplico per 2.
- _funct_ indica il tipo di operazione specifica (somma, sottrazione, ecc....)

### Rappresentazione dell'istruzione (I-Type)
![[Pasted image 20240305163057.png]]
- _op_ indica il tipo di operazione
- _rs, rt_ indicano rispettivamente il primo operando e il target register
- _constant or address_ indicano ad esempio costanti che vanno utilizzate nell'operazione
Viene utilizzata ad esempio nelle operazioni come _addi_ dove possiamo aggiungere anche costanti non presenti in registri.

### Formato delle istruzioni
![[Pasted image 20240305163805.png]]
