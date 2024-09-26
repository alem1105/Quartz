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
