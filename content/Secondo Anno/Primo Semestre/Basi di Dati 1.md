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

# Algebra Relazionale
**Linguaggio Formale** per interrogare una base di dati relazionale: Consiste in un insieme di operatori che possono essere applicati ad una o due relazioni e forniscono come risultato una nuova istanza di relazione.

Inoltre è un **Linguaggio Procedurale**: L'interrogazione consiste in un'espressione in cui compaiono operatori dell'algebra e istanze di relazioni della base di dati, in una sequenza che stabilisce l'ordine delle operazioni e i loro operandi.

## Proiezione
Consiste nell'effettuare un _taglio verticale_ su una relazione, ovvero selezionare soltanto alcuni attributi di essa.

Si denota con il simbolo $\pi$ ad esempio  $\pi_{A_{1},A_{2},\dots A_{k}}(r)$, in questo modo stiamo selezionando le colonne di $r$ che corrispondono agli attributi $A1, A2,\dots Ak$.

_Esempio_

![[Pasted image 20241002212523.png]]

**NOTA**: Si seguono le regole insiemistiche e quindi nella relazione risultato non ci sono duplicati, notiamo però che abbiamo cancellato delle ennuple significative, ovvero delle ennuple che sono in realtà diverse se consideriamo tutti gli attributi.

Dobbiamo considerare nella proiezione anche un attributo in più, in questo caso la chiave ovvero C#:

![[Pasted image 20241002212936.png]]

## Selezione
Consente di effettuare soltanto alcune tuple di una relazione.

Si denota con il simbolo $\sigma_{C}(r)$, in questo caso seleziona le tuple della relazione $r$ che soddisfano la condizione $C$.

La selezione è un'espressione booleana composta in cui i termini semplici sono del tipo:

- $A \theta B$ oppure $A\theta'a'$

Dove:
- $\theta$ è un operatore di confronto, $\theta\in \{ <,=,>,\leq,\geq \}$
- A e B sono due attributi con lo stesso dominio
- a è un elemento di dom(A)

_Esempio_

![[Pasted image 20241002213441.png]]

Da notare che al contrario della proiezione, con la selezione non rischiamo di perdere dati significativi.
## Unione
Costruisce una relazione contenente tutte le ennuple che appartengono ad almeno uno dei due operandi, si denota con $\bigcup$

![[Pasted image 20241002153358.png|300]]

L'unione può essere applicata soltanto ad operandi compatibili ovvero:
- Hanno lo stesso numero di attributi
- Gli attributi corrispondenti nell'ordine devono avere lo stesso dominio

Gli schemi in questo caso sono detti **union compatibili**.

**Inoltre**:
- Non è necessario che gli attributi abbiano lo stesso nome ma l'unione ha senso se hanno un significato omogeneo. 
  
  Ad esempio _Numero di esami_ ed _Età_ sono definiti sullo stesso dominio ma non avrebbe senso unire due relazioni che hanno questi attributi in colonne corrispondenti.

- Uno o entrambi gli operandi possono essere il risultato di operazioni precedenti, ad esempio eliminare gli attributi incompatibili.

_Esempio 1_

![[Pasted image 20241002153800.png]]

In questo caso l'unione è fattibile, dato che le istanze sono compatibili, otteniamo quindi:

![[Pasted image 20241002153838.png]]

Abbiamo un problema adesso, non riusciamo più a distinguere i _Docenti_ dagli _Amministrativi_, inoltre dovremmo avere 9 membri del personale ma ne abbiamo solo 8, questo perché una tupla era presente in entrambe le relazioni e quindi è stata riportata una sola volta (Bianchi, C4, Lingue).

Questo è un **problema di progettazione**, possiamo risolverlo cambiando la notazione per i COD:

![[Pasted image 20241002154154.png]]

In questo modo vediamo tutto il personale e riusciamo anche a ditinguerli.

_Esempio 2_

![[Pasted image 20241002154345.png]]

In questo caso non possiamo effettuare l'unione, le due istanze non hanno lo stesso numero di attributi. Come possiamo proseguire?

Possiamo proiettare su un sottoinsieme di attributi comuni (con significato compatibile):

![[Pasted image 20241002154607.png|400]]

Quindi _Amministrativi_ non ha più l'attributi _Stip_ e quindi le relazioni diventano compatibili.

_Esempio 3_

![[Pasted image 20241002154743.png]]

In questo caso non dobbiamo proiettare entrambe le relazioni dato che abbiamo si lo stesso numero di attributi ma _Dipartimento_ e _AnniServizio_ non sono compatibili, dobbiamo quindi rimuoverli entrambi.

![[Pasted image 20241002154951.png|400]]

_Esempio 4_

![[Pasted image 20241002155321.png]]

In questo caso _Dipartimento e Mansioni_ hanno lo stesso dominio ma significato diverso, in questo caso possiamo proiettare togliendo i due attributi, come visto prima.

![[Pasted image 20241002155412.png|400]]

## Differenza
Anche la differenza si applica a operandi **union compatibili**, quindi le condizioni sono uguali a quelle dell'unione.

La differenza consente di costruire una relazione contenente tutte le tuple che appartengono al primo operando e non appartengono al secondo operando.

