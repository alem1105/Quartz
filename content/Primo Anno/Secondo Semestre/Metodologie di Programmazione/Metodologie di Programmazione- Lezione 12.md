# Interfaccia Predicate\<T\>

È una funzione a valori booleani con un solo argomento 

```java
Predicate<String> predicate = s -> s.length() > 0
// Utilizzo
predicate.test("foo"); // Restituisce true
predicate.test("");  // Restituisce false
```

# Interfaccia Function\<T,R\>

Funzione a un argomento di tipo T e con un tipo di ritorno R

```java
Function<String, Integer> toInteger = Integer::valueOf;
Integer k = toInteger.apply("123"); // Inserisce in k l'intero 123
```

# Interfaccia Supplier\<T\>
È una funzione senza argomenti in input

```java
Supplier<String> stringSupplier = () -> "Ciao";
```

Possiamo riferirci anche a costruttori

```java
Supplier<Person> personSupplier = Person::new;
personSupplier.get() // Restituisce oggetto di tipo Person
```

# Interfaccia Consumer
Funzione con un tipo in input ma nessun tipo di ritorno

```java
Consumer<Person> greeter1 = p -> System.out.println("Hello, " + p.firstName);
greeter1.accept(new Person("A", "M"));
Consumer<Person> greeter2 = System.out::println;
```

![[Pasted image 20240423093319.png]]

# ForEach
Le collections sono iterabile tramite i _ForEach_ che prendono in input un'interfaccia _Consumer\<? super T\>_ dove _T_ è il tipo generico della collection

_Esempio_

```java
Collection<String> c = Arrays.asList("aa", "bb", "cc");

// Da Java 7
for (String s : c) System.out.println(s);

// Java 8
c.forEach(s -> System.out.println(s);
// Oppure
c.forEach(System.out::println)
```

# Pila e Coda

**Coda**:
- Si implementa tramite l'interfaccia _Queue_
- _Add_: Inserisce l'elemento in coda
- _Remove_: Rimuove un elemento alla testa
- _Peek_: Restituisce l'elemento in testa ma senza rimuoverlo

**Pila**:
- Si implementa tramite l'interfaccia _Stack_
- _Push_: Aggiunge un elemento in cima allo stack
- _Pop_: Rimuove un elemento dalla cima
- _Peek_: Restituisce l'elemento in cima ma senza rimuoverlo

> [!info]- Come scegliere la struttura dati
> ![[Pasted image 20240423094226.png]]
> ![[Pasted image 20240423094239.png]]

# Alberi
È una struttura dati ricorsiva dove ogni nodo possiede un padre tranne la radice dell'albero, spesso incontriamo alberi binari ovvero dove ogni nodo ha al più due figli.

In Java per rappresentare il nodo di un albero utilizziamo una classe annidata all'interno dell'albero.

```java
public class BinaryTree
{
	private Nodo root;
	static public class Nodo
	{
		private Nodo left;
		private Nodo right;
		private int valore;
		public Nodo(Nodo left, Nodo right, int valore)
		{
			this.left = left;
			this.right = right;
			this.valore = valore;
		}
	}
}
```

## Ricerca in un albero binario

```java
public boolean contains(int val) {
	return contains(root, val);
}

public boolean contains(Nodo n, int val) {
	if (n == null) return false;
	if (n.valore == val) return true;
	return contains(n.left, val) || contains(n.right, val);
}
```

# Eccezioni
Le eccezioni servono a gestire gli errori che si verificano durante l'esecuzione del codice

Alcune eccezioni che possiamo incontrare:
- `ArrayIndexOutOfBoundsException`: Indica che abbiamo superato i limiti di un array.
- `NumberFormatException`: Formato dell'interno fornito non valido
- `ArithmeticException`: Errore di calcolo

Dopo la tipologia di eccezione ci viene fornita anche una spiegazione più dettagliata del perché è stata generata, ad esempio da quale variabile.

**Eccezioni Notevoli**

![[Pasted image 20240423095617.png]]

## Cosa possiamo gestire?
Possiamo gestire gli errori **sincroni** che si verificano a seguito dell'esecuzione di un'istruzione.

- Errori non critici
	- Divisione per 0
	- Errore di I/O
	- Errori di parsing con tipi
- Errori critici
	- Conversione non consentita
	- Accesso ad una variabile contenente null
	- Mancanza di memoria
	- Riferimento a una classe inesistente

## Cosa non possiamo gestire?
Gli errori **asincroni**  che vengono quindi generati parallelamente all'esecuzione del programma.

- Ricezione messaggi su rete
- Click del mouse
- Completamenti nel trasferimento I/O

## Codice Java

```java
try
{
	// Istruzione 1
}
catch(ExceptionType el)
{
	// Istruzione da svolgere se catturiamo questo tipo
}
finally
{
	// Opzionale, viene eseguito SEMPRE
}
```

Possiamo inserire più di un blocco **catch** per gestire più tipi di eccezioni.

**Per i blocchi catch è importante mantenere un ordine**
Prima dobbiamo sempre cercare di catturare l'eccezioni più specifica e scendendo quella più generale, infatti nella cattura la **JVM** sceglie il primo **catch compatibile** ovvero dove il tipo dell'eccezione sia dichiarata sia lo stesso o un supertipo dell'eccezione generata dal programma.

