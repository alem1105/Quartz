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

## Spazio di Probabilità

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

### Proposizione 1

$$
P(\emptyset)=0
$$

La probabilità dell'evento impossibile è uguale a 0.

_Dimostrazione - Utilizzando l'assioma 3_

Prendiamo la successione $E_1,E_2,E_3,...$  dove $E_1=\emptyset,E_2=\emptyset,E_3=\emptyset,...$, quindi abbiamo che $\forall i\neq j$ l'intersezione $E_i\cap E_j=\emptyset$.

Per l'assioma 3 $P(\bigcup\limits^{\infty}_{i=1} E_{i})=\sum\limits_{i=1}^{\infty}P(E_{i})$, quindi $P(\emptyset)=\sum\limits_{i=1}^{\infty}P(\emptyset)$, per l'assioma 1 sappiamo che $P(\emptyset)\in [0,1]$.

Supponiamo che $P(\emptyset)\in (0,1]$ allora abbiamo che $\sum\limits_{i=1}^{\infty}P(\emptyset)=+\infty$ e quindi $P(\emptyset)\neq \sum\limits_{i=1}^{\infty}P(\emptyset)$, per esclusione quindi $P(\emptyset)=0$ altrimenti come appena visto otteniamo un valore infinito.

### Proposizione 2
Prendiamo un esempio:
- Domani piove con una probabilità 0.3
- Domani c'è il sole con una probabilità 0.6
- Domani nevica con una probabilità 0.1
Qual è la probabilità che piova o che nevichi? 0.3 + 0.1 = 0.4

**P soddisfa l'additività finita**: Dati $n$ eventi a 2 a 2 _incompatibili_ $E_1,E_2,...,E_n$ vale $P(\bigcup\limits^{n}_{i=1} E_{i})=\sum\limits_{i=1}^{n}P(E_{i})$

_Dimostrazione_

Consideriamo la successione $F_1:=E_1,F_2:=E_2,...,F_n:=E_n,F_{n+1}:=\emptyset,F_{n+2}:=\emptyset$, ovvero hanno dei valori fino ad $n$ e poi sono $\emptyset$.

Dato che la successione è fatta da eventi 2 a 2 _incompatibili_ posso applicare il 3 assioma e otteniamo:

$$
P(\bigcup\limits^{\infty}_{i=1} F_{i})=\sum\limits_{i=1}^{\infty}P(F_{i})
$$

Che è equivalente a:

$$
P(\bigcup\limits^{\infty}_{i=1} E_{i})=P(E_1)+P(E_2)+...+P(E_n)+P(\emptyset)+...
$$

Per la proposizione precedente sappiamo che $P(\emptyset)=0$ quindi tutti i $P(\emptyset)$ sono trascurabili lasciando soltanto:

$$
P(\bigcup\limits^{n}_{i=1} E_{i})=P(E_1)+P(E_2)+...+P(E_n)
$$
### Proposizione 3

$$
\forall E\subset S \text{ vale } P(E^c)=1-P(E)
$$

_Dimostrazione_

![[Pasted image 20241001105352.png|400]]

$E$ e $E^c$ sono eventi _incompatibili_, quindi per l'**additività finita** abbiamo che $P(E\cup E^c)=P(E)+P(E^c)$ ma sappiamo che $E\cup E^c=S$ quindi possiamo dire che $P(E\cup E^c)=P(S)=1$.

Possiamo scrivere quindi:

$$
P(E)+P(E^c)=1\rightarrow P(E^c)=1-P(E)
$$

### Proposizione 4 - Monotonia della Funzione di Probabilità
Dati $E$ e $F$ eventi con $E\subset F$ allora vale $P(E)\leq P(F)$.

![[Pasted image 20241001105832.png|400]]

$F=E\cup (F\backslash E)$, quindi $E$ ed $F\backslash E$ sono _disgiunti_.

