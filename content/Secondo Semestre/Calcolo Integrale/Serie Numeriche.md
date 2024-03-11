
> [!INFO] Obiettivo
> Data una successione ${a_n}$, vogliamo sommare tutti gli $a_n$

Per semplicità non scriveremo l'intera somma ma utilizziamo le **sommatorie**, quindi ad esempio data la successione $a_n = 1/n$ possiamo scrivere:
$$\sum_{n=1}^{100}a_n=1+1/2+1/3+...+1/100$$
In questo modo stiamo indicando la somma dei primi 100 valori di $a_n$.

Possiamo ovviamente sommare un numero $n$ di valori qualsiasi, ma **cosa significa sommare i $+\infty$ valori?
Significa sommare tutti i valori della successione**.

Dobbiamo fare attenzione però all'**ordine in cui effettuiamo queste somme**, infatti, se ad esempio $a_n=(-1)^n$ posso ottenere due valori:
- $(-1+1)(-1+1)(-1+1) = 0$
- Ma mettendo in evidenza un $-1$:
  $-1 (+1-1) (+1-1) (+1-1) = -1$
  _Le parentesi servono soltanto per evidenziare i raggruppamenti_

> [!warning] Ordine delle somme
> L'ordine lo definisce la successione stessa, dobbiamo aggiornare il nostro risultato ogni volta e vedere se questo si stabilizza.
> Nel caso dell'esempio precedente non si stabilizzerà mai infatti oscilleremo sempre tra 0 e -1

# Somme Parziali

**Data $\{a_k\}_{k\in\mathbb{N}}$ poniamo $S_n=\sum_{k=1}^{n}a_k$, la somma degli $n$ termini.**

> [!Info] Definizione di Serie
> Data una successione $\{a_n\}_{n\in\mathbb{N}}$ poniamo $\sum_{k=1}^{+\infty}a_k = \lim_{n\rightarrow +\infty}S_n = \lim_{n\rightarrow +\infty}\sum_{k=1}^na_k$
> Ovvero per ottenere una serie, la somma di tutti i valori di una successione, poniamo il limite a $+\infty$ della somma parziale, in questo modo sommeremo sempre più termini ottenendo un risultato che si stabilizza in un valore, **SE ESISTE IL LIMITE**.

A seconda del **valore del limite** si possono verificare più casi:

- Se $\lim_{n\rightarrow +\infty}S_n$ Esiste ed è finito, $S\in\mathbb{R}$, allora diremo che la **serie è convergente**.
- Se $S_n\rightarrow \pm\infty$ diremo che la serie **diverge** rispettivamente a $\pm\infty$.
- Se $S_n$ oscilla allora la serie **non è ben definita** _(oscilla/non regolare)_

## Esempi:

![[photo_2024-02-26_17-43-05.jpg]]


> [!tip] Convergenza
> Una serie converge se $a_n\neq 0$ solo per un numero finito di termini

> [!example] Quindi in generale abbiamo 3 casi:
> Definitivamente: Per un $n$ abbastanza grande
> - Se $\exists r>0:$ definitivamente $a_n\geq r$ allora $\sum\limits_{n=1}^{+\infty} a_n=+\infty$
> - $a_n=(-1)^n$ => $\sum\limits^{+\infty}_{n=1} (-1)^n$ è indeterminata
> - Se $a_n$ è definitivamente uguale a 0 allora $\sum\limits_{n=1}^{+\infty} a_n$ converge

--- 
# Teorema
Sia $\{a_n\}$ una successione se $\sum\limits_{n=1}^{+\infty} a_n$ **converge** allora $a_n$ è **infinitesima** (tende a 0).
_Dimostrazione:_
$a_n = S_n - S_{n-1}$ infatti:

$$
\begin{aligned}
S_n &= a_1+a_2+...+a_{n-1}+a_n \\
S_{n-1} &= a_1+a_2+...+a_{n-1}
\end{aligned}
$$

Notiamo che se effettuiamo la differenza possiamo cancellare tutti i termini tranne $a_n$
Quindi possiamo scrivere che:

$$
\begin{align}
\lim_{n\rightarrow +\infty} a_n = \lim_{n\rightarrow +\infty} (S_n - S_{n-1}) \\
\lim_{n\rightarrow +\infty}S_n - \lim_{n\rightarrow +\infty} S_{n-1} = S - S = 0
\end{align}
$$

