# Ripasso Teoria degli Insiemi
Possiamo vedere un insieme in modo generico come una **collezione di elementi**, per rappresentarli possiamo o descrivere chi ci appartiene o enumerare tutti gli elementi:

{Rosso, Nero} -> Insieme dei due colori Rosso e Nero
{0, 1, 2, ...} = $\mathbb{N}$ Insieme dei numeri naturali (non si usa questa convenzione di solito)

Poi c'è un insieme particolare chiamato **Insieme Vuoto**, si indica con $\emptyset$ e non ha nessun elemento al suo interno, inoltre questo è contenuto in tutti gli altri insiemi.

Per indicare un insieme il modo più utilizzato è quello di scegliere un **insieme universo U** e caratterizzare dei suoi sottoinsiemi attraverso delle proprietà, quindi gli elementi che rispettano tali proprietà faranno parte dei sottoinsiemi.

_Esempio_

$U = \mathbb{N}$     $I = \{x\in \mathbb{N} : \text{ x è pari }\}$
L'insieme $I$ è formato da tutti gli elementi appartenenti ad $\mathbb{N}$ tali che siano pari.

## Inclusione di Insiemi
Dati due insiemi $I, J$ sottoinsiemi di $U$, I si dice sottoinsieme di $J$ se tutti i suoi elementi appartengono a $J$:

$$
I\subset J \leftrightarrow \forall x\in I, x\in J
$$

La negazione si indica con:

$$
I\not\subset J \leftrightarrow \exists x \in I, x\not\in J
$$
## Insiemi Comparabili
Dati due insiemi $I, J \subset U$, si dicono comparabili se $I\subset J \bigvee J\subset I$ è vera.
Se invece è vera $I\subset J \bigwedge J\subset I$ allora i due insiemi sono uguali.

## Operazioni sugli Insiemi
Dati due insiemi $I, J \subset U$:

- **Intersezione**: sono gli elementi in comune fra i due insiemi
$$
  I\cap J = \{x\in U: x\in I \wedge x \in J\}
$$

- **Unione**: sono gli elementi presi da entrambi gli insiemi

$$
I \cup J = \{x\in U: x\in I \vee x \in J\}
$$

_Esempio_

$I \subset \mathbb{N} = \{x\in \mathbb{N}:x \text { è pari}\}$ 
$J \subset \mathbb{N} = \{x\in \mathbb{N}:x \text { è dispari}\}$ 

$I\cup J = \mathbb{N}$ mentre $I\cap J = \emptyset$. Perché?


> [!info] Algoritmo della Divisione Euclidea per 2
> 
> $$
> x\in \mathbb{N} \text{ Significa che } \exists ! (q,r) \in\mathbb{Z} \times \mathbb{N} \text{ t.c. } x=2q+r \text{ con } 0\leq r \leq 1
>$$
> Infatti i numeri interi si dividono in pari o dispari, ovvero possono avere o resto 0 o resto 1, per dimostrarlo supponiamo per assurdo che esista un $x\in I\cap J$ questo significa che:
> 
>$$
>\begin{align*}
>x=2q=2q' + 1 \\
>2(q-q')=1
>\end{align*}
>$$
>
>**Impossibile**


## Diagrammi di Venn
Sono un modo per rappresentare graficamente gli insiemi.

![[Pasted image 20240926100628.png]]

Per indicare gli insiemi possiamo anche utilizzare le tavole di verità basate sulle loro proprietà, utili per verificare alcune proprietà.

| P   | Q   | R   |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 0   | 1   |
| 0   | 1   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 0   |
| 1   | 0   | 1   |
| 1   | 1   | 0   |
| 1   | 1   | 1   |

Dalla tabella notiamo quindi che esistono 8 regioni nel nostro diagramma, una per ogni riga, infatti disegnandolo:

![[Pasted image 20240926101338.png||400]]

P, Q ed R sono rispettivamente le proprietà di A, B e C. Quindi a seconda del $n$ numero di insiemi abbiamo $2^n$ regioni.

I diagrammi di Venn hanno **un limite** infatti con dei soli cerchi non è possibile disegnare 4 insiemi o più, questo perché non rappresenteremo tutte le zone e avremo bisogno di figure più complesse.

> [!info] Terminologia
> $A\sqcup B$ indica l'unione di due insiemi nel caso in cui $A\cap B = \emptyset$.

_Esempio_

![[Pasted image 20240926101934.png|400]]

Notiamo che le zone colorate delle due proprietà che abbiamo scritto sono uguali, dimostriamolo anche con la tavola di verità, ricordando che:

- In caso di **Congiunzione (and)** si fa il **prodotto**.
- In caso di **Disgiunzione (or)** si fa il **massimo**.

$$\begin{array}{|c|c|c|c|c|c|c|c|} \hline P & Q & R & Q \lor R & P \land (Q \lor R) & P \land Q & P \land R & (P \land Q) \lor (P \land R) \\ \hline 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 1 & 1 & 0 & 0 & 0 & 0 \\ 0 & 1 & 0 & 1 & 0 & 0 & 0 & 0 \\ 0 & 1 & 1 & 1 & 0 & 0 & 0 & 0 \\ 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\ 1 & 0 & 1 & 1 & 1 & 0 & 1 & 1 \\ 1 & 1 & 0 & 1 & 1 & 1 & 0 & 1 \\ 1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 \\ \hline \end{array}$$

Anche le due tabelle di verità sono uguali quindi significa che gli insiemi sono uguali, **caratterizzati dalla stessa proprietà**.

Queste infatti prendono il nome di **Leggi di De Morgan**.

1) $A\cap (B\cup C) = (A \cap B) \cup (A \cap C)$
2) $A\cup (B\cap C) = (A \cup B) \cap (A \cup C)$

## Prodotto Cartesiano
Dati due insiemi $X,Y$ non vuoti si definisce $X \times Y = \{(x,y):x\in X, y\in Y\}$.
Con la scrittura $\mathbb{R}^2$ indichiamo $\{(x,y):x,y\in\mathbb{R}\}$.
Il prodotto cartesiano è formato da **coppie ordinate** quindi non confondiamo $(x,y)$ con $\{x,y\}$.

Si pone $(x,y)=\{x,\{x,y\}\}$. Infatti anche nell'insieme non possiamo scambiare $x,y$ altrimenti cambiamo significato a quest'ultimo.

Se aggiungiamo un elemento: $(x,y,z)=(x,(y,z))=(x,\{y,\{y,z\}\})=\{x,\{x,\{y, \{y,z\}\}\}\}$.

Questo serve per definire il concetto di ordine usando gli insiemi, una struttura dove l'ordine non conta. Abbiamo quindi rappresentato una coppia ordinata, mantenendo l'ordine, con un insieme.

Altre notazioni:

- $\mathbb{R}^n := \mathbb{R}\times \mathbb{R}^{n-1}$
- $\mathbb{R}^1 := \mathbb{R}$

## Corrispondenze
Prendiamo due insiemi $X,Y\neq \emptyset$, una corrispondenza su $X$ e $Y$ è il dato:

$$
(X,Y,\Gamma)\subset(X,Y,X\times Y)
$$

Dove:
- $X$ indica il dominio
- $Y$ indica il codominio
- $\Gamma$ è un sottoinsieme non vuoto di $X\times Y$ detto "**grafo**".

## Relazioni
Una relazione è una corrispondenza dove **dominio e codominio coincidono** quindi $(X,X,\Gamma)$, possiamo anche scrivere $(X,\Gamma)$.

Definiamo $R=(X,\Gamma)$, quindi $\Gamma$ sarà un sottoinsieme di $X^2$, presi due elementi $x,y\in X$ si dicono **in relazione** se:

$$
xRy \Leftrightarrow (x,y)\in\Gamma
$$

La parte a sinistra è una convenzione per dire che $x$ è in relazione con $y$.

### Proprietà delle Relazioni:
- **Riflessiva**: $R$ è riflessiva se $\forall x \in X$ abbiamo che $xRx$ (oppure che $\forall x \in X, (x,x) \in \Gamma$).
- **Simmetrica**: $R$ è simmetrica se $\forall x,y \in X$ se $xRy$ allora $yRx$ (oppure se $(x,y)\in\Gamma$ allora anche $(y,x)\in\Gamma$).
- **Transitiva**: $R$ è transitiva se presi 3 elementi $x,y,z\in X$, se $xRy \wedge yRz \Rightarrow xRz$.
- **Equivalenza**: $R$ è una relazione di equivalenza se è contemporaneamente Riflessiva, Simmetrica e Transitiva.

_Esempio 1 - Relazione d'uguaglianza_

Si prenda $R = (\mathbb{R}, \Delta)$ dove $\Delta = \{(x,x):x\in\mathbb{R}\}$. Al posto di scrivere $R$ scriviamo $=$.

- $=$ è riflessiva infatti $\forall x\in \mathbb{R}, x = x$
- $=$ è simmetrica infatti $\forall x,y \in \mathbb{R}, x=y\Rightarrow y=x$
- $=$ è transitiva infatti $\forall x,y,z \in \mathbb{R}, x=y\wedge y=z \Rightarrow x=z$

_Esempio 2 - Rette parallele_

$X=\{\text{rette di }\mathbb{R}^2\}$

Dati $r,r'\in X$ abbiamo che $r||r'\Leftrightarrow$ $r$ e $r'$ sono parallele.

- || è riflessiva: Ogni retta è parallela a se stessa
- || simmetrica: Se $r||r'$ allora anche $r'||r$
- || transitiva: Se $r||r'$ e $r'||r''$ allora $r||r''$

**Dimostrazione della transitività:**

> [!info] Vettori
> Quando indichiamo $(x',y')\in\mathbb{R}^2$ stiamo indicando dei vettori, se li sommiamo alla retta non cambiamo il suo coefficiente angolare e rimangono quindi parallele, infatti data l'equazione di una retta:
> 
> $$
> y = mx + q
> $$
> 
> Se sommiamo un vettore otteniamo:
> 
> $$
> y' = m(x + x') + (q + y')
> $$
> 
> Notiamo quindi che $m$, il coefficiente angolare, è rimasto invariato.

- $r || r' \Leftrightarrow r'=r+(x',y')$ con $(x',y')\in\mathbb{R}^2$.
- $r' || r'' \Leftrightarrow r''=r'+(x'',y'')$ con $(x'',y'')\in\mathbb{R}^2$

Queste due condizioni implicano che:

- $r''=r+(x',y')+(x'',y'')$ ovvero $r''=r+(x'+x'',y'+y'')$

Quindi dato che $r''$ è formata da $r$ traslata sul piano da un vettore e mantenendo quindi la stessa pendenza abbiamo che anche $r||r''$.

_Esempio 3 - Rette Ortogonali_

$X = \{\text{rette di } \mathbb{R}^2 \}$

Date $r,r'\in X$, abbiamo che $r\bot r'\Leftrightarrow r, r'$ sono ortogonali.

In questo caso:
- $\bot$ è simmetrica
- $\bot$ non è riflessiva
- $\bot$ non è transitiva

_Esempio 4 - Minore o Uguale_

$X = \mathbb{R}$, dati due elementi $x,y\in X$ abbiamo che $xRy\Leftrightarrow x\leq y$

- Riflessiva, $\forall x, x\leq x$
- Transitiva, $\forall x,y,z$ se $x\leq y \wedge y\leq z$ allora $y\leq z$
- Non è simmetrica, $2\leq3$ ma $2\not\leq3$

Però è:
- **Antisimmetrica**: $\forall x,y \in X, x\leq y \wedge y\leq x \Leftrightarrow x=y$
- **Totale**: $\forall x,y \in \mathbb{R}$ o $x\leq y$ o $y \leq x$

> [!info] Relazione Antisimmetrica
> Presi qualsiasi due elementi $x,y$ se $x$ è in relazione con $y$ e $y$ e in relazione con $x$ allora $x=y$.
> 
> $$
> \forall x,y \ \ \ xR y \wedge yR x \Leftrightarrow x=y
> $$
> 


> [!info] Relazione Totale
> Tutti gli elementi sono in relazione con almeno un altro elemento.
> 
> $$
> \forall x,y \in \mathbb{R} \ \ \ xRy \vee yRx
> $$
> 

Notiamo che l'inclusione come relazione è, come il minore o uguale, riflessiva, antisimmetrica e transitiva ma non totale.

## Studio delle Relazioni d'equivalenza
Sia $R=(X,\Gamma)$ relazione d'equivalenza e $x\in X$, poniamo $Cl(x)=\{y\in X \ \ t.c. \ \ xRy\}$.

$Cl$ è la **classe di equivalenza** di un elemento e da notare che **non può essere vuota** $Cl(x)\neq\emptyset$ infatti dato che siamo in una relazione d'equivalenza $x$ è in relazione con se stesso e quindi $x\in Cl(x)$ ovvero $xRx$.

L'elemento $x$ si chiama **rappresentante** della classe d'equivalenza, infatti si può avere che $Cl(x)=Cl(x')$ con $x\neq x'$.

### Proposizione 1
Data $R=(X,\Gamma)$ una relazione d'equivalenza abbiamo che:

1) Se $x,y\in X$, allora $Cl(x)=Cl(y)\Leftrightarrow xRy$
2) $\forall x,y \in X$ allora:
	1) o $Cl(x)=Cl(y)$
	2) oppure $Cl(x)\cap Cl(y)=\emptyset$

Quindi due classi di equivalenza di una relazione d'equivalenza **o sono uguali o sono disgiunte**, inoltre data una classe d'equivalenza $C, \forall x \in C, C=Cl(x)$ ovvero **ogni elemento è rappresentante.**

#### Dimostrazione
Ricordiamo che $Cl(x)=\{y\in X : xRy\}$.

**1° punto**: Supponiamo che $Cl(x)=Cl(y)$, dato che $R$ è **riflessiva** si ha che $y\in Cl(y)$ e quindi per l'ipotesi abbiamo che $y\in Cl(x)$ ovvero che $x$ è in relazione con $y$ $xRy$.

Adesso supponiamo che $xRy$, allora $y\in Cl(x)$. Sia $z\in Cl(y)$ si ha che $yRz$ quindi dato che $xRy \wedge yRz$ otteniamo che $xRz$ ovvero $z\in Cl(x)$ dato che la relazione è **transitiva**.

Quindi $Cl(y)\subset Cl(x)$, ma dato che $R$ è **simmetrica** e quindi $xRy\Leftrightarrow yRx$ posso scambiare $x$ e $y$ e mostrare nello stesso modo che $Cl(x)\subset Cl(y)$. Quindi siccome ho dimostrato che $Cl(y)\subset Cl(x) \wedge Cl(x)\subset Cl(y)$ allora so che $Cl(x)=Cl(y)$.

**2° punto**: Vogliamo dimostrare che $\forall x,y \in X$ o $Cl(x)=Cl(y)$ oppure sono disgiunte ovvero $Cl(x)\cap Cl(y)=\emptyset$.

Siano $x,y\in X$ se $Cl(x)\cap Cl(y)=\emptyset$ non c'è nulla da dimostrare. 

