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
![[Pasted image 20240929161113.png|400]]

Quindi un utente "non sviluppatore" usa semplicemente le applicazioni, un programmatore  si basa principalmente sulle utilities e sul Sistema Operativo mentre chi scrive il S.O. si basa sulle specifiche Hardware.

Nello specifico quali servizi ci offre il S.O.?
- **Esecuzione di programmi** anche in contemporanea.
- Accesso ai **dispositivi I/O**.
- Accesso al Sistema Operativo stesso tramite **shell**.
- **Sviluppo di Programmi** quindi compilatori, syscalls, debugger ecc...
- Rilevamento e reazione ad errori hardware / software.
- **Accounting** ovvero una collezione di statistiche di sistema e monitoraggio delle risorse. Viene utilizzato per capire cosa migliorare.

In sostanza quindi il Sistema Operativo è un programma ma che gestisce il funzionamento degli altri programmi, prepara i loro ambienti, li manda in esecuzione, gestisce errori. È **un'interfaccia** tra hardware e software.

Infatti è un normale programma in esecuzione con il suo ciclo di _fetch / execute_ ma ha privilegi più alti, in alcuni casi può passare questi privilegi ad altri programmi.

> [!info] Kernel
> Una parte del Sistema Operativo in codice macchina è racchiusa tutta insieme in una parte della RAM (solitamente quella iniziale), e serve appunto per eseguirlo. Questa parte si chiama **kernel** che significa **nucleo** infatti è la più importante dato che è sempre pronta in RAM.
> 

## Evoluzione dei Sistemi Operativi
I S.O. esistevano dagli anni 40 ed erano molto diversi da quelli di adesso, è importante vedere alcune tappe evolutive per capire i moderni sistemi.

Le evoluzione sono dovute principalmente a:
- Aggiornamenti Hardware
- Nuovi servizi
- Correzione di errori

**Anni Quaranta**

Non c'era nessun Sistema Operativo e per fornire comandi ad un computer si usavano delle speciali console con interruttori, i computer arrivavano a occupare intere stanze.

Il metodo di input venne presto migliorato grazie alle **schede perforate**:

![[Pasted image 20240929163035.png|400]]

In ogni caso i sistemi erano interamente sequenziali quindi potevano svolgere un calcolo alla volta e non essendoci un S.O. i programmi utente gestivano da soli gli input e gli output.

**Anni Cinquanta / Sessanta**

Si mettono insieme più programmi da eseguire (prendono il nome di **jobs**) e il primo sistema operativo serviva a gestire questi jobs, questo metodo funzionava molto bene in sistemi non interattivi chiamati **batch**, questi sistemi appunto vogliono solo un dato in input e poi l'utente deve soltanto aspettare la fine dei calcoli.

Questi sistemi mostrarono le prime problematiche:
- **Protezione della memoria**: ad esempio se un job andava a scrivere nella zona della memoria del controllore dei jobs, questa parte non doveva essere accessibile.
- **Timer**: Impedisce che un job blocchi l'intero sistema per essere eseguito, infatti alcuni di questi impiegavano anche giorni per essere eseguiti.
- **Istruzioni Privilegiate**: Ad esempio il sistema di controllo dei jobs doveva essere eseguito con dei privilegi più alti, infatti lui può accedere a quella zona di memoria.

Quindi i job venivano eseguiti in **modalità utente** (numero limitato di istruzioni) mentre il monitor dei job in **modalità sistema** (possono essere eseguite più istruzioni e possiamo accedere a zone di memoria protette).

C'era un problema molto importante:
- Più del 96% del tempo è sprecato ad aspettare i dispositivi I/O
   
   ![[Pasted image 20240929164349.png|400]]
   
   Come possiamo vedere dei 31 microsecondi soltanto 1 è lavoro effettivo della CPU gli altri 30 sono attesa di I/O.

Quindi prima veniva eseguita una **programmazione singola** ovvero un'operazione per volta con tante attese. Si passa alla **multiprogrammazione**.

