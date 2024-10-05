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
> 
> ![[Pasted image 20240929173422.png|500]]
> 
> **Kernel Moderno:**
> 
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

---

# I Processi
Il compito fondamentale del Sistema Operativo è quello di **gestire i processi**, infatti ogni tipo di computazione può essere vista come _processo_.

Il Sistema Operativo deve:
- Permettere l'esecuzione di processi multipli in modo alternato, **interleaving**.
- Assegnare risorse ai processi, come stampante, schermo, schede di rete, e inoltre proteggere da altri processi l'accesso a queste risorse.
- Permettere lo scambio di informazioni tra processi.
- Permettere la sincronizzazione tra processi.

> [!info] Che cos'è un processo?
> In modo semplice è un **programma in esecuzione**, ovvero quando un utente richiede la computazione svolta da quel programma.
> Possiamo definirlo anche in altri modi, ad esempio un processo è un'istanza di un programma in esecuzione, e per alcuni programma possiamo avere anche più istanze ovvero più processi.
> Ogni istanza viene assegnata ad un processore per l'esecuzione.
> Ogni processo è caratterizzato da:
> - Codice ovvero **una sequenza di istruzioni**
> - Un insieme di dati
> - Un numero di attributi che descrivono lo **stato del processo**
> - Alcuni hanno anche delle **risorse associate** (stampante, rete, ecc...)

Per adesso quando ci riferiamo ad un "_programma in esecuzione_" significa che un utente ha richiesto la sua esecuzione e che il programma non è ancora terminato, diciamo **per adesso** dato che più avanti vedremo altri casi di programmi in esecuzione.

Questo non significa necessariamente che il processo è in esecuzione su un processore, ovvero dal momento in cui inizia fino al momento in cui termina, non è detto che sia sempre in esecuzione e molto spesso non è così; decidere quando mandare in esecuzione un processo sul processore abbiamo visto essere un ruolo fondamentale del Sistema Operativo.

Dietro ad ogni processo c'è un programma:
- Nei moderni S.O. di solito è memorizzato sul disco rigido.
- Solo eseguendo un programma possiamo creare un processo ed eseguendo un programma creiamo **almeno un processo**.
- Possono far eccezione a queste regole alcuni dei processi creati dal sistema operativo, questi non sono presenti nella memoria di massa ma nel _kernel_.

## Fasi di un Processo
Un processo ha 3 _macro-fasi_, **creazione, esecuzione, terminazione**:
- La terminazione può essere **prevista**
	- Un programma svolge dei calcoli e alla fine dell'ultima operazione si termina.
	- Un programma viene terminato quando l'utente preme sulla "X" della finestra.
	- Se l'utente non lo chiude, potrebbe anche rimanere per sempre in esecuzione.
- **Non prevista**
	- Il processo esegue un'operazione non consentita, viene generata un'eccezione che può portare alla chiusura forzata da parte del sistema operativo.
- Da notare che la terminazione non è detto che sia sempre presente.

## Elementi di un Processo
Finché il processo è in esecuzione, ad esso sono associate delle informazioni:
- Identificatore, uno per ogni processo.
- Stato (esecuzione o anche altri).
- Priorità, sarà utile per lo **scheduling**.
- **Hardware Context**: È la situazione attuale dei registri della CPU, cioè i loro valori, fra questi è presente ad esempio il _Program Counter_.
- Puntatori alla memoria RAM usata da questo processo, questa porzione prende il nome di **immagine del processo**.
- Informazioni sullo stato input / output.
- Informazioni di accounting, chi sta usando il processo.

Ma come sono organizzate queste informazioni?

Per ogni processo c'è un **Process Control Block**, questo contiene le informazioni viste prime e viene mantenuto nella zona di memoria riservata al _kernel_, questo significa quindi che nessun processo deve poter accedere a questa zona ma soltanto il Sistema Operativo.

Questo Process Control Block quindi viene **creato e gestito dal sistema operativo** e permette a quest'ultimo di **gestire più processi contemporaneamente**, dato che il _blocco_ contiene sufficienti informazioni per bloccare l'esecuzione di un programma e farla riprendere più avanti sempre nello stesso punto in cui era stata fermata.

