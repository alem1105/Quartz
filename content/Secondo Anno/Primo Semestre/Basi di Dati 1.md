**SLIDE DI INTRODUZIONE**

Prima per immagazzinare i dati si utilizzavano sistemi informativi dove ogni applicazione aveva il suo file privato, quali erano li svantaggi?
- **Ridondanza**: Se due applicazioni usavano gli stessi dati questi venivano salvati due volte.
- **Inconsistenza**: Se abbiamo due copie, l'aggiornamento di un dato poteva riguardare soltanto una di queste.
- **Dipendenza dei Dati**: Ogni applicazione organizzava i dati in modo diverso, in base all'utilizzo che ne faceva.

Adesso si utilizzano le **Basi di Dati (Database)** ovvero un insieme di file **mutuamente connessi**, questi sono organizzati in strutture dati che ne facilitano la creazione e l'accesso, inoltre ottimizzano la gestione delle risorse fisiche.

Si utilizzano i **Sistemi di Gestione di Basi di Dati (DBMS)** per la gestione di grandi masse di dati residenti su memorie secondarie.

Quando un'informazione viene registrata in formato elettronico ci sono due possibilità:
- **Dati Strutturati**: I dati sono rappresentanti da stringhe di simboli e da numeri.
- **Dati non strutturati**: Rappresentati in linguaggio naturale.

La struttura di un dato **dipende dal suo utilizzo** e può essere modificate nel tempo, ad esempio se dobbiamo salvare i dati relativi ad una persona ci servirà: nome, cognome, codice fiscale ecc...

L'obiettivo è quello di facilitare l'elaborazione dei dati sulla base delle loro **relazioni**, infatti possiamo accedere singolarmente agli elementi della struttura tramite "interrogazioni" per recuperare informazioni o effettuare calcoli.

In una base di dati ogni componente è interessata ad una porzione del Sistema Informativo, queste porzioni possono sovrapporsi ma la base di dati ci permette di ridurre le ridondanze e conseguenti inconsistenze.

La condivisione non è mai completa, vanno regolamentati gli accessi e questa comporta il controllo della **concorrenza** ovvero l'accesso simultaneo allo stesso dato.

> [!info] Sistema Informativo
> Un sistema informativo è un complesso di dati organizzati fisicamente in una memoria secondaria e gestiti in maniera tale da consentirne la creazione, l'aggiornamento e l'interrogazione.

 I dati sono organizzati in aggregati di informazioni omogenee che costituiscono le componenti del sistema informativo, ogni operazione ha per oggetto un singolo aggregato mentre un'interrogazione può coinvolgerne più di uno.

Nelle basi di dati:
- Aggregati di informazioni omogenee: file
- Indici: File che permettono di recuperare velocemente delle informazioni.

L'informazione è rappresentata sotto forma di dati ovvero dei valori che devono essere interpretati e correlati per fornire un'informazione.

Ad esempio "Alessio Marini" e '1234567890' sono una stringa e un numero ovvero due dati, ma se li vediamo come risposta alla domanda "Di chi sono gli appunti e quel è il suo numero di telefono?" allora costituiscono informazione.

# Modello dei dati
Sono strutture da utilizzare per organizzare i dati e le loro relazioni, un componente fondamentale sono i costruttori di tipo, ad esempio nel **modello relazionale** abbiamo il costruttore di relazione che organizza i dati come insieme di record.

Ci sono due tipi di modelli:
- **Modelli Logici**: Sono indipendenti dalle strutture fisiche ma sono disponibili nei DBMS.
- **Modelli Concettuali**: Sono indipendenti dalle modalità di realizzazione e hanno lo scopo di rappresentare le entità del mondo reale e le loro relazione nella prima fase della progettazione.

## Modello Relazionale
Nel 1970 IBM introduce il **Modello Relazionale**, i dati e le relazioni vengono rappresentati come **valori** e non ci sono riferimenti espliciti come puntatori, garantendo quindi una rappresentazione di alto livello.

- Oggetto: record
- Campi: Informazioni di interesse

Ad esempio:

- Oggetto: "Membro dello Staff"
- Campi: Codice, Cognome, Nome, Ruolo, Anno di Assunzione