Si denota con il simbolo $-, \ r_{1}-r_{2}$.

![[Pasted image 20241002155900.png]]

**Attenzione**, la differenza non è commutativa:
- Studenti - Amministrativi: Sono gli studenti che non sono anche amministrativi
- Amministrativi - Studenti: Sono gli amministrativi che non sono anche studenti.

_Risultati:_

![[Pasted image 20241002160010.png|400]]

## Intersezione
Si applica sempre ad operandi **union-compatibili**, consente di costruire una relazione contenente tutte le tuple che appartengono ad entrambi gli operandi.

Si denota con $\bigcap, \ r_{1}\cap r_{2}=(r_{1}-(r_{1}-r_{2}))$

_Esempio_

![[Pasted image 20241002160852.png]]

- L'operazione intersezione **è commutativa**.

![[Pasted image 20241002160925.png]]

Come tutte le operazioni, se non rispetto la **union-compatibili** posso effettuare delle proiezioni.

# Algebra Relazionale II
Per garantire un'ottima qualità di una relazione occorre rappresentare in relazioni diverse più concetti. Infatti capita spesso che le informazioni che interessano un'interrogazione sono distribuite in più relazioni dato che coinvolgono più oggetti associati fra loro.

Dobbiamo individuare le relazioni in cui si trovano le informazioni che ci interessano e combinare queste informazioni in modo opportuno.

## Prodotto Cartesiano
Consente di costruire una relazione contenente tutte le ennuple che si ottengono concatenando ogni ennupla del primo operando con ogni ennupla del secondo.

Si denota con il simbolo $\times, \ r_{1}\times r_{2}$ e si utilizza quando le informazioni che occorrono per rispondere ad una query si trovano i relazioni diverse.

In questa operazione non dobbiamo rispettare la **union-compatibile** e per questo non tutti i risultati che otteniamo hanno un senso.

_Esempio_

![[Pasted image 20241002163748.png]]

_Query:_ Dati dei clienti e degli ordini ($Cliente \times Ordine$).

Per poter distinguere gli attributi con lo stesso nome nello schema risultante possiamo usare l'operazione di _ridenominazione_ per utilizzare una copia della relazione Ordine in cui l'attributo C# diventa CC#. Altrimenti avremmo anche potuto scrivere _Ordine.C#_.

![[Pasted image 20241002164117.png]]

Adesso però abbiamo delle ennuple "inutili" dato che C# e CC# non corrispondono.

Per risolvere questo problema possiamo fare una selezione dove C# e C## sono uguali ottenendo:

![[Pasted image 20241002164418.png]]

Notiamo anche che adesso le colonne C# e C## sono uguali, quindi se vogliamo fare una soluzione più elegante possiamo anche effettuare una proiezione sugli altri attributi e lasciare solo la colonna C#.

## Join Naturale
Consente di selezionare le tuple del prodotto cartesiano dei due operandi che soddisfano la condizione:

$$
R_{1}.A_{1}=R_{2}.A_{1}\wedge R_{1}.A_{2}=R_{2}.A_{2}\wedge \dots\wedge R_{1}.A_{k}=R_{2}.A_{k}
$$

Dove $R_{1}$ ed $R_2$ sono i nomi delle relazioni operando e $A_{1}\dots A_{k}$ sono gli attrinuti comuni, cioè con lo stesso nome, delle relazioni operando, eliminando le ripetizioni degli attributi.

Si scrive con $r_{1}\triangleright\triangleleft \ r_{2}=\pi_{XY}(\sigma_{C}(r_{1}\times r_{2}))$

![[Pasted image 20241002165744.png]]

**NOTA**:
- Nel join naturale gli attributi della condizione che consente di unire solo le ennuple giuste hanno lo stesso nome.
- Vengono unite le ennuple in cui questi attributi hanno lo stesso valore

![[Pasted image 20241002165908.png]]

Quindi il Join naturale fa tutte le operazioni che abbiamo visto prima con il prodotto cartesiano.

_Risultato Join:_

![[Pasted image 20241002170038.png]]

Spesso quando facciamo un join non vogliamo farlo su tutti gli attributi in comune ma solo su alcuni specificati, _si vede successivamente con altri tipi di join_.

Anche nel caso in cui gli attributi non hanno lo stesso nome, o come prima facciamo una ridenominazione oppure usiamo altri join, altrimenti in alcuni casi il join potrebbe restituire un prodotto cartesiano.

> [!info] Casi Limite Join Naturale
> - Attributi con lo stesso nome ma nessuna tupla della prima relazione ha valori uguali con la seconda relazione in corrispondenza degli attributi uguali, risultato vuoto.
> - Se non abbiamo attributi con lo stesso nome, il risultato diventa un prodotto cartesiano.
> 

Un possibile errore quindi può essere che gli attributi hanno lo stesso nome ma non lo stesso significato.

![[Pasted image 20241003135240.png]]

Quindi C# in _Artista_ è il codice artista mentre in _Quadro_ indica il codice quadro, il join per avere senso quindi deve essere effettuato tra Artista.C# e Quadro.Artista, **non possiamo** utilizzare un join naturale.