> [!info] Trace di un processo
> Il comportamento di un processo dipende dalle istruzioni che esegue, questa sequenza di istruzioni è detta **trace** ovvero **traccia del processo**.

> [!info] Dispatcher
> Il Dispatcher è un programma presente nel kernel che attraverso dei calcoli che vedremo più avanti decide quando sospendere un processo per mandarne in esecuzione un altro. Questo è presente sempre in memoria anche in sistemi _microkernel_.

## Esecuzione di un Processo
Si considerino 3 processi in esecuzione, quindi sono tutti presenti in memoria, ignoriamo la memoria virtuale:

![[Pasted image 20241005110817.png|150]]

Dal punto di vista di ciascuno dei processi, ognuno viene eseguito senza interruzioni fino al termine:

![[Pasted image 20241005111008.png]]

Adesso supponendo che su questo sistema ci sia soltanto un processo, in realtà i processi non sono stati eseguiti senza interruzioni:

![[Pasted image 20241005111132.png|300]]

Quindi sono stati eseguiti in ordine: A, Dispatcher, B, Dispatcher, C, Dispatcher, A, Dispatcher, C.
Ogni programma è ripartito dall'ultima interruzione.

Il vantaggio è per chi scrive i programmi dato che non devono preoccuparsi di queste interruzioni, infatti per il programma "non esistono". È ovviamente più difficile costruire un sistema operativo capace di fare ciò.

## Modello dei Processi a 2 Stati
Un processo visto in modo molto semplice può trovarsi in due stati:
- In Esecuzione
- Non in Esecuzione (ma comunque "attivo")

![[Pasted image 20241005111554.png|500]]

Da notare che un processo appena creato **non va subito in esecuzione**, deve mandarcelo il _Dispatcher_.

Se ci fossero soltanto due stati a livello implementativo possiamo vederlo in questo modo:

![[Pasted image 20241005111821.png|500]]

Quindi c'è una coda dei processi _non in esecuzione_ dove il _dispatcher_ prende il processo in cima alla coda e lo mette in esecuzione sul processore e successivamente dalla CPU alla coda, questo ciclo continua finché un processo non finisce (se finisce).

## Creazione di Processi
In ogni istante in un sistema operativo **c'è sempre almeno 1 processo in esecuzione**, infatti come minimo è in esecuzione un gestore dell'interfaccia, che sia grafica o solo testuale.

Se l'utente da un comando, quasi sempre viene creato un nuovo processo, ad esempio clicchiamo con il mouse su un programma oppure tramite un comando.

> [!info] Process Spawning: Un processo crea un altro processo
> Il processo **padre** è il processo originale ovvero quello che nell'esempio di prima è il gestore dell'interfaccia, mentre il processo **figlio** è quello nuovo appena creato.
> Il vecchio processo è comunque in esecuzione e quindi si passa da $n$ processi a $n+1$.
> Potrebbero anche crearsi più processi figli.

## Terminazione di un Processo
Abbiamo visto prima che c'erano più modi di terminazione, nel caso di un **normale completamento** del processo questo avviene tramite una particolare **istruzione macchina** che si chiama _HALT_, questa genera un'interruzione per il S.O.

In linguaggi di programmazione ad alto livello questa viene invocata da *system call* come _exit_. Inoltre questa istruzione per terminare il programma di solito viene inserita automaticamente nei compilatori dopo l'ultima istruzione del _main_ del programma.

L'altro caso era una terminazione forzata che chiamiamo **uccisioni** e possono avvenire:
- Dal S.O. per errori come la terminazione di memoria o altri errori fatali.
- Dall'utente come ad esempio premendo la "X" della finestra.
- Da un altro processo, ad esempio dal terminale uccidiamo un altro processo.

In entrambi i casi sicuramente diminuiamo il numero dei processi, però ci sarà sempre un processo **master** che non può essere terminato a meno che non si spenga il computer.

## Modello dei Processi a 5 Stati

![[Pasted image 20241005113110.png]]

Adesso al posto dello stato _not running_ ne consideriamo altri 2, uno chiamato _ready_ e l'altro _blocked_, da notare che si potrebbe anche andare da _blocked_ ad _exit_ in alcuni casi di terminazione forzata.