$$
\begin{array}{|c|c|c|c|c|} \hline \textbf{CODICE} & \textbf{COGNOME} & \textbf{NOME} & \textbf{RUOLO} & \textbf{ASSUNZIONE} \\ \hline \text{COD1} & \text{Rossi} & \text{Mario} & \text{Analista} & 1995 \\ \hline \end{array}
$$

- Tabella: Insieme di record di tipo omogeneo, creiamo ad esempio la Tabella STAFF ovvero l'insieme di record di tipo "Membro dello Staff":

$$
\begin{array}{|c|c|c|c|c|} 

\hline \textbf{CODICE} & \textbf{COGNOME} & \textbf{NOME} & \textbf{RUOLO} & \textbf{ASSUNZIONE} 

\\ \hline \text{COD1} & \text{Rossi} & \text{Mario} & \text{Analista} & 1995 \\ 

\hline \text{COD2} & \text{Bianchi} & \text{Pietro} & \text{Analista} & 1990 \\ 

\hline \text{COD3} & \text{Neri} & \text{Paolo} & \text{Amministratore} & 1985 \\ \hline 

\end{array}
$$

_Esempio più completo di DB Relazionale_

**Studenti:**

$$
\begin{array}{|c|c|c|c|} 

\hline \textbf{MATRICOLA} & \textbf{COGNOME} & \textbf{NOME} & \textbf{DATA NASCITA}

\\ \hline \text{276545} & \text{Smith} & \text{Mary} & \text{25/11/1980}\\ 

\hline \text{485745} & \text{Black} & \text{Anna} & \text{23/04/1981}\\ 

\hline \text{200768} & \text{Verdi} & \text{Paolo} & \text{12/02/1981} \\ \hline 

\end{array}
$$

**Corsi:**

$$
\begin{array}{|c|c|c|} 

\hline \textbf{CODICE} & \textbf{TITOLO} & \textbf{TUTOR}

\\ \hline \text{01} & \text{Physics} & \text{Grant} \\ 

\hline \text{03} & \text{Chemistry} & \text{Beale}\\ 

\hline \text{04} & \text{Chemistry} & \text{Clark}\\ \hline 

\end{array}
$$

**Esami:**

$$
\begin{array}{|c|c|c|} 

\hline \textbf{STUDENTE} & \textbf{VOTO} & \textbf{CORSO}

\\ \hline \text{276545} & \text{C} & \text{01} \\ 

\hline \text{276545} & \text{B} & \text{04}\\ 

\hline \text{200768} & \text{B} & \text{01}\\ \hline 

\end{array}
$$

Abbiamo la tabella Esami che mette collega i corsi e gli studenti.

> [!info] DB e DBMS
> - Il Database è la collezione di dati logicamente correlati di interesse per il Sistema Informativo
> - Il DBMS è un software che interagisce con il DB da una parte e con i programmi applicativi dall'altra
> - Oggetti nella base di Dati: Memorizzano proprietà di "Oggetti" e relazioni tra oggetti nel dominio di interesse.

Le componenti di un **Sistema Informativo Informatizzato** sono quindi:
- La base di dati **BD**
- Un **DBMS**
- Applicativo software che utilizza il DB
- Hardware del computer, ovvero i dispositivi di memorizzazione.
- Personale che gestisce il sistema.


![[Pasted image 20240927170754.png|400]]

La memorizzazione avviene in maniera astratta, ovvero, i sistemi di basi di dati utilizzano dei formati proprietari per salvare i dati, ma offrono all'utente una vista "normale" dell'oggetto memorizzato, in modo da rendere trasparenti i dettagli di memorizzazione e manipolazione.

# Livelli di Astrazione di un DB
![[Screenshot 2024-09-27 alle 17.09.51.png|500]]

- **Schema Esterno**:Descrizione di una **porzione** della base di dati in un modello logico attraverso delle **viste** parziali che possono prevedere organizzazioni dei dati diverse rispetto a quelle utilizzate nello schema logico, queste riflettono esigenze e privilegi dell'utente. Ad uno schema logico si possono associare più schemi esterni.
  (In poche parole non tutti gli utenti devono accedere a tutti i dati, chi ha più privilegi può vedere più cose)
- **Schema Logico**: Descrizione dell'intera base di dati nel modello logico principale del DBMS, come ad esempio la struttura delle tabelle.
- **Schema Fisico**: Rappresentazione dello schema logico per mezzo di strutture fisiche di memorizzazione, i file.

