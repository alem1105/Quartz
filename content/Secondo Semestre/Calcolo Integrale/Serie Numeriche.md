
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
