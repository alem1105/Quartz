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
Le interruzioni interrompono il normale flusso delle operazioni del processore per eseguire delle particolari operazioni del Sistema Operativo, quindi queste non sono scritte dall'utente.

Le cause di queste interruzioni sono molteplici e a seconda di queste prendono deo nomi diversi, **sincrone e asincrone**.

Quelle sincrone sono le interruzioni del programma e avvengono immediatamente dopo l'esecuzione di un'istruzione, quelle asincrone invece nella maggior parte dei casi vengono gestite molto dopo l'istruzione che le ha sollevate, e in alcuni casi non vengono nemmeno generate da un'istruzione ma da altri eventi.

### Interruzioni Asincrone
- **Interruzioni da input / output**: Sono generate da un dispositivo I/O e dato che i loro controller sono più lenti del processore, quest'ultimo manda un comando al dispositivo e poi aspetta che questo dispositivo lo interrompa. Queste segnalano il completamente o l'errore di un'operazione I/O. In generale quindi vengono comunque generate in risposta a qualche istruzione.
- **Interruzioni di fallimento Hardware**: Queste non hanno niente a che vedere con altre istruzioni, infatti potrebbero accadere con: **mancanza di potenza** oppure **errore di parità nella memoria**.
- **Interruzioni da comunicazione tra CPU**: Possono accadere in sistemi con più di una CPU, oppure una CPU con più processori interni.
- **Interruzioni da Timer**: Vengono generate da un timer interno del processore, una sorta di clock. Sono utilizzate dal sistema operativo per eseguire operazioni ad intervalli regolari. (Ad es. ogni 10 secondi mandami un avviso, ogni 10 secondi viene quindi generato un interrupt).

### Interruzioni Sincrone
Sono interruzioni **generate dal programma**, di solito causate da:
- Overflow.
- Divisione per 0.
- Debugging: servono per permettere allo sviluppatore di eseguire il programma passo dopo passo, ad esempio quando inseriamo dei _breakpoint_.
- Riferimento ad un indirizzo di memoria non accessibile (fatale), oppure **momentaneamente** non disponibile (memoria virtuale, gestibile).
- Esecuzione di un'operazione _illegale_, ad esempio un opcode non esistente.
- Chiamate **syscall**, queste sono **intenzionali**.

Quindi quando viene sollevate un'interruzione il sistema operativo crea un **handler** che esegue delle particolari operazioni sempre presenti nel S.O., nel caso di interruzioni **asincrone** una volta terminato l'handler si riprende la normale esecuzione del programma dall'istruzione successiva a quella che ha generato l'interruzione, a meno che l'operazione non sia stata completamente **abortita**.

Con le eccezioni **sincrone** non è detto accada questo:
- **faults**: Errore correggibile, viene rieseguita la stessa istruzione.
- **aborts**: Errore non correggibile, si esegue un software collegato all'interruzione.
- **traps e system calls**: Si continua dall'istruzione successiva.

Riprendendo quindi il ciclo delle operazioni eseguite dal processore visto prima, possiamo modificarlo in questo modo:

![[Pasted image 20240929104207.png|600]]

Quindi eseguiamo il fetch normalmente, dopo l'execute però nel caso in cui le interrupt sono abilitate viene anche controllato se l'operazione ne genera uno oppure se ne arriva uno da un'operazione precedente, se è presente viene eseguito l'handler corrispondente.

### Interrupt Handler
Come detto prima è una funzione presente nel Sistema Operativo e non prevista nel codice scritto dallo sviluppatore.

Quando viene eseguito l'handler, il Sistema Operativo e l'Hardware collaborano per memorizzare _program counter e registro di stato_ in modo da poterci tornare successivamente, se possibile.

![[Pasted image 20240929105311.png|400]]

Questo è quello che succede in generale quando viene eseguito un handler.

Nello specifico:

![[Pasted image 20240929105447.png|400]]

**Hardware**
1) Un dispositivo solleva un'interruzione.
2) Il processore finisce l'esecuzione dell'istruzione corrente.
3) Segnala che "è a conoscenza" dell'interruzione.
4) Salva alcune informazioni, PSW (registri di controllo) e PC, nel _Control Stack_.
5) Carica nel PC il valore per eseguire le istruzione dell'handler.

**Software**
1) Salva tutti i registri della CPU in un opportuno stack.
2) Esegue le opportune istruzioni.
3) Prende i registri salvati in memoria e li sposta negli opportuni registri di appartenenza.
4) Riporta al valore originario anche PSW e PC.

È possibile anche spegnere gli interrupt per togliere la fase di controllo di questi dalla CPU, vengono comunque sollevati e quindi **non gestiti**.

Ci possono essere anche **interrupt annidati**, per alcuni interrupt particolari però l'hardware **forza il sequenziamento**.

![[Pasted image 20240929110921.png|400]]

## I/O con Interrupt
Come visto prima, i controller per i dispositivi I/O sono più lenti del processore e vengono gestiti tramite interrupt.

Prima venivano gestiti in modo sequenziale, quindi quando c'era bisogno di un dispositivo esterno, il processore non svolgeva altre operazioni e aspettava che il dispositivo fosse pronto, con il tempo si è capito che questo metodo portava ad attese inutili.

Come vengono gestiti _adesso_ gli I/O, ovvero con le interruzioni:

![[Pasted image 20240929111652.png|200]]

La CPU manda un avviso al dispositivo, mentre il dispositivo si prepara la CPU può fare altro, nel momento in cui il dispositivo è pronto viene mandato un interrupt che fa capire alla CPU che è possibile usare quel dispositivo.