Infatti entrambi i limiti danno come risultato un valore $S$ dato che la serie è **convergente per ipotesi**, importante ricordare che $S-S=0$ è il valore del limite infatti le due $S$ non esattamente uguali ma molto simili.
**Quindi se il limite fa 0 la serie è infinitesima**


> [!warning] Differenze tra limiti e serie
> Prendiamo la serie numerica $\sum\limits_{n=1}^{+\infty} \frac{n^2+5}{2n^2+3}=+\infty$
> Dobbiamo fare attenzione perché il limite vale $\frac{1}{2}$ e noi stiamo sommando un numero infinito di $\frac{1}{2}$ quindi la serie vale $+\infty$.

**Caso inverso**
Se $a_n$ è **infinitesima** => $\sum\limits_{n=1}^{+\infty} a_n$ **converge**?

No, possiamo prendere come esempio la **serie armonica**:

$$
\begin{align}
a_n = \frac{1}{n}; \ \ \sum_{n=1}^{+\infty}\frac{1}{n}=+\infty
\end{align}
$$

Infatti questa serie si sviluppa in questo modo:

$$
\begin{align}
1 + \frac{1}{2} + (\frac{1}{3} + \frac{1}{4})  + (\frac{1}{5} + \frac{1}{6} + \frac{1}{7} + \frac{1}{8}) + (\frac{1}{9}+...+ \frac{1}{16})
\end{align}
$$

Notiamo che raggruppando i termini in potenze di 2, otteniamo sempre un valore **maggiore o uguale a 1/2**, quindi anche se avremo bisogno di sempre più termini prima o poi aggiungeremo 1/2 al nostro risultato.

---

# Serie Geometriche
Sia $q \in \mathbb{R} \ \ \sum\limits_{n=0}^{+\infty} q^n$ è la serie geometrica **di ragione q**.

_Esempio:_

$$
\begin{align}
&\sum^{+\infty}_{n=1}\frac{1}{2^n} = 1 \\
&S_1=\frac{1}{2};S_2=\frac{3}{4};S_3=\frac{7}{8} \\
\\
&\text{in generale } S_n=1-\frac{1}{2^n} \\
\\
&\sum_{n=1}^{+\infty}\frac{1}{2^n}=\lim_{n\rightarrow +\infty}S_n=\lim_{n\rightarrow +\infty} 1-\frac{1}{2^n}=1-0=1
\end{align}
$$

Vediamo cosa possiamo ottenere facendo dei raggruppamenti con questa tipologia di serie:

$$
\begin{align}
S_n &= 1 + q + q^2 + ... +q^n \\
q * S_n&=q+q^2+...+q^{n+1}
\end{align}
$$

Adesso possiamo fare **la differenza** $S_n - q*S_n$ ottenendo $S_n(1-q) = 1-q^{n+1}$ infatti nel termine a sinistra abbiamo effettuato un **raggruppamento** mentre per il risultato della differenza ci basta notare nelle due successioni sopra che togliendo i termini rimaniamo soltanto con $1-q^{n+1}$.

In generale otteniamo quindi che

$$
S_n = \frac{1-q^{n+1}}{1-q} \ \ \ \text{Se q $\neq$ 1}
$$


> [!example] **Vediamo ora tutti i casi che possiamo trovare:**
> Sia $q\neq 0$
> La serie geometrica di ragione $q$ $\sum\limits_{n=0}^{+\infty}q^n$:
> - $\sum\limits_{n=0}^{+\infty}q^n = +\infty$ se $q\geq 1$
> - $\sum\limits_{n=0}^{+\infty}q^n = \frac{1}{1-q}$ se $q\neq 0$ e $-1<q<1$
> - $\sum\limits_{n=0}^{+\infty}q^n$ è indeterminata se $q\leq -1$

> _Esempio_
> $\sum\limits_{n=0}^{+\infty}\frac{1}{4^n} = \frac{1}{1-1/4} = 4/3$

**E se partiamo da un n diverso da 0?**

$$
\begin{align}
&\sum\limits_{n=4}^{+\infty}\frac{1}{3^n} \\
\\
&\text{Rappresentiamo la successione e notiamo che:} \\
&\frac{1}{3^4}+\frac{1}{3^5}+\frac{1}{3^6}+... = \frac{1}{3^4}(1+\frac{1}{3}+\frac{1}{3^2}+...) \\
&\text{Quindi possiamo risolvere il nostro problema moltiplicando $\frac{1}{3^4}$} \\
&\text{per il risultato della successione che parte da 0, come nei casi visti sopra}\\
\\
&\sum\limits_{n=4}^{+\infty}\frac{1}{3^n} = \frac{1}{3^4}*\frac{1}{1-\frac{1}{3}} = \frac{3}{2*3^4} = \frac{1}{2*3^3}
\end{align}
$$

