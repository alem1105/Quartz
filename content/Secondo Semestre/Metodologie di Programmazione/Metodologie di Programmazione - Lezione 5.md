# Uscire da un ciclo
Può essere necessario uscire dal ciclo durante la sua esecuzione, si può fare tramite l'istruzione **break**, utilizzabile solo all'interno di un ciclo.

## Uscire dai cicli annidati
L'istruzione **break** rompe soltanto il ciclo corrente ma non quello più esterno (nel caso ci fosse).
Nel caso in cui volessimo rompere cicli annidati possiamo uscire con **break \<etichetta\>** e diamo l'etichetta al for che vogliamo rompere:

```java
outer:
for (int i = 0; i < h; i++)
{
	for (int j = 0; j < w; j++)
	{
		if (j == i) break outer;
	}
}
```

Quindi ad esempio con i cicli while possiamo creare dei cicli infinti e farli terminare solo in determinati casi.

# Saltare all'iterazione successiva
In alcuni casi con la parola chiave **continue** possiamo mandare il ciclo all'iterazione successiva

```java
int conta = 0;
for (int k = 0; k < s.length(); k++) {
	char c = s.charAt(k);
	if (!Character.isDigit(c)) continue;
}
```

# Array
Un array è un gruppo di variabili tutte dello stesso tipo (elementi).
**Gli array** sono oggetti quindi le variabili di tipo array contengono il riferimento all'array, i suoi elementi possono essere di tipi primitivi oppure riferimenti ad altri oggetti.

_Dichiarazione di un array senza valori:_

```java
int[] a;
a = new int[10];
```

![[Screenshot 2024-03-14 alle 13.17.52.png]]

Posso anche omettere la dimensione del vettore ma esplicitare i valori al suo interno

```java
int[] a = new int[10];
//Oppure
int[] a = new int[] {1,2,3,4,5,6,7,8,9,10};
```

