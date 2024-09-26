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