Possiamo o fare una ridenominazione o usare un $\theta$ join.

## $\theta$ Join
Consente di selezionare le tuple del prodotto cartesiano di due operandi che soddisfano una condizione: $A\theta B$.

Ci permette di effettuare un join sugli attributi che vogliamo noi.

Dove:
- $\theta$ è un operatore di confronto
- A è un attributo della prima relazione
- B è un attributo della seconda relazione
- $dom(A)=dom(B)$

Ad es. $r_{1}\underset{ A\theta B }{\triangleright\triangleleft} r_{2}=\sigma_{A\theta B}(r_{1}\times r_{2})$

## Condizione Negative

![[Pasted image 20241003140032.png]]

Quindi quando le informazioni che vogliamo non sono nella stessa relazione:
1) Troviamo tutte le relazioni che contengono le informazioni
2) Selezioniamo soltanto dei sottoinsiemi rilevanti per le interrogazioni
3) Combiniamo le informazioni attraverso i valori che in delle tuple fanno riferimento ad altre tuple

## Quantificatore Universale
Fino ad ora abbiamo visto query che implicano condizioni equivalenti al quantificatore esistenziale $\exists$ ovvero "esiste almeno un".

Era possibile rispondere a queste query dato che la valutazione delle tuple avviene in modo sequenziale quando si incontra una tupla che soddisfa la condizione si aggiunge al risultato.

La condizione però potrebbe richiedere la valutazione di gruppi interi di tuple prima di decidere se inserirerle o meno nel risultato, e le tuple una volta inserite non possono essere rimosse, in questo caso la query corrisponde al quantificatore universale $\forall$ oppure $\not \exists$.

_Esempio_

![[Pasted image 20241010092613.png]]

![[Pasted image 20241010092645.png]]

Notiamo che ad esempio la seconda tupla soddisfa la condizione di aver comprato più di 100 pezzi ma non possiamo inserirla, in qualche modo dovremmo memorizzare che "Rossi" compariva in una tupla precedente e non soddisfaceva la condizione.

Anche scambiando l'ordine delle tuple non risolviamo il problema, infatti lo inseriremo ma successivamente dovremmo toglierlo dal risultato.

> [!info] Negazione del quantificatore universale
> La negazione di "per ogni" **non è** "per nessuno" ma "esiste almeno un elemento per cui la condizione è falsa".

Grazie a questo possiamo risolvere il problema con una doppia negazione:
- Eseguiamo la query con la condizione negata
- In questo modo abbiamo trovato gli oggetti che almeno una volta soddisfano la condizione contraria e quindi non soddisfano sempre quella che ci interessa.
- Eliminiamo questi oggetti ottenuti dal totale tramite la **differenza**

Quindi in questo caso eseguiamo:

$$
\begin{align}
&\sigma_{N-pezzi\leq 100}(Cliente\bowtie Ordine) \\
&\text{Facciamo la proiezione sul nome e città} \\
&\pi_{Nome,Città}(\sigma_{N-pezzi\leq 100}(Cliente\bowtie Ordine)) \\
 \\
&\text{E abbiamo ottenuto chi non ci interessa} \\
 \\
&\pi_{Nome,Città}(Cliente\bowtie Ordine)-\pi_{Nome,Città}(\sigma_{N-pezzi\leq 100}(Cliente\bowtie Ordine))
\end{align}
$$

In questo modo ci sono rimasti soltanto chi **non ha mai** ordinato meno di 100.


> [!warning] Nota
> Se sappiamo di inserire un cliente nel struttura dati soltanto quando effettua un ordine allora nel primo operando della differenza potremmo scrivere semplicemente $\pi_{Nome,Città}(Cliente)$ ovvero i clienti totali.
> 
> Ma se questo non è vero allora nel risultato finale avremo anche clienti che non hanno mai effettuato ordine, per questo abbiamo effettuato un join cliente, in modo da avere soltanto chi avesse almeno un ordine.
> 
> Inoltre è importante anche valutare le proiezioni, nell'esempio precedente ci interessavano i nomi ma abbiamo proiettato anche su Città, questo perché altrimenti nella sottrazione sarebbe sparito anche il Rossi di Milano.

_Esempio_

![[Pasted image 20241010094224.png]]

Seguendo lo stesso ragionamento di prima, prendiamo prima chi non ci interessa:

$$
\pi_{Nome,Città}(\sigma_{N-pezzi>100}(Cliente\bowtie Ordine))
$$

E poi eseguiamo una differenza:

$$
\pi_{Nome,Città}(Cliente\bowtie Ordine)-\pi_{Nome,Città}(\sigma_{N-pezzi>100}(Cliente\bowtie Ordine))
$$

La query in questo caso restituisce un risultato vuoto.

## Condizioni che richiedono il prodotto di una relazione con se stessa
Ci sono anche casi in cui sono associati oggetti della stessa relazione.

_Esempio_

![[Pasted image 20241010094616.png]]

Le informazioni che ci servono sono tutte nella stessa relazione ma si trovano su tuple diverse e per poter confrontare valori, questi devono trovarsi sulla stessa tupla, come procediamo?