Supponiamo che $Cl(x)\cap Cl(y)\neq\emptyset$, sia $z\in Cl(x)\cap Cl(y)$ allora si ha che $xRz,yRz$ (per simmetria abbiamo che $zRy$) e quindi per transitività $xRz \wedge zRy \Rightarrow xRy$, inoltre per il punto 1 abbiamo che $Cl(x)=Cl(y)$ dato che sono in relazione.

## Insieme delle Parti
Dato $X\neq \emptyset$, consideriamo un insieme $\mathcal{P}$ di sottoinsiemi di $X$, quindi $P\in\mathcal{P}\Rightarrow P\subset X$.

Quindi $\mathcal{P}(X):=\{P:P\subset X\}$ viene chiamato **insieme delle parti**, si ha quindi che $P\in\mathcal{P}(X)\Leftrightarrow P\subset X$.

Sia $\mathcal{P}\subset\mathcal{P}(X)$ non vuoto si dice che $\mathcal{P}$ è **una partizione** di $X$ se:
1) $\forall P\in\mathcal{P} \ \ \ \ \ P\neq\emptyset$
2) $\forall P,Q\in\mathcal{P}\ \ \ \ \ P\neq Q\Rightarrow P\cap Q \neq \emptyset$
3) $\forall x\in X \ \ \ \ \ \exists !P\in \mathcal{P} \ t.c. \ x\in P$

Quindi, gli insiemi non devono essere vuoti, non ci devono essere insiemi con elementi in comune e tutti i punti del dominio devono stare in un solo insieme. L'unicità nell'ultima condizione non è obbligatoria dato che sono "coperto" dalla seconda condizione.

_Esempio_

Partizione di $X$ in 9 parti.

![[Pasted image 20240927113820.png|400]]

$$
X=\bigsqcup_{i=1}^{9} P_i
$$

### Proposizione 2
Data $R=(X,\Gamma)$ una relazione d'equivalenza, $\mathcal{P}=\{Cl(x):x\in X\}$ è una partizione di $X$.

#### Dimostrazione
Se $P\in\mathcal{P}$, allora $P$ è una classe di equivalenza di un elemento quindi $P=Cl(x)$ con $\exists x\in X$.

Dato che $R$ è riflessiva abbiamo che $x$ stesso appartiene alla classe di equivalenza e quindi $x\in P\Rightarrow P\neq \emptyset$ (Rispettiamo la prima condizione).

Se $Cl(x)\neq Cl(y)\Rightarrow Cl(x)\cap Cl(y) = \emptyset$ per via della preposizione precedente che ci dice che le intersezioni o sono uguali o sono disgiunte. (Rispettiamo anche la seconda condizione).

Come detto prima dato che $R$ è riflessiva abbiamo che sia $x\in X$ allora $x\in Cl(x)$. (Terza condizione).


> [!info] Definizione Quoziente di $X$ per $R$
> Prendiamo $X$ con relazione d'equivalenza $R$.
> Il quoziente di $X$ per $R$ indicato da:
> 
> $$
> X/R \ \ \ \text{ Oppure } \ \ \ \frac{X}{R} 
> $$
> 
> È l'insieme delle classi di equivalenza di $X$ per $R$:
> 
> $$
> X/R = \{Cl(x):x\in X\}
> $$
> 

## Sistema completo di Rappresentanti
Dati $X$ con relazione d'equivalenza $R$, un **sistema completo di rappresentanti (SCR)** è un sottoinsieme $X'\subset X$ tale che:
1) $\forall x_1',x_2'\in X'$ diversi si ha che $x_1'\not R x_2'\Rightarrow Cl(x_1')\cap Cl(x_2')=\emptyset$
2) $\forall x\in X \ \ \ \exists x'\in X'$ tale che $x\in Cl(x')$ ($x'$ è unico perché garantito dalla prima condizione)

Quindi un sistema completo di rappresentanti è un insieme di elementi scelti in modo che rappresentino esattamente una sola classe d'equivalenza.

_Esempio 1_

$X = \{r\text{ retta di } \mathbb{R}^2\}$, $R=||$ parallelismo, allora $R$ è una relazione d'equivalenza.

$X'=\{\text{rette per l'origine}\}$ è un sistema completo di rappresentanti per $R = ||$, infatti:

1) Due rette che passano per l'origine distinte non sono parallele, quindi nessun elemento di $X'$ è in relazione con un altro.
2) Data una retta $r\in X$ esiste un'unica retta $r'\in X'$ con $r' || r$, ovvero un'unica retta parallela ad $r$ passante per l'origine.

> [!info] Osservazione
> Non c'è unicità nella scelta di un SCR, questo significa che abbiamo a disposizione più scelte possibili purché rispettiamo le condizioni.

Un esempio più semplice per capire il funzionamento può essere ad esempio la divisione per 3 e i suoi resti, abbiamo 3 resti possibili:

- resto 0 dato da: {0, 3, 6, 9, 12, ...}
- resto 1 dato da: {1, 4, 7, 10, 13, ...}
- resto 2 dato da: {2, 5, 8, 11, 14, ...}

Possiamo scegliere come SCR {0, 1, 2} ma anche {9, 4, 14} e così via, l'importante è che scegliamo un solo elemento per ogni classe d'equivalenza.

_Esempio 2_

1) $X\neq \emptyset$ e dati $x,x'\in X$ si ha che $xR_1 x' \Leftrightarrow x = x'$ quindi $R_1$ è l'uguaglianza. In questo modo otteniamo che $X/R_1 = X$ quindi ogni classe d'equivalenza è un **singleton** infatti ogni elemento è uguale solo a se stesso e quindi $X$ è l'unico **SCR**
2) Se invece abbiamo $x,x' \in X$ allora $xR_2 x'$ avviene sempre, in questo caso abbiamo una sola classe di equivalenza e quindi $X/R_2$ è un **singleton**, ogni **SCR** è quindi un singleton della forma $\{x\}$ con $x\in X$.
   
   Ovvero possiamo prendere qualsiasi elemento dell'insieme come SCP dato che sono tutti in relazione fra loro.

## Applicazioni (funzioni)
Una corrispondenza $f=(A,B,\Gamma)$ con la proprietà che $\forall a\in A \ \exists !b\in B$ con $(a,b)\in\Gamma$ si dice **applicazione** e si scrive $b=f(a)$. Si scrive anche $A\xrightarrow{f} B$.

![[Pasted image 20240927143021.png|400]]

Quindi otteniamo che $\Gamma=\{(1,x),(2,y),(3,y)\}$ e ad esempio $x=f(1)$.

Il **codominio** si dice anche **insieme immagine**.

Sia $f:X\rightarrow Y$ applicazione e $X'\subset X$ allora $f(X'):=\{y\in Y : \exists x\in X'\text{ con } f(x)=y\}$, questo è **l'insieme immagine** di $X'$ per $f$, quindi $f(X')\subset Y$.

Dato invece un insieme $Y'\subset Y$, l'insieme $f^{-1}(Y')=\{x\in X: f(x)\in Y'\}$ è detto **co-immagine** o anche **immagine inversa** di $Y'$, abbiamo che $f^{-1}(Y')$ è sottoinsieme di $X$. 

In poche parole l'insieme coimmagine è l'insieme delle classi di equivalenza create dalla relazione, quindi prendendo l'esempio di prima abbiamo come insieme coimmagine: $\{\{1\},\{2,3\}\}$ dato che 1 è l'unico elemento che mappa $x$ mentre 2 e 3 sono gli elementi che mappano $y$.

Se invece noi scriviamo $f^{-1}(\{y\})$ otteniamo ${2,3}$.

### Tipi di Applicazioni

#### Funzioni Iniettive
È detta iniettiva se $x,x'\in X$ e $f(x)=f(x')$ allora $x=x'$ oppure possiamo scrivere anche $\forall y\in Y$ abbiamo $f^{-1}(\{y\})=\emptyset \vee \text{singleton}$.

#### Funzioni Suriettive
Si dice che $f$ è suriettiva se $f(X)=Y$ oppure $\forall y\in Y, \exists x\in X$ tale che $f(x)=y$, quindi ogni valore del codominio deve essere raggiunto da almeno un valore del dominio.

Si può anche scrivere $\forall y\in Y, f^{-1}(\{y\})\neq \emptyset$.

#### Funzioni Biettive
Una funzione $f:X\rightarrow Y$ è biiettiva se è al tempo stesso suriettiva e iniettiva.

Quindi $f$ biiettva se e solo se $\forall y\in Y, f^{-1}(\{y\})$ è un singleton, ovvero ogni elemento del codominio ha un unico elemento del dominio associato. Infatti la suriettività toglie una possibilità all'esito della condizione di initetività ($\emptyset$) lasciando soltanto il caso singleton.

### Operazioni sulle Funzioni
Prima di vedere le operazioni, vediamo cos'è un diagramma.

> [!info] Definizione Diagramma
> È una collezione di insiemi non vuoti collegati da applicazioni
> _Esempi_
>
>![[Pasted image 20241002110508.png|400]]
>
>Noi vedremo diagrammi del tipo:
>
>![[Pasted image 20241002110608.png|400]]
>

#### Composizione

![[Pasted image 20241002110744.png|400]]

Si definisce **funzione composta** $X \xrightarrow{g \circ f} Z$.

> [!info] Notazioni
> Nel diagramma vediamo prima $f$ e poi $g$ ma nella funzione composta scriviamo prima $g$ e poi $f$ questo perché si calcola prima il risultato di $f$ e si "fornisce" a $g$ ovvero $g(f(x))$. Si legge _"g composta f"_.

_Con tre funzioni:_

$$
X\xrightarrow{f}Y\xrightarrow{g}Z\xrightarrow{h}T
$$
Otteniamo:

$$
(h\circ g\circ f)(x)=h(g(f(x)))
$$

Per le funzioni composte vale **la proprietà associativa**:

$$
(h\circ g)\circ f = h \circ (g \circ f)
$$

##### Proposizione
Dato il diagramma $X \rightleftarrows Y$ con $f:X\rightarrow Y$ e $g:Y\rightarrow X$.

Diciamo che $f$ è biiettiva $\Leftrightarrow \exists g:Y\rightarrow X, t.c. \  f\circ g\overset{ ② }=id_{y}, g\circ f\overset{ ① }=id_{x}$.
Quindi $f$ è biiettiva se e solo se esiste una funzione $g$ che va da $Y$ ad $X$ tale che $f$ composta $g$ restituisca $y$ (parto da $Y$ con $g$ e ritorno in $Y$ con $f$) e tale che $g$ composta $f$ restituisca $x$ (parto da $X$ con $f$ e ritorno in $X$ con $g$).

$g$ è detta **funzione inversa** di $f$, se esiste è **unica**.

_Dimostrazione_

Partiamo dalla condizione che $f$ è biiettiva, allora $\forall y \in Y \  \exists !  \ x\in X \ t.c. \ f(x)=y$.

Poniamo $g(y)=x$.

Se $x\in X$, $g(f(x))=g(y)=x$ e $x$ è l'unico elemento t.c. $f(x)=y$ allora $g(x)=x\Rightarrow g\circ f=id_{x}$ (①), analogamente possiamo ottenere $f \circ g = id_{y}$ ovvero ②.

---

Partiamo dalla condizione a destra quindi abbiamo il diagramma $X \rightleftarrows Y$ con $f:X\rightarrow Y$ e $g:Y\rightarrow X$ e $f\circ g \overset{①}= id_{y}$ e $g \circ f\overset{②}=id_{x}$.

Possiamo mostrare allo stesso modo sia $f$ che $g$ suriettive e iniettive, mostriamo $g$:

_Suriettiva:_

Sia $x\in X$ poniamo $y=f(x)$, quindi $g(y)=g(f(x))=(g\circ f)(x)=x$ per via di ② ne deduciamo che $g^{-1}(\{ x \})\neq \emptyset$ e quindi $g$ è _suriettiva_.

_Iniettiva:_

Siano $y,y'\in Y$ t.c. $g(y)=g(y')=x$ allora applicando $f$ ottengo:

$$
\underbrace{ f(g(y)) }_{ \underbrace{ (f\circ g)(y) }_{ \text{Per ①, = y} } }=\underbrace{ f(g(y')) }_{ \underbrace{ (f\circ g)(y') }_{ \text{Per ①, = y'} } }=\underbrace{ f(x) }_{ y }
$$

Quindi $y=y'$, $g$ è _iniettiva_.

Se $g$ è sia iniettiva che suriettiva allora è **biiettiva**.

### Teorema Struttura Applicazioni
$X\xrightarrow{f}Y$, abbiamo come obiettivo quello di costruire una relazione d'equivalenza $\sim$ su $X$.

Si pone $x,x'\in X, x\sim x' \Leftrightarrow f(x)=f(x')$ allora $\sim$ è una relazione d'equivalenza:
- $x\sim x: f(x) = f(x)$ | **Riflessiva**
- $x\sim x' \Leftrightarrow f(x)=f(x')\Leftrightarrow f(x')= f(x)\Leftrightarrow x'\sim x$ | **Simmetrica**
- $x\sim x', x'\sim x''\Leftrightarrow f(x)=f(x'),f(x')=f(x'')\Rightarrow f(x)=f(x'')\Rightarrow x\sim x''$ | **Transitiva**

Consideriamo l'insieme quoziente $X \backslash \sim$ allora:

$$
X'\in X\backslash \sim \ \Leftrightarrow X'\subset X \ e \ \exists y\in Y:X'=f^{-1}(\{ y \})
$$

![[Pasted image 20241002121311.png]]

1) $\forall x\in X \ \ \exists X'\in X\backslash \sim \ t.c. \ x\in X'$ Ogni elemento fa parte di una classe di equivalenza.
2) $X_{1}', X_{2}'\in X\backslash \sim$ e $X_{1}'\neq X_{2}'\Rightarrow X_{1}'\cap X_{2}'=\emptyset$ Le classi di equivalenza non hanno elementi in comune.
3) Se $X'\in X\backslash \sim$ allora $f|_{X'}$ è costante ovvero l'immagine è un singleton, questo perché elementi di X in relazione (fanno parte di un X') hanno la stessa immagine.

Adesso, costruiamo a partire da $X\xrightarrow{f} Y$ un'applicazione $\phi=X\backslash \sim \rightarrow f(X)\subset Y$.

Sia $X'\in X\backslash \sim$ allora $X'=[x] \ \exists x\in X$.

Si pone $y=f(x)\in Y$ allora definiamo $\phi(X')=y$ **non deve dipendere dal rappresentante (ben definita):**

$$
C=[x]=[x'] \ \ f(x)=f(x')
$$

$\phi$ è biiettiva e permette di calcolare $f$ fattorizzandola nel diagramma:

![[Pasted image 20241002123137.png]]

** f(x) è un sottoinsieme di Y

> [!info]  Biiettiva
> Per vedere che $\phi$ è biiettiva poniamo per $y\in f(X), \psi(y)=\{ x\in X:f(x)=y \}$ tale insieme è $\neq \emptyset$ quindi $f$ è suriettiva nella sua immagine. $\psi(y)=[x]$ con $f(x)=y$ (dato che tutti gli elementi di $X$ in relazione hanno stessa immagine) di modo che $\psi=\phi^{-1}$.

1) $\phi$ è ben definita. Questo perché se $X'=[x]=[x']$ si ha $f(x)=f(x')=y\in f(X), f(X')$ è un singleton di $f(X)$
2) $\phi$ è biiettiva, $\phi^{-1}(y)=f^{-1}(\{ y \})\in X\backslash \sim$, $f^{-1}(\{ y \})$ mi restituisce tutti gli elementi di $X$ che hanno come immagine $y$ 
3) $f=i\circ \phi \circ \pi$. Poniamo $y=f(x)$ con $x\in X$. Allora $\pi(x)=f^{-1}(\{ y \})$. Quindi $(\phi\circ\pi)(x)=y$ e $(i\circ\phi\circ\pi)(x)=y=f(x)$.