_Esempio_

Dato lo schema logico:

![[Pasted image 20240927171521.png|400]]

Una possibile vista _CorsiSedi_ può essere:

![[Pasted image 20240927171558.png|400]]

Gli accessi alla base **avvengono solamente attraverso lo schema esterno** che può coincidere o meno con quello logico.

## Indipendenza dei Dati
- **Indipendenza Fisica**: Il livello logico e quello esterno sono indipendenti da quello fisico, questo comporta che una relazione è utilizzata nello stesso modo qualunque sia la sua realizzazione fisica ovvero l'organizzazione dei file sulla memoria. Inoltre la realizzazione fisica può cambiare senza causa problemi nei programmi che utilizzano la base di dati.
- **Indipendenza Logica**: Il livello esterno è indipendente da quello logico, infatti aggiunte o modifiche alle viste non richiedono modifiche al livello logico mentre modifiche che allo schema logico che lasciano inalterato lo schema esterno sono trasparenti.

## Schemi e Istanze
In ogni base di dati esistono:
- **Schema**: Non cambia nel tempo e ne descrive la struttura, sono le intestazioni delle tabelle.
- **Istanza**: I valori attuali che possono cambiare, sono gli elementi di ogni tabella.

## Linguaggi per le Basi di Dati
- **Data Definition Language (DDL)**: Per la definizione degli schemi
- **Data Manipulation Language (DML)**: Per l'interrogazione e l'aggiornamento delle istanze della base di dati.
- **SQL (Structured Query Language)**: Linguaggio standardizzato per database basati sul modello relazionale. In SQL le due funzionalità sono integrate in un unico linguaggio.

## Ricapitolando
Le basi di dati sono:
- Multiuso
- Integrazione
- Indipendenza dei dati
- Controllo centralizzato (**DBA: Database Administrator**).

I vantaggi sono:
- Minima ridondanza
- Indipendenza dei dati
- Integrità
- Sicurezza

### Integrità
I dati devo soddisfare i **vincoli** imposti dalla realtà di interesse, ad esempio:
- Uno studente vive in una sola città, **Dipendenze Funzionale**.
- La matricola identifica univocamente uno studente, **Vincoli di Chiave**.
- Un voto è un intero positivo compreso tra 18 e 30, **Vincoli di Dominio**.
- Lo straordinario di un impiegato è dato dal prodotto del numero di ore per la paga oraria, lo stipendio non può diminuire, **Vincoli Dinamici**.

### Sicurezza
I dati devono essere protetti da accessi non autorizzati, il DBA deve considerare chi può accedere a quali dati e in quale modalità e decidere il regolamento di accesso e gli effetti di una violazione, inoltre i dati devono essere protetti da malfunzionamenti hardware, software e dall'accesso concorrente alla base di dati.

Ad esempio una transazione deve essere eseguita completamente, **committed** oppure non deve essere eseguita affatto **rolled back**.

Per ripristinare un valore corretto si usa il **transaction log** che contiene i dettagli delle operazioni, si esegue il **dump** ovvero la copia dei dati.

### Concorrenza

![[Pasted image 20240927173453.png]]

La transazione 1 ha impostato il saldo a 2000 + 1000 mentre la due avendo letto il dato prima della fine della 1 lo ha impostato a 2000 + 500 e terminando per ultima lo ha impostato come valore finale. Per questo è importante gestire la concorrenza.

Il compito di un DBA è quindi:

- Definizione e descrizione di:
	- Schema Logico
	- Schema Fisico
	- Viste
- Mantenimento:
	- Modifiche per nuove esigenze o efficienza
	- Routine (analisi, ripristino ecc...)

# Modello Relazionale
Si basa sul **concetto matematico** di relazione, queste sono come delle tabelle e d'ora in poi le chiameremo appunto relazioni.

- Relazione matematica.
- Relazione secondo il modello relazionale dei dati.
- Relazione che rappresenta un'associazione nel modello **Entità - Relazioni**, rappresenta un collegamento concettuale tra entità diverse.

## Definizioni
- **Dominio**: un insieme, anche infinito, di valori.
Siano _D1, D2,...,Dk_ domini, il prodotto cartesiano di tali domini è dato da:

