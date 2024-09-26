# Combinatoria


> [!info] Principio Fondamentale della Combinatoria
> Supponiamo di avere 2 esperimenti, il primo ha _n1_ esiti possibili mentre il secondo, **indipendentemente dall'esito del primo** ha _n2_ esiti possibili.
> Allora il numero delle coppie $(a_1,a_2)$ possibili con $a_i$ esito dell'esperimento i-esimo è $n_{1}\cdot n_2$.

_Esempio_
Se lanciamo un dado 2 volte, la prima volta abbiamo 6 esiti possibili mentre al secondo lancio abbiamo comunque 6 esiti possibili, indipendentemente dal risultato del primo.

Quindi in totale $6 \cdot 6 = 36$ esiti.

$$
\#\{(a,b): a = \text{faccia al primo lancio}, b = \text{faccia al secondo lancio}\}
$$

> [!info] Notazione \#
> Il simbolo \# davanti ad un insieme indica la sua cardinalità


_Esempio_
Se abbiamo 140 studenti, in quanti modi possiamo scegliere un rappresentante e un suo vice?
Per scegliere il rappresentante abbiamo 140 modi, per il suo vice abbiamo uno studente in meno quindi 139, in totale quindi $140\cdot 139$ esiti.


> [!info] Principio Fondamentale della Combinatoria (Generale)
> Supponiamo di avere _R_ esperimenti.
> Il primo ha $n_1$ esiti possibili e qualunque sia il suo risultato il secondo avrà sempre $n_2$ esiti.
> Qualunque sia la realizzazione del secondo il terzo avrà sempre $n_3$ esiti possibili e così via.
> Allora il numero delle possibili stringhe $(a_1,a_2,\dots,a_R)$ dove $a_i$ è l'esito dell'esperimento i-esimo è $n_{1}\cdot n_{2} \cdot ... \cdot n_{R}$.

_Esempio_
Abbiamo 120 ragazzi e 20 ragazze, dobbiamo scegliere un rappresentante e un suo vice in modo che siano di sesso diverso.

Nel primo caso abbiamo 140 esiti possibili, ma nel secondo dipende dall'esito del primo, infatti se abbiamo un rappresentante maschio otteniamo $140 \cdot 20$ esiti, mentre se il rappresentante è femmina allora il secondo esperimento ha 120 esiti e quindi $140 \cdot 120$.

**È caduta l'ipotesi, possiamo però dividere il problema in più sottoproblemi**.

Infatti la soluzione che cerchiamo è l'unione di due soluzioni:

$\{(a,b): \text{a rappresentante M., b vice F.}\} \cup \{(a,b): \text{a rappr. F., b vice M}\}$

Il primo ha $120\cdot 20$ esiti mentre il secondo $20 \cdot 120$, quindi in totale abbiamo $120\cdot 20 + 20 \cdot 120$ esiti.

_Esempio_
$\#\{\text{Strighe binarie di lunghezza 5}\}$.

Ad ogni "entrata" ovvero ad ogni carattere della stringa ho sempre 2 possibili input, quindi $2\cdot2\cdot2\cdot2\cdot2 = 2 ^5$.

_Esempio_
Ho un insieme A di _n_ elementi distinti, quanti sono i suoi sottoinsiemi?

Possiamo utilizzare la stessa formula di prima, quindi $2^n$, questo perché è possibile applicare una **bigezione** (una funzione biettiva, ha lo stesso funzionamento di una mappa, è come convertire un elemento in un altro) per indicare ogni sottoinsieme con una stringa binaria.

$$
\begin{align*}
&A = \{a_1,a_2,...,a_{n}\} \\
&B = \{a_1,a_2,a_{4}\}, B\subset A \\
&\text{Indico B come una stringa, se l'elemento è presente 1, 0 altrimenti}\\
&B = (1,1,0,1,...)
\end{align*}
$$

Quindi la nostra bigezione funziona in modo che $a_{i}\in B \leftrightarrow x_{i} = 1$.

_Esempio_
Dobbiamo ordinare:
- 4 libri di matematica
- 3 di chimica
- 2 romanzi

1) In quanti modi possiamo ordinarli sullo scaffale?
   
   Usando il principio fondamentale otteniamo $9!$ esiti possibili.

