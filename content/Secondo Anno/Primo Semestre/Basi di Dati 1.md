
# DA SISTEMARE

scelgo il dominio per ogni attributo, imposto un valore per ogni attributo, ottengo delle tuple e un insieme di tuple è un'istanza.

Una tupla si ottiene quindi fornendo un valore ad ognuno dei domini scelti per gli attributi.
Il grado è il numero di attributi, la cardinalità il numero di tuple.
Le tuple devono essere tutte distinte, non ci sono duplicati.

Se in due taballe, una contiene un elemento univoco di un'altra questa si chiama slave e l'altra master.
Esempio una tabella studente ha come chiave la matricola e la tabella esame ha ogni esame svolto con il voto e la matricola dello studente.
Quindi studente e il master ed esami lo slave.
il master deve esistere prima dello slave, altrimenti la tabella slave non si potrebbe creare.

Se vogliamo inserire dei valori null è meglio stabilire un default, le chiavi non possono essere null. (Questo perché tutti i valori null sono diversi da altri null).

Le chiavi si identificano tramite le dipendenze funzionali.
Non devono essere obbligatoriamente composte da un solo attributo.

Un insieme si dice superchiave se contiene una chiave, una chiave è quindi superchiave dato che contiene se stessa.
La chiave primaria è la chiave che identifica univocamente un campo.
Ad esempio c.f. e data di nascita è una superchiave ma la chiave primaria è c.f.
Possiamo definirla tale se questa non contiene un altro sottoinsieme considerabile chiave.

Istanza legale: soddisfa tutte le dipendenze funzionali

Dipendenza funzionale: stabilisce un legame tra due insiemi di attributi X Y appartenenti ad uno schema, X -> Y, x determina Y.
Ad esempio in una macchina il modello determina la marca.
X = determinante, Y = Dipendente

Convenzione: Con le prime lettere (A, B, C) si indicano attributi mentre con le ulti,e (X, Y, Z) indichiamo insiemi di attributi.

**Una relazione r con schema R soddisfa la dipendenza funzionale X->Y se:**
...
se ad esempio codiceVolo determina ora e ho due tuple uguali sul codicevolo allora devono avera uguale anche l'ora.
Infatti le chiavi non possono violare le dipendenze dato che non posso avere tuple uguali sull'attributo chiave.

**Algebra Relazionale**