$$
\{(v1,v2,...,vk)|v1\in D1, v2\in D2, ..., Vk\in Dk\}
$$

- Una **relazione matematica** è un sottoinsieme del prodotto cartesiano di uno o più domini.
- Una relazione che è sottoinsieme del prodotto cartesiano di $k$ domini si dice **di grado k**. (grado = numero di domini)
- Gli elementi di una relazione sono detti **tuple**, il numero di tuple di una relazione indica la **cardinalità** di quest'ultima. (cardinalità = numero di coppie ordinate, ovvero tuple).
- Ogni tupla di una relazione di grado $k$ ha $k$ componenti ordinate (attributi) ma non c'è ordinamento tra le tuple.
- Le tuple di una relazione sono tutte **distinte** almeno per un valore dai vincoli sugli insiemi. (Almeno un elemento deve cambiare fra ciascuna).

_Esempio_

Supponiamo che $k=2$ e i due domini sono $D1=\{bianco,nero\}$ e $D2=\{0,1,2\}$, il prodotto cartesiano è dato da $D1\times D2=\{(bianco,0),(bianco,1),(bianco,2),(nero,0),(nero,1),(nero,2)\}$.

Come relazioni possiamo prendere:
- $\{(bianco,0),(nero,0),(nero,2)\}$: Ha come cardinalità 3 e come grado 2.
- $\{(nero,0),(nero,2)\}$: Ha come cardinalità 2 e come grado 2.

Spesso si usano come domini comuni ai linguaggi di programmazione come _String, Integer, Boolean_.

> [!info] Notazioni
> - Se $r$ è una relazione di grado $k$
> - Se $t$ è una tupla di $r$
> - Se $i$ è un numero intero nell'insieme $\{1,...,k\}$
> 
> Allora $t[i]$ indica la i-esima componente di $t$

_Esempio_

- Se $r=\{(0,a),(0,c),(1,b)\}$
- $t=(0,a)$
- $t[2]=a, t[1]=0, t[1,2]=(0,a)$

## Relazioni e Tabelle
Per interpretare le tabelle dobbiamo assegnare dei nomi a queste e alle loro colonne:

![[Pasted image 20240928125612.png|400]]

- Un **attributo** è definito da un _nome A_ e dal dominio dell'attributo A che indichiamo con _dom(A)_.
- Sia $R$ un insieme di attributi, un'**ennupla** su $R$ è una funzione definita su $R$ che associa ad ogni attributo $A$ in $R$ un elemento di _dom(A)_.
- Se $t$ è un'ennupla su $R$ ed $A$ è un attributo in $R$, allora con $t(A)$ indicheremo il valore assunto dalla funzione $t$ in corrispondenza dell'attributo A.

Vediamo gli elementi graficamente:

![[Pasted image 20240928130222.png|400]]

![[Pasted image 20240928130301.png|400]]

Quindi:
- Una relazione possiamo implementarla come una tabella dove ogni riga è una tupla della relazione e ogni colonna è un attributo.
- Le colonne corrispondono ai domini e hanno associati dei nomi univoci, detti **nomi degli attributi**.
- L'insieme degli attributi di una relazione è detto **schema**
- Se una relazione è denominata da $R$ e i suoi attributi hanno nomi _A1, A2, ..., Ak_ lo schema è indicato da $R(A1,A2,...,Ak)$, questo è lo **schema di relazione**.
- Lo schema spesso è **invariante nel tempo** e descrive la **struttura** della relazione.
- L'**istanza** di una relazione è un'insieme di tuple. (i valori presenti nella tabella)
- L'istanza contiene i valori attuali e possono anche cambiare molto spesso.


- **Schema di base di dati**: Un insieme di schemi di relazione con nomi differenti (un insieme di tabelle).
- **Schema di base di dati relazionale**: Insieme $\{R_1,R_2,...,R_n\}$ di schemi di relazione
- **Base di dati relazionale** con schema $\{R_1,R_2,...,R_n\}$: un insieme $\{r_1,r_2,...,r_n\}$ dove $r_i$ è un'istanza di relazione con schema $R_i$.
Quindi lo schema della base sono l'insieme delle strutture delle tabelle mentre la base di dati sono i valori presenti nelle rispettive tabelle (istanze).

_Esempio_