_Esempio_

Abbiamo $X=\mathbb{Z}, b\in\mathbb{N}^*$ e $Y=\{ 0,\dots,b-1 \}$, ricordiamo che $\mathbb{N}^*=\mathbb{N}\backslash \{ 0 \}$.

**Algoritmo della divisione euclidea per b**

$\forall x\in\underbrace{ \mathbb{Z} }_{ X } \ \exists!(q,r)\in\mathbb{Z}\times \underbrace{ \{ 0,\dots,b-1 \} }_{ Y }$ tale che $x=qb+r$ dove:
- $r$ resto
- $q$ quoziente

Stiamo dicendo quindi che per ogni numero appartenente a Z esiste una sola coppia appartenente al prodotto cartesiano fra Z e i possibili resti (da 0 a b-1). Infatti le coppie sono composte da un numero q quoziente e il resto associato.

Definiamo $f:X\rightarrow Y$ ponendo $f(x):=r$. Questa è ben definita e si chiama **riduzione modulo b**, è un'applicazione suriettiva: $f(X)=Y$.
Ad esempio se $b=2$ allora $f(5)=1, f(4)=0$.

Allora la relazione d'equivalenza associata, che scriviamo come $\equiv$ e la chiamiamo **congruenza modulo b**.

Se due interi $x,x'$ sono in relazione allora si scrive $x\equiv x'(mod \ b)$ e si legge _x congruente a x' modulo b_.

$$
X'\in X\backslash\equiv \ \Leftrightarrow \exists r\in Y,\forall x\in X',x=qb+r
$$
Quindi tutte le $x$ di $X'$ devono avere lo stesso resto.
Inoltre l'insieme $Y\subset\mathbb{Z}$ è in questo caso un **SCR** dato che:
1) $f$ suriettiva e quindi $\forall r\in Y, \exists x\in X$ t.c. $x\equiv r(mod\ b)$
2) Presi $r,r'\in Y$ con $r\neq r'$ si ha che $r\not\equiv r'(mod \ b)$ infatti supponiamo per assurdo che $r\equiv r'(mod\ b)$:

$$
\begin{cases}
r=qb+\tilde{r} \\
r'=q'b+\tilde{r}
\end{cases}
$$

Quindi $r-r'=(q-q')\cdot b$

$r-r'=b \cdot k\ (\underbrace{ k\in\mathbb{Z}\backslash\{ 0 \} }_{ \text{perché } r\neq r'}),\ k>0\Rightarrow r=r'+bk\geq r'+b$ ma $r\geq r'+b\geq b$ è una **contraddizione** dato che i resti vanno da 0 a $b-1$.

$\phi$ è la biiezione tra $X\backslash\equiv$ e $Y$ che manda ogni classe $X'$ nell'unico $r\in Y$ t.c. $\forall x\in X',f(x)=r$, in pratica $r$ è il resto in $Y$ della divisione euclidea di $x$ per $b$ e non cambia al variare di $x$ in $X'$, ovvero tutti gli elementi presenti in $X'$ hanno lo stesso resto.

$$
\forall X'\in X\backslash\equiv\text{ si scrive } X'=\overline{x}=\overline{x'}=\overline{r} \ \forall x,x'\in X
$$

e se

$$
\phi(X')=r\in Y=f(X)=f(Y)
$$


> [!NOTE] Congettura di Collatz
> Spiegato a lezione non so di preciso perché, però è simpatico [wikipedia](https://it.wikipedia.org/wiki/Congettura_di_Collatz)

_Esercizio_

> Studiare l'applicazione $f:\mathbb{Z}\rightarrow\mathbb{Z}$ che ad $x\in\mathbb{Z}$ associa $f(x)=ax+1$. Al variare del parametro $a\in\mathbb{Z}$ dire quando la funzione è suriettiva e iniettiva.

- Se $a=0$ allora $\forall x\in\mathbb{Z}$ abbiamo che $f(x)=1$ e quindi $f$ non è ne iniettiva ne suriettiva, infatti a $x$ diverse abbiamo immagini uguali (iniettività) e non tutto il codominio ha controimmagine (suriettività).

- Se $a=1$, otteniamo che $f(x)=x+1$, ha anche una formula inversa $g(y)=y-1$ ed è quindi biiettiva, infatti:

$(f\circ g)(y)=f(y-1)=(y-1)+1=y\Rightarrow f\circ g=Id_{\mathbb{Z}}$ e,

$(g\circ f)(x)=g(x+1)=(x+1)-1=x\Rightarrow g\circ f=Id_{\mathbb{Z}}$

- Se $a=-1$ con ragionamenti analoghi troviamo lo stesso risultato ovvero che $f$ è biiettiva

- Se $a\not\in \{ 0 \}$ allora $f$ è iniettiva, infatti:
  $f(n_{1})=f(n_{2})\Leftrightarrow an_{1}+1=an_{2}+1\Leftrightarrow \underbrace{ a(n_{1}-n_{2})=0\Leftrightarrow n_{1}-n_{2}=0 }_{ \text{Ricordiamo che a non può essere nullo} }\Leftrightarrow n_{1}=n_{2}$
- Se $a\not\in \{ -1,0,1 \}$ $f$ non è suriettiva, infatti:

$f^{-1}(\{ a \})=\emptyset$ infatti qualsiasi valore prendo per $a$ è impossibile che io copra tutto il codominio o comunque è impossibile che ci trovo $a$ stesso.

Infatti se $f$ fosse suriettiva avremmo $\exists x\in \mathbb{Z} \ t.c.\ f(x)=a$ e quindi $f(x)=ax+1=a$ che per risolverla $a(x-1)=-1\rightarrow a(1-x)=1$.

Per risolvere questa equazione in $\mathbb{Z}$ abbiamo solo due casi o $1\cdot 1$ oppure $-1\cdot (-1)$ e questo implica che $a\in \{ -1,1 \}$ ovvero un'ipotesi che abbiamo escluso all'inizio.

_Esercizio preparazione al 21_

Sia $\mathcal{P}=\{ X_{1},X_{2} \}$ una partizione di $X\neq \emptyset$ e $\mathcal{Q}=\{ Y_{1},Y_{2},Y_{3} \}$ una partizione di $Y\neq \emptyset$. Graficamente abbiamo una situazione come questa: 

![[Pasted image 20241004113428.png|400]]

Quindi per la definizione di partizione abbiamo che $X$ ha sicuramente 2 elementi e $Y$ ne ha sicuramente 3.

**Obiettivo**: Mostrare che $\mathcal{R}=\{ X_{i}\times Y_{j}:i=1,2;j=1,2,3 \}$ è una partizione di $X\times Y$.

Proviamo prima di tutto a rappresentare in modo grafico cosa vogliamo dimostrare:

![[Pasted image 20241004113745.png|400]]

Notiamo quindi che effettivamente è una partizione, adesso dobbiamo scriverlo in linguaggio matematico.

Nel nostro caso possiamo scrivere che $X= \underset{i\in \{ 1,2 \}}\bigsqcup X_{i}$ e $Y=\underset{i\in \{ 1,2,3 \}}\bigsqcup Y_{i}$ con $\{ X_{1},X_{2},Y_{1},Y_{2},Y_{3} \}\cap \{ \emptyset \}=\emptyset$, ovvero dove nessun di questi insiemi è vuoto, inoltre poniamo $I=\{ 1,2 \}, J=\{ 1,2,3 \}$.

Allora $\mathcal{R}=\{ X'\times Y':X'\in\mathcal{P},Y'\in\mathcal{Q} \}$=$\{ X_{1}\times Y_{1},X_{2}\times Y_{1},X_{1}\times Y_{2},X_{2}\times Y_{2},X_{3}\times Y_{1},X_{3}\times Y_{2} \}$.

Dobbiamo quindi dimostrare 3 punti:

1) $\forall(i,j)\in I\times J, X_{i}\times X_{j}\neq \emptyset$
   
   Ovvero nessuna partizione deve essere vuota, per dimostrare questo sappiamo che $X_{i}$ ed $Y_{j}$ sono partizioni rispettivamente di $\mathcal{P}$ e $\mathcal{Q}$ quindi non possono essere vuote e questo significa che non lo è nemmeno il loro prodotto cartesiano, possiamo quindi dire $(x,y)\in X_{i}\times Y_{j}\Rightarrow X_{i}\times Y_{j}\neq \emptyset$.
   
---

2) $\forall(x,y)\in X\times Y \ \exists(i,j) \ t.c. \ (x,y)\in X_{i}\times Y_{j}$
   
   Quindi che ogni elemento del prodotto cartesiano è all'interno di una partizione.
   
   Dati $(x,y)\in X\times Y$ dato che $\mathcal{P}$ è una partizione allora l'elemento $x$ farà sicuramente parte di una partizione di $X$: $x\in X_{i} \ \exists i\in I$, inoltre per lo stesso ragionamento dato che $\mathcal{Q}$ è una partizione allora anche $y$ farà sicuramente parte di una partizione di $Y:y\in Y_{j} \ \exists j\in J$.
   
   Mettendo insieme le conclusioni possiamo dire che $(x,y)\in X_i\times Y_{j}$, ovvero che qualsiasi coppia $(x,y)$ del prodotto cartesiano farà sicuramente parte di una partizione.
   
---

3) Se $(i,j)\neq(i',j')$ allora $X_{i}\times Y_{j}\cap X_{i'}\times Y_{j'}=\emptyset$
   
	Questo significa che due partizioni diverse non hanno elementi in comune.
	
	$(i,j)\neq(i',j')\Leftrightarrow i\neq i'\text{ oppure } j\neq j'$, vediamo entrambi i casi:
	
	Se $i\neq i'$ allora $X_{i}\cap X_{i'}=\emptyset$ dato che $\mathcal{P}$ è una partizione
	
	Calcoliamo allora $(X_{i}\times Y_{j})\cap(X_{i'}\times Y_{j'})$=
	
	$$
	\{ (x,y):x\in \underbrace{ X_{i}\cap X_{i'} }_{ =\emptyset }\ \ ; \ \ y\in Y_{j}\cap Y_{j'}\} = \emptyset
	$$
	
	Se invece $j\neq j'$ allora $Y_{j}\cap Y_{j'}=\emptyset$ e questo, per lo stesso ragionamento visto prima implica che $(X_{i}\times Y_{j})\cap(X_{i'}\times Y_{j'})=\emptyset$.

_Esercizio 12_

> Sia $f:\{ 1,\dots,n \}\rightarrow \{ 1,\dots,m \}$ un'applicazione. Si provi che se $n>m$ allora $f$ non è iniettiva e se $n>m$ allora $f$ non è suriettiva.

Iniziamo rappresentando graficamente il nostro problema per avere più chiarezza.

In questo caso $n>m$ è impossibile che $f$ sia iniettiva dato che tutti gli elementi del dominio devono avere un'immagine nel codominio.

![[Pasted image 20241004124447.png|300]]

In questo caso invece $m>n$ e non possiamo avere $f$ suriettiva dato che un elemento del dominio può avere una sola immagine nel codominio e quindi alcuni elementi del codominio rimangono "scoperti" cioè senza controimmagine.

![[Pasted image 20241004124716.png|300]]

--- 

Iniziamo mostrando che se $n>m\geq 1$ allora $f$ non è iniettiva $\forall f$ applicazione.

Definiamo $E_{n}=\{ 1,\dots,n \}$, abbiamo bisogno delle seguenti proprietà:
1) $E_{n}=E_{n-1}\bigsqcup\{ n \}$.
2) $\forall m_{0}\in E_{m},\exists \ \ \  E_{m}\backslash\{ m_{0} \}\underset{\cong}{\xrightarrow{f}}E_{m-1}$ 
3) Sia $X\xrightarrow{h}Y$ iniettiva allora il grafo $\Gamma$ di $h$ ha le proprietà che $\forall y\in Y,\text{ se }\exists x\in X\text{ con }(x,y)\in\Gamma$ allora $x$ è unico.

Quindi:

1) Per questa proprietà non abbiamo nulla da dimostrare infatti dato un insieme del tipo definito prima $E_{n}$ questo possiamo scriverlo come l'unione fra se stesso meno un elemento e l'insieme che contiene l'elemento mancante.

2) L'applicazione $E_{m}\backslash\{ m_{0} \}\xrightarrow{f}E_{m-1}$ definita da:
   
$$
f(x)=
\begin{cases}
x\ \text{ se  }\  x<m_{0} \\
x-1 \ \text{ se }\  x> m_{0}
\end{cases}
$$
   
   è invertibile, infatti:
   
$$
f^{-1}(y)=
\begin{cases}
y\ \text{ se  }\  y<m_{0} \\ \\
y+1 \ \text{ se }\  y\geq m_{0}
\end{cases}
$$
   
   _Esempi_
   
   ![[Pasted image 20241004131030.png|400]]
   
   Quindi esiste una funzione biiettiva definita come prima.

3) Abbiamo $h$ iniettiva $\Leftrightarrow \forall y\in Y, h^{-1}(y)=\emptyset\text{ oppure singleton}$. Si ha che $\exists x\in X\ t.c.\ h(x)=y\Leftrightarrow h^{-1}(y)\neq \emptyset$ dato che nel grafo $\Gamma$ ci sono solo $(x,y) \ t.c.\ \exists x\in X$ quindi la possibilità del vuoto è esclusa e quindi $x$ è sicuramente unico.
   
   Allora in questo caso $(x,y)\in\Gamma\Leftrightarrow f(x)=y\Leftrightarrow\{ x \}=f^{-1}(y)$.

---

Adesso usiamo queste 3 proprietà per dimostrare il punto principale dell'esercizio.

Se $m=1$ non ho nulla da dimostrare, infatti sto prendendo come dominio un insieme da almeno due elementi $(n>m)$ e come codominio un insieme con un solo elemento, l'applicazione non può essere iniettiva dato che tutti gli elementi hanno come immagine lo stesso elemento (Come abbiamo mostrato con il disegno sopra).

Adesso per dimostrarlo in generale, supponiamo per assurdo che l'enunciato sia falso.

Allora $\exists n_{o},m\text{ con } n_{0}>m>1 \ e \ g:E_{n_{0}}\rightarrow E_{m}$ iniettiva, questi $n_{0}$ li possiamo "collezionare" e quindi ne esiste uno che è il più piccolo possibile, focalizziamoci su questo elemento, dato che la nostra ipotesi dovrebbe funzionare sempre.

Quindi adesso consideriamo $n_{0}$ come l'elemento più piccolo possibile adesso possiamo porre $m_{0}:=g(n_{0})\in E_{m}$

