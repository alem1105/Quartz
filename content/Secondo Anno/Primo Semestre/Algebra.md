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


> [!warning]  Da capire 😢
> Per vedere che $\phi$ è biiettiva poniamo per $y\in f(X), \psi(y)=\{ x\in X:f(x)=y \}$ tale insieme è $\neq \emptyset$ quindi $f$ è suriettiva nella sua immagine. $\psi(y)=[x]$ con $f(x)=y$ di modo che $\psi=\phi^{-1}$.

