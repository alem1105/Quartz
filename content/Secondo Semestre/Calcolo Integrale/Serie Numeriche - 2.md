Introduciamo il concetto di serie considerando una **successione** di numeri Reali.

$$
a_1, a_2, a_3,...,a_n
$$

Calcolare la **somma** di tutti questi numeri equivale a calcolare la **serie**

$$
a_1+a_2+...+a_n=\sum_{n=1}^{+\infty}a_n
$$

Dove $a_n$ è detto **termine generale** della serie.
Questa scrittura nei termini generali delle somme non ha molto senso perché non stiamo sommando un numero finito di numeri, ma consideriamo invece questa scrittura:

$$
\begin{align}
&s_1=a_1\\
&s_2=a_1+a_2\\
&s_3=a_1+a_2+a_3\\
&s_n=a_1+a_2+a_3+...+a_n
\end{align}
$$

Quindi se noi volessimo sapere la somma di tutti gli $n$ termini ci basta calcolare:

$$
s=\lim_{n\rightarrow+\infty}s_n
$$

E a seconda del risultato si possono verificare **3 casi**:
- $l\in\mathbb{R}$: Si dice che la serie **converge**
- $\pm\infty$: Si dice che la serie **diverge**
- Se il limite non esiste la serie si dice **indeterminata**

Un esempio di serie indeterminata è la seguente:

$$
\sum_{n=0}^{+\infty}(-1)^n=+1-1+1-1+1+...
$$

Infatti la serie non si **stabilizzerà mai**.

# Serie Geometriche

Consideriamo di avere un numero $q\in\mathbb{R}$, si definisce serie geometrica la seguente serie:

$$
\sum_{n=0}^{+\infty}q^n
$$

Quindi una serie si dice **geometrica** quando alla base abbiamo una quantità **indipendente da n**


> [!question] Perché si dice geometrica?
> Perché tutti i termini della serie costituiscono una **progressione geometrica** ovvero quando il **rapporto** tra un termine e il suo precedente è costante.
> _Esempio con q = 2:_
> $1+2+4+8+16+32$   Il rapporto è sempre uguale a 2 tranne per il primo termine che ovviamente non può essere confrontato con altro

Secondo la teoria delle progressioni se $q\neq1$ la **somma dei primi n numeri** equivale a:

$$
S_n=\frac{1-q^n}{1-q} \ \ \ \lim_{n\rightarrow+\infty}S_n=S
$$

Grazie a questa formula possiamo studiare dei casi:

- $|q|<1$: In questo caso il termine $q^n$ **tenderà a 0** e quindi la serie **converge** al valore $\frac{1}{1-q}$
- $q=1$: È banale notare che stiamo sommando infinite volte 1 quindi la serie **diverge**
- $q>1$: Anche in questo caso notiamo che andremo a sommare numeri sempre più grandi quindi la serie **diverge**
- $q<-1$: La serie oscilla verso numeri sempre più grandi ma sia positivi che negativi, ad esempio se prendiamo $q=-2$ otteniamo: $1-2+4-8+16-32+64-...$

> [!danger] Attenzione agli indici
> La formula per calcolare il valore della somma vale quando contiamo tutti i termini quindi partendo da $n=0$, nel caso in cui partissimo da un indice diverso dobbiamo togliere i primi termini aggiuntivi.
> _Esempio:_
> $\sum\limits_{n=2}^{+\infty}(\frac{1}{2})^{n+2}=\frac{1}{4}\sum\limits_{n=2}^{+\infty}(\frac{1}{2})^n=\frac{1}{4}[\frac{1}{1-1/2}-1-1/2]=\frac{1}{8}$

# Criterio del rapporto

Consideriamo di avere una serie **a infiniti termini positivi**, se:

$$
\exists\ h \in\mathbb{R} \ \ \ 0<h<1 \text{ tale che } \frac{a_{n+1}}{a_n}\leq h
$$