Il funzionamento è molto simile a prima, quindi:
- Appena avviato non va subito in esecuzione ma in _Ready_.
- Il Dispatcher decide quando mandarlo in _Running_ e anche quando farlo tornare in _Ready_.
- Come visto prima, se ad esempio un programma deve aspettare un dispositivo I/O allora viene mandato in _Blocked_ cioè in attesa. Dopo che l'attesa è finita il processo torna in _Ready_.

**Per il Dispatcher quindi non avrebbe senso mandare in Running un processo Blocked**.

A livello implementativo possiamo vederlo così:

![[Pasted image 20241005113707.png]]

Basta quindi aggiungere una cosa per i processi in attesa.

Possiamo migliorare questa implementazione nel seguente modo:

![[Pasted image 20241005113818.png]]

In questo modo abbiamo diverse code per ogni tipo di blocco, quindi ad esempio i processi in attesa della stampante si trovano sulla stessa coda; quelli in attesa di un input dalla tastiera sono sulla stessa coda ecc...

In questo modo quando un blocco termina il Sistema Operativo può prendere il primo processo della coda corrispondente invece di andarlo a cercare in una coda generale come nell'implementazione precedente, questo quindi migliora le prestazioni.

## Processi Sospesi
Prima abbiamo detto che tutti i processi si trovano sulla RAM quando sono in esecuzione o bloccati, non sempre è così.

Quando i processi sono in attesa di I/O questi abbiamo visto andare in stato di _blocked_, questo significa che stanno sprecando memoria RAM dato che non stanno svolgendo operazioni. Lo stato _blocked_ per alcuni processi diventa _suspended_ e quando questo accade il processo viene spostato("swappato") dalla RAM al disco rigido.

Vengono introdotti due nuovi stati:
- **blocked / suspended** ovvero quando viene swappato mentre era bloccato.
- **ready / suspended** quando invece viene swappato mentre non era bloccato. (anche un processo pronto può venire sospeso per alcune ragioni)

Quindi otteniamo in totale un **modello dei processi a 7 stati**:

![[Pasted image 20241005121203.png]]

Appena il processo viene creato va fatta subito una scelta da parte del S.O. ovvero se mandare il processo in stato di _ready_ e quindi metterlo in RAM oppure se caricarlo sul disco in stato di _ready / suspended_, poi come prima il _dispatcher_ decide chi mandare in esecuzione e chi lasciare in _ready_; se ci sono attese vengono mandate i processi in _blocked_ e questo viene "sbloccato" solo quando l'evento che si sta aspettando accade.

Viene aggiunto che un programma _blocked_ potrebbe essere mandato in _blocked / suspended_ oppure che un programma in esecuzione venga mandato in _ready / suspended_, inoltre da notare che un programma _blocked / suspended_ può anche andare in _ready / suspended_ e quindi rimanere sul disco.

**Da notare anche che da qualsiasi stato si può passare ad Exit, ad esempio se un processo ne uccide un altro**.

### Motivi per Sospendere un Processo
- Swapping: Il S.O. ha bisogno di memoria per eseguire un programma _ready_.
- Interno al S.O.: Il S.O. sospetta che il processo stia causando problemi.
- Richiesta utente interattiva: Ad esempio quando eseguiamo debugging, oppure collegato all'uso di risorse.
- Periodicità: Il processo è stato pensato per eseguire poche istruzioni solo qualche volta al giorno (ad esempio monitoraggio per accounting), quindi durante il tempo in cui non esegue nulla non c'è motivo di tenerlo in RAM.
- Richiesta del padre: Il processo padre vuole sospendere l'esecuzione del figlio per esaminarlo o modificarlo oppure per coordinarlo con altri figli.

## Processi e Risorse
![[Pasted image 20241005122210.png]]

Vediamo che più processi quindi possono richiedere l'utilizzo delle stesse risorse, ad esempio la prima risorsa I/O possiamo dire che è esclusiva ovvero può essere utilizzata da un solo processo alla volta, infatti la sta utilizzando $P_{1}$ e $P_{2}$ è in attesa (freccia tratteggiata). Mentre altre risorse possono essere usate contemporaneamente come ad esempio la memoria, ovviamente non le stesse locazioni nello stesso momento ($P_n$ infatti sta aspettando per delle zone di memoria).

