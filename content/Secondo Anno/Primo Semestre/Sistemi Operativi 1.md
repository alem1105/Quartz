# Sistema Operativo - Che cosa fa?
Il compito principale del sistema operativo è quello di offrire servizi agli utenti, ad esempio per gli sviluppatori fornisce un utilizzo più semplice della RAM permettendoci appunto di creare semplicemente delle _variabili_, oppure fornisce un ambiente grafico per utilizzare le applicazioni non obbligandoci ad utilizzare i terminali con riga di comando.

Per fare questo il sistema operativo deve poter comunicare con l'hardware e gestire le sue risorse come:
- Processore
- RAM
- Dispositivi input / output

> [!info] Modello di Von Neumann
> 
> ![[Pasted image 20240928195605.png|400]]
> 
> Questa è la struttura più semplice di un computer monoprocessore, è composto da 3 blocchi principali visti prima e questi devono poter comunicare fra loro, lo fanno tramite il _sytem bus_.
> All'intero della CPU sono presenti dei registri molto veloci tra cui:
> - PC: Program Counter, contiene l'indirizzo della prossima istruzione da eseguire.
> - IR: Instruction Register, contiene l'istruzione da eseguire vera e propria.
>- MAR: Memory Address Register, contiene un indirizzo della memoria RAM
>- MBR: Memory Buffer Register, contiene un valore da scrivere sulla RAM
>  La ALU (Execution Unit) è la parte che svolge i calcoli logici e aritmetici.

**Componenti Principali**:
- Processore: Svolge le computazioni.
- Memoria Principale: è **volatile** ovvero se spegniamo il computer perdiamo tutto il contenuto, viene chiamata **memoria reale** o **primaria**.
- Moduli di Input / Output: Periferiche come tastiera e mouse, dischi esterni non volatili, schede di rete ecc...
- Bus di sistema: Serve a far comunicare tra loro le parti interne del computer.

Come visto prima all'interno del processore sono presenti dei registri, delle memorie molto veloci e molto piccole, vediamoli nello specifico:
- **Registri visibili all'utente**: Sono usati o da chi programma in _Assembler_ o dai _Compilatori di linguaggi non interpretati_.
- Alcuni sono **obbligatori** da usare per determinate operazioni su determinati processori mentre altri sono **facoltativi** e servono a minimizzare gli accessi alla RAM.
Quelli **non visibili** si dividono in:
- Registri di **controllo e di stato**: Usati dal processore per controllare l'uso del processore stesso, vengono inoltre usati anche da alcune funzioni del Sistema Operativo per controllare l'esecuzione dei programmi.
  Fanno parte di questi ad esempio:
  - PC
  - IR
  - PSW (Program Status Word): Contiene le informazioni di stato
  - Codici di Condizione (flag): Singoli bit settati dal processore come risultato di operazioni
- Registri **interni**: Sono usati dal processore tramite microprogrammazione, ovvero in determinate operazioni come il caricamento di un dato in RAM abbiamo bisogno ad esempio di un registro per l'indirizzo dove scrivere e un altro per il dato, questi sono i registri interni e non visibili dall'utente. Vengono anche utilizzati per la comunicazione con la memoria e I/O.
  Fanno parte di questi ad esempio:
  - MAR e MBR
  - I/O Address Register e I/O Buffer Register

## Esecuzione di Istruzioni
L'esecuzione si divide in due passi:
- **Fetch**: Il processore legge (preleva) le istruzioni dalla memoria RAM, nello specifico legge l'indirizzo di memoria presente nel PC e carica l'istruzione nel IR, quando parte l'esecuzione viene inoltre incrementato il valore del PC.
- **Execute**: Il processore esegue ogni istruzione prelevata. (presente nel IR).

![[Pasted image 20240928220709.png]]

**Categorie di Istruzioni**:
- Scambio dati tra processore e memoria. ad es. store word e load word
- Scambio dati tra processore e input / output.
- Manipolazione dati
	- Operazioni Aritmetiche
	- Di solito solo su valori presenti in registri (MIPS), ma in alcuni processori anche direttamente su RAM.
- Controllo: Modifica del Program Counter tramite salti condizionati o non
- Operazioni Riservate: abilitare o disabilitare alcune impostazioni come interrupt, cache, paginazione e segmentazione.

_Esempio di una Macchina_

![[Pasted image 20240928221801.png]]

Questo è un esempio di una macchina a 16 bit.

Nel caso di un'istruzione questi 16 bit vengono usati in questo modo:
- I primi 4 indicano il tipo di operazione, **Opcode**.
- I restanti sono informazioni utili all'istruzione
Se memorizziamo un numero:
- Primo bit indica il segno
- I restanti il numero stesso

Questa macchina ha 3 particolari istruzioni:
- 0001 = Salva in AC il dato presente nella memoria all'indirizzo fornito.
- 0010 = Salva in memoria il contenuto di AC, sempre nell'indirizzo fornito.
- 0101 = Aggiungi al valore di AC, il contenuto della memoria presente all'indirizzo fornito.

![[Pasted image 20240928223605.png]]

## Interruzioni