![[Pasted image 20240929164642.png|400]]

Quindi ci sono più programmi in esecuzione e durante l'attesa di uno ne viene svolto un altro, ci sono comunque attese ma molte di meno.

_Esempio_

![[Pasted image 20240929165103.png|400]]

Prendiamo questi 3 jobs, il primo è molto incentrato sulla CPU e dura 5 minuti mentre gli altri due utilizzano molto I/O e durano 15 e 10 minuti, vediamo cosa succede in entrambi i tipi di programmazione:

![[Pasted image 20240929165157.png|600]]

A sinistra abbiamo programmazione singola e quindi impieghiamo 30 minuti (1 job dietro l'altro) e un utilizzo non gestito molto bene delle risorse.

Nella multiprogrammazione invece eseguiamo tutti i job insieme, infatti job1 utilizza soltanto CPU e nessun dispositivo mentre gli altri 2 utilizzano dispositivi diversi e quindi possono essere eseguiti tutti contemporaneamente, ne impieghiamo soltanto 15, ovvero quello con il tempo massimo.

Come statistiche otteniamo:

![[Pasted image 20240929165552.png|700]]

**Throughput**: $\frac{job-completati}{ore}$
**Mean Response Time**: Media dei tempi di completamento. Nel caso di uniprogramming dobbiamo considerare che job1 = 5, job2 = job1 + 15 e job3 = job2 + 10, quindi (5 + 20 + 30) / 3

Ovviamente questo è un _esempio un po' estremo_.

### Sistemi Time Sharing
Dagli anni 70 era necessario gestire più **jobs interattivi** da parte di più utenti, il tempo del processore veniva gestito fra più utenti (da qui Time Sharing).

![[Pasted image 20240929170147.png|400]]

Quindi in un sistema Batch vogliamo vedere l'utilizzo della CPU con meno tempi morti possibile mentre nel Time Sharing vogliamo che quando un utente da un comando nel terminale debba attendere il minor tempo possibile per ottenere la risposta.

Nel primo caso veniva utilizzato un **Job Control Language** mentre nel secondo dei comandi dati da terminale gestiti dal S.O.

**Ricapitolando**:
- Computazione Seriale (Anni Quaranta)
- Sistema non interattivo / batch (Anni Cinquanta / Sessanta), introdotta la multiprogrammazione
- Time - Sharing (Anni Settanta), job principalmente interattivi

Questa evoluzione porta a degli sviluppi molto interessanti:
- Il concetto di **processi**
- **Gestione della Memoria**
- **Sicurezza** e protezione delle informazioni, dato che molti utenti potevano accedere ai dati.
- **Scheduling delle risorse**, decidere quale job eseguire in un determinato momento.
- **Strutturazione del Sistema**, scrivere il codice in moduli ben organizzati.

## Dal Job al Processo
Il processo racchiude in un solo concetto job interattivo e non interattivo.

Inoltre incorpora anche un altro tipo di job, quello **transazionale real-time**, ad esempio un sito per acquistare biglietti deve gestire il caso in cui due persone comprano nello stesso momento lo stesso posto per lo stesso giorno alla stessa ora.

Ogni processo è caratterizzato da:
- **Thread** di esecuzione ovvero il flusso del processo, ce ne possono essere più di uno.
- Uno **stato** corrente.
- Un insieme di **risorse** di sistema associate.

Tutto questo a portato dei problemi per chi scriveva sistemi operativi:
- Errori di sincronizzazione: alcuni interrupt si perdono o vengono ricevuti più volte.
- Violazione della mutua esclusione: Se 2 processi vogliono accedere alla stessa risorsa possono verificarsi problemi.
- Programmi con esecuzione non deterministica: Un programma accede ad una zona di memoria modificata da un altro processo.
- Deadlock (stallo): Più processi attendono l'esecuzione di altri processi in "loop", ad esempio A sta aspettando B e B sta aspettando A, nessun processo inizia l'esecuzione.

### Gestione della Memoria
- I processi andavano isolati, ovvero dovevano accedere a diverse zone di memoria senza andare in conflitto.
- Supporto per la programmazione modulare (stack), è quello che permette a noi programmatori di scrivere delle funzioni all'interno del codice.
- Allocazione e Deallocazione automatica
- Tutto questo viene gestito tramite **Paginazione e Memoria Virtuale**.

### Sicurezza
- Protezione dai DoS (Denial of Service), interruzione del servizio.
- Confidenzialità, gli utenti devono accedere soltanto ai dati per i quali hanno il permesso di lettura / scrittura.
- Integrità: Protezione da modifiche non autorizzate.
- Autenticità: Verificare l'identità degli utenti.

### Gestione delle Risorse
Il S.O. in tutto questo deve garantire:
- Equità: dare accesso alle risorse in modo equo.
- Velocità di risposta differenziate: alcuni processi hanno maggiore priorità.
- Efficienza: Massimizzare l'uso delle risorse nel tempo (throughput), minimizzare il tempo di risposta e servire più utenti possibili.

### Elementi Principali

![[Pasted image 20240929172450.png|500]]

## Struttura del Sistema Operativo
Da subito si è capito che non conveniva mettere tutto "a caso", infatti è stato diviso in una serie di livelli, dove ogni livello effettua un sottoinsieme delle funzioni di sistema.

Ogni livello si basa su quello più sotto, ad esempio il livello 4 può richiedere un'operazione al 5 ma non al 3.

- Livello 1:
	- Circuiti elettrici
	- Registri, celle di memoria, porte logiche
	- Operazioni come reset di un registro o leggere in una locazione di memoria
- Livello 2:
	- Insieme delle istruzioni macchina come _add, sub, load, store_.
- Livello 3:
	- Aggiunge il concetto di routine, operazioni di chiamata e ritorno.
- Livello 4:
	- Interruzioni.
- Livello 5:
	- Processo come programma in esecuzione.
	- Sospensione e ripresa di un processo.
- Livello 6:
	- Dispositivi di memorizzazione secondaria
	- Trasferimento di blocchi di dati
- Livello 7:
	- Crea uno spazio logico degli indirizzi per i processi.
	- Organizza lo spazio degli indirizzi virtuali in blocchi
- Livello 8:
	- Comunicazioni fra processi
- Livello 9:
	- Salvataggio di file a lungo termine
- Livello 10:
	- Accesso a dispositivi esterni con interfacce standard
- Livello 11:
	- Associazione tra identificatori interni ed esterni
- Livello 12:
	- Supporto di alto livello per i processi
- Livello 13:
	- Interfaccia utente



> [!info] Architettura UNIX
> ![[Pasted image 20240929173422.png|500]]
> 
> **Kernel Moderno:**
> ![[Pasted image 20240929173554.png|500]]
> 
> Solo per info.

### Kernel Moderno di Linux
I moderni kernel sono **monolitici** o **microkernel**:
- monolitico: Tutto il sistema operativo viene caricato in RAM all'accensione.
- microkernel: Solo una minima parte del S.O. viene caricato in RAM e il resto solo quando serve.
	- Sempre in memoria: scheduler, sincronizazzione.
	- Solo a richiesta: gestore memoria, filesystem, driver.
- Il monolitico è più efficiente in velocità ma ovviamente occupa più memoria RAM.

Quasi tutti i sistemi moderni sono a kernel monolitico ad eccezione di MacOS.

Linux invece è principalmente monolitico ma ha dei moduli:
- Alcune parti del sistema operativo possono essere caricate solo quando servono, la differenza è che in Linux cosa serve e cosa no lo decide l'utente e non il S.O.
- Le cose che Linux non carica sono vari filesystem che non gestisce, driver per alcuni dispositivi, funzionalità di rete.