2) In quanti modi possiamo ordinarli sullo scaffale, mantenendo vicini quelli della stessa categoria?
   
   In questo caso non possiamo utilizzare subito il principio fondamentale, perché una volta messo un libro non conosciamo la sua tipologia e ad un certo punto non sapremo come continuare.
   
   Possiamo però dividere in più sottoproblemi questo caso, prima **ordiniamo le categorie**.
   
   Abbiamo 3 categorie, quindi per ordinarle $3!$ modi possibili, teniamo questo numero da parte.
   
   Poi per ogni categoria vediamo quanti modi abbiamo per ordinarla, quindi matematica $4!$, chimica $3!$ e i romanzi $2!$, mettendo tutto insieme otteniamo $3!\cdot4!\cdot3!\cdot2!$ esiti possibili.


> [!info] Definizione Permutazioni
> Dati $n$ oggetti distinti, le loro permutazioni sono tutti i loro possibili ordinamenti (allineamenti), il numero di questi è $n!$.

> [!info] Dimostrazione
> Per ordinare gli $n$ oggetti scelgo il primo, per fare questo ho $n$ modi, per il secondo ho $n-1$ modi, per il terzo $n-2$ e così via fino a quando non arrivo all'ultimo oggetto che avrà un solo modo per essere ordinato.
> 
> $$
> n! := \left\{\begin{align*}
>&1 \text{ se } n=0 \\
>&1*2*3*\cdots*n \text{ se } n =1,2,3,...\end{align*} \right\}
>$$
>

_Esempio_
Anagrammi, anche senza senso, della parola "Mela".

Come prima dobbiamo trovare le permutazioni di 4 elementi distinti, quindi $4!$.

Se dovessimo trovare gli anagrammi di "Emma"? In questo caso abbiamo due elementi uguali, come si procede?

Proviamo a diversificare le M e ottenere $M_1,M_2$, in questo modo otteniamo $4!$ anagrammi, ma se riportiamo le M come prima avremo delle ripetizioni, ad esempio $EM_1M_2A$ e $EM_2M_1A$.

Quindi avendo 2 elementi uguali, per ogni permutazione otteniamo una sua copia, quindi per toglierle tutte dobbiamo calcolare $\frac{4!}{2!}$ dove $4$ indica il numero di elementi e $2$ quello di elementi uguali.


> [!info] Regola Generale per Permutazioni con elementi uguali
> Dati $n$ elementi con $r$ elementi distinti:
> - 1° elemento appare $n_1$ volte
> - 2° elemento appare $n_2$ volte
> - ...
> - R-esimo elemento appare $n_R$ volte
>   
>   $\#\text{permutazioni}\{\frac{n!}{n_1!,n_2!,...,n_R!}\}$
>   
>   _Esempio con Emma_
>   $\frac{4!}{1!*2!*1!}$ Dato che E=1, M=2, A=1.

_Esempio_
Numero di possibili targhe alfanumeriche di lunghezza 5.
Abbiamo 26 lettere e 10 cifre, quindi per ogni entrate 36 input possibili, dato che sono 5 otteniamo $36^5$.

$\#\{\text{Numero di targhe alfanumeriche con simboli distinti di lunghezza 5}\}$ = $36*35*34*33*32$, in questo caso abbiamo usato il principio fondamentale.

$\#\{\text{Targhe di lunghezza 5 con 3 lettere 2 cifre}\}$
Prima scegliamo come posizionare 3 lettere in 5 posti, questo è dato da $\frac{5!}{3!\cdot2!}$, poi le lettere sono 26 quindi in 3 posizioni abbiamo $26^3$ esiti, mentre per le cifre $10^2$, mettendo tutto insieme otteniamo:

$$
\frac{5!}{3!\cdot2!}\cdot26^3\cdot10^2
$$

_Esempio_
Nella finale di 100m, calcolare le possibili classifiche delle nazioni se non ci sono parimerito, con nazione A=3, B=2, C=1, D=2, E=1, F=1

Utilizziamo la formula per il numero di permutazioni con ripetizioni, quindi con 10 partecipanti abbiamo:

$$
\frac{10!}{3!\cdot2!\cdot2!}
$$

_Esempio_
Riprendiamo un esempio visto prima ma facciamo un'osservazione, scegliamo due rappresentanti in 140 studenti.

$$
\#\{(a,b):a\neq b \text{ studenti}\} = 140\cdot 139
$$