Quindi, $P(F)=P(E)+P(F\backslash E)$ dato che per l'assioma 1 $P(F\backslash E)\geq 0$
allora $P(E)+P(F\backslash E)\geq P(E)$.

### Proposizione 5
$\forall E,F$ eventi, allora $P(E\cup F)=P(E)+P(F)-P(E\cap F)$, questa è la **formula generale**, non l'abbiamo usata prima perché nel caso in cui $E,F$ sono disgiunti allora $P(E\cap F) = 0$.

_Esempio Grafico_

![[Pasted image 20241001110629.png|400]]

Anche se conosco l'area delle due figure, per conoscere l'area totale devo sottrarre l'area dell'intersezione fra le due.

_Dimostrazione_

![[Pasted image 20241001110726.png|300]]

Abbiamo che $I=E\backslash F, II = F\backslash E, III = E\cap F$, gli eventi quindi sono 2 a 2 disgiunti (gli eventi 2 a 2 disgiunti sono le zone I, II e III non E ed F).

Otteniamo che:
- $P(E)=P(I\cup III)= P(I)+P(III)$
- $P(F)=P(II\cup III)=P(II)+P(III)$
- $P(E\cap F)=P(III)$

Sappiamo che:
- $P(E\cup F)=P(I\cup II\cup III) = P(I)+P(II)+P(III)$
- E secondo la proposizione: $P(E\cup F)=P(E)+P(F)-P(E\cap F)$, sostituendo i valori : 
$$
P(E\cup F)=P(I)+P(III)+P(II)+P(III)-P(III)=P(I)+P(II)+P(III)
$$
Abbiamo ottenuto lo stesso risultato.

_Esempio_

Giulia porta ha 2 libri _L1, L2_, l'evento _E_ corrisponde a "Le piace _L1_" mentre _F_ a "Le piace _L2_".

- $P(E)=0.5$
- $P(F)=0.4$
- $P(E\cap F)=0.3$ -> "Le piacciono entrambi"

Quant'è la probabilità che non le piaccia alcun libro?

- Calcoliamo prima $E\cup F$ che equivale a "Le piace almeno un libro":
  $P(E\cup F)=P(E)+P(F)+P(E\cap F)=0.5+0.4-0.3=0.6$
- L'evento complementare di "Le piace almeno un libro" è "Non le piace nessun libro" quindi il risultato finale è:

$$
P((E\cup F)^c)=1-P(E\cup F)=1-0.6=0.4
$$

**Infatti**:

Dato uno spazio campionario _S_ e due eventi $E,F\subset S$ abbiamo che:

$$
x\in E\cup F\Leftrightarrow x\in E \text{ o } x\in F \Leftrightarrow \text{ x realizza almeno uno dei due eventi}
$$

Quindi $E\cup F$ significa che "Si verifica E oppure si verifica F" **non c'è esclusività**, invece $E\cap F$ significa che "Si verifica sia E che F".

_Esempio_

Abbiamo un dato truccato dove:
- 1 esce con probabilità $\frac{1}{2}$
- Gli altri numeri con probabilità $\frac{1}{10}$

Quant'è la probabilità che esce un numero dispari? $E=\{1,3,5\}$.

Per **additività finita**:

$$
\underbrace { P(E) }_{ \{1\}\cup\{3\}\cup\{5\} \text{ 2 a 2 incompatibili} }=P(\{1\})+P(\{3\})+P(\{5\})=\frac{1}{2}+\frac{1}{10}+\frac{1}{10}=\frac{7}{10}
$$

## Esiti su spazi di probabilità con esiti equiparabili
Supponiamo che $|S|<\infty$ quindi abbiamo una situazione del tipo, $S=\{ S_{1},S_{2},\dots,S_{n}\}$ con $n$ esiti.
Supponiamo che, ad esempio per simmetria, i vari esiti abbiano la stessa probabilità di realizzarsi, **sono equiprobabili**.

Come modelliamo questo esperimento con uno spazio di probabilità?