Un passo che rallenta questo metodo è la copia dei dati, infatti il dato preso dal dispositivo prima di andare in memoria deve passare per la CPU.

Infatti in alcuni casi anche questo metodo presenta delle **attese**:

![[Pasted image 20240929112635.png|500]]

Nel caso di sinistra non ci sono attese dato che tra una scrittura e un'altra il dispositivo è pronto e le completa, nel caso di destra la prima scrittura non è finita e intanto ne viene inviata una seconda, in questo caso il processore deve aspettare che finisca la prima.

**Non abbiamo risolto completamente il problema**.

### Accesso Diretto in Memoria (DMA)
Con questo metodo i dispositivi I/O non hanno più bisogno della CPU come tramite ma possono entrare direttamente in memoria.
Quindi utilizziamo comunque gli interrupt ma una volta che questo arriva la CPU non deve gestire nulla perché il trasferimento è già finito.

**È molto efficiente ma non risolve comunque completamente il problema**.

## Multiprogrammazione
Per riempire quelle attese inutili e far svolgere più lavoro possibile nello stesso momento al processore è stato pensato di fargli svolgere più programmi contemporaneamente.

La sequenza con cui questi vengono eseguiti dipende dalla loro priorità e dal fatto che siano in attesa di altre operazioni. In questo modo alla fine della gestione di un'interruzione il programma potrebbe non tornare all'istruzione successiva a dove è stata generata l'interruzione.

## Gerarchia della Memoria

![[Pasted image 20240929113546.png]]

- **Inboard Memory**: Si trova sui componenti interni del Computer ne fanno parte Registri, Cache e RAM. Tutte queste memorie sono **volatili**.
- **Outboard Memory**: Sono ad esempio i dispositivi di memoria esterni.
- **Off-line Storage**: Dispositivi scollegati dal Computer stesso.

### Cache
![[Pasted image 20240929114818.png|400]]

La cache contiene alcune porzioni della RAM, la CPU prima di andare a prendere un dato dalla RAM controlla se è presente nella Cache, se è presente siamo stati fortunati altrimenti lo andiamo a prendere in RAM e scriviamo quella porzione nella Cache, questo perché è molto probabile che questo dato (o uno molto vicino a lui) ci riservirà tra poco (**località dei riferimenti**).

La Cache è invisibile ai programmatori (anche in assembler) e non la vede quindi nemmeno il compilatore e questo significa che non la vede il Sistema Operativo anche se può decidere di non usarla, inoltre alcune parti del S.O. imitano il funzionamento di questa. 

La Cache è quindi **gestita completamente dall'Hardware** tramite dei circuiti.

![[Pasted image 20240929115355.png|400]]

Quindi date $2^n$ locazioni di memoria RAM le dividiamo per $K$ ovvero il numero di word in un blocco e otteniamo un numero molto più grande rispetto alla grandezza C della Cache.

Il Tag quindi deve essere grande a sufficienza per coprire tutti i blocchi.

_Schema Funzionamento:_

![[Pasted image 20240929115928.png|400]]

- **Capacità della Cache**: Anche con cache molto piccole diminuiamo di molto gli accessi in RAM.
- Ma c'è da considerare anche la **grandezza dei blocchi**: Con blocchi molto grandi ho molte possibilità di trovare i dati in cache ma incrementarli troppo è controproducente infatti saranno di più anche i **dati da sovrascrivere** quando non troviamo qualche dato.

Dobbiamo trovare **un giusto equilibrio**.

#### Nozioni sulla Cache
- **Funzione di Mappatura**: Determina in che locazione della cache va messo un determinato blocco di memoria.
- **Algoritmo di Rimpiazzamento**: Determina in che modo scegliere quale blocco va rimpiazzato in caso serva, tipicamente si usa l'algoritmo **LRU (Least Recently Used)** che rimpiazza il blocco usato meno recentemente ovvero il più vecchio presente in Cache.
- **Politica di Scrittura**: Quando vogliamo scrivere un dato in RAM abbiamo più strade, mettiamo caso che il dato è stato scritto in Cache, adesso lo scriviamo anche in RAM? Se si stiamo utilizzando un **Write-Through** ovvero ogni modifica che avviene in Cache avviene anche in RAM.
  
  Altrimenti stiamo utilizzando il **Write-Back**, scriviamo il dato in Cache ma non in RAM perché se successivamente dobbiamo leggerlo lo leggeremo dalla cache e quindi non c'è bisogno di averlo in RAM. Lo scriviamo solo in caso di rimpiazzi su quel blocco, altrimenti perdiamo lo stato aggiornato.
  In questo modo la memoria potrebbe trovarsi in uno stato "obsoleto" ma è sicuramente più efficiente del Write-Through.

_Esempio più complesso_

![[Pasted image 20240929123555.png|400]]

Il processore ha più processori interni, e ogni processore ha diverse cache (L1, L2, L3 ma questa è in comune fra tutti) salendo di numero diventano più grandi e più lente, quindi si controlla in ordine L1 -> L2 -> L3 -> RAM.

- L1: Sono due cache, una per istruzione e un'altra per il resto dei dati.
- L2 e L3: Sono sempre 2 ciascuna ma contengono qualsiasi tipo di dato.

Come detto prima il S.O. **può spegnere il caching** e inoltre può decidere **la politica di scrittura**, ad esempio Linux non la spegne mai e utilizza sempre write-back.

## Strati e Utenti