Questo perché in alcuni casi vogliamo rispondere con una soluzione più specifica piuttosto che generale.

![[Pasted image 20240423101349.png]]

Oppure nel costrutto **catch** posso utilizzare l'operatore _|_ per gestire diversi tipi di eccezione nello stesso blocco di codice.

```java
try
{
	if (condizione) throw new Eccezione1();
	else throw new Eccezione2();
}
catch (Eccezione1 | Eccezione2 e)
{
	// Gestione
}
```

Se vengono generate eccezione l'esecuzione del programma si blocca alla linea del costrutto try che ha generato l'errore e si sposta alla prima linea del costrutto catch interessato, poi il programma riprende dopo il costrutto try catch.
Se non ci sono eccezioni svogliamo il costrutto try e poi saltiamo ogni catch.
Il blocco finally se presente viene sempre eseguito.

**Possiamo gestire le eccezioni in due modi**
- **Ignorare** l'eccezione e propagarla al metodo chiamante aggiungendo però all'intestazione la clausola _throws_ seguita dall'elenco delle eccezioni potenzialmente sollevate. **Declare**
- **Gestire** l'eccezione con il costrutto **try catch**. **Catch**

Se non svolgiamo nessuna di queste due operazioni il compilatore genera un errore che ci indica che l'eccezione deve essere catturata o dichiarata.

_Codice per ignorare le eccezioni_

```java
public static void main(String[] args) throws Eccezione1, Eccezione2
{
	
}
```

Indica quindi che il metodo main può sollevare eccezioni di tipo _Eccezione1, Eccezione2_

Se tutti i metodi all'interno dello stack decidono di ignorare l'eccezione, si **interrompe** l'esecuzione del programma.

- Questo succede in applicazioni a singolo thread
- Nel caso di più thread si interrompe soltanto il singolo thread. L'applicazione termina solo se si interrompono tutti i thread

![[Pasted image 20240423102845.png]]

Quando non catturiamo mai un'eccezione viene generato un messaggio nella console che contiene un riassunto dell'eccezione generata chiamato **stack trace**.
Qui abbiamo diverse informazioni come:
- Thread interessato
- Nome dell'eccezione
- Successione dei metodi coinvolti
- Il file sorgente e il numero di riga interessato

## Metodi printStackTrace() e getMessage()
L'output generato sulla console da un'eccezione non catturata è prodotto dal metodo _printStackTrace()_ della classe _Throwable_
Sempre nella stessa classe troviamo il metodo _getMessage()_ che se disponibile restituisce una descrizione sintetica del perché è stata generata l'eccezione, è la parte del messaggio stampato che si trova due i : posti a fine nome eccezione

## Creare Eccezioni
Al momento della creazione è importante scegliere la super-classe più adeguata in base agli errori che deve gestire, se irreversibile o non ecc..

```java
public class MiaEccezione extends Exception
{}
```

Con la parola chiave _throw_ possiamo sollevare noi **volontariamente** un'eccezione ad un certo punto del codice.

```java
throw new MiaEccezione;
```

È importante creare eccezioni personalizzate per avere delle tipologie più precise e un codice più pulito.
Un tipo di errore generico potrebbe non avere senso nel contesto del codice in cui è stato generato.

# Finally
Il blocco finally posto dopo i blocchi _catch_ viene **SEMPRE ESEGUITO** anche se vengono sollevate eccezioni o usciamo dal blocco tramite **break** o **return**.
L'unico caso in cui non viene eseguito è quando eseguiamo un'uscita forzata con `System.exit()`

Generalmente vengono eseguite operazioni di **clean-up** come ad esempio la chiusura di file aperti durante l'esecuzione del programma o rilascio di risorse in modo da non comprometterle.

# Classe Throwable
La classe throwable è quella che implementa le eccezioni, questa estende _Object_.
Gli oggetti di tipo _Throwable_ sono gli **unici** oggetti che possiamo utilizzare con il meccanismo delle eccezioni.

## Gerarchia

![[Pasted image 20240423110001.png]]

- **Error** gestisce una condizione irrecuperabile come ad esempio quando finisce la memoria
- **Exception** sono eccezioni della _JVM_ legate ad errori nella logica del programma, sono errori che si possono gestire e dai quali è possibile riprendersi

## Eccezioni checked e unchecked

- **Checked**
	- Bisogna sempre utilizzare l'idea **catch-or-declare**
	- Sono eccezioni comuni ovvero che estendono _Exception_
	- _ParseException, ClassNotFoundException, FileNotFoundException_
- **Unchecked**
	- Non siamo obbligati a catturarle o dichiararle
	- Estendono _Error_ o _RuntimeException_
	- _NullPointerException, OutOfMemoryException, IndexOutOfBoundsException

![[Pasted image 20240423110603.png]]

**Rilanciare Eccezioni**
È possibile rilanciare un tipo di eccezione all'interno di un costrutto _catch_ quindi gestiamo l'eccezione generata precedentemente e ne viene sollevata un'altra.

```java
catch(Eccezione1 e)
{
	throw new Eccezione2();
}
```