Qualsiasi sia $n$ o anche da un certo $n$ in poi, se esiste possiamo dire che la **serie converge**, se invece il rapporto è **maggiore o uguale a 1** la serie **diverge**

Per svolgere gli esercizi però è utile considerare casi diversi:

$$
\begin{align}
&\lim_{n\rightarrow+\infty}\frac{a_{n+1}}{a_n}=l\\
\\
&l<1 \text{: La serie converge}\\
&l>1 \text{: La serie diverge}\\
&l=1 \text{: Dobbiamo utilizzare un altro metodo}
\end{align}
$$

_Esempi:_

![[Pasted image 20240324100515.png]]

![[Pasted image 20240324100643.png]]

# Criterio della Radice

Consideriamo sempre una serie a infiniti termini positivi, il criterio della radice è molto simile a quello del rapporto visto precedentemente, infatti abbiamo li stessi 3 casi ma con un procedimento diverso:

$$
\begin{align}
&\sqrt[n]a_n=l\\
\\
&l<1 \text{: La serie converge}\\
&l>1 \text{: La serie diverge}\\
&l=1 \text{: Dobbiamo utilizzare un altro metodo}
\end{align}
$$

_Esempi:_

![[Pasted image 20240324102454.png]]

![[Pasted image 20240324102635.png]]

# Serie Armonica

La serie armonica è una serie dove il termine generale è $\frac{1}{n}$ quindi la serie è uguale a:

$$
\sum_{n=1}^{+\infty}\frac{1}{n}
$$

Utilizzando metodi di confronto non riusciremo a dimostrare che questa serie **diverge**, come facciamo quindi?
La serie armonica equivale quindi a:

$$
\begin{align}
1+\frac{1}{2}+\frac{1}{3}+\frac{1}{4}+\frac{1}{5}+...
\end{align}
$$

Per dimostrare che converge possiamo fare dei piccoli raggruppamenti e notiamo che andremo a sommare sempre $\frac{1}{2}$ :

$$
\begin{align}
1 + \frac{1}{2} + (\frac{1}{3} + \frac{1}{4})  + (\frac{1}{5} + \frac{1}{6} + \frac{1}{7} + \frac{1}{8}) + (\frac{1}{9}+...+ \frac{1}{16})
\end{align}
$$

> [!info] Teorema
> Se una serie **converge** allora la successione è **infinitesima**, ma se una successione è infinitesima **non** è detto che la serie converga.
> _Esempio la serie armonica_
> 

# Serie Armonica Generalizzata

Il termine generale delle serie armoniche è $\frac{1}{n^k}$ con $k\in\mathbb{R}$ quindi la serie è:

$$
\sum_{n=1}^{+\infty}\frac{1}{n^k}
$$
Se:
- $k>1$: La serie **converge**
- $k\leq 1$: La serie **diverge**

# Criterio del Confronto

Consideriamo di avere due serie a termini positivi

$$
\begin{align}
&\sum_{n=1}^{+\infty}a_n=a_1+a_2+...+a_n \\
&\sum_{n=1}^{+\infty}b_n=b_1+b_2+...+b_n
\end{align}
$$

Adesso supponiamo che ogni termine della prima serie sia $a_n\leq b_n$, in questo caso si dice che la serie $a_n$ è la **minorante** di $b_n$ oppure che quest'ultima è la **maggiorante** di $a_n$

Adesso si possono verificare più casi:

- Se $\sum\limits_{n=1}^{+\infty}b_n$ converge allora anche $\sum\limits_{n=1}^{+\infty}a_n$ converge
- Se $\sum\limits_{n=1}^{+\infty}a_n$ diverge allora anche $\sum\limits_{n=1}^{+\infty}b_n$ diverge

**Tutti gli altri casi non ci danno informazioni utili**

_Esempio_

![[Pasted image 20240324181642.png]]

![[Pasted image 20240324182953.png]]

# Criterio del Confronto Asintotico