Se utilizziamo le () significa che conta l'ordine, quindi ad esempio la coppia ("Lorenzo", "Cristina") è diversa da ("Cristina", "Lorenzo") ma noi sappiamo che in realtà sono uguali, quindi in questo caso non ci interessa l'ordine, in questo caso per togliere i doppioni ci basta dividere per due.

**Generalizzazione**
Ho un insieme di $n$ elementi distinti, in quanti modi posso scegliere $k$ elementi distinti e non conta l'ordine?

$$
\frac{n(n-1)(n-2)\cdots(n-k+1)}{k!}=\binom{n}{k}
$$

Se invece l'ordine conta utilizziamo il principio fondamentale e quindi non dobbiamo dividere per $k!$. Nella formula vista sopra abbiamo ottenuto il **coefficiente binomiale**.

> [!info] Coefficiente Binomiale
> Dati $0\leq k \leq n$ interi:
> 
> $$
> \binom{n}{n} = \frac{n!}{k!\cdot(n-k)!}
> $$
> 

Questo ha varie proprietà:

- Se $n=0$ allora anche $k=0$ e $\binom{0}{0}=\frac{0!}{0!*0!} = 1$
- $\forall n$ se $k=0$ ottengo $\binom{n}{0}=\frac{n!}{0!*(n-0)!}=1$
- $\binom{n}{k} = \binom{n}{n-k}$

**Triangolo di Tartaglia per i Coefficienti Binomiali**

![[Pasted image 20240925104452.png]]

_Esempio_
Ho 10 studenti, in quanti modi ne posso scegliere 3 se conta l'ordine? E se non conta?

Se conta l'ordine facciamo $10\cdot 9 \cdot 8$, se invece l'ordine non conta utilizziamo il C.B. quindi:

$$
\binom{10}{3}=\frac{10!}{3!\cdot 7!}
$$

_Esempio_
Ho 10 informatici, 5 segretari e 20 operai, devo scegliere un gruppo di rappresentanti composto da 3 inf. 2 seg. e 6 op., in quanti modi posso farlo?

$$
\frac{10!}{3!\cdot 7!}\cdot \frac{5!}{2!\cdot 3!}\cdot \frac{20!}{6!\cdot 14!}
$$

_Esempio_
In un gruppo da 10 amici devo formare 2 squadre, devo assegnare 5 maglie rosse e 5 maglie blu, in quanti modi posso farlo?

$$
\binom{10}{5}=\frac{10!}{5!\cdot 5!}
$$

Infatti le combinazione per assegnare una maglietta sono uguali per entrambe le squadre.

_Esempio_
Cambiando l'esempio di prima, se voglio formare due squadre scegliendo mano mano ogni membro, in quanti modi posso farlo?

$$
\binom{10}{5} \cdot \frac{1}{2}
$$

Vediamo due esempi utili per capire come si svolge.

_Esempio 1_
Ho 6 studenti e devo dividerli in 2 gruppi, uno da 4 e uno da 2.
In questo caso mi basta calcolare i modi di un gruppo, quindi:

$$
\binom{6}{4} \ \ oppure \ \ \binom{6}{2}
$$

Infatti una volta scelto un gruppo l'altro è già formato.
La situazione cambia se i due gruppi hanno la stessa dimensione.

_Esempio 2_
Dividiamo in 2 gruppi da 3 persone.
Se ne scelgo solo 3 per un gruppo, avrò delle ripetizioni, infatti se ad esempio ho come persone A,B,C,D,E,F e scelgo nel primo {A, B, C} nel secondo avrò {D, E, F} ma se come primo gruppo scelgo {D, E, F} come secondo ottengo {A, B, C}, ho ottenuto una ripetizione.

Per eliminarle:

$$
\binom{6}{3}\cdot\frac{1}{2}
$$

_Esempio_
5 studenti vogliono organizzare una festa e si dividono i ruoli:
- C1) Pulire il locale - 2 persone
- C2) Comprare bibite - 2 persone
- C3) Pubblicizzare la festa - 1 persona

Per risolvere scelgo gli studenti per C1, dai rimanenti per C2 e dai rimanenti per C3:

$$
\binom{5}{2}\cdot \binom{3}{2} \cdot \binom{1}{1}
$$


