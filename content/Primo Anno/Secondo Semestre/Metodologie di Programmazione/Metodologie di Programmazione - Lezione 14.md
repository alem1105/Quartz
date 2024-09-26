# Ricorsione
Dato un problema, individuiamo:
- **Caso Base**: Problema di dimensione minima e calcolabile
- **Passo Ricorsivo**: Passo in cui si riduce l'attuale problema in uno o più sottoproblemi di dimensione minore fino ad arrivare ad un caso base.

_Esempio Fattoriale_

```java
public int fattorialeRicorsivo(int n) {
	if (n == 0) return 1;
	return n * fattorialeRicorsivo(n - 1);
}
```

Ogni volta che viene effettuata una chiamata viene creato un ambiente chiamato **redord di attivazione** che contiene la zona di memoria delle variabili locali del metodo e l'indirizzo di ritorno al metodo chiamante, ad ogni chiamata il record corrispondente viene **aggiunto allo stack**.
Lo stack è la **pila** dei record di attivazione delle chiamate effettuate.

![[Pasted image 20240507093653.png]]


> [!info] Casi Base
> È importante definire i giusti casi base, infatti se ad esempio chiamiamo _fattoriale(-1)_ il nostro programma andrà in ricorsione infinita fino a riempiere lo stack e interrompere forzatamente l'esecuzione

Possiamo ad esempio creare una nostra eccezione per gestire meglio i casi base:

```java
public int fattorialRicorsivo(int n) throw NumeroNonAmmessoException
{
	if (n < 0) throw new NumeroNonAmmessoException(n);
	if (n == 0) return 1;
	return n * fattorialeRicorsivo(n - 1);
}
public class NumeroNonAmmessoException extends Exception
{
	private int n;
	public NumeroNonAmmessoException(int n)
	{
		this.n = n;
	}
	public String toString()
	{
		return super.toString() + ": " + n;
	}
}
```

In questo caso se stiamo chiamando il fattoriale su un numero negativo viene generata la nostra eccezione e interrompiamo il programma.

_Esempio Ricorsivo con overloading_

Riconoscere se una stringa è una frase palindroma

```java
public boolean isPalindroma(String s) {
	return isPalindroma(s, 0, s.length() - 1);
}
private boolean isPalindroma(String s, int a, int b) {
	if (a >= b) return true;
	return s.charAt(a) == s.charAt(b) && isPalindroma(s, a+1, b-1);
}
```

> [!info]
> È buona norma lasciare la chiamata e quindi il calcolo più pesante come ultima istruzione e quindi verificare prima se possiamo terminare la chiamate tramite casi base.
 
_Ricerca Binaria Ricorsiva_

```java
public int cerca(int[] array, int elemento)
{
	return cerca(array, elemento, 0, array.length);
}
private int cerca(int[] array, int elemento, int a, int b)
{
	if (a > b) return - 1;
	int meta = (b + a) / 2;
	if (array[meta] == elemento) return meta;
	if (elemento < array[meta] return cerca(array, elemento, a, meta-1));
	return cerca(array, elemento, meta - 1, b)
}
```

## Strutture Dati Ricorsive
Ad esempio le liste linkate

```java
public class Lista
{
	private int k;
	private Lista succ;

	public Lista(int k) {this.k = k;}

	public void aggiungi(int k)
	{
		if (succ == null) succ = new Lista(k);
		else
		{
			Lista old = succ;
			succ = new Lista(k);
			succ.succ = old;
		}
	}

	public int getValore() {return k;}
	public Lista getSuccessivo() {return succ;}
}
```

## Mutua Ricorsione
Accade quando il metodo _a_ richiama il metodo _b_ e _b_ a sua volta richiama _a_, per questo è sempre necessario stabilire uno o più casi base per evitare chiamate infinite tra _a_ e _b_.

_Esempio Controlla Numeri Pari e Dispari_
Scrivere una classe che controlla ricorsivamente se ciascun numero in posizione pari sia dispari e ciascun numero in posizione dispari sia pari.

```java
public class PariDispari {
	public boolean pariDispari(ArrayList<Integer> l)
	{
		return pariDispari(l, 0);
	}
	private boolean pariDispari(ArrayList<Integer> l, int k)
	{
		if (k == l.size()) return true;
		return l.get(k) % 2 == 0 && dispariPari(l,k+1);
	}
	private boolean dispariPari(ArrayList<Integer> l, int k)
	{
		if (k == l.size()) return true;
		return l.get(k) % 2 == 1 && pariDispari(l, k+1);
	}
}
```

# Input / Output

Per l'output su console usiamo la classe _System.out_ che è un campo _statico, pubblico e final_ di _System_ di tipo _java.io.PrintStream_ che estend _java.io.OutputStream_.

```java
System.out.println("Stampa su Console");
```

_Metodi di PrintStream_

![[Pasted image 20240507103853.png]]

**Il print(Object) va a chiamare il metodo toString() dell'oggetto**.

Per gli input da tastiera invece utilizziamo la classe _java.util.Scanner_ costruita con la standard _input stream_.
_System.in_ è un campo _statico, pubblico e final_ di _System_ di tipo _java.io.InputStream_

```java
Scanner s = new Scanner(System.in);
int k = scanner.nextInt();
```

![[Pasted image 20240507104100.png]]

Si può utilizzare lo _scanner_ anche passando un file o altre fonti invece della console.

![[Pasted image 20240507104245.png]]

> [!info]
> Alcuni di questi canali di flussi dati hanno il metodo _close_ per chiuderli, su alcuni tipi di flussi questo sarà molto importante per evitare comportamenti indesiderati.

# File

I file sono una collezione di dati salvati sul supporto di memoria, questi non fanno parte del codice sorgente del programma e lo stesso file può essere **letto e moedificato** da programmi differenti.
È importante che il programma **conosca il formato** del file e distinguere **file di testo** da **file binari**.

## File di Testo
Un file di testo contiene _linee di testo_ ad esempio in formato ASCII, per capire la fine di una linea è presente un carattere speciale ovvero '_\n_' che indica la fine della linea e un a capo oppure un '_\r_' _carriage return_ concatenato con una nuova linea

## File Binari
I file binari possono contenere qualsiasi tipo di informazione sottoforma di sequenza di byte e solo il programmatore / progettista **sa interpretarlo**, infatti diversi programmi potrebbero interpretare lo stesso file in modo diverso.
_Qualsiasi file può essere interpretato come file binario_.