# Strutture di Controllo del S.O.
Dato che il Sistema Operativo gestisce l'uso delle risorse di sistema da parte dei processi ma anche le risorse che questi utilizzano deve conoscere lo stato di ogni processo e di ogni risorsa. Per fare questo il S.O. crea **una o più tabelle per ogni entità da gestire**.

Con un livello di astrazione molto alto possiamo vederlo in questo modo:

![[Pasted image 20241005122641.png|500]]

Per ora noi abbiamo visto soltanto i **Process Control Block** e sono i blocchi che vediamo in _Primary Process Table_, uno per ogni processo, le _process image_ sempre come visto prima sono le zone di memoria che utilizzano i corrispettivi processi, questa non si trova quindi nel _PCB_.

Da ricordare inoltre che tutto questo è **contenuto nel kernel** e quindi non accessibile ai processi.

> ***!!! Tutte le tabelle di seguito verranno approfondite più avanti nel corso !!!***

## Tabelle di Memoria
Sono usate per la gestione della memoria principale e secondaria, la secondaria serve per la **memoria virtuale**. Contengono diverse informazioni:
- Allocazione di memoria principale da parte dei processi.
- Allocazione di memoria secondaria da parte dei processi.
- Attributi di protezione per l'accesso a zone di memoria condivisa
- Informazioni per gestire la memoria virtuale

## Tabelle per I/O
Sono usate per gestire i dispositivi I/O:
- Sapere se il dispositivo è disponibile
- Stato dell'operazione I/O
- La locazione di memoria principale usata come sorgente o destinazione dell'operazione di trasferimento I/O

## Tabelle dei File
Hanno informazioni su:
- Esistenza dei file
- Locazione di memoria secondaria
- Stato correnti
- Altri attributi come nome ecc...
Queste sono memorizzate su disco e una parte in RAM.

## Tabelle dei Processi
Il SO deve sapere:
- Stato del processo
- Identificatore
- Locazione di memoria
- altre info...
Tutte queste informazioni si trovano nel **PCB** e queste informazioni prendono il nome di **attributi del processo**.

Si dice **process image** "quello che vede il programmatore" o anche il processo vero e proprio quindi, come visto anche prima è la zona di memoria RAM utilizzata quindi:
- Programma sorgente
- Dati (variabili)
- Stack delle chiamate
Questi 3 visti si trovano in RAM mentre
- Il PCB si trova nel kernel

Da notare che se eseguiamo un'istruzione l'immagine del processo cambia, ad esempio viene modificata una cella di memoria o un registro, l'unica eccezione a questa regola è un _jump_ sulla stessa istruzione, infatti qualsiasi altra istruzione come minimo deve modificare il _Program Counter_.

## Attributi dei Processi
Le informazioni contenute in un _PCB_ possono essere raggruppate in 3 categorie:
- Identificazione
- Stato
- Controllo

Per identificare un processo abbiamo visto che gli viene assegnato un identificativo unico che si chiama **PID (Process IDentifier)**, un numero positivo che gli viene assegnato. Molte tabelle del SO usano i PID per realizzare collegamenti fra le varie tabelle e quella dei processi, ad esempio per tenere conto di quella processo sta utilizzando una determinata risorsa.

> [!warning] Stato del Processo e Stato del Processore
> È importante non confondere le due cose, gli stati del processo sono quelli visti prima come ad esempio _ready, blocked ecc..._ mentre lo stato del processore è il contenuto dei suoi registri, le sue **informazioni di stato**.


## Process Control Block
Contiene le informazioni necessarie al SO per controllare e coordinare i vari processi attivi.

- **Identificatori**
	- PID del processo
	- PID del processo padre ovvero PPID (Parent PID)
	- Identificatore dell'utente che lo ha avviato
- **Informazioni sullo stato del Processore**, queste informazioni possono essere copiate sul PCB (RAM):
	- Registri utente (accessibili dai programmatori)
	- Program Counter
	- Stack Pointer
	- Registri di Stato
- Informazioni di **controllo del processo**:
	- Stato (_ready, blocked,..._)
	- Priorità e altre info per lo scheduling (ultima volta che è stato eseguito ad esempio)
	- L'evento da attendere per tornare _ready_ se in attesa.
