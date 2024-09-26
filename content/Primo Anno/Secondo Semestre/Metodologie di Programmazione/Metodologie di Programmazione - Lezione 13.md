# Tipi Generici
Con i tipi generici possiamo definire con una sola dichiarazione un insieme di metodi o classi.
Ad esempio quando due classi hanno gli stessi campi e metodi ma di **tipi diversi**.

_Esempio Classe Generica_

```java
public class Valore<T>
{
	private final T val;
	public Valore(T val) { this.val = val; }
	public T get() { return val; }
	@Override
	public String toString() { return ""+val; }
	public String getType() { return val.getClass().getName(); }
}
```

Per definire il tipo generico si utilizzano le parentesi angolari \<\> dopo il nome della classe con all'interno il tipo generico.
A quel punto possiamo utilizzare questo tipo generico all'interno della classe come sempre.
Infatti possiamo utilizzarlo in più modi:

```java
Valore<Integer> i = new Valore<>(42);
Valore<String> s = new Valore<>("Ciao");
Valore<Valore<String>> v = new Valore<>(s);

System.out.println(i.get()+":"+i.getType()); // 42:Integer
System.out.println(s.get()+":"+s.getType()); // Ciao:String
System.out.println(v.get()+":"+v.getType()); // Ciao:Valore
```

I tipi generici funzionano soltanto con i tipi derivate **non con i primitivi**

I tipi generici sono compatibili in base ai loro "tipi" in _input_
Nell'esempio precedente $s$ non è compatibili cone $i$, non possiamo fare:

```java
s = i;
```

Possiamo anche estendere le classi generiche 

```java
public class Orario extends Coppia<Integer, Integer>
{
	public Orario(Integer a, Integer b)
	{
		super(a, b);
	}
}

public class Data extends Coppia<Integer, Coppia<Integer, Integer>>
{
	public Data(Integer giorno, Integer mese, Integer anno)
	{
		super(giorno, new Coppia<Integer, Integer>(mese, anno));
	}
}
```

**Estendere un'interfaccia generica con un vincolo di comparabilità sul tipo generico**

```java
public interface MinMax<T extends Comparable<T>>
{
	T min();
	T max();
}
// Altro Esempio
public class MyClass<T extends Comparable<T>> implements MinMax<T>
{

}
```

Quindi T deve essere comparabile o un suo sottotipo.
Usiamo _extends_ al posto di _implements_ nella prima riga per convenzione di Java, questo serve a creare il **vincolo** su _T_.

![[Pasted image 20240430101906.png]]

- Nel primo esempio abbiamo scritto due volte il vincolo
- Nel secondo non abbiamo definito un tipo per l'interfaccia, lasciando il tipo generico

**Esempi su Collezioni**

```java
public interface List<E>
{
	void add(E x);
	Iterator<E> iterator();
}
public interface Iterator<E>
{
	E next();
	booleans hasNext();
	default void remove();
}
```

Infatti l'utilizzo dei tipi generici avviene principalmente nelle liste, ad esempio:

```java
//QUando scriviamo
new ArrayList<String>();
//Stiamo trattando la classe come
public class ArrayList<String> extends AbstractList<String>;
```

**Definire metodi con un proprio tipo generico**

```java
static public <T> void esamina(ArrayList<T> lista)
{
	for (T o : lista) System.out.println(o.toString());
}
```

Vanno messe le parentesi angolari prima del tipo di ritorno.
Posso chiamare _.toString_ su tutti gli elementi anche se generici perché sono tutti _Object_.
Questo viene utilizzato principalmente per **Sintassi**.

---

![[Pasted image 20240430105302.png]]

Con i tipi generici **non funziona** il polimorfismo quindi il primo esempio non funziona, il metodo accetterà soltanto _ArrayList di Frutto_.
Mentre con il secondo esempio possiamo utilizzare sia il tipo _Frutto che suoi sottotipi_, dato che abbiamo creato un **vincolo**.