Allora per la seconda proprietà sappiamo che $\exists E_{m}\backslash\{ m_{0} \}\underset{\cong}{\xrightarrow{f}}E_{m-1}$, quindi abbiamo $g$ iniettiva e $f$ biiettiva.

Adesso dato che $n_{0}>m$ allora $n_{0}-1>m-1$ e dato che $m>1$ possiamo supporre $m\geq 1$, allora:

$$
E_{n_{0}-1}\underbrace{ \xrightarrow{g|_{E_{n_{0}-1}}}E_{m}\backslash\{ m_{0} \}\xrightarrow{f} }_{ g'=f\circ g|_{E_{n_{0}-1}} }E_{m-1}
$$

$g'$ non è iniettiva perché va da $E_{n_{0}-1}$ a $E_{m-1}$, e noi avevamo affermato che $n_{0}$ era il più piccolo valore per cui esisteva una funzione iniettiva.

--- 

Per la proprietà 3 sappiamo che sia $\Gamma'$ il grafo di $g'$ e $g'$ non è iniettiva allora $\exists y\in Y=E_{m-1}$ e $x_{1},x_{2}\in X=E_{n_{0}-1}\ x_{1}\neq x_{2}\ t.c. \ (x_{1},y),(x_{2},y)\in\Gamma'$, ovvero che esistono due valori del dominio diversi tali che hanno la stessa immagine.

Questo implica che $g|_{E_{n_{0}-1}}$ non è iniettiva.

_Da capire meglio:_

Infatti $(x_{1},f^{-1}(y)),(x_{2},f^{-1}(y))$ appartengono al suo grafo $\tilde{\Gamma}$ , ma il grafo $\Gamma$ di $g$ è dato da $\tilde{\Gamma}\bigsqcup\{ (n_{0},m_{0}) \}$ che contiene sempre i due elementi visti prima, per cui $g$ non è iniettiva -> **contraddizione**.

# Anelli
Possiamo prendere come esempio di anello l'insieme dei numeri relativi $\mathbb{Z}$.


> [!info] Definizione Anello
> Un **anello commutativo unitario** è una sestupla del tipo $(A,+,-,\cdot,0_{A},1_{A})$.

Prendendo come esempio $\mathbb{Z}$ abbiamo che:
- $A$ è un insieme $\neq\emptyset$
- $+,\cdot$ sono applicazioni $A\times A\rightarrow A$ dette _somma e moltiplicazione_
- $-$ è un'applicazione $A\rightarrow A$, e si chiama _opposto_; abbiamo che $a+(-a)=0$
- $0_{A}$ è l'elemento neutro per l'operazione $+$
- $1_{A}$ è l'elemento neutro per l'operazione $\cdot$

Nel caso della moltiplicazione abbiamo che:

$$
a\cdot b=\begin{cases}
\text{se } b=0\rightarrow_{0}\\
\text{se } b>0\rightarrow \underbrace{ a+\dots+a }_{ b\text{ volte} }\\
\text{se } b<0 \rightarrow(-a)\cdot(-b)\text{ che è ben definita dall'opposto}
\end{cases}
$$


Deve soddisfare varie proprietà e le dividiamo in due categorie:

1) **Proprietà Commutativa per la Somma**: $\forall a,b\in A,a+b=b+a$
2) **Associatività dell'addizione**: $\forall a,b,c\in A,(a+b)+c=a+(b+c)$
3) **Elemento Neutro addizione**: $\exists 0_{A}\in A \ t.c.\ \forall a\in A,a+0_{A}=0_{A}+a=a$
4) **Elementro Opposto**: $\forall a\in A \ \ \exists(-a) \ t.c.\ a+(-a)=0_{A}$

Queste 4 proprietà ci spiegano che $(A,+,-,0_{A})$ è un **gruppo commutativo abeliano**.

5) **Commutatività moltiplicazione**: $\forall a,b\in A \ \ a\cdot b=b\cdot a$, grazie a questa si dice che l'anello è **commutativo**
6) **Associtatività moltiplicazione**: $\forall a,b,c\in A \ \ (a\cdot b)\cdot c=a\cdot(b\cdot c)$, A è **associativo**
7) **Elemento neutro moltiplicazione**: $\exists \ 1_{A}\in A \ t.c.\ \forall a\in A,a\cdot 1_{A}=1_{A}\cdot a=a$, si dice che A è **unitario**
8) **Proprietà distributiva**: $\forall a,b,c\in A, a\cdot(b+c)=a\cdot b+a\cdot c$

$(\mathbb{Z},+,\cdot)$ è un **anello commutativo unitario**. Questo perché l'addizione lo è sempre, quindi dobbiamo guardare se valgono le operazioni per la moltiplicazione.

> [!info] Elementi Neutri
> Se gli elementi neutri di moltiplicazione e addizione coincidono allora l'anello è un singleton 0. Se $1_{A}=0_{A}$ allora $A=\{ 0 \}$.

Esistono anche altre due proprietà che valgono per $\mathbb{Z}$:

**Proprietà di Tricotomia**:

Esiste un sottoinsieme $\mathbb{N}^*\subset\mathbb{Z}$ che permette di definire una relazione su $\mathbb{Z}$:

$$
a>b\Leftrightarrow a-b\in\mathbb{N}^*
$$

Infatti:

$$
\forall a\in\mathbb{Z} \text{ si ha } \begin{cases}
a\in N^* \text{ oppure}
\\ a=0 \text{ oppure } \\
-a\in\mathbb{N}^*
\end{cases}
$$

Quindi: _Un intero può essere soltanto positivo, negativo o nullo._

**Assioma di buon ordinamento**:

Ogni sottoinsieme $E\subset\mathbb{N}^*$ non vuoto possiede un più piccolo elemento che per $< \text{ vale la proposizione } \exists c\in E\ t.c.\ \forall e\in E\backslash\{ c \}$ si ha $e>c$.

_Un anello che rispetta buon ordinamento e triconomia è "essenzialmente $\mathbb{Z}$"_.

Se $a<b,c<d$ allora $a+c<b+d$ e $-a>-b$, le operazioni $+,>$ sono compatibili e in modo simile c'è compatibilità anche tra $\cdot,>$.

**Legge di Cancellazione in $\mathbb{Z}$**:

Se $ab=ac$ con $a\neq 0$ allora $b=c$ infatti si può supporre che $a>0$, nel caso $a=1$ è chiaro mentre prendiamo $(a-1)$ e vediamo per induzione:

$$
\begin{align*}
&(a-1)\cdot b=(a-1)\cdot c\\ 
&\text{Se } b\neq c \text{ e } b>c \Rightarrow (a-1)\cdot b+b>(a-1)\cdot c+c \\
&\text{E questo significa che } \underbrace{ (a-1+1)\cdot b }_{ ab }>\underbrace{ (a-1+1)\cdot c }_{ ac }
\end{align*}
$$

Abbiamo aggiunto $+b,+c$ anche se valori diversi per l'ipotesi perché abbiamo portato l'espressione da $=$ a $>$ e dato che abbiamo detto $b>c$ questo non altera il valore dell'espressione.

Dato che avevamo supposto $ab=ac$ ma abbiamo ottenuto una contraddizione ovvero $ab>ac$ con $b\neq c$, per tricotomia deve essere necessariamente vero che $b=c$.

**Elementi Invertivibili:**

$A$ è un anello commutativo unitario dove $1_{A}\neq 0_{A}$.

_Definizione_

$a\in A \ t.c. \ \exists b\in A : ab=ba=1_{A}$, è detto **elemento invertibile** (si dice che $b$ è l'inverso di $a$ e si scrive $b=a^{-1}$)

_Esempio_

$1_{A}$ è invertibile con inverso $1_{A}^{-1}=1_{A}$

_Esercizio_

Se $a$ è invertibile allora $a^{-1}$ è unicamente determinato.

$$
\begin{align*}
&a\cdot b=a\cdot b'=1\text{ con } b,b'\in A \\
&\text{allora} \\
&(a\cdot b)\cdot b'=1_{A}\cdot b'=b' \ \ e \ \ (a\cdot b')\cdot b=1_{A}\cdot b=b \\
\\
&\underbrace{ (a\cdot b)\cdot b' }_{ (a\cdot b)\cdot b' }=a(b\cdot b')\underbrace{ = }_{ = }a\cdot(b'\cdot b)=\underbrace{ (a\cdot b')\cdot b }_{ (a\cdot b')\cdot b }
\end{align*}
$$

Quindi abbiamo ottenuto che le due proposizioni iniziali sono uguali e quindi $b=b'$ e l'inverso $a^{-1}$ di $a$ è ben determinato.


**Altri Esempi**

$A$ è sempre anello.

---

$\forall a\in A,a\cdot 0_{A}=0_{A}$

Allora

$$
\begin{align*}
a\cdot 0_{A}=a\cdot(0_{A}+(-0_{A}))=a\cdot0_{A}+a\cdot(-0_{A})&=a\cdot 0_{A}+(-a)\cdot 0_{A} \\
&=a\cdot 0_{A}+(-a\cdot 0_{A}) \\
&=\underbrace{ a\cdot 0_{A}+(-(a\cdot 0_{A})) }_{ \text{Somma fra opposti} } = 0_{A}
\end{align*}
$$

---

Supponiamo che $0_{A}=1_{A}$ mostriamo che $\forall a\in A$ si ha che $a=0_{A}$ ovvero $A=\{ 0_{A} \}$.

$$
a\in A: \ 1_{A}=0_{A}\Rightarrow \underbrace{ a\cdot 1_{A} }_{ a }=a\cdot 0_{A}\overset{(1)}=0_{A} \text{ Quindi } \forall a\in A:a= 0_{A}
$$

---

Se $1_{A}\neq 0_{A}$ allora $0_{A}\not\in A^X$ (non invertibile). Infatti supponiamo per assurdo che sia invertibile allora $\exists x\in A^X \ t.c\ 1_{A}=x\cdot 0_{A}\text{ Ma sappiamo che è}\overset{(1)}=0_{A}$ ed è quindi una contraddizione.

**Nota:**

Si pone $A^X=\{ a\in A \ t.c.\ \text{a è invertibile} \}$.

> [!info] Elementi neutri pt2
> Anello con $0_{A}\neq 1_{A}$ significa che $0_{A}$ non è invertibile, questa proprietà infatti vale solo in anelli $=\{ 0 \}$ ovvero quando $0_{A}=1_{A}$.

_Esercizio - Unico elemento neutro ad ogni anello commutativo unitario_

Siano $u,u'$ due elementi neutri quindi significa che $\forall a\in A$ otteniamo:

$$
au=ua=a \ \ e \ \ au'=u'a=a
$$

Se prendiamo $a=u$? Otteniamo $uu'=u'u=u$

Se prendiamo $a=u'$? Otteniamo $u'u=uu'=u'$

Quindi notiamo che $u=u'$ e quindi l'elemento neutro per la moltiplicazione è unicamente determinato.

## Relazione di Divisibilità

Introduciamo la relazione che dati $a,b\in A$   $a|b\Leftrightarrow \exists c\in A \ t.c. \ b=a\cdot c$, ovvero "$a$ divide $b$" se e solo se esiste un certo $c$ in $A$ tale che possiamo scrivere $b=a\cdot c$. Ad esempio $2|6$ infatti $6=2\cdot 3$

Innanzitutto notiamo che questa è una relazione **riflessiva** infatti $\forall a\in A, a=a\cdot 1_{A}$ ovvero $a$ divide sempre $a$.

Inoltre è anche **transitiva** infatti supponiamo di avere $a,b,c\in A$ e supponiamo che $a|b$ e $b|c$:

$$
\begin{align*}
&a|b\Leftrightarrow b =a\cdot a' \ \ \exists a'\in A \\
&b|c\Leftrightarrow c=b\cdot b' \ \ \exists b'\in A \\
&\text{Facendo una sostituzione notiamo che} \\
&c=a\cdot \underbrace{ (a'\cdot b') }_{ a'' }=a\cdot a''
\end{align*}
$$

Abbiamo mostrato che anche $c$ quindi è divisibile per $a$, infatti possiamo scriverlo come $a$ moltiplicato per un altro valore $a''$ e quindi $a|c$.

**Non è simmetrica né antisimmetrica**.

### Altre proprietà della divisibilità