- Supporto per strutture dati:
	- Puntatori ad altri processi
	- Questi puntatori possono servire ad esempio a mantenere delle [[Strutture Dati#Liste Semplici con Puntatori|liste puntate]] di processi, come abbiamo visto per l'attesa delle risorse.
- Comunicazione tra processi
	- Flag, segnali e messaggi per supportare la comunicazione.
- Permessi Speciali (a cosa può accedere il processo)
- Gestione della Memoria
	- **Puntatori** ad aree di memoria (**NON memoria effettiva**) che gestiscono l'utilizzo della memoria virtuale.
- Uso delle risorse
	- File aperti
	- Uso di altre risorse come il processore o altri componenti

_Process Image_ vista in memoria virtuale ovvero astraendo da come è realmente utilizzata (non sono tutte vicine queste informazioni):

![[Pasted image 20241005130127.png]]

La parte del _Process Control Block_ quindi ricordiamo **non** essere sotto il controllo del processo ma bensì del Sistema Operativo. Da notare inoltre che l'ultima zona bianca in fondo è condivisa fra tutti i processi, infatti normalmente questo non potrebbe accadere ma se chi ha li ha scritto lo ha previsto allora è possibile.

Il _Process Control Block_ quindi è una parte fondamentale del Sistema Operativo dato che descrive il suo stesso stato e proprio per questo richiede delle protezioni, un blocco non deve essere modificato in modo errato.

## Modalità di Esecuzione
Le avevamo accennate all'inizio, abbiamo la **kernel mode** dove si ha pieno controllo sul sistema, quindi possiamo accedere ovunque; e la **user mode** dove non possiamo accedere a zone di memoria protette, di solito viene usata per i programmi utente.
Questo è anche un modo di protezione da utenti malintenzionati.

### Kernel Mode
È stata creata per le operazioni eseguite appunto dal kernel come ad esempio:
- Gestione dei processi tramite PCB
	- Creazione e terminazione
	- Scheduling e dispatching
	- Process Switching (La logica del dispatching)
	- Sincronizzazione e comunicazione fra processi
- Gestione della memoria principale
	- Allocazione di spazio per i processi
	- Gestione della memoria virtuale
- Gestione I/O
	- Gestione buffer e cache per I/O
	- Assegnazione risorse I/O ai processi
- Funzione di supporto
	- Gestione di interrupt ed eccezioni, accounting e monitoraggio

Spesso però i _programmi utente_ hanno bisogno degli I/O, per fare questo i programmi possono passare in modalità kernel per poi tornare in _user mode_.

> [!summary] Da User Mode a Kernel Mode e ritorno
> Un processo inizia sempre dalla _User Mode_, a seguito di un interrupt si porta a _Kernel Mode_:
> - La prima cosa che fa l'hardware, prima ancora di copiare lo stato del processore, è cambiare la modalità, quindi adesso ci troviamo in modalità sistema.
> 
> A questo punto possiamo eseguire gli interrupt handler in modalità kernel, ed è proprio quello che vogliamo dato che questi si trovano nel kernel, che altrimenti sarebbe inaccessibile.
> L'handler a questo punto una volta terminato, prima di restituire il controllo al processo, lo farà tornare in modalità utente.
> > [!warning]
> > Quando un processo va in modalità kernel può eseguire soltanto istruzioni presenti nel kernel stesso (software di sistema) e non comandi scritti nel suo codice sorgente.
> > 
> 

L'interrupt handler può essere eseguito in diversi "modi", e in tutti questi dobbiamo essere in kernl mode:
- Eseguito per conto dello stesso processo interrotto che lo ha esplicitamente voluto
	- System calls oppure in risposta ad una sua richiesta di I/O
- Eseguito per conto dello stesso processo interrotto ma non voluto:
	- Errore fatale (_abort_): Il processo viene terminato
	- Errore non fatale (_fault_): Trasparente rispetto al processo
- Codice eseguito per conto di un altro processo
	- È un caso particolare dove ad esempio un processo _A_ ha fatto richiesta di I/O e si trova adesso in stato _blocked_, se durante l'esecuzione di un altro processo _B_ viene eseguita la richiesta di _A_ allora l'interrupt viene eseguito per conto del processo _B_ ma è in risposta a quello che ha chiesto _A_. Questo è ormai "accettato" nei moderni sistemi operativi.

## Creazione di un Processo
Il Sistema Operativo deve:
- Assegnargli un **PID**
- Allocargli spazio in RAM
- Inizializzare il suo **PCB**
- Inserire il processo nella giusta coda, quindi se in _ready_ o _suspended_.
- Creare o espandere strutture dati come ad esempio quelle per l'accounting

## Switching tra Processi
In questa logica di switching possono esserci alcuni problemi, ad esempio:
- Quali fattori determinato uno switch?
- Cosa deve fare il S.O. per tenere aggiornate tutte le strutture relative ai processi? (ad esempio le code _ready_)

> [!warning] Switch modalità e switch processi
> È importante non confondere le due cose, lo switch di modalità lo abbiamo visto prima e serve a permettere l'esecuzione degli handler in modalità sistema.
> Lo switch tra processi è il meccanismo che decide quale processo mandare in esecuzione e quale in stato di sospensione.

### Quando effettuare uno switch

Questo può succedere quando il S.O. prende il controllo togliendolo al processo, questa cosa può accadere per vari motivi:

![[Pasted image 20241005192035.png|500]]


> [!abstract] Passaggi per switching fra processi
> Ricordiamo che vanno tutti eseguiti in Kernel Mode
> 1) Salvare il contesto del programma ovvero registri e PC (copiati nel PCB)
> 2) Aggiornare il PCB attualmente in esecuzione
> 3) Spostare il PCB nella coda appropriata
> 4) Scegliere un altro processo da eseguire (potrebbe avvenire anche prima)
> 5) Aggiornare il PCB del nuovo processo
> 6) Aggiorna le strutture dati per la gestione della memoria
> 7) Ripristina il conteso del processo (registri)
> 
> Notiamo quindi che escluso il processo 4 i primi 3 sono per un processo _A_ e gli ultimi 3 che fanno le stesse cose ma in ordine inverso sono per il nuovo processo _B_.