Per le classi generiche invece non vale l'ereditarietà dei tipi generici, quindi una classe _ArrayList\<Integer\>_ non è di tipo _ArrayList\<Object\> o ArrayList\<Number\>_ ma rimane invece l'ereditarietà fra le classi quindi possiamo scrivere:

```java
List<Integer> lista = new ArrayList<Integer>();
```

**Jolly come tipi generici**
Nel caso in cui non sia necessario usare il tipo generico _T_ nel corpo della classe, possiamo utilizzare il _Jolly_?

```java
public static void mangia(ArrayList<? extends Mangiabile> frutta)
{
	
}
//Equivalente
public static <T extends Mangiabile> void mangia2(ArrayList<T> frutta)
{

}
```

Quindi il jolly lo utilizzo quando non ho bisogno di utilizzare il simbolo _T_ nel codice.
Utilizziamo _?_ quando non è necessario conoscere il tipo parametrico

![[Pasted image 20240430110603.png]]

Nella classe main non ho bisogno di specificare che Punto vuole parametri interi.
Quindi ogni volta posso definire un tipo diverso per i campi _x, y_ 

**Come funziona?**
È implementato con la **cancellazione del tipo**, quando il compilatore traduce la classe / metodo in _bytecode_:
1) Elimina la sezione del tipo parametrico e sostituisce il tipo parametrico con quello reale
2) Per default il tipo generico viene sostituito con il tipo _Object_

Viene creata **una sola copia** del metodo o della classe.

Infatti a tempo di esecuzione non possiamo conoscere il tipo generico.

```java
List<Integer> x = Arrays.asList(4,2);
boolean b = x instanceof List<Integer>; // Errore

// Possiamo verifica il tipo
List<Integer> x = Arrays.asList(4,2);
boolean b = x instanceof List<?>; // true
```

**Super e Extends**
Possiamo imporre vincoli nei seguenti modi:
- **extends** T deve essere un sottotipo della classe specificata o la classe stessa (**covarianza**)
- **super** T deve essere una superclasse della classe specificata o della classe stessa (**controvarianza**)

![[Pasted image 20240430112900.png]]

![[Pasted image 20240430112910.png]]

**PECS: Producer Extends, Consumer Supers**
- _Extends e Super_ esistono per due necessità primarie: leggere e scrivere in una collezione generica
- Abbiamo 3 modi
	- List\<?\> lista = new ArrayList\<Number\>();
	  lista è diventato soltanto un riferimento perdendo la capacità di fare controlli sui tipi
	- List\<? extends Number\> = new ArrayList\<Number\>();
	  Qui il compilatore sa che la lista è composta da tipi Number o suoi sottotipi
	- List\<? super Number\> = new ArrayList\<Number\>();
	  Qui sappiamo che i tipi sono Number o suoi supertipi
- \<?\> non so nulla sul tipo, posso solo leggere e non scrivere non sapendo che tipo aggiungere, **primo metodo**
- _extends_ abbiamo bisogno di una lista in input che fornisca elementi di tipo _T_ ma non possiamo aggiungere elementi a questa, soltanto leggere
- _super_ ci serve una lista che consuma elementi di tipo _T_ per scrivere nella lista senza assumere il tipo di questi, possiamo sia leggere che scrivere

_Esempio_

![[Pasted image 20240430113359.png]]

Quindi la lista sorgente è vincolata su T o un suo sottotipo mentre la lista destinazione è vincolata a T o un suo supertipo

![[Pasted image 20240430114226.png]]

## Overloading dei metodi generici
Un metodo generico può essere sovraccaricato, sia da un metodo generico che da uno non generico con lo stesso nome e numero di parametri.
Quando il compilatore riceve una chiamata ad un metodo cerca prima il più specifico, quindi prima il non generico e poi il generico.

![[Pasted image 20240507091839.png]]

# Tipi Raw