Se $a|b$ e $a|c$ allora $a|b+c$ (compatibilità con l'addizione), vediamo perché:

$$
\begin{align*}
&a|b \Leftrightarrow \exists a'\in A \text{ t.c. } b=aa' \\
&a|c \Leftrightarrow \exists a''\in A \text{ t.c. } c=aa'' \\
 \\
&\text{Quindi}\\
&b+c=aa'+aa''=a\underbrace{ (a'+a'') }_{ a''' }=aa''' \Leftrightarrow a|b+c
\end{align*}
$$

Più generalmente se $\alpha,\beta\in A$ e $a|b,a|c\Leftrightarrow a|\alpha b+\beta c$. Infatti facendo sempre lo stesso ragionamento di prima otteniamo tramite le sostituzioni otteniamo che:

$$
\alpha b+\beta c=\alpha aa'+\beta aa''=a\underbrace{ (\alpha a'+\beta a'') }_{ a''' }=aa'''
$$

E quindi, come prima, $a|\alpha b+\beta c$.

---

In $\mathbb{Z}$ la relazione di divisibilità è "quasi antisimmetrica", ovvero:

$$
\begin{align*}
&\text{Prendiamo } a,b\in \mathbb{Z} \text{ t.c. } a|b \text{ e } b|a \\
&a|b \text{ e } b|a \overset{?}{\Rightarrow} \exists c\in \mathbb{Z}^X \text{ t.c. } a=bc (\text{Ovvero } a\in \{ b,-b \} \text{ oppure } \{ a,-a \}=\{ b,-b \}) \\
\\
&(\text{nota dopo})\text{Possiamo supporre che } a,b\neq 0 \text{ e quindi:} \\
&a|b,b|a \Leftrightarrow b=aa',a=bb' \ \exists a',b'\in \mathbb{Z} \\
 \\
&\text{Adesso facendo le sostituzioni:} \\
&\cancel b=\cancel bb'a'\Rightarrow 1=a'b'\underbrace{ \Rightarrow a'b'\in \{ 1,-1 \} }_{ \text{Questo perchè a',b' sono invertibili} } \\
 \\
&\text{Questo significa che i due numeri devono essere o uguali o opposti, dato che } a'b'\in \{ 1,-1 \}\\
\end{align*}
$$

Nota, possiamo supporre che i due numeri sono non nulli, questo perché 0 non divide mai un altro elemento non nullo e quindi se uno dei due fosse 0, questo significa che lo sarebbe anche l'altro.

## Elementi Irriducibili e Primi

### Numero irriducibile

_Definizione:_ $a\in A\backslash A^X$ con $a\neq 0$, questo è detto irriducibile se $\forall b,c\in A$ con $a=bc$ allora si che o $b\in A^X$ oppure $c\in A^X$ .

_Esempi con_ $A=\mathbb{Z}$, ricordiamo inoltre che $\mathbb{Z}^X=\{ -1,1 \}$

$$
\begin{align*}
&12=4\cdot 3 \text{ ma } 4,3\not\in \mathbb{Z}^X \Rightarrow \text{12 non è irriducibile} \\
&7 =1\cdot 7 \ \ \ 1\in \mathbb{Z}^X \Rightarrow \text{7 è irriducibile} \\
&9=3\cdot 3 \Rightarrow \text{Non è irriducibile}
\end{align*}
$$

### Numero Primo

_Definizione:_ $a\in A\backslash A^X$ con $a\neq 0$ è detto primo se $\forall b,c \in A$ se $a|bc$ allora $a|b$ oppure $a|c$.

Supponiamo che $A=\mathbb{Z}$

**Lemma:** $p\in \mathbb{Z}$ primo allora $p$ è irriducibile, quindi primo $\Rightarrow$ irriducibile

_Dimostrazione_

Scegliamo $p$ primo, siano $a,b\in \mathbb{Z} \ t.c. \ p=a\cdot b$, per dimostrare che è irriducibile dobbiamo quindi dimostrare che o $a$ o $b$ sono uguali a 1 o -1.
 
$$
\begin{align*}
&p=a\cdot b\Rightarrow p|a\cdot b\Rightarrow \underbrace{ \text{o } p|a \text{ o } p|b }_{ p\text{ è primo} } \\
&\text{Prendiamo il primo caso, quindi supponiamo che } p|a: \\
&p|a\Rightarrow a=p\cdot a' \ \ \ \exists a'\in \mathbb{Z} \\
 \\
&\text{Se adesso sostituiamo con la condizione iniziale } p=a\cdot b: \\
&\cancel p=\cancel p\cdot a'\cdot b\Rightarrow 1=a'\cdot b\Rightarrow a',b\in \{ 1,-1 \}=\mathbb{Z}^X \\
 \\
&\text{Quindi:} \\
&\text{Se } a'=1 \text{ allora } a=p\Rightarrow p=pb\Rightarrow b=1 \\
&\text{Se } a'=-1 \text{ allora } a=-p\Rightarrow p=-pb\Rightarrow b=-1 \\ \\
&\text{Quindi in entrambi i casi almeno un fattore è uguale a 1 o -1} \\
&\text{Quindi p è irriducibile}
\end{align*}
$$

## Valore Assoluto
È un'applicazione che si denota $\mathbb{Z}\rightarrow \mathbb{N}$, prendiamo un $a\in \mathbb{Z}$:

$$
\begin{align*}
&\text{Se } a=0 \text{ allora } |a|=0 \\
&\text{Se } a\neq 0 \text{ allora } |a|= \text{L'unico elemento di } \mathbb{N} \text{ contenuto in } \{ a,-a \}
\end{align*}
$$

### Teorema algoritmo divisione euclidea
Prendiamo $a,n\in \mathbb{Z}$ con $n\neq 0$ allora esistono unicamente determinati $q\in \mathbb{Z}$ ed $r\in \{ 0,\dots,|n|-1 \}$ tali che $a=nq+r$, dove $n$ è il quoziente e $r$ il resto.

Non facciamo dimostrazione dato che è una riformulazione del **principio del minimo su $\mathbb{N}$**.

## Legame con le Congruenze
$a\equiv b(\text{mod n})\Leftrightarrow n|a-b\Leftrightarrow \exists q\in \mathbb{Z} \ t.c. \ a-b=qn$ ovvero il resto della divisione euclidea di $a-b$ per $n$ è 0.

Ricordiamo inoltre che la congruenza è una **relazione d'equivalenza**.

_Esempio Congruenza Modulo 2_

Nota, con la notazione $2\mathbb{Z}$ indichiamo l'insieme di tutti i numeri

$\mathbb{Z}=\underbrace{ 2\mathbb{Z} }_{ \text{pari} }\bigsqcup \underbrace{ 2\mathbb{Z}+1 }_{ \text{dispari} }$

E notiamo che: $2\mathbb{Z} = \overline 0$ e che $2\mathbb{Z}+1=\overline 1$ notiamo infatti che $\mathbb{Z}\backslash\equiv_{\text{mod2}}=\{ 2\mathbb{Z},2\mathbb{Z}+1 \}$

Ad esempio con la congruenza modulo 3 otteniamo $\mathbb{Z}\backslash\equiv_{\text{mod3}}=\{ 3\mathbb{Z},3\mathbb{Z}+1,3\mathbb{Z}+2 \}$

In generale otteniamo che:

$$
\mathbb{Z}\backslash\equiv_{\text{mod n}}=\{ \underbrace{ n\mathbb{Z} }_{ \overline 0 },\underbrace{ n\mathbb{Z}+1 }_{ \overline 1 },\dots,\underbrace{ n\mathbb{Z}+n-1 }_{ \overline{n-1} } \}
$$

Notiamo che:

$$
\overline 2_{3}=\{ m\in \mathbb{Z}:m\equiv 2\text{ mod3} \}=\{ m\in \mathbb{Z}:3|m-2 \}
$$

Con la notazione $\overline 2_{3}$ indichiamo la classe di equivalenza di $2$ nell'applicazione congruenza modulo 3.

_Esempio_

$m=5, m-2=3, 3|3$ quindi $5\in\overline 2_{3}$ oppure $m=-1, m-2=-3, 3|-3$ quindi $-1\in\overline 2_{3}$

### Compatibilità con la congruenza modulo n
Le operazione $+,\cdot,-$ di $\mathbb{Z}$ sono compatibili con $\equiv_{n}$ con $n>0$ se rispettano delle proprietà:

1) $\forall a,a'\in \mathbb{Z}$ abbiamo che $a\equiv a'(\text{mod n})\Leftrightarrow -a\equiv -a'(\text{mod n})$.
2) $a,a',b,b'\in \mathbb{Z}$ se $a\equiv a'$ e $b\equiv b'$ allora $a+b\equiv a'+b'$
3) $a,a',b,b'\in \mathbb{Z}$ se $a\equiv a'$ e $b\equiv b'$ allora $ab\equiv a'b'$

In tutti i casi intendiamo $\equiv_{n}$

_Dimostrazione di 2_

$a\equiv_{n} a'\Leftrightarrow n|a'-a$ e allo stesso modo $b\equiv_{n}b'\Leftrightarrow n|b'-b$ quindi:

$$
\begin{align*}
&\text{Sappiamo che } a\equiv_{n} a'\Leftrightarrow n|a'-a \\
&\text{E che } b\equiv_{n}b'\Leftrightarrow n|b'-b \\
&\text{Inoltre:}\\
&n|a'-a\Leftrightarrow \exists k\in \mathbb{Z} \ t.c. \ a'-a=nk \\
&n|b'-b\Leftrightarrow\exists k'\in \mathbb{Z} \ t.c. \ b'-b=nk' \\
 \\
&\text{Addizionando termine a termine:} \\
&a'+b'-(a+b)=n(k+k')\Leftrightarrow n|n(k+k') \\
&\text{Quindi dato che n divide } a'+b'-(a+b) \text{ otteniamo che:} \\
&a'+b'\equiv_{n}a+b
\end{align*}
$$

---

Adesso prendiamo l'insieme $\mathbb{Z}\backslash n\mathbb{Z}$ e data $\overline a\in \mathbb{Z}\backslash n\mathbb{Z}$ definiamo la classe $-(\overline a):=\overline{(-a)}$, questa applicazione $\mathbb{Z}\backslash n\mathbb{Z}\rightarrow \mathbb{Z}\backslash n\mathbb{Z}$ è ben definita ed è l'operazione di opposto.

Date le classi $\overline a,\overline b\in \mathbb{Z}\backslash n\mathbb{Z}$ definiamo $\overline a+\overline b:= \overline{a+b}$ ed è ben definito quindi è indipendente dalla scelta di un rappresentante. Dimostriamolo:

$$
\begin{align*}
&\text{Scelgo } a'\in\overline a,b'\in\overline b \text{ quindi } (\overline a=\overline{a'},\overline b=\overline{b'}) \\
&\overline{a'+b'}=\{ m:n|m-a'-b' \}=\{ m:n|m-a-b \}\Leftrightarrow\overline{a+b}=\overline{a'+b'}
\end{align*}
$$

Definiamo inoltre una funzione che date $\overline a,\overline b\in \mathbb{Z}\backslash n\mathbb{Z}$ allora $\overline a\cdot\overline b=\overline{a\cdot b}$, che è sempre ben definita.


> [!info] Teorema
> $(\mathbb{Z}\backslash n\mathbb{Z},+,-,\cdot,\overline 0,\overline 1)$ è un anello.

## Alcuni sottoinsiemi di $\mathbb{Z}$

$$
\begin{align}
&n\mathbb{Z}=\{ m\in \mathbb{Z} \ t.c. \ \exists k\in \mathbb{Z} \text{ con } m=kn \} = \text{multipli di } n \\
&\mathbb{Z}\backslash\{ 0 \}=\mathbb{Z}^*
\end{align}
$$

_Esercizio_

Dati $a,b\in \mathbb{Z}^*$ con $a|b\Leftrightarrow b\mathbb{Z}\subset a\mathbb{Z}$:

$$
\begin{align*}
&\text{Supponiamo che } a|b \text{ allora } \exists k\in \mathbb{Z}\ t.c. \ b=ka \\
&\text{Sia } b'\in b\mathbb{Z} \text{ allora } \exists l\in \mathbb{Z} \ t.c. \ b'=lb \text{ ma sappiamo che } b=ka \text{ quindi:} \\
&b'=\underset{:=l'}{(lk)}a\Rightarrow b'\in a\mathbb{Z}
\end{align*}
$$

--- 

Adesso vediamo insiemi nella forma $a\mathbb{Z}+b\mathbb{Z}:=\{ m\in \mathbb{Z}:\exists k,k'\in \mathbb{Z}\text{ con } m=ka+k'b \}$.

Ad esempio possiamo scrivere che $2\mathbb{Z}+3\mathbb{Z}=\{ 0,2,4,6,\dots,-2,-4,-6,\dots,3,6,9,-3,-6,-9,\dots,5,8,7,\dots \}=\mathbb{Z}$

Questo perché appunto prendiamo ogni volta due valori $k,k'$ con i quali moltiplicare 2 e 3 in questo caso, e sempre in questo caso notiamo che stiamo sommando i numeri pari e quelli dispari quindi otteniamo tutti i numeri.

$a\mathbb{Z}+b\mathbb{Z}=MCD(a,b)\mathbb{Z}$ quindi ad esempio nel caso di prima $MCD(2,3)=1$ e infatti come abbiamo notato $2\mathbb{Z}+3\mathbb{Z}=1\mathbb{Z}$

**Lemma**:

Poniamo $\mathcal{E}:=a\mathbb{Z}+b\mathbb{Z}$ con $ab\neq 0$ allora esiste $\delta\in \mathbb{N}^*$ unico t.c. $\mathcal{E}=\delta \mathbb{Z}$.

_Dimostrazione:_

$$
\begin{align*}
&\text{Poniamo } \mathcal{E}^*:=\mathcal{E}\cap \mathbb{N}^*\subset \mathbb{N}^* \\
&\text{Sappiamo che } \mathcal{E}^* \text{ sicuramente non è vuoto} \\
&\text{Infatti se } a,b>0 \text{ esiste una coppia } (k,k')\in \mathbb{N}^2 \ t.c. \ \underbrace{ ka+k'b }_{ \in\mathcal{E}^* }>0 \\
&\text{Se invece } a>0,b<0 \text{ allora esiste } (k,k')\in \mathbb{N}\times(-\mathbb{N}) \\
&\text{Ci sono ancora 2 casi semplice che non vediamo} \\
 \\
&\text{Adesso poniamo } \delta=min(\mathcal{E}^*) \text{ ed è ben definito in } \mathbb{N}^* \text{(principio del minimo)} \\
&\text{Osserviamo che } \delta <|a|, \delta <|b| \text{ infatti } |a|,|b|\in\mathcal{E}^* \\
 \\
&\text{Diciamo che } \delta|a \text{ e per il principio della divisione euclidea:} \\
&a=q\delta+r \ \ \  r\in \{ 0,\dots,\delta-1 \} \text{ dobbiamo quindi dimostrare che } r = 0  \\
&\text{Notiamo che } r =a-q\delta \\
 \\
&a\in\mathcal{E} \\
&\delta\in\mathcal{E}^*\subset\mathcal{E}=a\mathbb{Z}+b\mathbb{Z} \text{ quindi:} \\
&\delta=\underset{\in \mathbb{Z}}{ua}+\underset{\in \mathbb{Z}}{vb} \\
 \\
&r=a-q(ua+vb)=a(1-qu)+b(-qv) \Rightarrow r\in\mathcal{E} \\
&\text{Quindi dato che } r \text{ può essere o uguale a 0 o positivo}: \\
&\text{Se} = 0 \text{ abbiamo finito dato che } \delta|a  \\
&\text{Altrimenti se > 0 otteniamo che } r\in\mathcal{E}^* \text{ e quindi } r>\delta \text{ ma è impossibile per la definizione di r iniziale}
\end{align*}
$$

Per la stessa ragione abbiamo che $\delta|b$.

$$
\begin{align*}
&\forall \alpha,\beta\in \mathbb{Z} \ \ \ \delta|\alpha a+\beta b\Rightarrow  \mathcal{E}\subset \delta \mathbb{Z} (\text{ Per la dimostrazione di prima } a|b\Leftrightarrow b\mathbb{Z}\subset a\mathbb{Z}) \\
&\text{D'altronde } \delta\in\mathcal{E} \Leftrightarrow \delta=ka+k'b \\
&\forall l\in \mathbb{Z}, l\delta=lka+lk'b\Rightarrow l\delta\in\mathcal{E}\Rightarrow \delta \mathbb{Z}\subset \mathcal{E} \\
&\text{ Se i multipli di } \delta \text{ sono elementi di } \mathcal{E} \text{ allora } \delta \mathbb{Z} \text{ è contenuto in } \mathcal{E}. \\
&\text{Abbiamo ottenuto quindi che } \mathcal{E}\subset \delta \mathbb{Z} \text{ e che } \delta \mathbb{Z}\subset\mathcal{E} \text{ quindi } \mathcal{E}=\delta \mathbb{Z}
\end{align*}
$$

## Massimo Comun Divisore

Data $(a,b)\in \mathbb{Z}\times \mathbb{Z}$ con $(a,b)\neq(0,0)$

_Definizione_

$d\in \mathbb{N}^*$ è MCD di $a$ e $b$ se:

1) $d|a$ e $d|b$
2) Se $d'\in \mathbb{N}^*$ t.c. $d'|a$ e $d'|b$ allora $d'|d$

**Lemma**: Se $d$ soddisfa (1) e (2) allora è unicamente determinato

_Dimostrazione_

Supponiamo che $d_{1},d_{2}$ soddisfano (1) e (2) e mostriamo che $d_{1}=d_{2}$

$$
\begin{align*}
&\text{Si ha che:} \\
&d_{2}|d_{1} \text{ e che } d_{1}|d_{2}\Rightarrow \{ d_{1},-d_{1} \}=\{ d_{2},-d_{2} \}\Rightarrow d_{1}=d_{2} \text{ Dimostrato sopra nelle proprietà}
\end{align*}
$$

