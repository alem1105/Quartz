**Metodo Arrays.CopyOf(array, int)**
Possiamo copiare un array e aumentare/diminuire la sua dimensione con l'intero fornito, se diminuiamo tagliamo gli elementi di posizione superiore mentre se aumentiamo aggiungiamo elementi null / 0.

**Se aggiungo ho creato un nuovo array mentre se taglio non ho creato nuovi oggetti.**

# Metodi con parametri variabili

```java
public static double sum(double... valori) {
	double somma = 0.0;
	for (int k = 0; k < valori.length; k++) {
		somma += valori[k];
	}
	return somma;
}
```

Con la notazione _..._ posso indicare un numero di parametri variabili e scorrerli con un ciclo for.
**Posso specificare una sola sequenza di parametri variabile** e la devo specificare solo dopo i parametri classici.

# Matrici

Per specificare matrici possiamo semplicemente indicare le due coppie di parentesi quadre

```java
String[][] matrice = new String[int righe][int colonne];
```

Per accedere alla celle mi basta indicare i due indici all'interno delle parentesi quadre.

# Importare campi statici

È possibili importare i campi statici di una classe come se fossero definiti nella classe in cui sono stati importati

```java
import static java.lang.Math.E;
```

# Enumerazioni

I valori di un tipo enumerazione possono essere scelti tra un insieme di identificatori univoci, ogni identificatore è una costante.
- Le costanti enumerative sono static
- Non si possono creare oggetti del tipo enumerato
Un tipo enumerazione viene dichiarato in questo modo

```java
public enum NomeEnumerazione {
	COSTANTE1, COSTANTE2, COSTANTE...
}

public enum SemeCarta {
	CUORI,
	PICCHE,
	QUADRI,
	FIORI
}
```

La dichiarazione di un'enumerazione può contenere altri componenti come campi, costruttori e metodi.

**Implementazione classe mese con Enumerazioni**

```java
public enum Mese {
	GEN(1), FEB(2), MAR(3), APR(4), MAG(5);
	private int mese;
	Mese(int mese) { this.mese = mese; } //Costruttore
	public int toInt() { return mese; }
}

public static void main(String[] args) {
	System.out.println(Mese.APR.toInt()) //Stampa 4
}
```

Ogni enumerazione ha dei metodi statici
- _values()_: restituisce un array delle costanti enumerative
- _valueOf()_: restituisce la costante enumerativa associata alla stringa fornita come paramatro; se la stringa non esiste si genera un'eccezione.


```java
SemeCarta[] valori = SemeCarta.values();
for (int k = 0; k < valori.length; k++) {
	System.out.println(valori[k]); //Stampo tutte le costanti
}

String v = "PICCHE";
SemeCarta picche = SemeCarta.valueOf(v);
System.out.println(picche); //Stampo valore di "PICCHE"
```

Posso utilizzare le enumerazioni anche all'interno dei costrutti _switch_:

```java
SemeCarta seme = null;

switch(seme) {
case CUORI -> System.out.println("A");
case QUADRI -> System.out.println("B");
case FIORI -> System.out.println("C");
case PICCHE -> System.out.println("D");
}
```

# Classi Wrapper

Permettono di convertire i tipi primitivi in oggetti fornendo metodi di accesso e visualizzazione

![[Pasted image 20240319101759.png]]

Se facciamo questo passaggio non possiamo più confrontare gli interi ad esempio con gli operatori di confronto ma con i metodi già visti in precedenza:
- _equals()_: Restituisce true se l'oggetto in input è un intero di valore uguale al proprio
- _compareTo()_: Restituisce 0 se sono uguali, < 0 se il suo valore è minore di quello in ingresso e > 0 se maggiore di quello in ingresso.

```java
new Integer(5) != new Integer(5)
```

## Elementi Statici delle classi Wrapper

![[Pasted image 20240319102205.png]]

# Autoboxing e auto-unboxing

- _Autoboxing_: Converte automaticamente un tipo primitivo alla classe wrapper associata

```java
Integer k = 3;
Integer[] array = {1, 2, 3, 4, 5};
```

- _Auto-unboxing_: Converte automaticamente un oggetto wrapper nel tipo primitivo corrispondente

```java
int j = k;
int n = array[j];
```

# Memoria

![[Pasted image 20240319103155.png]]
![[Pasted image 20240319103215.png]]

# Ereditarietà

Permette il riutilizzo del codice andando a creare classi che "ereditano" campi e/o metodi da altre classi.
Possiamo ad esempio progettare una classe forma molto generica e andarla a specializzare più volte con ogni forma specifica

![[Pasted image 20240319110835.png]]

Per creare una classe che eredita da un'altra usiamo questa sintassi:

```java
public class Forma {
	...
}

public class Cerchio extends Forma {
	...
}
```

Una sottoclasse può quindi ereditare campi e metodi della superclasse ma anche aggiungerne di nuovi oppure ridefinirli.
Il livello di accesso di campi e metodi definisce quali verranno ereditati da eventuali sottoclassi.

## Classi astratte

Una classe astratta non può essere istanziata, quindi non possiamo creare oggetti con essa.
Possiamo anche dichiarare metodi astratti

```java
public astract class PersonaggioDisney {
	abstract void faPasticci();
}
```

Questo può essere utile per creare delle generalizzazioni.
Se una sottoclasse non astratta eredita elementi da una classa astratta allora devo **definire** ogni elemento all'interno della classe.

> [!info] **Parola chiave protected**
> A differenza della parola chiave private rende i campi o metodi visibili soltanto alle sottoclassi o classi dello stesso package.

![[Pasted image 20240319114511.png]]