## Esecuzione del SO

> [!question] Il SO è un processo?
> Il Sistema Operativo è un insieme di programmi ed è eseguito dal processore come ogni altro programma.
> Molto spesso lascia che altri programmi vadano in esecuzione per poi riprendere il controllo tramite gli interrupt.
> È un processo? Possiamo vedere che il comportamento è molto simile ma se si, come viene controllato?
> 
> **Dipende dal Sistema Operativo**

### Kernel Separato

![[Pasted image 20241005193546.png|300]]

Il Kernel viene eseguito al di fuori dei processi, quindi in questo caso il sistema operativo **non è un processo**. Questo è **eseguito come entità separata** con privilegi elevati e zone di memoria riservate.

### Kernel all'interno dei processi utente

![[Pasted image 20241005193709.png|300]]

In questo caso il Sistema Operativo viene eseguito nel contesto di un processo utente dopo un interrupt. Come visto prima questo interrupt è una parte del SO che viene eseguita e "delegata" al processo in esecuzione.

**Comunque lo stack delle chiamate del processo e quello del SO è separato, questo per questioni di sicurezza**.

Inoltre ricordiamo che non è necessario eseguire un process switch ma soltanto un mode switch.

### Kernel basato sui Processi

![[Pasted image 20241005194336.png|300]]

Qui **tutto è un processo** anche gli interrupt del Sistema Operativo, l'unica cosa che non lo è sono le funzioni che permettono il **process switching**. In questo caso quindi anche i processi del sistema operativo si trovano all'interno delle varie code.

### Linux - Misto tra 2 e 3
Le funzioni del Kernel sono eseguito per lo più tramite interrupt per conto del processo corrente, ci sono però dei processi di sistema chiamati **kernel threads** che partecipano alla normale competizione del processore senza essere invocati, ci sono già all'accensione.

Di solito sono periodici, quindi ogni "tot tempo" eseguono un'operazione come ad esempio:
- Riorganizzare la RAM liberando spazio
- Gestire dispositivi I/O
- Operazioni di rete