---

# Serie Armoniche Generalizzate
 Possiamo generalizzare la serie armonica elevando $n$ ad un valore $\alpha$, ottenendo quindi $\sum\limits_{n=1}^{+\infty}$

Analizziamo due casi:
- $\alpha \leq 1$: Notiamo che $\frac{1}{n^\alpha}\geq\frac{1}{n}$ quindi anche in questo caso abbiamo che $\sum\limits_{n=1}^{+\infty}\frac{1}{n^\alpha}=+\infty$
- $a>1$: Non lo dimostriamo ma $\sum\limits_{n=1}^{+\infty}\frac{1}{n^\alpha}$ converge

# Serie Telescopiche
In queste successioni abbiamo sia termini positivi che negativi che si _"mangiano"_ a vicenda lasciando soltanto il primo termine e l'ultimo (anche se molto vicino allo 0).

$$
\begin{align}
&a_k=\frac{1}{k(k+1)}=\frac{1}{k}-\frac{1}{k+1}=b_k-b_{k+1} \ \ \text{dove} \ b_k=\frac{1}{k} \\
&S_1=1-\frac{1}{2};S_2=1-\frac{1}{2}+\frac{1}{2}-\frac{1}{3}\\
&S_n = 1-\frac{1}{2}+\frac{1}{2}-\frac{1}{3}+\frac{1}{3}+...-\frac{1}{n}+\frac{1}{n}-\frac{1}{n+1} = 1 - \frac{1}{n+1}\\
&\text{Quindi:}\\
&\lim\limits_{n\rightarrow +\infty}S_n = 1
\end{align}
$$

Otteniamo quindi che

$$
\sum_{n=1}^{+\infty}\frac{1}{n(n+1)} = 1
$$

**In Generale:**
Sia $\{b_n\}$ una successione infinitesima e sia $a_n=b_n-b_{n+1}$ allora $\sum\limits_{n=1}^{+\infty}a_n=b_1$

> [!attention] Attenzione
> $\lim\limits_{n\rightarrow +\infty}S_{2n}=+\infty$ mentre $\lim\limits_{n\rightarrow +\infty}S_{2n+1}=-\infty$, infatti abbiamo una successione del tipo $-2+4-8+16-32...$, la successione è indeterminata infatti:
> Se $\nexists\lim\limits_{n\rightarrow +\infty}S_n$ allora $\sum\limits_{n=1}^{+\infty}...$ è indeterminata.

**Teorema**
Siano $a_n\geq 0$ $\forall n \in \mathbb{N}$ allora $\sum\limits_{n=1}^{+\infty}a_n$ o converge o diverge a $+\infty$.
_Dimostrazione_
Se $\{S_n\}_{n\in\mathbb{N}}$ è una successione monotona non decrescente allora $\exists\lim\limits_{n\rightarrow +\infty}S_n=$ finito o $+\infty$

_Esempi_
$\sum\limits_{n=1}^{+\infty}\frac{n^2+7}{n^2+5}=+\infty$ infatti $\lim\limits_{n\rightarrow +\infty}\frac{n^2+7}{n^2+5}=1$; I termini sono definitivamente positivi quindi non posso oscillare.

$\sum\limits_{n=1}^{+\infty}\frac{1}{n^\alpha}$ Converge? Se e solo se $\alpha > 1$

$\sum\limits_{n=1}^{+\infty}sen(\frac{1}{n^2})$ posso studiare l'andamento della funzione e notare che la serie converge o anche confrontarla, infatti:

**Teorema (Confronto)**
Siano $a_n,b_n\geq 0$ $\forall n\in \mathbb{N}$ con $a_n\leq b_n$ $\forall n \in \mathbb{N}$

Se $\sum\limits_{n=1}^{+\infty}b_n$ converge allora $\sum\limits_{n=1}^{+\infty}a_n$ converge

Quindi ad esempio se non abbiamo una serie geometrica o telescopica possiamo comunque confrontarla con una di queste e capire il suo risultato.

# Teorema del confronto asintotico
Siano $a_n,b_n \geq 0 \ \ \forall n$, se $\lim\limits_{n\rightarrow +\infty}\frac{a_n}{b_n}=l\in(0,+\infty)$ allora $\sum\limits_{n=1}^{+\infty}a_n$ converge allora  $\sum\limits_{n=1}^{+\infty}b_n$ converge