Si scrive $d=MCD(a,b)$, inoltre se $MCD(a,b)=1$ si dice che $a,b$ sono primi fra loro (co-primi).

**Lemma**: 

$$
\begin{align}
&\delta=MCD(a,b) \\
&a\mathbb{Z}+b\mathbb{Z}=\delta \mathbb{Z} \ (\delta>0; a,b\neq 0)
\end{align}
$$

_Dimostrazione_

$$
\begin{align*}
&\delta \mathbb{Z}=a\mathbb{Z}+b\mathbb{Z}\supset a\mathbb{Z}\Rightarrow \delta|a \\
&\text{Allo stesso modo } \delta \mathbb{Z}=a\mathbb{Z}+b\mathbb{Z}\supset b\mathbb{Z}\Rightarrow \delta|b \\
&\text{Abbiamo quindi verificato la prima condizione del MCD } \\
 \\
&\text{Sia } d'\in \mathbb{N}^* \ t.c. \ d'|a,d'|b \\
&d'|a\Leftrightarrow a\mathbb{Z}\subset d'\mathbb{Z} \\
&d'|b\Leftrightarrow b\mathbb{Z}\subset d'\mathbb{Z} \\
&\text{Quindi} \\
&\underbrace{ a\mathbb{Z}+b\mathbb{Z} }_{ \delta \mathbb{Z} }\subset \underbrace{ d'\mathbb{Z}+d'\mathbb{Z} }_{ d'\mathbb{Z} } \Rightarrow d'|\delta \\
&\text{Abbiamo quindi verificato anche la seconda condizione}
\end{align*}
$$

### Algoritmo di Euclide per trovare MCD
Possiamo vederlo come una funzione che prende in input $a,b>0$ e restituisce un $\delta=MCD(a,b)$

![[Pasted image 20241015183317.png|500]]

_Esempio_

![[Pasted image 20241015184302.png|500]]

Prendendo l'esempio sopra allora sappiamo che $\exists u,v\in \mathbb{Z} \ t.c. \ 3=3522u+321v$ ma come si calcolano? **Identità di Bèzout**

![[Pasted image 20241015185436.png]]

**Lemma di Gauss**: Se $a,b\in \mathbb{Z}^X$ e $c\in \mathbb{Z}$ e se $MCD(a,b)=1$ allora $a|bc\Rightarrow a|c$

_Dimostrazione_

Sappiamo che $MCD(a,b)=1$ e quindi sappiamo che $a\mathbb{Z}+b\mathbb{Z}=\delta \mathbb{Z}=\mathbb{Z}$ (teoremi visti precedentemente). Questo inoltre significa che $\exists u,v\in \mathbb{Z} \ t.c. \ au+bv=1$, allora:

$$
\begin{align*}
&\text{Moltiplichiamo per c} \\
&auc+\underbrace{ bc }_{ \text{Divisibile per a} }v=c \\
&\text{Questo significa che } \exists k \ t.c. \ b=k\cdot a \\
&auc+kav=c\rightarrow a\underbrace{ (uc+kv) }_{ \exists l \ t.c. \ c=al }=c \\
&\text{Questo significa quindi che } a|c
\end{align*}
$$

**Lemma**: Dato $p\in \mathbb{N},p>1$ allora $p$ è irriducibile $\Rightarrow p$ è primo.

_Dimostrazione_

Prima di tutto dimostriamo una proprietà utile per dopo: Se $p$ è irriducibile e $p \not{|} a$ allora $a\mathbb{Z}+p\mathbb{Z}=\mathbb{Z}\Leftrightarrow MCD(a,p)=1$, altrimenti $\exists\delta>1 \ t.c. \ \delta|a \ e \ \delta|p$ ma visto che $p$ è irriducibile allora $\delta$ è $=p\Rightarrow p|a$ ma questo va in contraddizione con l'ipotesi ovvero che $p$ non divide $a$.

Adesso passiamo alla dimostrazione del Lemma.

Supponiamo che $p|ab$ con $p$ irriducibile. Allora $p$ deve dividere $a$ o $b$, senza perdere generalità possiamo quindi supporre che non divide $a$ e dobbiamo dimostrare che necessariamente divide $b$.

$$
\begin{align}
&a\mathbb{Z}+p\mathbb{Z}=\mathbb{Z} \\
&\text{Moltiplichiamo per b} \\
&\underbrace{ \underbrace{ ab }_{ p|ab }\mathbb{Z}+\underbrace{ pb }_{ p|pb }\mathbb{Z} }_{ \subset p\mathbb{Z} }=b\mathbb{Z} \\
&\text{Quindi dato che } b\mathbb{Z}\subset p\mathbb{Z}\Rightarrow p|b
\end{align}
$$


_Esercizio_

Calcolare $(\mathbb{Z}\backslash N\mathbb{Z})^X$ con $N\in \mathbb{N}$

Premesse:
- $A=\mathbb{Z}\backslash N\mathbb{Z}=\mathbb{Z}\backslash\equiv_{N}$
- $[a]+[b]=[a+b]$ e $[a]\cdot[b]=[a\cdot b]$
- Con l'elemento $[0]=(N\mathbb{Z})$ per l'elemento neutro di $+$ e con l'elemento $[1](=N\mathbb{Z}+1)$ per l'elemento neutro di $\cdot$, si ottiene che $A$ è un anello commutativo unitario

Si cerca:
- $A^X=\{ [n] \ t.c. \ \exists[m] \text{ con } [m]\cdot[n]=[1] \}$ "Insieme delle unità"

1) Sia $[a]\in(\mathbb{Z}\backslash N\mathbb{Z})^X$ allora esiste $b\in \mathbb{Z}\backslash N\mathbb{Z}$ t.c. $[a]\cdot[b]=[1]$, $[ab]=[1]\Leftrightarrow N|ab-1\Leftrightarrow \exists k\in \mathbb{Z}$ t.c. $kN=ab-1$. (È invertibile se e solo se scelto un qualsiasi rappresentante, quando faccio $ab-1$ è divisibile per N).
   
   Spostando i termini di prima otteniamo $ab-kN=1$ che è un'**identità di Bèzout** per $a,N$ e questo significa che $a,N$ sono **primi fra loro** perché il loro MCD è 1.

Quindi otteniamo che $(\mathbb{Z}\backslash N\mathbb{Z})^X=\{ [a]:a\in \mathbb{Z} \ e \ MCD(a,N)=1 \}$.

Esiste quindi un'applicazione biiettiva tra $\{ r\in \{ 0,\dots,N-1 \} \ t.c. \ MCD(r,N)=1 \}$ e $(\mathbb{Z}\backslash N\mathbb{Z})^X$,
$r\rightarrow [r]$.

_Esempio_

$N=24=2^3\cdot 3$, verificare che $(\mathbb{Z}\backslash 24\mathbb{Z})^X=\{ r:2\not{|} r, 3\not{|}r \}$, quindi $(\mathbb{Z}\backslash 24\mathbb{Z})^X=\{ [5],[7],[11],[13],[17],[19],[23] \}$.

_Cosa si osserva se N è primo?_

- $N=p$ primo: Sia $r\in \{ [1],\dots,[p-1] \}$ allora $MCD(p,r)=1$ altrimenti qualora si avesse $\delta=MCD(p,r)>1$ avrei che $\delta|p,\delta|r\Rightarrow \delta=p$ e quindi si avrebbe che $p|r$ ma $r<p$ siccome è resto e quindi è una contraddizione, abbiamo quindi che $r,p$ sono coprimi.

Si ottiene $(\mathbb{Z}\backslash p\mathbb{Z})^X=\{ [r]:1\leq r\leq p-1 \} \ (\forall r\in \mathbb{Z} \backslash p\mathbb{Z} - \{ 0 \},r \text{ è invertibile})$

> [!info] Terminologia
> Dato un anello $A$ commutativo t.c. $\forall a\in A\backslash\{ 0 \}$ invertibile, si dice **campo**. Ad esempio $\mathbb{Z}\backslash p\mathbb{Z}=\mathbb{F}_{p}$ è un campo.

---
 
_Esercizio 5_

Dimostrare il Piccolo Teorema di Fermat.

Dato un numero $p$ primo e un intero $n$ tali che $n^p\equiv n\text{(mod p)}$ mostrare che se $n$ e $p$ sono primi fra loro allora $n^{p-1}\equiv 1\text{(mod p)}$.

A cosa serve il teorema di Fermat? Serve a ridurre l'esponente nel calcolo delle potenze quando il numero è molto grande.

---

**Proprietà**: Sappiamo che $\mathbb{F}_{p}=\mathbb{Z}/p\mathbb{Z}$ è un campo ovvero $\mathbb{F}^X_{p}=\{ [1],[2],\dots,[p-1] \}$ inoltre sappiamo anche che $([a]+[b])^p=[a]^p+[b]^p$ con $[a],[b]\in\mathbb{F}_{p}$, (non vera in $\mathbb{Z}$).

Scegliamo come $a,b$ come rappresentanti e scriviamo:

$$
(a+b)^p=a^p+\binom{p}{1}\cdot a^{p-1}\cdot b+\binom{p}{2}\cdot a^{p-2}\cdot b^2+\dots+\binom{p}{p-2}\cdot a^2\cdot b^{p-2}+\binom{p}{p-1}\cdot a\cdot b^{p-1}+b^p
$$

- Prendiamo $0<i<p$ e scriviamo $\binom{p}{i}=\frac{p!}{i!\cdot (p-i)!}\in \mathbb{N}$ e quindi si ha che $p|i!\cdot (p-i)!$
- Supponiamo che $1\leq i\leq p-1$ e inoltre $i\neq i(i-1)\dots 3 \cdot 2 \cdot 1$ e quindi siccome $p>i$ ed $i$ si scompone in tutti fattori più piccoli di $p$ e quindi non divisibili per $p$ (nemmeno il loro prodotto dato che $p$ è primo) abbiamo che $p\not{|}\ i$
- Allo stesso modo otteniamo che $p>p-i$ e quindi $p\not{|} \ (p-i)!$

Quindi abbiamo che:

$$
p\neq \underbrace{ k }_{ a }\cdot \underbrace{ i!\cdot (p-i)! }_{ b } \ \ \exists k\in N^*
$$

E per le condizioni viste sopra sappiamo che $p\not{|} \ b$, ma per definizione di fattoriale sappiamo che $p|p! = ab$, quindi visto che $p$ è primo e non divide $b$ allora deve sicuramente dividere $a$ per **il lemma di Gauss**.

Noi sappiamo però che $a=k=\binom{p}{i}$ dato che $\binom{p}{i} = \frac{p!}{i!(p-i)!}\to p! = \binom{p}{i}\cdot i!\cdot(p-i)!$.

Quindi siccome $p$ dividi tutti i $\binom{p}{i}$ questi si riducono tutti a $\overline 0$ nella formula vista sopra, ad eccezione del primo e l'ultimo.

Abbiamo dimostrato che $([a]+[b])^p=[a]^p+[b]^p$ dato che se $1\leq i\leq p-1$ e $p$ primo abbiamo che $\binom{p}{i}=\binom{p}{p-i}\equiv_{p}0$.

---

**Tornando alla dimostrazione del teorema di Fermat**

$$
\begin{align}
&[0]^p=[0] \\
&[1]^p=[1] \\
&[2]^p=([1]+[1])^p=[1]^p+[1]^p=[1]+[1]=[2]
\end{align}
$$

Facciamo una dimostrazione per induzione, la nostra ipotesi è $[n-1]^p=[n-1]$, quindi:

$$
[n]^p=([n-1]+[1])^p=[n-1]^p+[1]^p=[n-1]+[1]=[n]
$$

In questo modo abbiamo dimostrato che $\forall n\in \mathbb{Z}, n^p\equiv_{p} n$ con $p$ primo.

_Precisazione_

Se $[n]\neq [0]$ in $\mathbb{F}_{p}$ ovvero se $[n]\in\mathbb{F}_{p}^X$ allora $[n]$ è invertibile di inverso $[n]'$, per il PTF sappiamo che $[n]^p=[n]$, moltiplichiamo per $[n]'$:

$$
\underbrace{ [n]^p[n]' }_{ [n]'[n][n]^{p-1}=[n]^{p-1} }=\underbrace{ [n][n]' }_{ 1 }
$$

Otteniamo quindi che $[n]^{p-1}=[1]$

_Difetti del PTF_

Se $[a]\in F_{p}^X$ e quindi è invertibile, calcolare il suo inverso $[a]^{-1}$ usando il PTF, ricordiamo che $[a]^{p-1}=[1]$

So che $[a]^{p-1}=[a]^{p-2}\cdot[a]$, quindi:

$$
\begin{align*}
&[1]=\underbrace{ [a]^{p-2}\cdot[a] }_{ \text{Inversi} } \\
&[a]^{-1}=[a]^{p-2}
\end{align*}
$$

Questo però per numeri molto grandi risulta scomodo, infatti se ad esempio vogliamo calcolare $[2]^{-1}$ con $p=691$, dobbiamo calcolare $[2]^{p-2}=[2]^{689}$.

![[Pasted image 20241018161511.png]]

Svolgendo i calcoli però, ovvero calcolando $2^i \% 691$ per $i$ che va da $1$ a $690$ notiamo che si l'ultima è 1 e quindi il suo inverso (689) ma ci sono anche altri 1 prima, perché le classi sono cicliche.

_Esercizio_

Dimostrare che in $4\mathbb{Z}+3$ nessun intero è somma di due quadrati.

Calcoliamo le classi dei resti modulo 4 e i loro quadrati.

![[Pasted image 20241018162201.png|400]]

# Successione di Fibonacci
La successione di Fibonacci è definita induttivamente da $F_{0}=0,F_{1}=1,F_{n}=F_{n-1}+F_{n-2}$, i numeri della successione di Fibonacci hanno alcune proprietà:

- $MCD(F_{m},F_{n})=F_{MCD(m,n)}$ 
- $MCD(F_{m},F_{m+1})=F_{1}=1$

_Dimostriamolo per Induzione_

Quindi sappiamo che:

$$
F_{0}=0; F_{1}=1;F_{n+1}=F_{n}+F_{n-1}
$$

Definiamo $MCD(F_{n},F_{n+1})=\delta_{n}$, possiamo inoltre scrivere $\mathbb{Z}F_{n}+\mathbb{Z}F_{n+1}=\mathbb{Z}\delta_{n}$ e dobbiamo dimostrare che $\mathbb{Z}\delta_{n}=1\mathbb{Z}$ ovvero che il loro $MCD$ è 1.

$$
\begin{align}
\mathbb{Z}F_{n}+\mathbb{Z}F_{n+1}=\{ aF_{n}+bF_{n+1}:a,b\in \mathbb{Z} \}=\underbrace{ \{ aF_{n}+b\overbrace{ (F_{n}+F_{n-1}) }^{ \text{Definizione Fib.} } :a,b\in \mathbb{Z}\} }_{ \text{Dobbiamo dimostrare che } = \mathbb{Z}F_{n-1}+\mathbb{Z}F_{n}}
\end{align}
$$

Quell'insieme possiamo scriverlo come:

$$
\{ (a+b)F_{n}+bF_{n-1}:a,b\in \mathbb{Z} \}
$$

E quindi possiamo scrivere:

$$
\underbrace{ \{ (a+b)F_{n}+bF_{n-1}:a,b\in \mathbb{Z} \} }_{ A }\subseteq \mathbb{Z}F_{n-1}+\mathbb{Z}F_{n}
$$

Quindi l'insieme a sinistra è sicuramente sottoinsieme di quello a destra, ma per dimostrare che sono uguali devo dimostrare che esiste un'applicazione biiettiva $f:\mathbb{Z}^2\to \mathbb{Z}^2$ che manda $(a,b)\to(\underbrace{ a+b }_{ u },\underbrace{ b }_{ v })$. Sia $f(\mathbb{Z}^2)$ l'immagine noi sappiamo che $A=\{ uF_{n-1}+vF_{n}:(u,v)\in \mathbb{Z}^2 \}$  quindi se dimostriamo che l'applicazione è suriettiva abbiamo dimostrato che qualsiasi $a,b$ prendo raggiungo tutti gli $u,v$ e quindi i due insiemi sono uguali.

Dimostreremo che l'applicazione è biiettiva che comprende anche suriettiva.

> [!info] Richiamo
> $A\xrightarrow{f}B$ è biiettiva $\Leftrightarrow \forall b\in B, f^{-1}(\{ b \})$ è un singleton, ma deve esserci anche un'inversa $\exists g:B\to A$ t.c. $f\circ g=Id_{B}$ e simultaneamente $g\circ f(A)=Id_{A}$.
> 

Quindi noi sappiamo che $f(a,b)=(a+b,b)=:(u,v)$ e questo è equivalente a un sistema:

$$
\begin{cases}
a+b=u \\
b=v
\end{cases}
\Leftrightarrow
\begin{cases}
a=u-v \\
b=v
\end{cases}
$$

Adesso poniamo l'inversa $g:\mathbb{Z}^2\to \mathbb{Z}^2$ e quindi abbiamo le coppie $(u,v)\to(u-v,v)$ adesso verifichiamo se le funzioni composte ci danno le Identità.

$$
\begin{align*}
&(f\circ g)(u,v)=f(g(u,v))=f(u-v,v)=(u-v+v,v)=(u,v) \text{ La prima è verificata} \\
&(g\circ f)(a,b)=g(f(a,b))=g(a+b,b)=(a+b-b,b)=(a,b) \text{ Anche la seconda è verificata}
\end{align*}
$$

Quindi l'applicazione è biiettiva e quindi suriettiva e quindi i due insiemi sono uguali.

Sapendo che è sempre verificato possiamo sempre diminuire il numero di Fibonacci e ottenere:

$$
\forall n>0 \ \ \ F_{n+1}\mathbb{Z}+F_{n}\mathbb{Z}=F_{n}\mathbb{Z}+F_{n-1}\mathbb{Z}=F_{n-1}\mathbb{Z}+F_{n-2}\mathbb{Z}=\dots=F_{1}\mathbb{Z}+F_{0}\mathbb{Z}
$$

Quindi $F_{1}\mathbb{Z}+\{ 0 \}=\mathbb{Z}$ che può essere anche scritto $\forall n>0, F_{n}\mathbb{Z}+F_{n-1}\mathbb{Z}=\mathbb{Z}$ e questo equivale anche a dire che $MCD(F_{n-1},F_{n})=1$.

# Teorema Fondamentale Dell'Aritmetica
$\forall a\in \mathbb{Z}^*$ abbiamo che:
1) $I_{a}=\{ p \text{ primo}:p|a \}$ è finito, quindi c'è solo un numero finito di primi che dividono $a$.
2) Inoltre $a=(\pm 1)\cdot \prod\limits_{p}p^{v_{p}(a)}$ dove $v_{p}(a)$ è un certo esponente in $\mathbb{N}$ e sono unicamente determinati. Ovvero ogni numero intero diverso da 0 è il prodotto di alcuni numeri primi elevati a determinati esponenti.

Notiamo che nella seconda condizione i numeri primi sono infiniti e quindi otterremmo un valore infinito, però ad un certo punto $v_{p}(a)$ sarà uguale a 0 e quindi avremo un numero finito di primi e poi un numero infinito di 1 che non cambia il nostro valore. Formalizziamolo

_Osservazione_

Si sa che $\mathbb{P}=\{ p\in \mathbb{N},\text{p primo} \}$ è infinito però siccome $\forall a\in \mathbb{Z}^*$ abbiamo che $I_{a}$ è finito:

$$
\prod_{p}p^{v_{p}(a)}=\underbrace{ \prod_{p\in I_{a}}p^{v_{p}(a)} }_{ \text{Questo è finito} }\cdot \underbrace{ \prod_{p\not\in I_{a}}p^{v_{p}(a)} }_{ \text{Questo è infinito} }
$$

Però nell'insieme infinito avremo che $v_{p}(a)=0$ e quindi tutto quel prodotto sarà uguale a $1\cdot ... \cdot 1=1$.

_Esempi_

$$
\begin{align*}
&a=1 \\
&1=+1\cdot \prod_{p}p^{v_{p}(1)} \text{ Con } v_{p}(1)=0 \ \forall p \\
&\text{Questo ci dice che } I_{1}=\emptyset\text{ Ovvero non abbiamo nessun primo}
\end{align*}
$$

$$
\begin{align*}
&a=2 \\
&2=+1\cdot \prod_{p}p^{v_{p}(2)} \\
&v_{p}(2)=1 \text{ se } p=2, \text{altrimenti } v_{p}(2)=0 \\ \\
&\text{Quindi possiamo scrivere } 2=2\cdot \prod_{p\neq 2}p^{0}
\end{align*}
$$

$$
\begin{align*}
&a=7! = 7\cdot 5\cdot 3^2 \cdot 2^4 \\
&\text{Possiamo definire:} \\
&v_{p}(a)=
\begin{cases}
1 \ \ \ p=7 \\
1 \ \ \ p=5 \\
2 \ \ \ p=3 \\
4 \ \ \ p=2 \\
0 \ \ \ p>7
\end{cases} \\
&\text{Possiamo poi utilizzare la formula:} \\
&7! = +1\cdot \prod_{p}p^{v_{p}(a)}
\end{align*}
$$

Cosa possiamo dedurre con queste notazioni? Scriviamo due numeri $a,b$:

$$
\begin{align*}
&a=\prod_{p}p^{v_{p}(a)} \ \ \ b=\prod_{p}p^{v_{p}(b)} \\
 \\
&\text{Scriviamo } a\cdot b=\prod_{p}p^{v_{p}(a)}\cdot\prod_{p'}{p'}^{v_{p'}(b)} \\ \\
&\text{Che è uguale a: } \prod_{p}p^{v_{p}(a)+v_{p}(b)} \\
 \\
&\text{Cosa ci dice questo? Che } v_{p}(ab)=v_{p}(a)+v_{p}(b)
\end{align*}
$$

Vediamo un _esempio:_

$$
\begin{align*}
&a=12=2^2 \cdot 3 \\
&b=15=5\cdot 3 \\ \\
&\begin{cases}
v_{2}(a)=2 \\
v_{3}(a)=1 \\
v_{5}(a)=0
\end{cases} \ \ \ 
\begin{cases}
v_{2}(b)=0 \\
v_{3}(b)=1 \\
v_{5}(b)=1
\end{cases} \\ \\
&v_{p}(a\cdot b)=v_{p}(12\cdot 15)=v_{p}(a)+v_{p}(b) \\ \\
&\text{Otteniamo quindi, facendo le somme:} \\
&v_{2}(ab)=2; v_{3}(ab)=1; v_{5}(ab)=1; v_{p}(ab)=0 \text{ Quando } p>5
\end{align*}
$$

---

Dimostriamo il teorema ovvero che:

$$
a=(\pm 1)\cdot \prod_{p}p^{v_{p}(a)}
$$

Per prima cosa dimostriamo che $I_{a}$ è un insieme finito. (1)

Supponiamo per assurdo che $I_{a}$ sia infinito e questo significa che esiste una collezione infinita di primi $p$ t.c. $p|a$ e questo significa che ogni  $p\leq a$. Supponiamo anche $a>0$.

Abbiamo ottenuto una contraddizione, infatti essendo $a$ un intero, non esiste un numero infinito di numero inferiori a lui. Abbiamo provato che $I_{a}$ è finito.

Adesso dimostriamo la fattorizzazione per induzione (2).

 Per $a=1$ lo abbiamo già mostrato prima, abbiamo che per ogni $\forall p,v_{p}(a)=0$ e otteniamo un prodotto infinito di 1 che fa 1.

Adesso supponiamo che $a>1$, abbiamo due casi: 
- Se $a$ è primo non abbiamo nulla da dimostrare infatti il $v_p(a)$ è sempre 0 tranne quando $p=a$.
- Se $a$ non è primo allora non è irriducibile e allora posso scrivere $a=u\cdot v$ con $1<u<a,1<v<a$ ovvero due divisori di $a$ diversi da 1.
  
  Per ipotesi induttiva visto che $u,v<a$ posso scrivere:
  
  $$
   \begin{align*}
   &u=\prod_{p}p^{v_{p}(u)} \\
   &v=\prod_{p}p^{v_{p}(v)} \\
   &a=u\cdot v=\prod_{p}p^{v_{p}(u)+v_{p}(v)} \\
   &\text{Per la formula di prima sappiamo che } v_{p}(uv)=v_{p}(u)+v_{p}(v) \\
   &\text{Quindi dato che } uv=a \text{ allora quell'esponente è } =v_{p}(a)
   \end{align*}
   $$

---

_Enunciato Teorema_

$\forall a>0, \exists$ un numero finito di primi distinti $p_{1},\dots,p_{r}$ tali che $a=p^{\alpha_{1}}_{1},\dots,p_{r}^{\alpha_{r}}$ e questa fattorizzazione è unicamente determinata.

Questo è un enunciato differente ma con lo stesso significato di quello visto sopra, ma qui dobbiamo numerare i $p$.

_Esercizio_

Prendiamo $a,b\in \mathbb{N}^*$ e quindi possiamo scriverli come:

$$
\begin{align*}
a=\prod_{p}p^{v_{p}(a)} \\
b=\prod_{p}p^{v_{p}(b)} \\
\end{align*}
$$

Mostrare che $a|b\Leftrightarrow\forall p, v_{p}(a)\leq v_{p}(b)$.

1:

Supponiamo che $v_{p}(a)\leq v_{p}(b)$ e questo è equivalente a dire che $\underbrace{ v_{p}(b)-v_{p}(a) }_{ \in \mathbb{N} }\geq 0$ .

Adesso poniamo $k=\prod\limits_{p}p^{v_{p}(b)-v_{p}(a)}$ e quindi l'esponente è un intero.

Adesso calcoliamo $k\cdot a$:

$$
\prod\limits_{p}p^{v_{p}(b)-v_{p}(a)} \cdot \prod_{p}p^{v_{p}(a)}=\prod_{p}p^{v_{p}(b)-\cancel{v_{p}(a)}+\cancel{v_{p}(a)}}=b
$$

Questo implica che $b=k\cdot a, \exists k\in \mathbb{N}^*$ e quindi $a|b$.

2:

Supponiamo che $a|b$ questo implica che $b=k\cdot a,\exists k\in \mathbb{N}^*$, applichiamo il teorema fondamentale dell'aritmetica:

$$
\prod_{p}p^{v_{p}(b)}=\prod_{p}p^{v_{p}(k)}\cdot\prod_{p}p^{v_{p}(a)}=\prod_{p}p^{v_{p}(k)+v_{p}(a)}
$$

Per unicità della fattorizzazione (quando prendo un primo, gli esponenti devono essere uguali da entrambe le parti) $v_{p}(b)=\underbrace{ v_{p}(k) }_{ \geq 0 }+v_{p}(a),\forall p$ quindi questo significa che $v_{p}(b)\geq v_{p}(a)$.

---

_Esercizio_

Prendiamo $a,b\in \mathbb{N}^*$ dimostriamo che:

$$
MCD(a,b)=\prod_{p}p^{min(v_{p}(a),v_{p}(b))}
$$

Come abbiamo definito $MCD(a,b)$? L'abbiamo definito come l'unico intero $\delta$ in $N^*$ tale $\delta|a,\delta|b$ (1) e $\forall d'\in \mathbb{N}^*$ tale che $d'|a,d'|b$ allora $d'|\delta$ (2)

Come traduciamo queste condizioni in termini di produttorie usando il teorema fondamentale?

Ricordiamo che nell'esercizio precedente abbiamo dimostrato che $a|b\Leftrightarrow \forall p, v_{p}(a)\leq v_{p}(b)$, quindi:

1) Equivale a dire $\forall p,v_{p}(\delta)\leq v_{p}(a)$ e $v_{p}(\delta)\leq v_{p}(b)$
2) Se $d'$ soddisfa la condizione 1 (al posto di $\delta$) allora soddisfa anche $v_{p}(d')\leq v_{p}(\delta)$ 

