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

## Probabilità Condizionata

Dati $E, F$ eventi con $P(F)>0$, la probabilità di $E$ condizionata a $F$ è definita come $P(E|F)=\frac{P(E\cap F)}{P(F)}$. Per $E,F$ eventi con $P(F)$ positiva.

Si svolge l'esperimento e so che "si verifica F", questa informazione muta la mia speranza che si verifichi $E$ e la nuova probabilità di $E$ sapendo che si è verificato $F$ è data da $P(E|F)$.

_Esempio_

Lancio 1 dado.

$E=\text{Esce 1 o 2}, P(E)=\frac{2}{6}=\frac{1}{3}$.

Immaginiamo di sapere che si è verificato l'evento $F$ dove $F=\text{Uscito un numero } \leq 4$, se so che $F$ si realizza allora so che è uscito o 1 o 2 o 3 o 4. Ho 4 possibili esiti e c'è simmetria.

Quindi in questo modo se si verifica $F$ allora $P(E)=\frac{2}{4}=\frac{1}{2}$, ci aspettiamo quindi $P(E|F)=\frac{1}{2}$, calcoliamolo usando la definizione:

$$
\begin{align*}
&P(E|F)=\frac{P(E\cap F)}{P(F)}=\frac{\frac{2}{6}}{\frac{4}{6}}=\frac{1}{2} \\ \\
&S=\{ 1,2,\dots,6 \} \\
&F=\{ 1,2,3,4 \}
\end{align*}
$$

_Proposizione_

Se $S$ è finito e ha esiti equiprobabili allora $P(E|F)=\frac{|E\cap F|}{|F|}$ con $E,F$ eventi con $P(F)$ positiva.

_Dimostrazione_

$P(E|F)=\frac{P\cap F}{P(F)}$ e per ipotesi $P(F)>0$ quindi vale la definizione di $P(E|F)$

$$
P(E|F)=\frac{P(E\cap F)}{P(F)}=\frac{\frac{|E\cap F|}{|S|}}{\frac{|F|}{|S|}}=\frac{|E\cap F|}{|F|}
$$

_Esercizio_

Estraggo 3 carte da un mazzo da 40 senza rimpiazzo, sapendo che ho estratto solo carte di bastoni, qual è la probabilità di aver estratto un asso?

$$
\begin{align*}
&E=\text{Estraggo un asso} \\
&F=\text{Le carte sono di bastoni} \\
&S=\{ A\subset M:|A|=3 \}\text{ dove M = mazzo, S ha esiti equiprobabili} \\
 \\
&\underbrace{ P(E|F)=\frac{|E\cap F|}{|F|} }_{ \text{proposizione precedente} }=\frac{\binom{9}{2}}{\binom{10}{3}}=\frac{3}{10} \\
 \\