![[Pasted image 20240928144715.png|400]]

Prima abbiamo utilizzato la notazione $t[i]$ per indicare il valore ad un determinato attributo di una tupla con $i$ intero, adesso si utilizza $t[Ai]$ con $Ai$ nome dell'attributo, ad esempio se prendiamo seconda tupla dell'esempio sopra $t[Regione]=Lombardia$.

Se $Y$ è un sottoinsieme di attributi dello schema $X$ di una relazione allora $t[Y]$ è il sottoinsieme dei valori nella tupla $t$ che corrispondono ad attributi contenuti in $Y$, detto **restizione** di $t$.

## Valori
Nel modello relazionale i riferimenti fra dati in relazioni diverse sono rappresentati per mezzo di valori dei domini che compaiono nelle ennuple.

![[Pasted image 20240928145442.png|400]]

Qui ad esempio la tabella **Esami** mette in relazione gli **Studenti** e i **Corsi** rispettivamente tramite la **Matricola** e il **Codice**.
Se una tabella contiene un elemento univoco di un'altra questa si chiama **slave** mentre l'altra **master**, in questo caso abbiamo quindi due master ovvero **Studenti e Corsi** mentre lo slave è **Esami**.

Il master quindi deve esistere prima dello slave altrimenti non è possibile creare il secondo.

All'interno di una tupla è possibile inserire anche dei valori **nulli** ma non possiamo omettere completamente un campo, le tuple devono seguire tutte lo stesso schema.
Se vogliamo "omettere" dei campi possiamo stabilire un valore di **default**.

> [!info] Valore Speciale NULL
> Il valore **null** non appartiene a nessun dominio ma può essere assegnato a un dominio qualsiasi (qualsiasi attributo).
> Se prendiamo confrontiamo due valori null, anche sullo stesso dominio di attributo, questi risulteranno sempre diversi.
>Non è possibile assegnare NULL ai valori usati come identificativi delle tuple. 

## Vincoli
![[Pasted image 20240928150835.png|400]]

![[Pasted image 20240928150856.png|400]]

Entrambe questi basi di dati presentano degli errori, nella prima abbiamo una data di assunzione impossibile, un codice impiegato ripetuto ma che è un valore univoco e un codice DIP non esistente.

Nella seconda altri tipi di errori ad esempio 32 un voto che non esiste, una lode con un 27 un valore sotto al 18, mentre sugli studenti una matricola duplicata.

I **Vincoli di Integrità** sono delle regole che devono essere soddisfatte da ogni istanza della base di dati.

Quindi nel primo caso possiamo stabilire che:
- Assunzione deve essere > 1980
- Codice impiegato deve essere **UNIQUE**
- Il campo **DIP** è collegato al campo **Dipartimento.Numero**.
Nella seconda base:
- Voto >= 18 AND Voto <= 30
- Voto = 30 OR NOT Lode = "si"
- Il campo Esami.Studente è collegato a Studenti.Matricola
- Matricola deve essere **UNIQUE**

Possiamo dividerli in due categorie: **Vincoli Intra-Relazionali** e **Vincoli Inter-Relazionali**

### Vincoli Intra-Relazionali
Sono definiti su valori di singoli attributi oppure tra valori di una stessa tupla o ancora tra tuple della stessa relazione.

- **Vincoli di chiave Primaria**: unica e mai nulla
- **Vincoli di Dominio**: ad esempio Assunzione > 1980
- **Vincoli di Unicità**: li indichiamo con UNIQUE
- **Vincoli di Tupla**: Voto = 30 OR NOT Lode = "si"
- **Vincoli di esistenza del valore per un certo attributo**: NOT NULL
- **Espressioni sul valore di attributi della stessa tupla**: ad esempio orario_partenza < orario_arrivo, con gli orari di un treno.

### Vincoli Inter-Relazionali
Sono vincoli definiti tra più relazioni ad esempio:
- Impiegato.DIP references dipartimento.numero
- Esami.studente references Studenti.Matricola

## Chiavi
In un'istanza di relazione dobbiamo identificare **univocamente** le tuple di una relazione e per fare questo utilizziamo le **chiavi**, la chiave può essere un attributo o un insieme di attributo.