La condizione (1) ci suggerisce che $v_{p}(\delta)\leq min(v_{p}(a),v_{p}(b))$ allora (2) vuol dire che se $d'$ è tale che $v_{p}(d')\leq min(v_{p}(a),v_{p}(b))$ allora $v_{p}(d')\leq v_{p}(\delta)$

Quindi $\forall p, v_{p}(\delta)$ è il più grande degli interi $n$ t.c. $n\leq min(v_{p}(a),v_{p}(b))$ questo implica che $v_{p}(\delta)=min(v_{p}(a),v_{p}(b))$.

# Divisori di Zero

Iniziamo da degli _esempi_:

Prendiamo $\mathbb{Z}/6\mathbb{Z}=\{ [0],[1],[2],[3],[4],[5] \}$, notiamo che ad esempio le classi $[2],[3]$ non sono nulle ma il loro prodotto da $[6]$ che è uguale a $[0]$. In $\mathbb{Z}$ questo non può accadere, non ci sono due elementi non nulli che moltiplicati fra loro danno come risultato zero, qui invece può succedere.

_Definizione_

Dato $A$ anello, $a\in A$ è divisore di zero se $\exists b\in A\backslash\{ 0 \}\ t.c.\ ab=0_{A}$, non impostiamo che $a\neq 0$ perché vogliamo ammettere 0 come divisore di 0.

_Esempi_

In $\mathbb{Z}/6\mathbb{Z}$ come divisori di zero abbiamo $[0],[2],[3]$.

In $A$ qualsiasi $0_{A}$ è divisore di zero. Con $A\neq \{ 0 \}$ ovvero quando i due elementi neutri sono distinti.

Invece, dove **non abbiamo divisori di zero**? Nei campi, se $A=K$ campo (ad esempio $A=\mathbb{Q},\mathbb{R},\mathbb{C},\mathbb{F}_{p}$ primo) cioè $\forall a\in K\backslash\{ 0 \}, a$ è invertibile ovvero $K^X=K^*$. L'unico di divisore di zero in un $K$ campo è $0_{K}$, perché?

Supponiamo di avere $a$ divisore di zero, allora $\exists b\neq 0 \ t.c. \ ab=0$, però $b$ è invertibile perché **non nullo**, quindi $\exists b^{-1}\in K^X \ t.c. \ b\cdot b^{-1}=1$.

Adesso moltiplichiamo termine a termine $ab=0$ per $b^{-1}$ e otteniamo:

$$
\begin{align*}
&a\cdot \overbrace{ b\cdot b' }^{ 1 }=0\cdot b' \\
&a\cdot 1=0
\end{align*}
$$

Quindi se $a$ è divisore di 0 allora $a=0$.

---

In $\mathbb{Z}$ se $a$ è divisore di zero allora $a=0$ **anche se $\mathbb{Z}$ non è campo**, dimostriamolo:

Sia $a$ divisore di zero allora $\exists b\in \mathbb{Z}^* \ t.c. \ ab=0$, e anche $-a$ è divisore di zero:

$$
\begin{align*}
&(-a)\cdot(-b)=a\cdot b=0 \\
&\text{Questo vuol dire a divisore di zero} \Leftrightarrow -a \text{ è divisore di zero}
\end{align*}
$$

Possiamo supporre quindi, senza perdere generalità, che $a$ sia $\geq 0$.

Quindi abbiamo detto che $\exists b\neq 0 \ t.c. \ ab=0$ e quindi possiamo scrivere:

$$
0=a\cdot b=\underbrace{ b+b+\dots+b }_{ \text{a volte} } \geq b >0
$$

Se $a>0$ questo non è possibile e allora l'unica scelta che ci rimane è $a=0$, quindi abbiamo dimostrato che $\mathbb{Z}$ ha come unico divisore di zero, 0.

**Definzione Dominio**

Dato un anello $A\neq \{ 0 \}$ si dice che è un dominio se l'unico divisore di zero in $A$ è zero. Quindi **ogni campo è un dominio**, ma anche $\mathbb{Z}$ è un dominio. Invece ad esempio $\mathbb{Z}/6\mathbb{Z}$ non è un dominio.

---

Se $a\in A$ non è divisore di zero e se $ax=0$ allora $x=0$, da questo possiamo scrivere il seguente **lemma**


> [!info] Lemma - Legge di Cancellazione
> Prendiamo $a\in A$ non divisore di zero, allora se $ab=ac\Rightarrow b=c$.
> 
> **Dimostrazione**:
> 
> Supponiamo $ab=ac$, che è equivalente a $a(b-c)=0$, se $a$ non è divisore di zero allora $b-c=0\Rightarrow b=c$.
> 
> _Osservazione_, questo implica la legge di cancellazione in $\mathbb{Z}$.

# Risoluzione di Equazioni in A

Come anello $A$ prendiamo $A=\mathbb{Z},A=\mathbb{Z}/n\mathbb{Z}$.

Studieremo l'equazione lineare:

$$
aX=b \ \ a,b\in A
$$

$X$ viene detta **Indeterminata**. Se vogliamo risolverla significa che vogliamo trovare tutti gli $X$ tali che la soddisfano. Vediamo i casi semplici:

$$
A=\mathbb{Z}:2X=3 \text{ L'insieme delle soluzioni è } \{ x\in \mathbb{Z}:2x=3 \}=\emptyset
$$

Infatti sia $x$ soluzione dell'equazione $2x=3$ allora $x$ è un intero tale che moltiplicato per 2 mi dà 3 ovvero che $2|3$ che è impossibile. 

Cambiamo l'equazione:

$$
2X=6 \text{ Soluzioni:} \{ x\in \mathbb{Z}:2x=6 \}=\{ 3 \}
$$

In questo caso abbiamo una soluzione, in $\mathbb{Z}$. Osserviamo che utilizzando il T.F.A (Teorema Fondamentale dell'Aritmetica) $6=2\cdot 3$ e sia $x$ una soluzione allora $2x=2\cdot 3$ e utilizzando la legge di cancellazione su $2$ otteniamo $x=3$.

In generale una soluzione di $aX=b$ (sempre con $A=\mathbb{Z}$) esiste $\Leftrightarrow a|b$. Infatti se l'insieme delle soluzioni è _non vuoto_ e se $x$ è soluzione, si ha $ax=b\Leftrightarrow a|b$.

Allo stesso tempo se $a|b$ allora $\exists k\in \mathbb{Z} \ t.c. \ ak=b$ e posso prendere $x=k$.

---

Adesso vediamo cosa succede nel caso $A=\mathbb{Z}/n\mathbb{Z}$ con $n\in N^*$. Vogliamo risolvere:

$$
aX=b
$$

Nel caso in cui $A$ è un anello qualsiasi e $a\in A^X$ di inverso $a^{-1}$, possiamo moltiplicare termine a termine e ottenere:

$$
\underbrace{ a^{-1}\cdot a }_{ 1 } \cdot X=b\cdot a^{-1}
$$

E quindi otteniamo che $x=b\cdot a^{-1}$ che è **un'unica soluzione**.

> [!info] Indeterminata X
> Con $X$ indichiamo l'insieme delle soluzioni mentre con $x$ un elemento di questo insieme.

Se per esempio $A=K$ campo (anelli dove ogni elemento non nullo è invertibile, visto che un elemento invertibile non è divisore di zero allora un campo è **sempre dominio di integrità**, infatti l'unico divisore di zero è zero), allora in questo caso l'equazione $aX=b$ con $a\neq 0$ ammette sempre l'unica soluzione $x=a^{-1}\cdot b$.

Torniamo nel caso $\mathbb{Z}/n\mathbb{Z}$ e scriviamo la seguente

**Proposizione**: 

$$
aX=b \ \ a,b\in A=\mathbb{Z}/n\mathbb{Z}
$$

L'equazione ammette soluzioni **se e solo se** dati $a=\overline\alpha,b=\overline\beta \ (\alpha,\beta\in \mathbb{Z})$, $MCD(\alpha,n)|\beta$ 

**Dimostrazione**:

Sia $\overline{x}$ una soluzione, questo significa che $a\overline{x}=b$, quindi sostituendo $\overline{a}\cdot\overline{x}=\overline{\beta}$ e questo significa che $\alpha x-\beta=nk \ \ \  \exists k\in \mathbb{Z}$. Se spostiamo i membri possiamo scrivere $\alpha x-nk=\beta$ e questo implica che $\beta\in \alpha \mathbb{Z}+n\mathbb{Z}$, notiamo che $\alpha \mathbb{Z}+n\mathbb{Z}=\delta \mathbb{Z}$ dove $\delta=MCD(\alpha,n)$ e quindi possiamo scrivere che $\delta|\beta$ e questo dimostra che **se ammette soluzioni allora $MCD(\alpha,n)|\beta$**.

Adesso dimostriamola nel senso opposto.

Supponiamo quindi che $\delta=MCD(\alpha,n)|\beta$ quindi possiamo scrivere che $\beta=\delta x$ e questo significa che $\beta\in \alpha \mathbb{Z}+n\mathbb{Z}\Leftrightarrow\exists u,v\in \mathbb{Z} \ t.c. \ \beta=u\alpha+vn\Leftrightarrow(\text{Riduzione modulo n})\beta\equiv u\alpha(mod \ n.)\Leftrightarrow\overline{\beta}=\overline{u}\overline{\alpha}$. Possiamo chiamare $\overline{u}=x$ e abbiamo trovato la soluzione.

---

_Esempio_

L'equazione $\overline{3}\cdot x=\overline{0}$ in $A=\mathbb{Z}/6\mathbb{Z}$ quindi abbiamo che $\alpha=3,\beta=0, n=6$ e $MCD(\alpha,6)=3|\beta$ e quindi ci sono soluzioni: $x=\overline{2}, x=\overline{4}, x=\overline{0}$, questo è l'insieme delle soluzioni.

**Lemma**

Prendiamo $a,b,c\in \mathbb{Z}$ se $a,b|c$ e $MCD(a,b)=1$ allora $ab|c$.

**Dimostrazione**

Sappiamo che $a,b|c\Leftrightarrow c=ak=bh$ ma questo vuol anche dire che $ak=bh$ e quindi $a|bh$. Notiamo che se $MCD(a,b)=1$ allora implica che $a|h$ e quindi $ab|c$, mostriamolo.

$MCD(a,b)=1\Leftrightarrow b\text{ è invertibile modulo a}\Rightarrow \exists b' \ t.c. \ bb'\in 1+a\mathbb{Z}$ (equivalente a dire che $bb'$ appartiene alla classe di 1 modulo $a$).

Possiamo dire che $a|bh\Rightarrow ab'|\underbrace{ b\cdot b'\cdot h }_{ (1+ak)\cdot h \ \exists k\in \mathbb{Z}}$ adesso facendo un po' di manipolazioni:

$$
\begin{align*}
&ab'=h+ahk \\
&ab'-ahk=h \\
&a(b'-hk)=h\Rightarrow a|h
\end{align*}
$$

---

# Teorema Cinese dei Resti
È un modo di risoluzione di sistemi di equazioni lineari a coefficienti interi, queste equazioni sono di tipo congruenziale.

Prendiamo $r_{1},\dots,r_{s}\in \mathbb{N}^*$ e supponiamo che $MCD(r_{i},r_{j}=1) \ \forall i\neq j$ quindi sono 2 a 2 primi fra loro. Inoltre consideriamo degli interi $c_{1},\dots,c_{s}\in \mathbb{Z}$, allora il sistema di congruenze:

$$
*\begin{cases}
X\equiv c_1 \ \text{mod }r_{1} \\
X\equiv c_{2} \ \text{mod }r_{2} \\
\dots \\
X\equiv c_{s} \ \text{mod }r_{s}
\end{cases}
$$

Questo sistema ha un'unica soluzione modulo $R:=r_{1}\cdot ... \cdot r_{s}$. Ovvero, l'insieme $\mathcal{E}_{*}=\{ x \text{ soluzione in } \mathbb{Z} \text{ di *} \}$ è della forma $x_{0}+\mathbb{Z}R$. Ricordiamo che abbiamo $X$ indeterminata che è una sola e abbiamo $s$ equazioni congruenziali.

Calcoliamo una soluzione particolare $x_{0}$ del sistema.

Poniamo $R_{i}:=\frac{R}{r_{i}}=r_{1}\cdot...\cdot \cancel{r_{i}}\cdot...\cdot r_{s}$ ovvero il prodotto fra tutti gli $r$ senza $r_{i}$, notare che $MCD(R_{i},r_{i})=1$ questo vuol dire che $\overline{R_{i}}$ con $R_{i}\in \mathbb{Z}/r_{i}\mathbb{Z}$ è invertibile, ovvero $\exists\overline{S_{i}}\in \mathbb{Z}/r_{i}\mathbb{Z} \ t.c. \ \overline{R_{i}}\cdot \overline{S_{i}}=\overline{1}$ allora questo implica che moltiplicando possiamo scrivere $\overline{R_{i}}\cdot\underbrace{ \overline{S_{i}}\cdot \overline{c_{i}} }_{ =:\overline{y_{i}}\in \mathbb{Z}/r_{i}\mathbb{Z} }=\overline{c_{i}}$, in questo modo abbiamo costruito elementi $\overline{y_{i}},\dots,\overline{y_{s}}$ ciascuno in $\mathbb{Z}/r_{i\mathbb{Z}}$.

_Dimostriamo che_ $x_{0}=\sum\limits_{{i=1}}^s y_{i}R_{i}\in \mathbb{Z}$ è soluzione di $*$.

Se $i\neq j$ allora abbiamo che $r_{i}|R_{j}$ quindi $x_{0}=\sum\limits_{j=1}^s y_{j}R_{j}$ e siccome $R_{j}$ è divisibile da tutti gli $r_{i}$ che sono diversi da $r_{j}$ possiamo scrivere $x_{0}=\underbrace{ \sum\limits_{j=1,j\neq i}^s y_{j}R_{j} }_{ \equiv 0 \text{ mod }r_{i} }+y_{i}R_{i}\equiv y_{i}R_{i}\text{ mod }r_{i}\equiv c_{i}\text{ mod }r_{i}$ e questo è valido $\forall i=1,\dots ,s$. Dunque $x_{0}=\sum\limits_{j} y_{j}R_{j}$ è una soluzione particolare del nostro sistema $*$.

Adesso vogliamo trovare tutte le soluzioni e non soltanto una. **Sistema Omogeneo Associato**

$$
*_{H}\begin{cases}
X\equiv 0 \ \text{mod }r_{1} \\
X\equiv 0 \ \text{mod }r_{2} \\
\dots \\
X\equiv 0 \ \text{mod }r_{s}
\end{cases}
$$

Ovvero $x\equiv 0\text{ mod } r_{i}$ con $i=1,\dots,s$, quali sono tutte le soluzioni?

$$
\begin{align*}
&x\equiv 0\text{ mod} r_{1}\Leftrightarrow r_{1}|x \\
&x\equiv 0\text{ mod} r_{2}\Leftrightarrow r_{2}|x \\
&\text{Ma } r_{1} \ e \ r_{2} \text{ sono primi fra loro quindi (lemma) } r_{1}r_{2}|x \\
&x\equiv 0\text{ mod} r_{3}\Leftrightarrow r_{3}|x \\
&\text{Ma } MCD(r_{3},r_{1},r_{2})=1 \Rightarrow r_{1},r_{2},r_{3}|x \\
&\text{Iterando fino a }r_{s} \to R:=r_{1}\cdots r_{s}|x
\end{align*}
$$

Le soluzioni di questo sistema quindi sono tutti i multipli di $R$ e quindi $R\mathbb{Z}$. Scriviamolo:

L'insieme delle soluzioni $\mathcal{E}_{H}:=R\mathbb{Z}$, concludiamo con la **proposizione**: L'insieme delle soluzioni di $*$ denotato $\mathcal{E}_{*}$ è dato da $x_{0}+R\mathbb{Z}$ ovvero il "traslato" dell'insieme di tutti i multipli di $R$ appunto traslato dalla soluzioni particolare $x_{0}$, dimostriamolo.

**Dimostrazione**:

$x_{0}+R\mathbb{Z}$ è contenuto nell'insieme delle soluzioni, infatti se $x\in x_{0}+R\mathbb{Z}$ allora posso scrivere $x=x_{0}+Rk, \exists k\in \mathbb{Z}$ ma $Rk\equiv 0$ mod $r_{i}$ $\forall i=1,\dots,s$ infatti $r_{i}|Rk$ e addizionando con $x_{0}$ che è soluzione particolare ottengo che $x\equiv c_{i}+0\equiv c_{i}$ mod $r_{i}$.

Dimostriamo adesso che l'insieme delle soluzioni è contenuto in $x_{0}+R\mathbb{Z}$, sia $x$ una soluzione di $*$, allora $x-x_{0}\equiv 0$ mod $r_{i}$ $\forall i=1,\dots,s$ e questo vuol dire che $x-x_{0}\in R\mathbb{Z} (lemma)$, questo implica che $x\in x_{0}+R\mathbb{Z}\Rightarrow\mathcal{E}_{*}\subset x_{0}+R\mathbb{Z}$.

![[are-we-cooked-cooked.gif]]

_We're so cooked :'(_