- Dato che gli esiti sono tra di loro paritari richiederanno che $P(\{ 1 \})=P(\{ 2 \})=\dots=P(\{ S_{n} \})=z$, questo valore lo chiameremo $z$.
- Inoltre abbiamo che
  $$
  1=P(S)=\underbrace{ P(\{ 1 \}\cup \dots\cup \{ S_{n} \}) }_{ S=\{ 1 \}\cup \dots\cup \{ S_{n} \} \text{ 2 a 2 incompatibili} }=\sum\limits_{i=1}^{n}P(\{ S_{i} \})=n \cdot z
  $$
Questo perché abbiamo la somma di $n$ valori uguali che valgono tutti $z$.

In questo modo abbiamo provato che $1=n \cdot z$ e quindi $z=\frac{1}{n}$, e dato che sono equiprobabili sappiamo che $\forall i, 1 \leq i \leq n, P(\{ S_{i} \})=\frac{1}{n}$.

### Proposizione
Se $|S|=n$ e gli esiti sono equipossibili, allora $\forall E, P(E)=\frac{|E|}{|S|}=\frac{\text{\# esiti favorevoli a E}}{\text{\# esiti possibili}}$

_Dimostrazione_

Dato $E=\bigcup\limits_{S\in E}\{ S \}$ gli eventi $\{ S \}$, con $S \in E$ sono 2 a 2 incompatibili. Possiamo applicare l'additività finita e ottenere:

$$
P(E)=\sum_{S\in E}P(\{ S \})=\sum_{S\in E} \frac{1}{n}=\frac{|E|}{n}=\frac{|E|}{|S|}
$$
_Esempio_

Lancio 2 dadi, qual è la probabilità che la somma dei numeri usciti dia 6?

$$
\begin{align*}
&S=\{ (a,b):a,b\in \{ 1,2,\dots,6 \} \}\\
&a=\text{numero al 1° lancio} \\
&b=\text{numero al 2° lancio}
\end{align*}
$$

Il dado è onesto e quindi tutti i numeri sono equipossibili, quindi:

$$
P(E)=\frac{|E|}{|S|} \text{ dove } E\subset S
$$

$$
\begin{align*}
E=\text{"La somma da 6"}&=\{ (a,b)\in S:a+b=6 \} \\
&=\{ (1,5),(2,4),(3,3),(4,2),(5,1) \} \\ \\
&P(E)=\frac{|E|}{|S|}=\frac{5}{\underbrace{ 6 \cdot 6 }_{ \text{esiti possbili 2 dadi} }}=\frac{5}{36}
\end{align*}
$$


> [!info] Ordine
> Conviene non prendere i numeri dimenticando l'ordine, altrimenti gli esiti non sono equipossibili:
> $$
> P(\text{"Sono usciti 2 e 3 in qualunque ordine"})=\frac{2}{36}, \{ (2,3),(3,2) \}
> $$
> 
> $$
> P(\text{"Uscito 1 e 1"})=P(\{ (1,1) \})=\frac{1}{36}
> $$

_Esempio_

Ho un mazzo da 40 carte, estraggo 2 carte senza rimpiazzo, quant'è la probabilità che escano 2 carte di bastoni?

Il mazzo è composto da 4 semi e 10 carte per seme.
- $M$ = Mazzo
- $S=\{ (a,b):a,b\in M, a \neq b \}$

Per simmetria ho esiti equiprobabili quindi vale $P(E)=\frac{|E|}{|S|}$.

In questo caso abbiamo che $E=\{ (a,b)\in S:a,b \text{ sono di bastoni} \}$, $|S|=40 \cdot 39$ che sono i modi possibili per estrarre due carte ed $|E|=10 \cdot 9$ che sono i modi possibili per estrarre due carte dello stesso seme.

$$
P(E)=\frac{|E|}{|S|}=\frac{10 \cdot 9}{40 \cdot 39}=\frac{1}{4}\cdot \frac{3}{13}=\frac{3}{52}
$$

_Approccio Alternativo_

$S=\{ \{ a,b \}:a,b\in M, a\neq B \}$, adesso consideriamo di estrarre 2 carte nello stesso momento e quindi non sono più coppie ordinate, non conta l'ordine.

Gli esiti sono comunque equiprobabili ma adesso per selezionare due carte senza contare l'ordine in tutto il mazzo posso fare $\binom{40}{2}$ mentre per due carte dello stesso seme $\binom{10}{2}$ quindi:

$$
P(E)=\frac{\binom{10}{2}}{\binom{40}{2}}=\frac{3}{52}
$$

_Esempio Libro_

Ho un'urna con 6 palline bianche e 5 nere.
Estraggo 3 palline a caso senza rimpiazzo, quant'è la probabilità che esca 1 bianca e 2 nere?

Non ci conviene registrare soltanto il colore delle palline, **questo perché rompe la simmetria**, ci conviene invece numerarle una per una in modo da distringuerle.

$Urna=U=\{ B_{1},B_{2},B_{3},B_{4},B_{5},B_{6},N_{1},N_{2},N_{3},N_{4},N_{5} \}$ abbiamo quindi 11 palline distinguibili.

$S=\{ A\subset U:|A|=3 \}$, un esempio di esito è $\{ B_{2},B_{4},N_{3} \}$.

Quindi adesso $S$ ha esiti equiprobabili per simmetria: $P(E)=\frac{|E|}{|S|}$ dove $|S|=\binom{11}{3}$.

Quanto vale $|E|$? $E=\{ A \subset U:|A|=3, \text{A ha una pallina bianca e 2 nere} \}$

$|E|=6 \cdot\binom{5}{2}$ dove $6$ sono i modi per estrarre una pallina bianca e $\binom{5}{2}$ quelli per scegliere due palline nere senza considerare l'ordine. Quindi:

$$
P(E)=\frac{6 \cdot\binom{5}{2}}{\binom{11}{3}} = \frac{4}{11}
$$


_Esempio dei Compleanni_

A quanto corrisponde la probabilità che due persone condividano lo stesso giorno di compleanno? Prendendo in considerazione soltanto anni da 365 giorni.

$S=\{ (x_{1},x_{2}):x_{1},x_{2}\in \{ 1,2,\dots,365 \} \}$, $E=\{ (x_{1},x_{2})\in S:x_{1}=x_{2} \}=\{ (1,1),(2,2),\dots,(365,365) \}$.

Allora $P(E)=\frac{365}{365^2}$ infatti ho una sola coppia fra le 365 di $E$ ed ho $365^2$ per scegliere i compleanni di due persone.

Se abbiamo 3 persone?

$S=\{ (x_{1},x_{2},x_{3}):x_{1},x_{2},x_{3}\in \{ 1,2,\dots,365 \} \}$, $E=\{ (x_{1},x_{2},x_{3})\in S: \exists i\neq j \text{ con }1\leq i,j\leq 3, x_{i}=x_{j}\}$

Ma calcolare tutte le triplette con 3 valori uguali è molto complesso, è invece più semplice calcolare quelle con 3 valori distinti ovvero $E^c$ e poi per calcolare $P(E)$ svolgere $1-P(E^c)$.

$E^c=\{ (x_{1},x_{2},x_{3})\in S:x_{1},x_{2},x_{3}\text{ sono distinti} \}$, per il principio fondamentale della combinatoria $|E^c|=365\cdot 364\cdot 363$, mentre $|S|=365^3$ e quindi:

$$
P(E)=1-\frac{365\cdot 364\cdot 363}{365^3}
$$

_In Generale per n persone:_

$$
P(E)=1-\frac{|E^c|}{|S|}=1-\frac{365\cdot 364\cdot \dots. \cdot (365-n+1)}{365^n}
$$

_Esercizio_

Creare una commissione di 5 persone estratte da un gruppo composto da 6 uomini e 9 donne. Se scelgo le persone da bendato, quante sono le probabilità che la commissione sia formata da 3 uomini e 2 donne.

$S=\{ A\subset G:|A|=5 \}$ dove $G=$ gruppo delle 15 persone totali.
Dobbiamo calcolare quindi $P(E)=\frac{|E|}{|S|}$ dove $E=\{ A\subset G:|A|=5\wedge\text{A contiene 3U e 2D} \}$.

Come visto in esempi precedenti ci conviene numerare tutte le persone in modo da distinguerle in questo modo otteniamo che per scegliere 3 uomini da un gruppo di 6 posso calcolare $\binom{6}{3}$ e per le donne $\binom{9}{2}$ in totale per formare un gruppo da 5 = $\binom{6}{3}\cdot \binom{9}{2}$.

$|S|$ è più semplice dato che dobbiamo semplicemente scegliere 5 persone da un gruppo di 15 e quindi $\binom{15}{5}$, la probabilità è data quindi da:

$$
P(E)=\frac{|E|}{|S|}=\frac{\binom{6}{3}\cdot\binom{5}{2}}{\binom{15}{5}}=\frac{240}{1001}
$$

_Proviamo a tenere conto dell'ordine di scelta:_

Allora $S=\{ (x_{1},x_{2},x_{3},x_{4},x_{5}):\forall i,\ x_{i}\in G,x_{1},\dots,x_{5}\text{ sono distinti} \}$.

$|S|=15\cdot 14\cdot 13\cdot 12\cdot 11$.

$E=\{ (x_{1},\dots,x_{5})\in S:\text{ci sono 3u e 2d} \}$.

In questo caso non posso procedere subito con il principio fondamentale dato che se appunto inizio a calcolare $15\cdot 14\cdot ?$ a questo punto non so cosa scegliere, perché dipende dagli esiti precedenti, se ho scelto 2 donne devo scegliere un uomo ma se ho scelto 2 uomini posso scegliere sia una donna che 1 uomo, o altri casi ancora.

Posso però stabilire in che posizione scelgo gli uomini e le donne ad esempio $(U_{*},D_{*},D_{*},U_{*},U_{*})$ in questo modo posso calcolare tutte le combinazioni di posizioni possibili con il coefficiente binomiale $\binom{5}{3}=\binom{5}{2}$ oppure calcolare le permutazioni della stringa e quindi $\frac{5!}{3!\cdot 2!}$, tutti e 3 i modi sono validi.

A questo punto scelgo gli uomini nella cinquina con il principio fondamentale e quindi $6\cdot 5\cdot 4$, e poi scelgo le donne $9\cdot 8$. Mettendo tutto insieme:

$$
\frac{5!}{3!\cdot 2!}\cdot 6\cdot 5\cdot 4\cdot 9\cdot 8 =\frac{240}{1001}
$$

**Considerando o meno l'ordine, il risultato NON cambia, avrò sempre le stesse probabilità**

## Principio di Inclusione / Esclusione

- Con 2 eventi: $P(A\cup B) = P(A)+P(B)-P(A\cap B)$
- Con 3 eventi: $P(A\cup B\cup C)=P(A)+P(B)+P(C)-P(A\cap B)-P(A\cap C)-P(B\cap C)+P(A\cap B\cap C)$
- Con $n$ eventi: (***!!! NON FA PARTE DEL PROGRAMMA !!!***) 

$$
P\left( \bigcup_{i=1}^{n}E_{i} \right)=\sum_{i=1}^nP(E_{i})-\sum_{i\leq i\leq j\leq n}P(E_{i}E_{j})+\sum_{1\leq i\leq j\leq k\leq n}P(E_{i}\cap E_{j}\cap E_{k})\dots(-1)^nP(E_{1}\cap E_{2}\cap E_{n})
$$