Creiamo una copia della relazione ed effettuiamo un prodotto in modo da combinare le informazioni di un impiegato con quelle del suo capo, quindi creiamo una relazione _ImpiegatiC_ che con un join sarà collegata ad _Impiegati_ combinando le tuple che hanno il valore _C#_ uguale a _Capo#_. Utilizziamo anche la ridenominazione per aiutarci.

$$
ImpiegatiC=p_{Nome,C\#,Dipart,Stip,Capo\#\leftarrow CNome,CC\#,Cdipart,Cstip,Ccapo\#}(Impiegati)
$$

Poi eseguiamo:

$$
\sigma_{Capo\#=CC\#}(Impiegati\times ImpiegatiC)
$$

> [!info] Ridenominazione
> Se non avessimo usato la ridenominazione il join naturale ci avrebbe fatto combinare anche ogni impiegato con se stesso, inoltre C3 non ha capo quindi non entra nel join dal lato impiegato.

A questo punto ci basta confrontare gli stipendi e infine proiettare:

$$
r=(\sigma_{Stip\geq CStip}(\sigma_{Capo\#=CC\#}(Impiegati\times ImpiegatiC)))
$$

$$
\pi_{Nome,C\#}(r)
$$

_Esempio_

Abbiamo come query: "Nomi e codici dei capi che guadagnano più di tutti i loro impiegati".

Possiamo prendere la query dell'esempio precedente che trova gli impiegati che guadagnano quanto o più del loro capo, i capi che compaiono **anche una sola volta** in questo risultato **non** ci interessano.

$$
r=(\sigma_{Stip\geq CStip}(\sigma_{Capo\#=CC\#}(Impiegati\times ImpiegatiC)))
$$

$$
\pi_{CNome,CC\#}(\sigma_{Capo\#=CC\#}(Impiegati\times ImpiegatiC))-\pi_{CNome,CC\#}(r)
$$

_Note_

![[Pasted image 20241010100522.png]]

# Progettazione basi di dati - Problemi e Vincoli

Vogliamo creare una base di dati per studenti universitari che contiene:

Dati Anagrafici e identificativa:
- Nome e cognome
- Data, comune e provincia di nascita
- matricola
- codice Fiscale

Dati curriculari, per ogni esame:
- Voto
- data
- codice, titolo e docente del corso

## Ipotesi 1

Creiamo una sola relazione con schema:

$$
\text{Curriculum(Matr,CF,Cogn,Nome,DataN,Com,Prov,C\#,Tit,Doc,DataE,Voto)}
$$

Che problemi si presentano?

![[Pasted image 20241010142811.png]]

**Ridondanza:**

I dati di uno studente vengono memorizzati ogni volta che questo sostiene un esame mentre i dati di un corso sono memorizzati per ogni esame sostenuto in quel corso, questo porta a spreco di memoria ed errori durante _aggiornamento, inserimento e cancellazione_.

**Anomalia di Aggiornamento**:

Se cambia il docente di un corso, dobbiamo cambiarlo per ogni esame sostenuto in quel corso, stessa cosa per ogni altro dato.

**Anomalia di Inserimento**:

Non posso inserire i dati di uno studente finché non ha sostenuto almeno uno esame, a meno che non inserisco molti valori NULL. Non posso comunque farlo dato che questi attributi fanno parte della chiave.

**Anomalia di Cancellazione**:

Se elimino i dati di uno studente sto cancellando anche i dati di un corso, se ad esempio lo studente è l'unico ad aver sostenuto l'esame di quel corso.

Tutti questi problemi accadono perché ho messo insieme 3 informazioni di oggetti diversi, _corsi, esami e studenti_.

## Ipotesi 2

Possiamo passare quindi a tre schemi di relazione:

- $\text{Studente(Matr,CF,Cogn,Nome,Data,Com,Prov)}$
- $\text{Corso(C\#,Tit,Doc)}$
- $\text{Esame(Matr,C\#,Data,Voto)}$

![[Pasted image 20241010144018.png]] 

Non abbiamo i problemi di prima però se ne presenta un atro con Comune e Provincia dato che il Comune determina la Provincia

**Ridondanza**:

Il fatto che un comune si trova in una provincia è ripetuto molte volte

**Anomalia di aggiornamento**:

Se un comune cambia provincia devono essere modificate più tuple

**Anomalia di Inserimento**:

Non è possibile memorizzare il fatto che un comune si trova in una provincia se non abbiamo almeno uno studente di quel comune

**Anomalia di Cancellazione**:

Cancellando studenti potremmo perdere informazioni relative ai comuni

La base di dati adesso è formata da:

- $\text{Studente(Matr,CF,Cogn,Nome,Data,Com)}$
- $\text{Corso(C\#,Tit,Doc)}$
- $\text{Esame(Matr,C\#,Data,Voto)}$
- $\text{Comune(Com, Prov)}$

In questo modo non abbiamo più ridondanze e anomalie

![[Pasted image 20241010144510.png]]

> [!info] Schema "buono"
> Uno schema è buono se non presenta ridondanza e anomalie di aggiornamento, inserimento e cancellazione, come si progetta?
> **Occorre rappresentare ogni concetto in una relazione distinta**

> [!warning] Rappresentazione dei concetti
> Tutti i problemi di prima derivano dal fatto che abbiamo rappresentanto in un'unica relazione tre concetti diversi, 4 considerando anche i comuni e le province.

## Vincoli
I vincoli sono delle condizioni sulla realtà che stiamo progettando, ad esempio:
- Un voto va da 18 a 30
- La matricola deve essere univoca
- ecc..

Quando rappresentiamo una realtà deve essere possibili rappresentare anche tutti i suoi vincoli, un'istanza **è legale** se soddisfa tutti i vincoli imposti. Più avanti vedremo che per questa definizione ci interessano soltanto le **dipendenze funzionali** e non ad esempio i vincoli di dominio.

Un _DBMS_ permette di:
- Definire insieme allo schema della base anche i suoi vincoli
- Verificare che un'istanza sia legale
- Impedire l'inserimento di tuple che violerebbero tali vincoli

Le **dipendenze funzionali** di uno schema esprimono dei vincoli di dipendenza tra sottoinsiemi di attributi dello schema stesso, questi devono essere soddisfatti da ogni istanza dello schema. Se io ad esempio ho _Matricola e CF_ nel caso di matricola uguale dovrà essere uguale anche CF.

# Dipendenze Funzionali

## Schema di relazione
Uno schema di relazione $R$ è un insieme di attributi $\{ A_{1},\dots,A_{n} \}$

Notazione:
- $R=A_{1},\dots,A_{n}$
- Le prime lettere dell'alfabeto denotano singoli attributi
- Le ultime lettere denotano insiemi di attributi
- Se $X$ ed $Y$ sono insiemi di attributi $XY$ denota $X\cup Y$

## Tupla
Dato uno schema di relazione $R$ una tupla $t$ su $R$ è una funzione che associa ad ogni attributo $A$ in $R$ un valore $t[A_{i}]$ nel corrispondente $dom(A_{i})$.

Se $X$ è un sottoinsieme di $R$ e $t_{1},t_{2}$ sono due tuple su $R$, $t_{1}\ e \ t_{2}$  coincidono su $X$ se $\forall A\in X(t_{1}[A]=t_{2}[A])$.

## Istanza di Relazione
Dato uno schema di relazione $R$ una istanza di $R$ è un insieme di tuple su $R$

---

**Dipendenze Funzionali**

Dato uno schema di relazione $R$, una dipendenza funzionale su $R$ è una coppia ordinata di sottoinsiemi non vuoti $X,Y$ di $R$.

Notazione:

- $X\rightarrow Y$
- $X$ **determina funzionalmente** $Y$ oppure $Y$ **dipende funzionalmente da** $X$
- $X$ = **Determinante**
- $Y$ = **Dipendente**

Dati uno schema $R$ e una dipendenza funzionale $X\rightarrow Y$ su $R$, un'istanza $r$ di $R$ soddisfa la dipendenza funzionale $X\rightarrow Y$ se:

$$
\forall t_{1},t_{2}\in r(t_{1}[X]=t_{2}[X]\Rightarrow t_{1}[Y]=t_{2}[Y])
$$

Se $t_{1}[X]\neq t_{2}[X]$ allora la dipendenza è comunque **soddisfatta** qualsiasi siano i valori di $t_{1}[Y],t_{2}[Y]$.

Quindi notiamo che il minimo numero per violare una dipendenza è 2, infatti istanze da 1 o 0 elementi è **impossibile che violino una qualsiasi dipendenza**.

**Istanza Legale**

Dati uno schema di relazione $R$ e un insieme $F$ di dipendenze funzionali, un'istanza di $R$ è legale se soddisfa tutte le dipendenze in $F$.

![[Pasted image 20241010155443.png]]

_Osservazione_

![[Pasted image 20241010155527.png]]

Notiamo che ogni istanza legale che quindi soddisfa $A\rightarrow B,B\rightarrow C$ soddisfa sempre anche la dipendenza $A\rightarrow C$, possiamo quindi considerarla come se fosse in $F$?

Dato uno schema di relazione $R$ e un insieme $F$ di dipendenza funzionali su $R$ ci sono delle dipendenze funzionali che non sono in $F$ ma che sono comunque soddisfatte da tutte le istanze legali di $R$.

## Chiusura di un insieme di Dipendenze Funzionali
Dato uno schema di relazione $R$ e un insieme $F$ di dipendenze funzionali su $R$ la **chiusura di $F$** è l'insieme delle dipendenze funzionali che sono soddisfatte da ogni istanza legale di $R$.

Lo scriviamo $F^+$.

Otteniamo quindi che $F\subseteq F^+$.

## Chiave
Dati uno schema di relazione $R$ e un insieme di dipendenze funzionali $F$, un sottoinsieme $K$ di uno schema di relazione $R$ è una **chiave** se:
- $K\rightarrow R\in F^+$
- Non esiste un sottoinsieme proprio $K'$ di $K$ tale che $K'\rightarrow R\in F^+$

Se rispettiamo soltanto la prima condizione allora $K$ è detta **superchiave**. Se soddisfa la seconda e quindi non ha altri sottoinsiemi che soddisfano la prima condizione allora è detta **chiave**. Possiamo anche diri quindi che una chiave è sempre superchiave dato che contiene se stessa ma una superchiave non è detto che sia sempre chiave, ma ne contiene sempre una.

$K\rightarrow R$ significa che se due tuple sono uguali su $K$ allora le tuple devono essere uguali e dato che non possiamo avere due tuple uguali significa che non possiamo avere due chiavi uguali.

_Esempio_

Consideriamo lo schema $\text{Studente = (Matr, Cognome, Nome, Data)}$. Il numero di matricola viene assegnato allo studente per identificarlo e quindi non ci possono essere 2 studenti con la stessa matricola e un'istanza di Studente non può contenere due tuple con lo stesso numero di matricola.

Otteniamo quindi che $\text{Matr}\rightarrow \text{Matr, Cognome, Nome, Data}$ deve essere soddisfatta da ogni istanza legale. **Matr è chiave per lo schema Studente**.

### Chiave Primaria
Dati uno schema $R$ e un insieme $F$ di dipendenze funzionali, possono esistere più chiavi, in SQL una di esse verrà scelta come **chiave primaria** (non può avere valore nullo).

Di solito si sceglie quella con meno attributi (**non minimale, minimale significa che non ha altri sottoinsiemi chiave, superchiave**) questo perché migliora la velocità di ricerca nella base di dati. Quindi una volta scelta chiave primaria le altre chiavi devo impostarle come attributi **unique** per rispettare il fatto che non si deve ripetere.

## Dipendenze Funzionali Banali
Dati uno schema di relazione $R$ e due sottoinsiemi non vuoti $X,Y$ di $R$ tali che $Y\subseteq X$ si ha che ogni istanza $r$ di $R$ soddisfa la dipendenza funzionali $X\rightarrow Y$.

Queste dipendenze sono soddisfatte da ogni tupla anche da quelle non legali.

Quindi ad esempio se io ho due tuple uguali su $X=ABC$ allora saranno uguali anche su $Y=AB$ e quindi $X\rightarrow Y$ è soddisfatta.

Quindi se $Y\subseteq X$, $X\rightarrow Y\in F^+$, questa è detta **dipendenza banale**.

### Proprietà delle dipendenze funzionali
Dati uno schema di relazione $R$ e un insieme di dipendenze funzionali $F$ si ha:

$$
X\rightarrow Y\in F^+ \Leftrightarrow \forall A\in Y(X\rightarrow A\in F^+)
$$

Quindi se $A\rightarrow BC\in F^+$ allora anche $A\rightarrow B\in F^+$ e $A\rightarrow C\in F^+$.

---

Per la terza forma normale l'insieme $F^+$ è molto importante, è l'insieme di tutte le dipendenze soddisfatte da tutte le istanze legali. Ma come si calcola questo insieme $F^+$?

---

Dato che calcolare $F^+$ è molto "pesante" ci limiteremo a capire se una dipendenza ne fa parte o meno.

## Assiomi di Armstrong

Introduciamo $F^A$, con gli **Assiomi di Armstrong**

Denotiamo $F^A$ come l'insieme di dipendenze funzionali definito:
- Se $f\in F$ allora $f\in F^A$
- Se $Y\subseteq X\subseteq R$ allora $X\rightarrow Y\in F^A$ **Assioma della Riflessività**
- Se $X\rightarrow Y\in F^A$ allora $XZ\rightarrow YZ\in F^A$, per ogni $Z\subseteq R$, **Assioma dell'aumento**
- Se $X\rightarrow Y\in F^A$ e $Y\rightarrow Z\in F^A$ allora $X\rightarrow Z\in F^A$, **Assioma della transitività**

Dimostreremo che $F^+=F^A$, ma prima alcune osservazioni su questi assiomi:

**Riflessività**:  Se $Y\subseteq X\subseteq R$ allora $X\rightarrow Y\in F^A$

Ad esempio $\text{Nome} \subseteq (\text{Nome, Cognome})$ e quindi se due tuple hanno uguale la coppia (Nome, Cognome) allora avranno uguale l'attributo Nome e stesso ragionamento per Cognome. Questo significa che $\text{(Nome,Cognome)}\rightarrow\text{Nome (o Cognome)}$ è sempre soddisfatta.

**Aumento**:  Se $X\rightarrow Y\in F^A$ allora $XZ\rightarrow YZ\in F^A$, per ogni $Z\subseteq R$

Ad esempio $\text{CodiceFiscale}\rightarrow\text{Cognome}$ è soddisfatta quando tutte le tuple che hanno lo stesso CodiceFiscale hanno anche lo stesso Cognome.

Se aggiungiamo un altro attributo Indirizzo avremo che se due tuple sono uguali su (CodFiscale, Indirizzo) lo saranno anche su (Cognome, Indirizzo), quindi se viene soddisfatta $\text{CodFiscale}\rightarrow\text{Cognome}$ viene soddisfatta anche $\text{CodFiscale,Indirizzo}\rightarrow\text{Cognome,Indirizzo}$.

**Transitività**: Se $X\rightarrow Y\in F^A$ e $Y\rightarrow Z\in F^A$ allora $X\rightarrow Z\in F^A$

Ad esempio $\text{Matricola}\rightarrow\text{CodFiscale}$ è soddisfatta quando tutte le tuple con la stessa Matricola hanno anche lo stesso CodFiscale.

$\text{CodFiscale}\rightarrow\text{Cognome}$ è soddisfatta quando tutte le tuple con stesso CodFiscale hanno anche lo stesso Cognome.

Se entrambe le dipendenze sono soddisfatte quindi possiamo dire che ogni volta che le tuple hanno la stessa Matricola avranno hanno lo stesso Cognome, è soddisfatta quindi anche la dipendenza $\text{Matricola}\rightarrow\text{Cognome}$.

_Vediamo altre regole che ci permettono di derivare altre dipendenze in $F^A$_:

1) Se $X\rightarrow Y\in F^A$ e $X\rightarrow Z\in F^A$ allora $X\rightarrow YZ\in F^A$, **Regola dell'unione**
2) Se $X\rightarrow Y\in F^A$ e $Z\subseteq Y$ allora $X\rightarrow Z\in F^A$, **Regola della decomposizione**
3) Se $X\rightarrow Y\in F^A$ e $WY\rightarrow Z\in F^A$ allora $WX\rightarrow Z\in F^A$, **Regola della pseudotransitività**

**Teorema**: Sia $F$ un insieme di dipendenze funzionali dove valgono le implicazioni viste sopra.

**Dimostrazione 1)** 

Se $X\rightarrow Y\in F^A$ per l'assioma dell'aumento si ha $X\rightarrow XY\in F^A$ (aggiungiamo X da entrambe le parti quindi XX=X). Analogamente $X\rightarrow Z\in F^A$ diventa $XY\rightarrow YZ\in F^A$  e quindi per transitività si ha che $X\rightarrow YZ\in F^A$.

**Dimostrazione 2)**

Se $Z\subseteq Y$ allora per riflessività si ha $Y\rightarrow Z\in F^A$. Quindi poiché $X\rightarrow Y\in F^A$ e $Y\rightarrow Z\in F^A$ per transitività $X\rightarrow Z\in F^A$

**Dimostrazione 3)**

Se $X\rightarrow Y\in F^A$ per aumento si ha $WX\rightarrow WY\in F^A$, quindi dato che $WX\rightarrow WY\in F^A$ e $WY\rightarrow Z\in F^A$ allora per transitività abbiamo $WX\rightarrow Z\in F^A$.


> [!info] Osservazione
> Da riscrivere
> ![[Pasted image 20241017132946.png]]

## Chiusura di un insieme di attributi
Siano $R$ uno schema di relazione, $F$ un insieme di dipendenze funzionali su $R$ e $X$ un sottoinsieme di $R$.

La chiusura di $X$ rispetto ad $F$ denotata con $X^+_{F}$ o anche $X^+$ è definito da:

$$
X^+_{F}=\{ A|X\rightarrow A\in F^A \}
$$

Fanno parte della chiusura, gli attributi che vengono determinati direttamente da $X$ (da dipendenze che sono in $F$), oppure indirettamente (da dipendenze che sono in $F^A$). Quindi otteniamo che:

$$
X\subseteq X^+_{F} \text{ Riflessività}
$$

Quindi in ogni istanza legale se due tuple sono uguali su $X$ allora sono uguali su tutti gli attributi della chiusura di $X$, ovviamente se $F^A=F^+$.


> [!info] Chiusure
> La chiusura di $F$ non è mai vuota dato che abbiamo sempre almeno le dipendenze banali stessa cosa per la chiusura di $X$, infatti $X$ determina sicuramente se stesso.

**Lemma**:

Siano $R$ uno schema di relazione ed $F$ un insieme di dipendenze funzionali su $R$ si ha che: $X\rightarrow Y\in F^A$ se e solo se $Y\subseteq X^+$

_Dimostrazione_

Sia $Y=A_{1},A_{2},\dots,A_{n}$

**PARTE SE**:

Poiché $Y\subseteq X^+$ per ogni $i, i=1,\dots,n$ si ha che $X\rightarrow A_{i}\in F^A$, pertanto per la **regola dell'unione** $X\rightarrow Y\in F^A$

**PARTE SE E SOLO SE**

Poiché $X\rightarrow Y\in F^A$ per la regola **della decomposizione** si ha che per ogni $i,i=1,\dots,n,X\rightarrow A_{i}\in F^A$ cioè $A_{i}\in X^+$ per ogni $i,i=1,\dots,n$ e quindi $Y\subseteq X^+$.

---

**Teorema** $F^+=F^A$

Siano $R$ uno schema di relazione ed $F$ un insieme di dipendenze funzionali su $R$ si ha $F^+=F^A$.

_Dimostrazione_, dobbiamo dimostrare che $F^A\subseteq F^+\wedge F^+\subseteq F^A$.

Iniziamo dimostrando $F^A\subseteq F^+$, Sia $X\rightarrow Y$ una dipendenza funzionale in $F^A$, dimostriamo che $X\rightarrow Y\in F^+$ per induzione sul numero $i$ di applicazioni degli assiomi di Armstrong.

Base dell'induzione: $i=0$, in questo caso $X\rightarrow Y$ è in $F$ e quindi $X\rightarrow Y\in F^+$, questo perché appunto non abbiamo applicato nessun assioma e $F\subseteq F^+$.
Inoltre questo significa che $X\rightarrow Y\in F^+$ significa che è rispettata da ogni istanza legale.

Ipotesi Induttiva: $i>0$, Prendiamo $i-1$ applicazioni e per ipotesi induttiva abbiamo $X\rightarrow Y\in F^A\Rightarrow X\rightarrow Y\in F^A$

Passo Induttivo: Ci troviamo a $i-1$ e per ipotesi ogni dipendenza ottenuta da $F$ applicando gli assiomi fino a $i-1$ si trova in $F^+$ dobbiamo dimostrarlo anche per $i$ e si possono presentare 3 casi, ovvero l'applicazioni di ognuno dei 3 assiomi:

1) Riflessività
   
   All'i-esimo passo decidiamo di applicare la riflessività, quindi se $X\rightarrow Y$ è stata ottenuta per riflessività allora implica che $Y\subseteq X$.
   
   $$
   \forall r(legale) \text{ se } t_1[X]=t_{2}[X]\Rightarrow t_{1}[Y] \ (Y\subseteq X)=t_{2}[Y]\Rightarrow X\rightarrow Y\in F^+
   $$

2) Aumento
   
   Se  $X\rightarrow Y$ è stata ottenuta per aumento, quindi in $i-1$ passi avevamo $V\to W\in F^+,F^A$ al quale possiamo applicare l'aumento con $Z$ ottenendo $VZ\to WZ\in F^A$ e possiamo chiamare $VZ=X$ e $WZ=Y$.
   
   $$
   \begin{align}
   &\forall r(legale) \ t_{1}[X]=t_{2}[X]\Rightarrow t_{1}[VZ]=t_{2}[VZ]\Rightarrow t_{1}[V]=t_{2}[V]\wedge t_{1}[Z]=t_{2}[Z] \\
   &\text{Per ipotesi so che } V\to W\in F^+ \text{ e quindi } t_{1}[V]=t_{2}[V]\Rightarrow t_{1}[W]=t_{2}[W] \\
   &t_{1}[W]=t_{2}[W]\wedge t_{1}[Z]=t_{2}[Z]\Rightarrow t_{1}[WZ]=t_{2}[WZ]\Rightarrow t_{1}[Y]=t_{2}[Y]
   \end{align}
   $$
   
   Essendo quindi soddisfatta da ogni istanza legale abbiamo che la nuova dipendenza è in $F^+$.


3) Transitività
   
   $X\to Y\in F^A$ è stata ottenuta per transitività quindi a $i-1$ $X\to Z\in F^A\Rightarrow Z\to Y\in F^A$. E per ipotesi induttiva si trovano in $F^+$ quindi:
   
   $$
   \forall r(legale) \ t_{1}[X]=t_{2}[X]\Rightarrow t_{1}[Z]=t_{2}[Z]\Rightarrow t_{1}[Y]=t_{2}[Y]
   $$

Quindi qualunque sia il numero di applicazioni di Armstrong, ogni dipendenza di $F^A$ si troverà anche in $F^+$.

---

Adesso dobbiamo dimostrare che se una dipendenza si trova in $F^+$ allora si trova in $F^A$. $F^+\subseteq F^A$ ovvero:

$$
X\to Y\in F^+\Rightarrow X\to Y\in F^A
$$

![[Pasted image 20241017152218.png]]

Prendiamo una qualunque dipendenza $V\to W\in F$ e mostriamo per prima cosa che $r$ è un'istanza legale perché la soddisfa:

Se $t_{1}[V]\neq t_{2}[V]$ ovvero se $V\cap R-X^+\neq \emptyset$ allora è soddisfatta.

Se $t_{1}[V]=t_{2}[V]\Rightarrow V\subseteq X^+$ (sappiamo che sono uguali sicuramente solo in $X^+$).
Per il **lemma 1** sappiamo che $V\subseteq X^+\Rightarrow X\to V\in F^A$ e per transitività insieme a $V\to W\in F\Rightarrow X\to W\in F^A\underbrace{ \Rightarrow W\subseteq X^+ }_{ \text{Lemma 1} }\Rightarrow t_{1}[W]=t_{2}[W]$. Quindi le due tuple sono uguali sia sui valori di $V$ che su quelli di $W$. L'istanza è legale.

Adesso mostriamo che se $X\to Y\in F^+$ allora $X\to Y\in F^A$.

Dato che è un'istanza legale significa che $X\to Y\in F^+$, quindi se $t_{1}[X]=t_{2}[X]\Rightarrow t_{1}[Y]=t_{2}[Y]$, noi sappiamo che le tuple sono uguali per gli attributi di $X^+$ e per riflessività $X\subseteq X^+$, quindi le tuple sono sicuramente uguali sui valori di $X$ e quindi l'implicazione ci dice che lo sono anche sui valori di $Y$.

Se sono uguali sui valori di $Y$ significa che anche $Y\subseteq X^+$ e per il **lemma** che $X\to Y\in F^A$.
