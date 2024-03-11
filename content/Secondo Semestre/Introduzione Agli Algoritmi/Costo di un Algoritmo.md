Calcoleremo il costo degli algoritmi utilizzando il **criterio della misura di costo uniforme**.
Il costo computazionale lo possiamo vedere come una funzione **monotona non decrescente** che rappresenta il tempo di esecuzione in base alla dimensione dell'input.
Come prima cosa dobbiamo quindi definire la dimensione del nostro input che può essere il numero di elementi di una lista da ordinare, i nodi di un albero o il numero di elementi da cercare.

**Il costo computazionale è ritenuto valido solo asintoticamente, ovvero attraverso la notazione asintotica.**

## Pseudocodice
Per valutare il costo computazionale non si scrive il codice in un linguaggio specifico ma lo **pseudocodice** ovvero un linguaggio di programmazione informale:
- si usano i costrutti di base come _for, while, if_
- si può usare la nostra lingua naturale per specificare passaggi
- si possono omettere molti dettagli al fine di rappresentare soltanto la soluzione vera e propria

## Regole per valutare la complessità di un algoritmo
- Le **istruzioni elementari** hanno costo $\theta(1)$ (aritmetiche, lettura, assegnazione, if, stampa)
- Le **istruzioni iterative** hanno un costo pari alla somma dei costi massimi di ciascuna delle iterazioni, da notare che viene valutata anche la condizione (es. while) e che questa viene valutata una volta in più rispetto al numero delle iterazioni, ovvero quando l'iterazione termina.

## Dipendenza del costo dall'input
Un algoritmo potrebbe avere tempi di esecuzione diversi a seconda dell'input, in questo caso dobbiamo individuare prima di tutto i **casi migliore e peggiore**, capire quindi quale input è più vantaggioso e quale no.
É molto importante, a prescindere dall'input, trovare il tempo di esecuzione del caso peggiore in termini di $\theta$ o se non possibile arrotondarlo a $\ohm$ oppure $O$.

_Esempio: Troviamo il massimo in una lista di n valori_

```python
m = A[0] #Costo 1
for i in range(A): #Costo Θ(lunghezzaA)
	if i > m: #Costo 1
		m = i #Costo 1
print("Il valore massimo è: " + m) #Costo 1
```

$T(n) = \theta(1) + n[\theta(1) + \theta(1)] + \theta(1) = \theta(n)$

_All'interno dell'iterazione le operazione hanno tutte lo stesso costo quindi possiamo svolgere il prodotto_

In realtà la complessità sarebbe $lunghezza-1$ ma le costanti non le consideriamo nel calcolo dei limiti asintotici.

## Variazione dei tempi di esecuzione di un algoritmo in funzione del suo costo computazionale
Ipotizziamo di avere a disposizione una macchina in grado di svolgere un'operazione in un nanosecondo ($10^9$ operazioni al secondo) e supponiamo che la dimensione del problema sia $n=10^6$:
- Tempo di computazione $O(n)$ **1 millesimo di secondo**
- Tempo di computazione $O(nlogn)$ **20 millesimi di secondo**
- Tempo di computazione $O(n^2)$ **1000 secondi = 16 minuti**

E se il costo cresce esponenzialmente $O(2^n)$?
Anche se abbassassimo $n=100$ con la stessa macchina vista prima avremo un costo pari a $\frac{2^{100}}{10^9}=\frac{2^{{10}^{10}}}{10^{3^3}}=\frac{1024^{10}}{1000^3}=\frac{1000^{10}}{1000^3}=10^{21}\text{ secondi}$ ovvero circa $10^{10}$ **secoli**. 


> [!NOTE] Un algoritmo con una complessità esponenziale non serve a molto
> Anche con un avanzamento tecnologico un algoritmo del genere non è molto conveniente, ad esempio prendendo una macchina estremamente veloce in grado di risolvere un problema simile con $n=1000$ e prendendone un'altra 1000 volte più veloce, nello stesso periodo T riusciremo a risolvere soltanto un problema con $n=1010$, non abbiamo quindi fatto grandi progressi.

# Algoritmi Ricorsivi
Una funzione si dice ricorsiva quando chiama se stessa.
- Deve avere un caso base
- E un meccanismo di calcolo ricorsivo, ovvero come posso calcolare il valore successivo conoscendo quello che ho

In ambito informatico di solito con la ricorsione risolviamo tanti piccoli sottoproblemi e combinando le soluzioni otteniamo la soluzione al problema originale.

**Le chiamate a sottoproblemi devono sempre convergere ad un caso base per permettere la terminazione del programma**

Ogni funzione, ricorsiva o non, richiede una certa quantità di memoria per:
- Caricare il codice
- Passare i parametri
- Memorizzare il valore delle variabili

In generale le funzioni ricorsive hanno maggiori esigenze in termini di memoria delle funzioni non ricorsive

**Qualsiasi problema risolvibile con un algoritmo ricorsivo può essere risolto anche con un algoritmo iterativo**
Quando conviene quindi utilizzare un algoritmo ricorsivo?

- Quando permette di scrivere una soluzione in modo più chiaro e simile alla natura del problema
- Non conviene quando esiste una soluzione iterativa semplice e chiara
- Non conviene utilizzare la ricorsione quando è importante avere una buona efficienza

![[Pasted image 20240311230307.png]]

Abbiamo un costo elevato di spazio perchè ogni volta che andiamo in ricorsione creiamo una copia della lista con un elemento in meno, possiamo ottimizzare il codice passando un indice invece che delle copie della lista: 

![[Pasted image 20240311230422.png]]

**Costo di fibonacci iterativo e ricorsivo**

![[Pasted image 20240311230740.png]]

Il calcolo di Fibonacci ricorsivo ha costo in memoria molto elevato e vedremo più avanti un costo in tempo di $\theta(n^2)$ mentre la sua versione iterativi ha spazio $\theta(1)$ e in tempo $\theta(n)$
Questo perchè nella versione ricorsiva eseguiamo tantissimi calcoli che abbiamo già svolto precedentemente