> [!info] Osservazione
> Svolgendo i calcoli dei coefficienti binomiali visti prima otteniamo:
> $$
> \frac{5!}{2!\cdot 2! \cdot 1!}
> $$
 Che è la stessa formula che utilizziamo per gli anagrammi, infatti possiamo assegnare ad ogni posizione uno studente e ad ogni studente il numero dell'incarico, in questo modo dobbiamo soltanto calcolare gli anagrammi della stringa "13221" (qualsiasi altra combinazione va bene).

**Generalizzazione**
Se abbiamo $n$ oggetti distinti che vogliamo ripartire in $r$ scatole $s_1,s_2,...,s_r$ in modo che $\forall i$ che vanno da $1$ a $r$ nella scatola $s_i$ inserisco l'oggetto $n_i$ dove:

$$
n_1+n_2+...+n_r=n
$$

Quante sono le ripartizioni possibili?

$$
\frac{n!}{n_{1}!\cdot n_{2}! \cdot ... \cdot n_{r}!} =: \binom{n}{n_1,n_2,...,n_r}
$$

E prende il nome di **Coefficiente Multinomiale**.
Quindi se prendiamo l'esempio di prima rappresentando il gruppo che svolge $c_i$ otteniamo $n_{1}=2, n_{2}=2, n_{3}=1, R=3$.

Perché si calcola in questo modo?
**Applichiamo il principio fondamentale della combinatoria**:

1) Scelgo $n_1$ oggetti distinti da mettere in $s_1$.
   Ho $\binom{n}{n_1}$ modi

2) Ne scelgo $n_2$ da mettere in $s_2$ dai rimanenti.
   Ho $\binom{n - n_1}{n_2}$ modi

3) Per $n_3$ ottengo $\binom{n-n_1-n_2}{n_3}$ modi

Quindi le ripartizioni totali sono:

![[Pasted image 20240925224536.png]]

# Probabilità
Consideriamo un esperimento (fenomeno con vari esiti) e chiamiamo **spazio campionario (S)** l'insieme dei possibili esiti dell'esperimento.

_Esperimento 1_
Lancio di un dado $S=\{1,2,3,4,5,6\}$.

_Esperimento 2_
Lancio 2 volte una moneta $S=\{(T,T), (T,C), (C,C), (C,T)\}$.

Un evento è descritto matematicamente da un sottoinsieme di $S$, più precisamente dall'insieme degli esiti che lo realizzano.

L'evento "esce un numero pari" è descritto da $\{2,4,6\} \subset S$.

La **Famiglia degli eventi** = **Famiglia dei sottoinsiemi di S**.
(Questa identità solo se S è numerabile altrimenti vanno fatte delle precisioni, introdurre $\sigma - algebre$).

## Proprietà

- Due eventi $E, F \subset S$ si dicono **incompatibili** se $E \cap F = \emptyset$.
- $S$ come evento è detto **evento certo**, nel caso del dado l'evento "esce un numero intero" è dato da $S$.
- Dato un evento $E$, l'evento complementare $E^c$ è dato da $E^{c}=S\backslash E$, ad esempio se l'evento è "esce un numero minore o uguale a 2" l'evento complementare è dato da $\{3,4,5,6\}$.
- Leggi di **De Morgan**
  $(A \cup B)^{c}=A^{c}\cap B^{c}$                   $(A \cap B)^{c}=A^{c}\cup B^{c}$

- L'evento **impossibile** è descritto da $\emptyset$.

> [!info] Definizione Spazio di Probabilità
> Uno spazio di probabilità è descritto dalla coppia $(S, P)$ dove **S è lo spazio campionario** dell'esperimento e **P detta funzione di probabilità**, è una funzione definita sulla famiglia degli eventi che soddisfa i seguenti assiomi:
> 
> 1) $P(E)\in [0,1] \ \ \forall E$ evento cioè $\forall E \subset S$
> 2) $P(S)=1$
> 3) Data una successione $E_{1},E_{2}...$ di eventi 2 a 2 disgiunti vale:
>    
> $$
>    P(\bigcup^{\infty}_{i=1} E_{i})=\sum\limits_{i=1}^{\infty}P(E_{i}) 
> $$
>    
>    Questo quando $\forall i\neq j$ e $E_{i}\cap E_{j}\neq \emptyset$
>    Ovvero $\forall i\neq j$ abbiamo $E_{i}$ e $E_{j}$ incompatibili.
>    
>    Terminologia: Dato $E$ evento, $P(E)$ si dice probabilità dell'evento E.
>



