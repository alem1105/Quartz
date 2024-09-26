	# Strutture Dati
Le strutture dati servono ad organizzare i dati e a seconda dell'utilizzo che dobbiamo fare dobbiamo scegliere la più adatta:
- Dobbiamo mantenere un **ordine**?
- Gli oggetti nella struttura possono **ripetersi**?
- È necessaria una **chiave** per **accedere** ad uno specifico oggetto?

## Collection
In java sono disponibili grazie al framework delle collezioni (_Java Collection Framework_), sono già pronte all'utilizzo con interfacce e algoritmi.
Contengono e strutturano riferimenti ad altri oggetti tutti dello stesso tipo.

_Esempi:_

![[Pasted image 20240411125917.png]]

**Gerarchia delle interfacce di tipo Collection**

![[Pasted image 20240411130103.png]]

Posso iterare sulle **Collections** tramite:
- Cicli _foreach_
- _Iterator_
- _Indici_ solo se sto utilizzando una lista

## Iterazione su una collezione
Mediante il metodo _Iterable.forEach_ possiamo iterare su qualsiasi collezione senza specificare come effettuare l'iterazione, grazie al polimorfismo.
_forEach_ prende in input un **Consumer** che è un'interfaccia funzionale con un solo metodo:

```Java
void accept(T, t)
```

_Esempio_

```Java
List<Integer> l = List.of(4,8,15,16,23,42);
l.forEach(x -> System.out.println(x));
```

Non possiamo modificare una lista durante un'iterazione, questo genera un'eccezione ma possiamo utilizzare _Iterator.remove_:

```Java
Iterator<Integer> i = l.iterator();
while(i.hasNext())
	if (i.next() == x) i.remove();
```

**Collezioni Fondamentali**

![[Pasted image 20240411131907.png|500]]

# ArrayList e LinkedList

Implementano l'interfaccia _List_, sottointerfaccia di _Collection e Iterable_, estendono anche la classe _AbstractList_.
- **ArrayList** implementa la lista mediante un array anche ridimensionabile
- **LinkedList** implementa la lista mediante elementi linkati
  La LinkedList contiene gli elementi in dei _container_, la lista contiene l'indirizzo al primo container e quel container il link al successivo, se dobbiamo aggiungere un elemento quindi non ridimensioniamo la lista ma creiamo un nuovo container linkato dal container precedente.


> [!info] Quando usarli
> Per immagazzinare e accedere ai dati usiamo gli _ArrayList_ mentre per manipolari i dati quindi eseguire molte azioni utilizziamo le _LinkedList_

**Metodi Linked List**

![[Pasted image 20240416093226.png]]

Possiamo quindi usare gli iteratori ad esempio in questo modo:

```java
ListIterator<Integer> i = l.listIterator();
while(i.hasNext()) {
	System.out.println(i.next());
}
```

# Insiemi HashSet, TreeSet, LinkedHashSet

Si basano sui _set_ una sottointerfaccia di _Collection e Iterable_
Contengono tutti elementi distinti ed estendono la classe **AbstractSet** e **Set**

- **HashSet** memorizza gli elementi in una tabella hash
- **TreeSet** memorizza gli elementi in un albero mantenendo un ordine sugli elementi, quello base del tipo dell'elemento
- **LinkedHasSet** memorizza gli elementi in ordine di inserimento

_Come funziona un HashSet?_

Si basa sulle **tabelle hash**

![[Pasted image 20240416093707.png|500]]

Quindi ad ogni elemento viene associato una chiave univoca restituita dalla funzione _hashCode()_

Gli algoritmi di _hashing_ infatti non si basano su confronti e sui loro esiti ma si cerca di accedere direttamente agli elementi attraverso la chiave generata da operazioni aritmetiche.
Ogni elemento infatti è memorizzato su un vettore e la sua posizione è determinata dalla funzione _hashCode()_


> [!info] Oggetti uguali e Hascode
> Se _a.equals(b)_ allora _a.hashCode() = b.hashCode()_ ma se _a.hashCode() = b.hashCode()_ non è detto che _a.equals(b)_

# Mappe
Mette in corrispondenza _chiavi_ e _valori_ quindi non può contenere chiavi duplicate e viene implementata da _HashMap, TreeMap e LinkedHashMap_

![[Pasted image 20240416095927.png]]

Nelle mappe possiamo utilizzare il metodo _entrySet()_ che ci restituisce un oggetto _Map.Entry<K, V>_ e ad ogni oggetto cioè coppia possiamo ottenere chiave e valore con i metodi _getKey() e getValue()_.

**Metodi di Map**

![[Pasted image 20240416100847.png]]

- Per il _foreach_ dobbiamo fornire coppia chiavi valori quindi ad esempio:

```java
for (Map.Entry<Integer, String> entry : mappa.entrySet()) {
	Integer key = entry.getKey();
	String value = entry.getValue();
}
```
# Ordinamento "Naturale"
Per garantire un ordinamento naturale sui tipi è necessario che implementino l'interfaccia _Comparable\<T\>_ dotata di un solo metodo _compareTo(T o)_ che confronta se stesso con l'oggetto fornito come parametro, 0 se uguali -1 se >= o e +1 altrimenti.

## Ordinamento con interfaccia Comparator\<T\>

Se le classe non fornisce di base il suo ordinamento con _Comparable_ o se vogliamo ordinare diversamente degli oggetti possiamo creare un'istanza e passarla in input al costruttore:

![[Pasted image 20240416101824.png|500]]

# Riferimenti a Metodi

È possibile utilizzare riferimenti ad altri metodi invece delle funzioni lambda con la sintassi:

```java
Classe::metodoStatico
riferimentoOggetto::metodoNonStatico
Classe::metodoNonStatico
```

_Esempio_

```java
Converter<String, Integer> converter = Integer::valueOf;
Integer converted = converter.convert("123");
```

![[Pasted image 20240416104437.png]]

![[Pasted image 20240416105058.png]]

Quindi invece di utilizzare Comparator possiamo _implicitamente_ sovrascrivere _compareTo_ di _String_ fornendo implicitamente due parametri con il metodo sort.

# Visibilità Lambda
- Accesso alle variabili esterne da un'espressione lambda
- Possiamo accedere a campi d'istanza e variabili statiche, variabili final del metodo che definisce la lambda

_Esempio_

```java
final int num = 1;
Converter<Integer, String> stringConverter = from ->    String.valueOf(from + num);
stringConverter.convert(2); //"3"
```

# Ordinamento - Lambda

```java
Collections.sort(names, (a,b) -> b.compareTo(a));
```

# Ordinamento per Lunghezza - Java

```java
Collections.sort(names, (a,b) -> a.length()-b.length());
//oppure
Collections.sort(names, (a,b) -> Integer.compare(a.length(), b.length()));
```

# Metodi default nell'interfaccia Comparator

![[Pasted image 20240416111155.png]]

**Oppure posso utilizzare:**

![[Pasted image 20240416111231.png]]

