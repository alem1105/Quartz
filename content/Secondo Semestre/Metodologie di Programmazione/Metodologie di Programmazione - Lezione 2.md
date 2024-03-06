# Programmazione a Oggetti
Definendo una classe nel nostro programma Java è come se stessimo definendo un nuovo tipo di dato, una classe può contenere _campi e metodi_ e grazie a questi definisce il nuovo tipo di dato "generale" grazie al quale creeremo gli _oggetti_, ovvero le istanze di questa classe.

_Esempio:_
![[Screenshot 2024-03-05 alle 09.13.50.png|500]]

La classe viene definita dal programmatore nel momento della scrittura del codice sorgente e contiene quindi le definizioni generali dei suoi campi.
Gli oggetti esistono soltanto durante l'esecuzione del programma e contengono dati specifici.
In questo caso possiamo vedere la classe _automobile_ che contiene campi generici come _modello, colore, passeggeri e benzina_ mentre l'oggetto di tipo automobile ha valori specifici, rispettivamente _5, PINK, 1, 50_.

Ogni classe viene salvata in un file esterno che ha lo stesso nome della classe e termina con l'estensione _.java_, i nomi delle classi iniziano con lettere maiuscole ed i nomi sono **case-sensitive**

La classe si dichiara con un'intestazione simile

```java
public class Automobile
{

}
```

Le classi sono organizzate in **package**, ad esempio _java.lang_ contiene le classi fondamentali per la programmazione in Java.

## Modificatori di visibilità
- _public:_ un campo dichiarato public risulterà visibile in ogni punto del nostro programma
- _private:_ un campo dichiarato private risulterà visibile soltanto agli elementi della stessa classe in cui è dichiarato

## Metodo Costruttore
É il metodo che definisce cosa fare quando viene creato un nuovo oggetto, questo si definisce all'interno della classe e ha il suo stesso nome.

## Parole chiave nelle dichiarazioni dei campi
- _private / public / protected:_ Modificatore di visibilità
- _static (campo di classe):_ Indica se il campo o metodo è condiviso da tutti gli oggetti di quella classe e quindi allocato in memoria una sola volta e visibile a tutti.
  Se non viene specificato il campo o metodo sarà utilizzato individualmente da ogni oggetto, ogni oggetto potrà quindi avere un valore diverso e il dato viene allocato più volte nella memoria
- _final:_ Indica che il dato è una costante e non può cambiare valore durante l'esecuzione del programma
- _tipo:_ int, double, String

Esempio Sintassi:

```java
private [static] [final] String nome;
```

## Metodi
Un metodo è una serie di operazioni che può svolgere il nostro programma (funzione), questo infatti può prendere in input dei valori e restituirne un altro (non obbligatorio).
Anche per i metodi si una la notazione _CamelCase_ iniziando a scriverlo quindi con una lettera minuscola.

Anche i metodi possono essere definiti statici (_static_), se statico un metodo può essere utilizzato anche senza aver creato oggetti mentre se non definito statico potrà essere chiamato soltanto da oggetti.

La definizione di un metodo avviene in questo modo:
_modificatore_di_visibilità, tipo_di_ritorno, nome (parametri) { }

```java
public int getValue()
{
	return value;
}

public void reset(int newValue)
{
	value = newValue;
}
```

## Metodo Costruttore
- É il metodo usato per creare gli oggetti
- Ha lo stesso nome della classe
- Può prendere dei parametri ma non ha **MAI** valori di uscita
- Possiamo anche avere più costruttori in una classe che prendono in input tipi e/o numero di parametri diversi (_overloading_).

Non è obbligatorio specificare un costruttore e in questo caso il compilatore inserisce il costruttore di default vuoto.

```java
public NomeClasse() {}
```

## Creare Oggetti
Si creano con l'operatore _new_

```java
public static void main(String[] args)
{
	Counter contatore1 = new Counter();
	Counter contatore2 = new Counter(42);

	Sysmte.out.println("Valore contatore 1: " + contatore1.getValue());
}

// I Costruttori avranno una sintassi simile:

public Class Counter
{
	public Counter(int initialValue)
	{
		value = initialValue;
	}
	public Counter()
	{
		value = 0;
	}
}
```

## Metodo Reset
- Ver 1: azzera il contatore 

```java
public void reset() { value=0; }
```

- Ver 2: Reimposta il contatore a un determinato valore

```java
public void reset(int newValue) { value = newValue; }
```

Anche in questo caso abbiamo utilizzato _l'overloading_.

## Variabili locali e campi
I campi sono variabili dell'oggetto ed esistono per tutta la vita dell'oggetto.
Le variabili locali vengono definite all'interno di un metodo o come suoi parametri ed esistono fino alla fine dell'esecuzione del metodo stesso.

## Incapsulamento
Utilizziamo i modificatori di visibilità _public, private_ per nascondere le informazioni all'utente (_information hiding_), questo processo prende il nome di _incapsulamento_:
- Dettagli realizzativi che vengono nascosti: campi e implementazione
- Interfaccia resa pubblica: metodi pubblici

Questo serve rendere modulare il codice, _funzionamento a scatola nera_, questo infatti facilita ad esempio il rilevamento degli errori, perché l'errore verrà individuato in una classe specifica.
Le classi infatti interagiscono fra loro principalmente soltanto attraverso i metodi pubblici e le altre classi non devono conoscere i dettagli implementativi di una classe per usarla.

## Accesso a campi e metodi
Possiamo avere campi e metodi public o private (anche protected)

- I metodi di una classe possono chiamare i metodi pubblici e private della stessa classe
- I metodi di una classe possono chiamare i metodi pubblici ma non privati di altre classi

## Linguaggio UML
![[Screenshot 2024-03-05 alle 11.32.07.png]]