Più nello specifico **si comportano allo stesso modo**, quindi se una converge o diverge allora anche l'altra.
Quindi analizzando anche altri case, in fine otteniamo:
- Se $\lim\limits_{n\rightarrow +\infty}\frac{a_n}{b_n}=l\in(0,+\infty)$ allora $\sum\limits_{n=1}^{+\infty}a_n = \sum\limits_{n=1}^{+\infty}b_n$
- Se $\lim\limits_{n\rightarrow +\infty}\frac{a_n}{b_n}=0$ e se $\sum\limits_{n=1}^{+\infty}b_n$ converge allora anche $\sum\limits_{n=1}^{+\infty}a_n$ converge
- Se $\lim\limits_{n\rightarrow +\infty}\frac{a_n}{b_n}=+\infty$ e se $\sum\limits_{n=1}^{+\infty}b_n$ diverge allora anche $\sum\limits_{n=1}^{+\infty}a_n$ diverge

_Esempi:_
![[Pasted image 20240308154015.png]]
![[Pasted image 20240308154101.png]]
![[Pasted image 20240308154120.png]]

**Con serie Infinitesima**
![[Pasted image 20240308154214.png]]

---

![[Pasted image 20240308154249.png]]

# Esempi Esercizi

$$
\begin{align}
&\sum_{n=1}^{+\infty}e^{\frac{1}{n}}-1 \\
&\text{Ricordando il ilimite notevole} \\
&\lim_{x\rightarrow 0}\frac{e^x-1}{x}=1 \\
&\text{Posso quindi confrontare con} \frac{1}{n} \\
&\lim_{x\rightarrow +\infty}\frac{e^{\frac{1}{n}}-1}{\frac{1}{n}}=1 \\
&\text{Quindi} \\
&\sum_{n=1}^{+\infty}\frac{1}{n}=+\infty \rightarrow \sum_{n=1}^{+\infty}e^{\frac{1}{n}}-1=+\infty
\end{align}
$$

--- 

![[Pasted image 20240311221610.png]]

# Completezza Decimale

$$
\begin{align}
&r=0.785... = \frac{7}{10} +\frac{8}{10^2}+\frac{5}{10^3}\\
&\sum_{n=1}^{+\infty}\frac{a_n}{10^n}
\end{align}
$$

**Osservazione**

$$
\begin{align}
&0.\overline{9}=\sum_{n=1}^{+\infty}\frac{9}{10^n}=9\sum_{n=1}^{+\infty}(\frac{1}{10})^n \\
&\text{Sappiamo che la sommatoria è una serie geometrica che converge}\\
&\text{Siccome parte da 1 togliamo il primo valore e otteniamo che converge a:}\\
&9*\frac{1/10}{1-1/10}=\frac{9/10}{9/10}=1
\end{align}
$$

Abbiamo utilizzato la formula per le serie geometriche $\frac{1}{1-q}$ ma sottraendo anche il primo elemento ovvero 1 quindi $\frac{1}{1-q}-1=\frac{q}{1-q}$.

# Criteri Radici e Confronto
$\sum\limits_{n=1}^{+\infty}a_n$ Si comporta come $\sum\limits_{n=1}^{+\infty}q^n$ ? Con quale $q$?

Oltre al confronto asintotico possiamo utilizzare altri due metodi:

- Rapporto $\frac{a_{n+1}}{a_n}$
- Radice n-esima $\sqrt[n]a_n$

Vediamo meglio:
Siano $a_n > 0 \ \ \ \forall n \in \mathbb{N}$

Supponiamo che 

$$
\begin{align}
&\lim_{n\rightarrow +\infty}\sqrt[n]a_n = l \\
\\
&\lim_{n\rightarrow +\infty}\frac{a_{n+1}}{a_n} = l
\end{align}
$$

Allora:

- Se $0 \leq l < 1$ allora $\sum\limits_{n=1}^{+\infty}a_n$ converge
- Se $l>1$ allora $\sum\limits_{n=1}^{+\infty}a_n = +\infty$
- Se $l=1$ non possiamo dire nulla

**Osservazione**

Se $a_n = \frac{1}{n^\alpha}$ i due metodi falliscono, infatti da notare che praticamente sempre i due metodi sono equivalenti.

**Se $a_n$ cambia cosa facciamo?

![[Pasted image 20240311223539.png]]

**Altra dimostrazione utile**

![[Pasted image 20240311223841.png]]