Un insieme $X$ di attributi di una relazione $R$ è una **chiave** se soddisfa le seguenti condizioni:
- Per ogni istanza di $R$, non esistono due tuple $t1$ e $t2$ che hanno gli stessi valori per tutti gli attributi in $X$, ovvero che $t1[X]=t2[X]$. Quindi i valori in questi attributi devono essere tutti diversi fra le tuple, unici.
- Nessun sottoinsieme **proprio** di X soddisfa la condizione 1. Questo significa che la chiave può essere semplicemente quel sottoinsieme, ovviamente dovremo ricontrollare la seconda condizione anche all'interno di quest'ultimo.

Nel caso in cui un sottoinsieme proprio di $X$ non soddisfi la seconda condizione, $X$ prende il nome di **superchiave**.
Una chiave è anche superchiave dato che è unsieme che contiene se stessa.

Una relazione potrebbe avere più chiavi alternative e si sceglie quella più usata o quella composta da un numero minore di attributi, questa prende il nome di **chiave primaria**.
Questa non ammette valori nulli, deve esserci sempre una chiave dato che le tuple non possono essere uguali e inoltre consentono di mettere in relazione diverse tabelle fra loro.

### Vincolo di Integrità Referenziale
Delle informazioni presenti in relazioni diverse possono essere messe in relazione fra loro tramite le **foreign key**:

![[Pasted image 20240928154000.png|400]]

Nella tebella **Infrazioni** l'attributo **Vigile** è una foreign key che la mette in relazione con la tabella **Vigili**.

Come detto prima la chiave può essere composta da più attributi:

![[Pasted image 20240928154112.png|400]]

In questo caso la chiave primaria della Relazione Auto è formata da _Prov_ e _Numero_ e quindi in **Infrazioni** sono presenti entrambe le informazioni come **foreign key**.

Le Chiavi si stabiliscono in base alle **Dipendenze Funzionali**.

## Dipendenze Funzionali
Una dipendenza funzionale stabilisce un legame semantico tra due insiemi non vuoti di attributi $X, Y$ appartenenti ad uno schema $R$.

Il vincolo si scrive $X\rightarrow Y$ e si legge $X$ _determina_ $Y$.

_Esempio_

Il nostro schema è: VOLI(CodiceVolo, Giorno, Pilota, Ora).

Stabiliamo dei vincoli:
- Un volo con un certo codice parte sempre alla stessa ora
- Esiste un solo volo con un dato pilota, in un dato giorno ad una data ora
- C'è un solo pilota di un dato volo in un dato giorno.
Otteniamo le seguenti dipendenze funzionali:
- CodiceVolo -> Ora (Dato che un volo con lo stesso codice parte sempre alla stessa ora)
- {Giorno, Pilota, Ora} -> CodiceVolo (Dato che c'è un solo volo con un determinato pilota, giorno e ora)
- {CodiceVolo, Giorno} -> Pilota (Dato che c'è un solo pilota dato un volo in un dato giorno)

Questo significa che come chiave posso usare l'insieme {CodiceVolo, Giorno} dato che CodiceVolo mi determina l'ora e con CodiceVolo e Giorno posso determinare il Pilota.

Non posso usare ad esempio soltanto il CodiceVolo dato che in quel caso saprei soltanto a che ora parte l'aereo ma non saprei chi sarà il pilota e che giorno partirà.

Diremo che una relazione $r$ **soddisfa** la dipendenza funzionale $X\rightarrow Y$ se:
- La dipendenza funzionale $X\rightarrow Y$ è applicabile a $R$, ovvero che $X,Y$ sono sottoinsiemi di $R$.
- Le ennuple in $r$ che concordano su $X$ concordano anche su $Y$, ovvero per ogni coppia di ennuple $t1$ e $t2$ in $r$ abbiamo che $t1[X]=t2[X]\Rightarrow t1[Y]=t2[Y]$.
Prendendo l'esempio di prima quindi, se due tuple concordano sul CodiceVolo (X) devono concordare anche sull'ora (Y).
- Nel caso in cui $X\cup Y=R$ allora ci basta verificare che prese due tuple qualsiasi $t1[X]=t2[X]$ per stabilire che la dipendenza non è rispettata.

**X** prende il nome di **Determinante** e **Y** di **Dipendente**, inoltre un'istanza si dice **legale** quando **soddisfa tutte le dipendenze funzionali**.