&\binom{9}{2} \text{ sono le terne non ordinate di bastoni dove non c'è asso}
\end{align*}
$$

_Esempio_

Ho un dado truccato dove 1 esce con probabilità $\frac{1}{2}$ mentre gli altri numeri $\frac{1}{10}$, qual è la probabilità che esca $1$ o $2$ sapendo che è uscito un numero $\leq 4$.

$$
\begin{align*}
&S=\{ 1,2,3,4,5,6 \} \\
&E=\{ 1,2 \} \\
&F=\{ 1,2,3,4 \} \\
\\
&P(E|F)=\frac{P(E\cap F)}{P(F)}= \dots \\  \\
&E\cap F=\{ 1,2 \},P(E\cap F)=P(\{ 1 \})+P(\{ 2 \})=\frac{1}{2}+\frac{1}{10}=\frac{3}{5} \\
\\
&P(F)=P(\{ 1,2,3,4 \})=\frac{1}{2}+\frac{3}{10}=\frac{4}{5} \\
\\
&\dots=\frac{\frac{3}{5}}{\frac{4}{5}}=\frac{3}{4}
\end{align*}
$$

**Regola del Prodotto**

Se $P(F)>0,P(E|F)=\frac{P(E\cap F)}{P(F)}$ quindi $P(E\cap F)=P(F)\cdot P(E|F)$

_Esempio_

Abbiamo un'urna con 10 palline bianche e 4 palline nero, estraggo 2 palline senza rimpiazzo. Qual è la probabilità che siano entrambe bianche? Lo avevamo già risolto con la combinatoria, vediamo senza:

$$
\begin{align*}
&F=\text{La prima pallina estratta è bianca} \\
&E=\text{La seconda pallina estratta è bianca} \\
&G=E\cap F, P(G)=P(E\cap F)=P(F)\cdot P(E|F)=\frac{10}{14}\cdot \frac{9}{13}
\end{align*}
$$

_Dimostrazione_

Siano $E_{1},\dots,E_{n}$ eventi allora $P(E_{1}\cap\dots\cap E_{n})=P(E_1)\cdot P(E_{2}|E_{1})\cdot P(E_{3}|E_{1}\cap E_{2})\dots \cdot P(E_{n}|E_{1}\cap \dots\cap E_{n-1})$ supponendo che $P(E_{1}>0,P(E_{1}\cap E_{2})>0,\dots,P(E_{1}\cap\dots\cap E_{n-1})>0)$.

_Dimostrazione per n=2 già fatta, vediamo con n=3_

$$
\begin{align*}
&n=3  \\
&\text{Dobbiamo provare che} \\
&P(E_{1}\cap E_{2}\cap E_{3})=P(E_{1})\cdot P(E_{2}|E_{1})\cdot P(E_{3}|E_{1}\cap E_{2}) \\
 \\
&\text{Per definizione di prob cond.} \\
 \\
&P(E_{1})\cdot P(E_{2}|E_{1})\cdot P(E_{3}|E_{1}\cap E_{2})=P(E_{1})\cdot\frac{P(E_{2}\cap E_{1})}{P(E_{1})}\cdot\frac{P(E_{3}\cap E_{1}\cap E_{2})}{P(E_{1}\cap E_{2})}=\dots \\
 \\
&=P(E_{1}\cap E_{2}\cap E_{3})
\end{align*}
$$

Per $n$ generico è simile.

_Esempio_

Estraggo 3 carte senza rimpiazzo da un mazzo da 40, qual è la probabilità che la prima carta è di bastoni, la seconda di denari e la terza di bastoni.

$$
\begin{align*}
&P(G)=? \ G=\text{1 carta bastoni, 2 denari, 3 bastoni} \\
 \\
&\text{1° Metodo combinatoria} \\
&S=\{ (a,b,c):a,b,c\in M, distinti \} \\
&P(G)=\frac{|G|}{|S|}=\frac{10\cdot 10\cdot 9}{40\cdot 39 \cdot 38}=\dots \\
 \\
&\text{2° Metodo prob. cond.} \\
&G=E_{1}\cap E_{2}\cap E_{3} \text{ dove} \\
&E_{1}=\text{prima carta B},E_{2}=\text{seconda carta D},E_{3}=\text{terza carta B} \\
 \\
&\text{Per regola prodototto} \\
&P(G)=P(E_{1}\cap E_{2}\cap E_{3})=P(E_1)\cdot P(E_{2}|E_{1})\cdot P(E_{3}|E_{1}\cap E_{2})= \\
&=\frac{10}{40}\cdot \frac{10}{39}\cdot \frac{9}{38}=\dots
\end{align*}
$$

**Teorema di Bayes**

$$
P(A|B)\overset{\text{Definizione}}=\frac{P(A\cap B)}{P(B)}\overset{\text{Regola prodotto}}=\frac{P(A)\cdot P(B|A)}{P(B)}
$$

Enunciato:

$$
P(A|B)=\frac{P(A)\cdot P(B|A)}{P(B)}
$$

---

_Esempio_

Ho un'urna con 10 palline di cui 1 d'oro, lancio 1 dado, se esce 1 estraggo 2 palline senza rimpiazzo altrimenti estraggo 1 sola pallina, con che probabilità estraggo la pallina d'oro?


> [!info] Formula probabilità totale
> Dati $E,F$ eventi allora $P(E)=P(F)\cdot P(E|F)\cdot P(F^C)\cdot P(E|F^C)$
> 
> _Dimostrazione_
> 
> $E=(E\cap F)\cup (E\cap F^C)$ quindi  dato che sono incompatibili $P(E)=P(E\cap F)+P(E\cap F^C)\overset{\text{Regola Prodotto}}=P(F)\cdot P(E|F)+P(F^C)\cdot P(E|F^C)$.

Se so cosa da il dado allora posso calcolare la probabilità.

$F=\text{Il dado da 1}$, $E=\text{La pallina d'oro viene estratta}$

E quindi per la legge della probabilità totale:

$$
\begin{align*}
&P(E)=P(F)\cdot P(E|F)\cdot P(F^C)\cdot P(E|F^C)=\dots  \\ \\
&\text{Calcoliamo i valori:} \\
&P(F)=\frac{1}{6} \\
&P(E|F)=\frac{P(E\cap F)}{P(F)}=\frac{9}{\binom{10}{2}}=\frac{1}{5} \\
&P(F^C)=\frac{5}{6} \\
&P(E|F^C)=\frac{1}{10} \\ \\
&\text{Quindi:} \\
&\dots=\frac{1}{6}\cdot \frac{1}{5}+\frac{5}{6}\cdot \frac{1}{10}=\frac{7}{60}
\end{align*}
$$

---

Adesso invece sappiamo che la pallina d'oro è stata estratta, qual è la probabilità che dal dado è uscito 1?

Noi sappiamo calcolare $P(E|F)$ e $P(E|F^C)$ ma adesso vogliamo ottenere $P(F|E)$.

Per il teorema di Bayes:

$$
P(F|E)=\frac{P(F\cap E)}{P(E)}=\frac{P(F)\cdot P(E|F)}{P(E)}
$$

Quindi:

$$
P(F|E)=\frac{P(F)\cdot P(E|F)}{P(E)}=\frac{\frac{1}{6}\cdot \frac{1}{5}}{\frac{7}{60}}=\frac{2}{7}
$$


---

_Esempio Parte I_

In un'agenzia di assicurazioni le persone vengono divise in due categorie: _propense e non propense a fare incidenti_. 

Le persone propense hanno una probabilità di 0.4 di fare un incidente in un anno mentre le non propense 0.2.

Il 30% degli automobilisti è propensa agli incidenti.

Qual è la probabilità che un nuovo cliente abbia un incidente in quell'anno?

$$
\begin{align*}
&A:=\text{Il nuovo cliente è propenso agli incidenti} \\
&A_{1}:= \text{Il nuovo cliente ha un incidente in un anno} \\
&P(A_{1})=? \\
&P(A_{1}|A)=0.4, P(A_{1}|A^C)=0.2, P(A)=0.3 \\
 \\
&\text{Per la formula di probabilità totale:} \\
&P(A_{1})=P(A)\cdot P(A_{1}|A)+P(A^C)\cdot P(A_{1}|A^{C})=0.3\cdot 0.4+0.7\cdot 0.2=0.26=26\%
\end{align*}
$$

_Parte II_

Sapendo che il cliente ha avuto un incidente in quell'anno, qual è la probabilità che sia propenso agli incidenti?

Quindi 

$$
P(A|A_{1})=\frac{P(A\cap A_{1})}{P(A_{1})}=\frac{P(A)\cdot P(A_{1}|A)}{P(A_{1})}=\frac{0.3\cdot 0.4}{0.26}=\frac{6}{13}
$$


## Legge probabilità totale generalizzata
Siano $F_{1},\dots,F_{n}$ eventi 2 a 2 disgiunti tali che $S=\bigcup\limits^{n}_{i=1}F_{i}$ allora per ogni evento $E_{i}$ vale $P(E)=\sum\limits_{i=1}^n P(F_{i})\cdot P(E| F_{i})$.

_Esempio con $n=2$_

$$
P(E)=P(F_{1})\cdot P(E | F_{1})+P(F_{2})\cdot P(E|F_{2})
$$

_Esempio Test Malattia_

Abbiamo un esame efficace al 95% quando la malattia è presente, 1% di falsi positivi e il 5x1000 della popolazione ha effettivamente la malattia.

$D=\text{La persona testata ha la malattia}$

$E=\text{Persona è positiva all'esame}$

$$
\begin{align*}
&P(E|D)=0.95 \\
&P(E|D^C)=0.01 \\
&P(D)=0.005 \\
&\text{Qual è la probabilità che una persona testata abbia la malattia?} \\
&P(D|E)=? \\
&P(D|E)=\frac{P(D\cap E)}{P(E)}=\frac{P(D)\cdot P(E|D)}{P(D)\\cdot P(E|D)+ P(D^C)\cdot P(E|D^C)}=\frac{0.005\cdot 0.95}{0.005\cdot 0.95+0.995\cdot 0.01}=0.323 \\
&\text{Quindi se il test dice che siamo malati, lo siamo veramente in un caso su 3 circa.}
\end{align*}
$$

Il test è buono se $P(D|E)$ è vicina al 100% e anche se $P(D^C|E^C)$ è vicina al 100%.

Questo non è un buon test per la popolazione e la malattia presa in esame, infatti ci sono troppi pochi malati e se vengono effettuati tanti test con questa probabilità di falsi positivi avremo più test sbagliati che veri malati.

Infatti con 995 sani e 5 malati abbiamo molti falsi positivi.

Infatti:

$P(D|E)=\frac{P(D\cap E)}{P(E)}=\frac{\text{\#Persone malate con test positivo}}{\text{\#Persone con test positivo}}$ dove il numero di persone con test positivo (denominatore) è dato da $\text{\#Persone malate con test positivo + \#Persone sane con test positivo}$.

Prendiamo ad esempio 995.000 sani testati allora 9950 sani avranno un test positivo ovvero test sbagliati mentre i malati che sono 5000, solo il 95% ovvero 4750 avranno un test positivo e quindi corretto.

Notiamo quindi che i testi sbagliati 9950 sono molto maggiori rispetto ai test corretti 4750.

Questo test sarebbe più corretto se usato per una malattia con più infetti.

## Rapporto a Favore

_Definizione_: Il rapporto a favore di un evento $A$ è dato da:

$$
\frac{P(A)}{P(A^C)}=\frac{P(A)}{1-P(A)}
$$

_Esempio_:

Abbiamo la partita di calcio Italia - Brasile. Se la vittoria dell'italia è data 1 a 5 intendiamo che il rapporto a favore dell'evento "l'italia vince" è $\frac{1}{5}$ e quindi $\frac{P(A)}{P(A^C)}=\frac{1}{5}$.

Data l'espressione possiamo calcolare A:

$$
\begin{align}
&P(A)=\frac{1}{5}\cdot(1-P(A)) \\
&P(A)=\frac{1}{5}-\frac{P(A)}{5} \\
&\frac{6}{5}P(A)=\frac{1}{5} \\
&P(A)=\frac{1}{6};P(A^C)=\frac{5}{6}
\end{align}
$$

_Esempio di Criminologia_

Abbiamo $H$ ipotesi "Mario Rossi è l'assassino", abbiamo una stima di $P(H)$, ad esempio per Sherlock Holmes $P(H)=0.8$.

Introduciamo una nuova prova $E$ e questa modifica la nostra stima in $P(H|E)$, avendo introdotto una nuova prova, come cambia il rapporto a favore? Questo è dato da:

$$
\frac{P(H|E)}{P(H^C|E)} \text{ Mentre prima era } \frac{P(H)}{P(H^C)}
$$

Inoltre per il teoria di Bayes sappiamo che:

$$
P(H|E)=\frac{P(H)\cdot P(E|H)}{P(E)};P(H^C|E)=\frac{P(H^C)\cdot P(E|H^C)}{P(E)}
$$

Quindi il nuovo rapporto è dato da:

$$
\frac{P(H|E)}{P(H^C|E)}=\frac{\frac{P(H)\cdot P(E|H)}{P(E)}}{\frac{P(H^C)\cdot P(E|H^C)}{P(E)}}=\frac{P(H)}{P(H^C)}\cdot\frac{P(E|H)}{P(E|H^C)}
$$

Quindi possiamo vederlo anche come:

$$
\text{Vecchio rapporto }\cdot \frac{P(E|H)}{P(E|H^C)}
$$

Il nostro rapporto a favore quindi aumenta se $P(E|H)>P(E|H^C)$ ovvero se il loro rapporto > 1. Aumenta se appunto l'ipotesi è vera piuttosto che quando è falsa.

## Bayes Generalizzato
Avevamo visto la probabilità totale generalizzata, possiamo generalizzare anche il teorema di Bayes:

$$
P(F_{i}|E)=\frac{P(F_{i})\cdot P(E|F_{i})}{\sum\limits_{j=i}^{n}P(F_{j})\cdot P(E|F_{j})}
$$

_Esercizio_

Un aereo è scomparso, si presume sia finito con uguale probabilità in una di 3 zone $Z_{1},Z_{2},Z_{3}$.

Abbiamo:
- $1-\beta_{i}$ = Probabilità di trovare l'aereo in $Z_{i}$ se è effettivamente in $Z_{i}$.
- Sapendo che le ricerche in $Z_{1}$ hanno dato esito negativo, qual è la probabilità che l'aereo sia in $Z_{i}$ con $i=1,2,3$?
- $R_{i}=\text{L'aereo è in } Z_{i}$
- $E=\text{La ricerca in } Z_{1}\text{ ha dato esito negativo}$
- $P(R_{1})=P(R_{2})=P(R_{3})=\frac{1}{3}$
- $P(R_{i}|E)=?$

$$
\begin{align*}
P(R_{1}|E)=\frac{P(E\cap R_{1})}{P(E)}=\frac{P(R_{1})\cdot P(E|R_{1})}{P(E)}=\frac{P(R_{1})\cdot P(E|R_{1})}{\sum\limits_{k=1}^3 P(R_{k})\cdot P(E|R_{k})}=\frac{\frac{1}{3}\cdot \beta_{1}}{\frac{1}{3}\beta_{1}+\frac{1}{3}\cdot 1+ \frac{1}{3}\cdot 1}=\frac{\beta_{1}}{\beta_{1}+2}
\end{align*}
$$

Adesso prendiamo $j=2,3$

$$
\begin{align}
P(R_{j}|E)=\frac{P(R_{j})\cdot P(E|R_{j})}{P(E)}=\frac{\frac{1}{3}\cdot 1}{\frac{1}{3}\beta_{1}+\frac{1}{3}+\frac{1}{3}}=\frac{1}{\beta_{1}+2}
\end{align}
$$

**Proposizione**

Sia $F$ evento con $P(F)>0$ allora la funzione $E\rightarrow P(E|F)$ al variare di $E$ eventi è una funzione di probabilità. Abbiamo quindi una serie di indentità:

1) $P(E^C|F)=1-P(E|F)$
2) $P(A\cup B|F)=P(A|F)+P(B|F)-P(A\cap B|F)$
3) $A_{1},\dots,A_{n}$ eventi 2 a 2 disgiunti allora $P\left( \bigcup\limits_{i=1}^n A_{i}|F \right)=\sum\limits_{i=1}^n P(A_{i}|F)$

_Dimostrazioni negli appunti non so se le metto =P dato che dobbiamo solo fare esercizi_

_Esempio_: lanciamo 2 dadi e valutiamo la speranza degli eventi con $P$. Sappiamo che "il primo dado ha dato un numero pari" e chiamiamo questo evento $A$ quindi adesso la calcoliamo $P(\cdot,A)$. Se poi sappiamo che si verifica $B=\text{"Il 2 dato da un numero dispari"}$ allora valutiamo $Q(\cdot,B)$ dove $Q=P(\cdot,A)$ ottenendo quindi che $Q=(\cdot,A\cap B)$.

## Indipendenza di Eventi
Due eventi $E$ e $F$ si dicono indipendenti se $P(E\cap F)=P(E)\cdot P(F)$ e si scrive $E\perp\!\!\!\!\!\!\perp F$, sarebbe più intuitivo dire che $E$ ed $F$ sono indipendenti se $P(E|F)=P(E)$ e $P(F|E)=P(F)$ però per dare un senso a $P(E|F)$ è necessario che $P(F)>0$ e analogamente per $P(F|E)$ serve che $P(E)>0$.

Tolto il caso in cui uno tra $E$ ed $F$ abbia probabilità 0, la formulazione intuitiva e la definizione coincidono.

Infatti vale:

$$
\begin{align*}
\text{Sia } F \text{ con } P(F)>0 \text{ allora, per ogni evento } E \\
 \\
P(E|F)=P(E)\Leftrightarrow P(E\cap F)=P(E)\cdot P(F)
\end{align*}
$$

_Dimostrazione_

$$
\begin{align*}
&\text{Sia } P(E|F)=P(E) \text{ allora siccome } P(E|F)=\frac{P(E\cap F)}{P(F)} \text{ abbiamo che } \frac{P(E\cap F)}{P(F)}=P(E) \\
 \\
&\text{Moltiplichiamo per } P(F) \to P(F)\cdot\frac{P(E\cap F)}{P(F)}=P(E)\cdot P(F) \Leftrightarrow P(E\cap F)=P(E)\cdot P(F) \\
 \\
&\text{Quindi supponiamo che } P(E\cap F)=P(E)\cdot P(F) \text{ e dividiamo per } P(F)>0 \\
 \\
&\underbrace{ \frac{P(E\cap F)}{P(F)} }_{ P(E|F) }=P(E)
\end{align*}
$$

Analogamente possiamo provare che se $P(E)>0$ allora $P(F|E)=P(F)\Leftrightarrow P(E\cap F)=P(E)\cdot P(F)$.

_Osservazione_

Se $P(E)=0$ allora $E,F$ sono indipendenti per ogni $F$ evento, ovvero esistono eventi con probabilità nulla ma possibili.

Sia $E$ con $P(E)=0$ e sia $F$ evento dobbiamo verificare che $P(E\cap F)=\overbrace{ P(E) }^{ 0 }\cap P(F)$.

Quindi dobbiamo provare che $P(E\cap F)=0$, sappiamo che $E\cap F\subset E$ e per monotonia $P(E\cap F)\leq P(E)=0$.

_Esempio_

Lancio due volte un dado $E=\{ \text{Il 1° lancio dà 4} \},F=\{ \text{La somma dei lanci dà 6} \}$. $E\perp\!\!\!\!\!\!\perp F$?

$$
\begin{align*}
&S=\{ (a,b):a,b\in \{ 1,2,3,4,5,6 \} \} \text{ esiti equiprobabili} \\
&P(E)=\frac{1}{6} \\
&F=\{ (a,b)\in S:a+b=6 \}=\{ (1,5),(2,4),(3,3),(4,2),(5,1) \} \\
&P(F)=\frac{5}{36} \\
&P(E\cap F)=\{ (4,2) \}=\frac{1}{36} \\
 \\
&P(E\cap F)\neq P(E)\cdot P(F) \text{ quindi } E\not{\perp\!\!\!\!\!\!\perp} F
\end{align*}
$$

_Esempio_

Lancio due volte un dado $E=\{ \text{Il 1° lancio dà 4} \},F=\{ \text{La somma dei lanci dà 7} \}$. $E\perp\!\!\!\!\!\!\perp F$?

$$
\begin{align*}
&S=\{ (a,b):a,b\in \{ 1,2,3,4,5,6 \} \} \text{ esiti equiprobabili} \\
&P(E)=\frac{1}{6} \\
&F=\{ (a,b)\in S:a+b=6 \}=\{ (1,6),(2,5),(3,4),(4,3),(5,2),(6,1) \} \\
&P(F)=\frac{6}{36}=\frac{1}{6} \\
&P(E\cap F)=\{ (4,3) \}=\frac{1}{36} \\
 \\
&P(E\cap F)= P(E)\cdot P(F) \text{ quindi } E\perp\!\!\!\!\!\!\perp F
\end{align*}
$$

Se ho un esperimento composto da sottoesperimenti che non si influenzano allora eventi riferiti a sottoesperimenti diversi risultano indipendenti.

_Esempio_

Lancio due volte un dado e ho due sottoesperimenti: primo e secondo lancio. I due sottoesperimenti non si possono influenzare.

$E=\text{1° dà pari},F=\text{2° dà multiplo di 3}$, trattandosi di eventi che si riferiscono a lanci diversi ci aspettiamo che siano indipendenti, verifichiamo che $P(E\cap F)=P(E)\cdot P(F)$.

$$
\begin{align*}
&S=\{ (a,b):a,b\in \{ 1,2,3,4,5,6 \} \} \text{ esiti equiprobabili} \\
&P(E)=\frac{3}{6}=\frac{1}{2} \\
&P(F)=\frac{2}{6}=\frac{1}{3} \\
&E\cap F=\{ (a,b):a\in \{ 2,4,6 \},b\in \{ 3,6 \} \} \\
&P(E\cap F)=\frac{|E\cap F|}{|S|}=\frac{6}{36}=\frac{1}{6} \text{ che è uguale a }\frac{1}{2}\cdot \frac{1}{3} \text{ quindi } E\perp\!\!\!\!\!\!\perp F
\end{align*}
$$

**Proposizione**: Dati $E,F$ eventi, $E\perp\!\!\!\!\!\!\perp F\Rightarrow E^C\perp\!\!\!\!\!\!\perp F$

_Dimostrazione_

Supponiamo $E\perp\!\!\!\!\!\!\perp F$ e quindi $P(E\cap F)=P(E)\cdot P(F)$, dobbiamo provare che $E^C\perp\!\!\!\!\!\!\perp F$, cioè $P(E^C\cap F)=P(E^C)\cdot P(F)$.

$$
\begin{align*}
\text{Abbiamo che } P(E^C)=1-P(E) \\ \\
P(E^C\cap F)=(1-P(E))\cdot P(F)&=P(F)-\underbrace{ P(E\cap F) }_{ E\perp\!\!\!\!\perp F\Rightarrow P(E)\cdot P(F) } \\
&=P(F)-P(E)\cdot P(F) \\
\text{ Raggruppando } P(F)\to \ &=P(F)\cdot(1-P(E))  \\
&=P(F)\cdot P(E^C)
\end{align*}
$$

Supponiamo adesso di avere tre, eventi $E,F,G$: sappiamo che $E,F$ sono indipendenti e anche $E,G$ sono indipendenti. Possiamo dire che $E$ è indipendente da $F\cap G$? **No, possono essere dipendenti**.

_Esempio_

Lancio 2 dadi e definisco gli eventi:

$$
\begin{align*}
&E=\text{La somma dei dadi dà 7} \\
&F=\text{Il primo dado dà 4} \ \ \ G=\text{Il secondo dado dà 3}
\end{align*}
$$

Prendendo gli esempi precedenti sappiamo che $E\perp\!\!\!\perp F$, quindi dobbiamo provare che $E\perp\!\!\!\perp F$:

$$
\begin{align*}
&P(E)=\frac{6}{36}=\frac{1}{6} \\
&P(G)=\frac{1}{6} \\
&P(E\cap G)=\frac{1}{36} \\
&\text{Abbiamo che } P(E)\cdot P(G)=\frac{1}{6}\cdot \frac{1}{6}=\frac{1}{36}=P(E\cap G) \\
&\text{Quindi abbiamo mostrato che } E\perp\!\!\!\perp G \\
 \\
&\text{Notiamo però che } E\cancel{\perp\!\!\!\perp} (F\cap G) \text{ infatti } P(E|F\cap G)=1\neq P(E)
\end{align*}
$$

**Definizione**

Dati 3 eventi $E,F,G$ si dice che sono indipendenti se:

$$
\begin{align*}
&P(E\cap F) = P(E)\cdot P(F) \to E\perp\!\!\!\perp F \\
&P(E\cap G) = P(E)\cdot P(G) \to E\perp\!\!\!\perp G \\
&P(F\cap G) = P(F)\cdot P(G) \to F\perp\!\!\!\perp G \\
&P(E\cap F\cap G)=P(E)\cdot P(F)\cdot P(G)
\end{align*}
$$

**Teorema**

Se $E,F,G$ sono indipendenti, allora $E$ è indipendente da ogni evento costruito a partire da $F$ e $G$ usando unione, intersezione e complementare.

_Quindi, ad esempio:_

Se $E,F,G$ sono indipendenti, allora:

$$
\begin{align*}
&E\perp\!\!\!\perp(F\cap G) \\
&E\perp\!\!\!\perp(F\cup G) \\
&E\perp\!\!\!\perp(F^C \cup G) \\
&E\perp\!\!\!\perp F^C \\
&ecc\dots
\end{align*}
$$

E se ho più di 3 eventi?

**Definizione**

Dati $n$ eventi $E_1,\dots,E_{n}$ questi sono detti indipendenti se $\forall A\subset \{ 1,2,\dots,n \}$ con $A\neq \emptyset$ vale:

$$
P\left( \bigcap_{i\in A}E_{i} \right)=\prod_{i\in A}P(E_{i})
$$

Questa formula è interessante per $A$ tale che $|A|\geq 2$ infatti se $A=\{ i_{0} \}$ allora diventa $P(E_{i_{0}})=P(E_{i_{0}})$ che è banalmente vero.

_Esempio_

![[Pasted image 20241021200031.png|300]]

Prendiamo questi ponti, ogni ponte è integro con probabilità $p$ (e quindi distrutto con probabilità $1-p$), indipendentemente da ponte a ponte. Supponiamo $p=0.3$

Calcolare $P(\text{Partendo da A arrivo B})$.

Definiamo l'evento $E_{i}=\text{Il ponte i è integro}$.

Le strade che posso percorrere sono date da $(E_{1}\cap E_{2})\cup E_{3}$, quindi:

$$
\begin{align*}
P(A\to B)&= P((E_{1}\cap E_{2})\cup E_{3}) \\
&=P(E_{1}\cap E_{2})+P(E_{3})-P(E_{1}\cap E_{2}\cap E_{3}) \\
&=P(E_{1})\cdot P(E_{2})+P(E_{3})-P(E_{1})\cdot P(E_{2})\cdot P(E_{3}) \\
&=p^2+p-p^3=(0.3)^2+0.3-(0.3)^3
\end{align*}
$$

_Oppure possiamo calcolare_

$$
\begin{align*}
1-\underbrace{ P(\text{Da A non arrivo B}) }_{ E_{3}^C\cap(E_{1}^C\cup E_{2}^C) } =\overbrace{ P(E_{3}^C\cap(E_{1}^C\cup E_{2}^C))U }^{ \text{3 rotto e almeno 1 o 2 rotto} }=\text{Da finire :(}
\end{align*}
$$