# Unix
Usa il modello 2 dove la maggior parte del SO viene eseguito all'interno dei processi utente con le stesse tecniche che abbiamo visto prima.


> [!info] Transizioni tra Stati dei Processi
> 
> ![[Pasted image 20241005195853.png|500]]
> 
> Qua abbiamo più stati ma il funzionamento è simile a quello visto prima.
> Quando un processo chiama la funzione **fork** crea un processo figlio, va in _ready to run in memory_ dove è pronto per essere selezionate mentre se si trova in _ready to run swapped_ significa che si trova sul disco. Il running è diviso in _kernel running_ e _user running_ che indicano in che modalità è eseguito un processo, da notare che prima bisogna passare per la _kernel running_.
> La _preemted_ indica quando togliamo il processore ad un processo prima che finisca, la _asleep in memory_ indica che non può essere eseguito finché non avviene un altro evento ma si trova comunque in memoria.
> _Sleeping Swapped_ è come il precedente ma si trova in memoria.
> Quando un processo finisce va nello stato _zombie_, più nello specifico quando un processo viene terminato deve mandare al suo padre un codice che indica la sua terminazione, finché non lo fa il processo figlio si trova in questo stato zombie. In questo stato inoltre non esiste più l'immagine del processo ma soltanto il suo PCB.

## Il Processo Unix
L'immagine di un processo Unix è divisa in diverse categorie.
### Livello Utente
Questi sono visti dai programmatori
- Process Text: Codice Sorgente in linguaggio macchina
- Process Data: Sezione di dati del processo ovvero i collegamenti ai valori delle variabili.
- User Stack: Le chiamate del processo
- Shared Memory: Memoria condivisa con altri processi se presente.

### Livello Registro
- Program Counter: Indirizzo della prossima istruzione del process text da eseguire
- Processor status register: Registro di stato del processore, relativo a quando è stato swappato l'ultima volta
- Stack Pointer: puntatore alla cima dello user stack
- General purpose registers: Registri accessibili al programmatore, relativo a quando è stato swappato l'ultima volta.

### Livello Sistema
Gestire un proesso a livello di memoria

- Process table entry: Puntatore alla tabella di tutti i processi che individua quello corrente
- U Area: Informazioni per il controllo del processo
- Process Region Table: Definisce il mapping tra indirizzi virtuali ed indirizzi fisici
- Kernel Stack: Lo stack di chiamate separato da quello utente usato per le funzioni di sistema.

**Formato del PCB di un processo UNIX**:

![[Pasted image 20241005211418.png]]

- Process Size: Indica la dimensione dell'immagine del file e **non** quella del PCB, quest'ultimo ha grandezza predefinita.
- User Identification: Ad esempio se un processo è in esecuzione utente e va in modalità kernel, l'**effective user ID** diventa il "sistema operativo" mentre il **real user ID** rimane l'utente iniziale.
- Event Descriptor: Indica perché il processo è in _asleep_
- P_Link: Puntatore al prossimo processo in coda (coda ready o altre code).

### Creazione di un Processo Unix
- Viene effettuata una chiamata di sistema `fork()`
- Il SO, in kernel mode:
	1) Alloca una entry nella tabella dei processi
	2) Assegna un PID al processo
	3) Copia l'immagine del padre escludendo la memoria condivisa, una volta fatto questo sia padre che figlio vorranno eseguire la stessa istruzione successiva al fork.
	4) Incrementa i contatori di ogni file aperto dal padre dato che ora sono anche del figlio
	5) Assegna al processo lo stato _Ready to Run_
	6) La fork ritorna il PID del figlio al padre e 0 al figlio, nello specifico all'interno del codice posso inserire un _if_ sul valore della fork, se è 0 sono nel figlio e posso eseguire le istruzioni che voglio, se non è 0 sono il padre e allora posso continuare con le vecchie istruzioni oppure ad esempio aspettare la terminazione del figlio.

Quindi quando creiamo un processo figlio, inizialmente questo è una copia del padre, si è notato che è la cosa più efficiente dato che è la situazione più comune quella dove un figlio esegue una parte del codice del padre.

Una volta creato, il kernel decide se continuare ad eseguire il padre, eseguire il figlio o un altro processo ancora.

# Thread
Circa 1:20:00