# Tipo Optional
È un contenitore di un riferimento, che può riferirsi a qualcosa o null.
Quindi un metodo può restituire un optional invece di restituire un riferimento che potrebbe essere null.
Questo serve ad evitare le _NullPointerException_.

**Quindi: se posso ritornare null meglio ritornare optional**

## Creare e verificare un Optional
- Vuoto: `Optional.empty()`
- Non nullo: `Optional.of("oggetto")`
- Optional di un riferimento che può essere nullo: `Optional<String> optional = Optional.ofNullable(s)`
- Controllo della presenza di un valore non null:
  `Optional.empty().isPresent() == false`
  `Optional.of("Stringa").isPresent() == true`

## Ottenere il valore
- Con orElse:
  
  ```java
  Optional<String> op = Optional.of("eccomi");
  op.orElse("fallback"); // eccomi
  Optional.empty().orElse("fallback") // fallback
  ```

orElse restituisce il valore se presente altrimenti il valore dato come parametro

  
- ifPresent o ifPresentOrElse
`op.ifPresent(System.out::println) //eccomi`

- Non usare
  `op.get` // valore o se non presente solleva eccezione

Con il get se restituisce null non abbiamo sfruttato l'optional


# Sequenze di elementi: Stream

**Definiscono elaborazioni di flussi di dati**, non rappresentano obbligatoriamente flussi di input / output come i precedenti.

Gli stream rappresentano una sequenza di elementi sui quali svolgiamo operazioni.
Uno stream viene creato a partire da un'altra sorgente come ad esempio una Collection ma al contrario di queste non memorizza ne modifica i dati dalla sorgente ma opera su di essi.
Supportano operazioni sequenziali e parallele.

Esistono due tipi di operazioni definibili sugli stream:
- **intermedie o terminali**
-  intermedie restituiscono un altro stream su cui continuare a lavorare
- terminali restituiscono il tipo atteso

![[Pasted image 20240514093349.png]]

Data la collection abbiamo con l'operazione filter (intermedia) abbiamo creato un nuovo stream sul quale abbiamo eseguito l'operazione terminale count che restituisce il valore 3 e non un nuovo stream.

**Con le operazioni intermedie posso quindi creare una catena di operazioni**.
Queste sono le operazioni che DICHIARO sullo stream e una volta eseguito tutte eseguo l'elaborazione finale con un'operazione terminale.
Di base quindi dichiaro più operazioni intermedie e una soltanto terminale (l'ultima).
Le intermedie descrivono le operazioni da svolgere sui dati.

**Builder pattern: serie di operazioni intermedie (configurazione) e ultima terminale per costruire l'oggetto**

Una volta eseguita la terminale, l'elaborazione creata e quindi lo stream viene consumato e  non può essere più utilizzato.

## Metodi principali di Stream\<T\>

![[Pasted image 20240514093934.png]]

## Lazy Behavior:

Le operazioni intermedie definite sugli stream non vengono eseguite immediatamente ma soltanto quando si chiama l'esecuzione di un'operazione terminale.
Le operazioni intermedie possono essere:
- Senza Stato (Stateless): l'elaborazione dei vari elementi procede in modo indipentende (es. filter), l'ordine delle operazioni intermedie non è importante con queste operazioni.
- Con Stato (Stateful): l'elaborazione di un elemento potrebbe dipendere da quella di altri elementi, qui invece impatta l'ordine in cui vengono eseguite.

Dato che è la JVM ha decidere che operazioni svolgere e in che ordine, se lo stream precede solo operazioni stateless la jvm ha piena libertà per gestire al meglio le risorse, invece con operazioni stateful la jvm deve "adeguarsi" e non ha piena libertà per ottimizzare le risorse durante l'esecuzione.

## Tipi di Stream
Dato che gli stream operano su oggetti esistono diverse interfacce:
- IntStream
- DouleStream
- LongStream
Tutte queste interfacce estendono BaseStream che è l'interfaccia di base

## Come ottenere uno stream

- Metodo `Stream.of(elenco di dati)`
- L'interfaccia Collection include due metodi di defualt:
	- `default Stram<E> stream()` che restituisce uno stream sequenziale
	- `default Stream<E> parallelStream()` restituisce uno stream parallelo se possibile altrimenti uno sequenziale
- Metodo statico `Stream<T> Arrays.stream(T[] array)` per ottenere uno stream da un array
- Per ottenere uno stream di righe di testo da un buffer `BufferedReader.lines()` oppure `Files.lines(Path)`
- Possiamo ottenerlo anche con `String.lines`

## Stream vs Collection
- Lo stream permette uno stile **dichiarativo**.
- La collection impone uno stile imperativo.
- Lo stream si focalizza sulle operazioni di alto livello da eseguire senza sapere come verranno eseguite.
- Stream: Dichiarativo, componibile, parallelizzabile.

**Imperativo**: Scegliamo come svolgere le operazioni ma anche in quale ordine. 
**Dichiarativo**: Utilizziamo operazioni di alto livello senza preoccuparci di come verrano eseguite: filtra, conta, spezza, ordina, ecc...

## min e Max di Stream
I metodi min e max restituiscono il minimo e il massimo di uno stream sottoforma di Optional.
Prendono in input un Comparator sul tipo degli elementi dello stream

```java
List<Integer> p = Arrays.asList(2,3,4,6);
Optional<Integer> max = p.stream().max(Integer::compare);
// Restituito se esiste altrimenti -1
System.out.println(max.orElse(-1));
```

## Filter, ForEach
Filter accetta un _Predicate_ per filtrare gli elementi dello stream, è un'operazione intermedia.
ForEach prende in input un Consumer e lo applica ad ogni elemento, è un'operazione temrinale.

## Esempi di Stream

![[Pasted image 20240514101116.png]]

Nel secondo esempio poteva tornare utile utilizzare _.intStream_.

--- 

![[Pasted image 20240514101133.png]]

## Count
È un'operazione terminale che restituisce il numero di elementi nello stream sottoforma di _long_

```java
long startsWithA = l.stream().filters(s -> s.startsWith("a")).count();
System.out.println(startsWithA); // 2
```

Conta numero di righe in un file:

```java
long numberOfLines = Files.lines(Paths.get("percorso.txt")).count();
```

## Sorted
È un'operazione intermedia che restituisce una vista ordinata dello stream ma non modifica la collezione.

```java
List<String> l = Arrays.asList("da","ac","ab","bb");
l.stream()
.sorted() // op state (bloccante) viene eseguita prima
.filter(s -> s.startsWith("a")) // Conviene filtrare prima di ordinare
.forEach(System.out::println);
```

Stampa: _ab, ac_.

## Map
Map è un'operazione intermedia che restituisce un nuovo stream dove ogni elemento è convertito in un altro oggetto attraverso la funzione passata in input.

Restituire tutte le stringhe portate in maiuscolo e in ordine inverso

```java
l.stream()
.map(String::toUpperCase) // Ho un altro stream con le lettere MAIUSC
.sorted(Comparator<String>.naturalOrder().reversed()) // Ordine inverso
.forEach(System.out::println); // Stampa
```

![[Pasted image 20240514103152.png]]

## Collect
È un'operazione terminale che raccoglie elementi dello stream in un oggetto (liste, collection, string ecc...).
Ad esempio quindi invece di stampare i risultati possiamo inserirli in una lista.

```java
List<Integer> ivaEsclusa = Arrays.asList(10, 20, 30);
List<Double> l = ivaEsclusa.stream()
.map(p->p*1.22).collect(Collectors.toList());
```

![[Pasted image 20240514105533.png]]

_Altro Esempio, trasformare una lista di stringhe in una lista di interi corrispondenti alla lunghezze di queste_.

![[Pasted image 20240514105657.png]]

# Collectors

Servono a ridurre gli elementi di uno stream e raccoglierli in un modo specificato da noi.
Per semplificare la sintassi li importiamo con `import static java.utils.stream.Collectors.*`, per importare tutti i metodi statici.
In questo modo possiamo scrivere il nome del metodo senza scrivere davanti a questo `Collectors.`, quindi possiamo scrivere `.toList()`invece di `Collectors.toList()`.

- **Counting()**: restituisce il numero di elementi dello stream (long).

  ```java
  List<Integer> l = Arrays.asList(2,3,4,5);
  long k = l.stream()
  .filter(x->x<5)
  .collect(Collectors.counting());
  ```

- **maxBy / minBy(comparator)**: restituisce un Optional con il massimo o minimo valore.

```java
Optional<Integer> max = l.stream()
.collect(maxBy(Integer::compareTo));
```

**summingInt(lambda che mappa ogni elemento intero) / averageInt, summingDouble, averaginDouble**: Somma e media degli elementi.

- **joining () (separatore) (separatore, prefisso, suffisso)**: concatena gli elementi stringa dello stream in un'unica stringa
  
  ```java
  List<Integer> l = Arrays.asList(1,2,3,4,5);
  String str = l.stream()
  .map(x->""+x).collect(joining(","));
  ```

- **toList, toSet, toMap**: Accumulano gli elementi in una lista, insieme o mappa
  
  ```java
  Set<String> set = l.stream()
  .map(x->x+"")
  .collect(toSet());
  ```

- **toCollection**: Accumula gli elementi in una collection

```java
ArrayList<String> str = l.stream()
.map(x->x+"")
.collect(toCollection(ArrayList::new));
```

## toMap

Prende fino 4 argomenti e almeno 2:
- la funzione per mappare l'oggetto dello stream nella chiave della mappa
- la funzione per mappare l'oggetto dello stream nel valore della mappa
- la funzione da utilizzare per unire il valore preesistente nella mappa se ho una chiave con più valori. Non devono comunque esserci 2 chiavi uguali _IllegalStateException_. (**opzionale**)
- Supplier che crea la mappa (**opzionale**)

```java
Map<Integer, String> map = persons.stream()
.collect(Collectors.toMap(
Person::getAge,
Person::getName,
(name1, name2) -> name1 + "; " + name2
));
```

Quindi la chiave nella mappa è l'età di una persona, il valore è il nome e se abbiamo persone con la stessa età, i due nomi vengono concatenati con un "; ".
Il supplier è utile ad esempio se vogliamo obbligare l'utilizzo di una HashMap o altre mappe, di solito infatti si passa come supplier il costruttore della struttura che vogliamo utilizzare.

## Raggruppamenti di Elementi

- **groupingBy (lambda che mappa gli elementi di tipo T in bucket rappresentati da oggetti ti un altro tipo S)**: restituisce una `Map<S, List<T>>`.
  Lo usiamo per avere un collezionatore che mette elementi dello stream in una mappa dove le chiavi sono di tipo S e gli elementi sono liste di elementi di tipo T.
- **groupingBy (lambda, downStreamCollector)**: raggruppamento multilivello.

Possiamo ottenere una mappa da città a lista di persone a partire da una lista di persone (multimappa).

_people è una collection di Person_

```java
Map<City, List<Person>> peopleByCity = people.stream()
.collect(groupingBy(Person::getCity));
```

Otteniamo una mappa dove le chiavi sono le città e i valori sono le persone residenti in quella città.
Con i raggruppamenti possiamo quindi prendere un tipo di oggetti e creare una mappa che come chiave ha un campo di questo oggetto e come valori una lista di questi oggetti (un raggruppamento in base ad un campo).

Prendendo l'esempio di prima possiamo utilizzare il secondo parametro per forzare l'utilizzo di un set come contenitore dei valori:

```java
Map<City, set<Person>> peopleByCity = people.stream()
.collect(groupingBy(Person::getCity, toSet()));
```

Quindi con _downStreamCollector_ specifico il tipo del raggruppamento di valori, di base utilizzo le liste.
Il _downStreamCollector_ è un collector.

## Collectors.mapping
In raccolte multilivello, usando ad esempio un _groupingBy_ è utile mappare il valore del raggruppamento a qualche altro tipo.

```java
Map<City, Set<String>> peopleSurnamesByCity = people.stream()
.collect(
groupingBy(Person::getCity),
	mapping(Person::getLastName, toSet())
);
```

Quindi mentre raccogliamo le persone in base alla città vogliamo convertire anche il tipo di Persona nel loro cognome collezionando quindi i cognomi e non gli oggetti di tipo Persona.

Abbiamo quindi utilizzato il secondo parametro _downStreamDetector_ come .mapping che mette i cognomi in un set.

Otteniamo quindi una mappa che ha come chiavi le città e come valore l'insieme dei cognomi delle persone che vivono in quella città.

## Creare il proprio Collector
Con il metodo _Collector.of_ che prende 4 argomenti:
- Un supplier: fornisce un riferimento ad un oggetto che gestisce una "rappresentazione" intermedia degli elementi dello stream che vogliamo rappresentare
- Un accumulatore: BiConsumer che dato il riferimento agli elementi che vogliamo rappresentare (j è un riferimento al primo supplier) e dato p che è uno degli oggetti
- Combiner: Fonde le rappresentazioni dei due joiner
- Finisher: Trasforma il tutto nel tipo finale

Questo permette di parallelizzare la rappresentazione nello stream.


```java
Collector<Person, StringJoiner, String> personNameCollector =
Collector.of(
() -> new StringJoiner(" | "), //Supplier
(j,p) -> j.add(p.name.toUpperCase()), //Accumulator
(j1, j2) -> j1.merge(j2), // Combiner
StringJoiner::toString); // Finisher
)
String names = people.stream().collect(personNameCollector);
System.out.println(names);
```

## Partizioni di elementi

Distribuire gli elementi di un insieme in due insiemi.
Divido gli elementi dello stream in una mappa con chiavi valori booleani e come valori collezioni di elementi

`partitioningBy(predicato)`:  raggruppa in una `Map<Boolean, List<T>>`.

```java
Map<Boolean, List<Integer>> m = l.stream()
.collect(Collectors.partitioningBy(x -> x % 2 == 0));
```

Crea una mappa con chiavi booleane impostate a true per i valori che soddisfano il predicato dato in input.

## Distinct
È un'operazione intermedia degli stream, elimina le ridondanze fra gli elementi dello stream.

```java
List<Integer> l = List.of(3,4,5,3,4,1);
List<Integer> distinti = l.stream().map(x -> x*x)
.distinct().collect(Collectors.toList());
```

## Reduce
È un'operazione terminale che riduce lo stream utilizzando la funzione fornita in input.

_Somma:_

```java
int somma = 0;
for (int k : lista)
	somma += k;

//Con gli stream

lista.stream().reduce(0, (a,b)->a+b); //Oppure
lista.stream().reduce(0, Integer::sum);
```

![[Pasted image 20240516124721.png|500]]

Il primo parametro è l'identità ovvero il valore iniziale della riduzione, in questo esempio sopra riduciamo lo stream ad un solo elemento ovvero la somma di tutti gli elementi.

Esiste anche una versione senza identità che restituisce un `Optional<T>`.

```java
lista.stream().reduce(Integer::sum);
````

Perché restituiamo `Optional<T>`? In questo modo se lo stream è vuoto non avendo un'identità iniziale non sappiamo che valore restituire, con un optional possiamo restituire null.

_Esempio_

![[Pasted image 20240516125207.png]]

In questo modo dato uno stream di stringhe, lo riduciamo ad un'unica stringa composta da tutti gli elementi concatenati dal carattere '#'.

_Esercizio_
Calcolare la somma del doppio dei valori pari

![[Pasted image 20240516125951.png|500]]

## Limit
Limita lo stream a _k_ elementi, è un'operazione intermedia

```java
List<String> elementi = List.of("uno","due","tre");
List<String> reduced = l.stream().limit(2).collect(toList());
//Conterrà ["uno","due"]
```

## Skip
È un'operazione intermedia, salta _k_ elementi con _k long_ passato in input

```java
List<String> elementi = List.of("uno","due","tre");
List<String> reduced = l.stream().skip(2).collect(toList());
```

Contiene solo `["tre"]`.

## takeWhile / dropWhile

- takeWhile prende elementi finché si verifica la condizione del predicato
- dropWhile salta gli elementi finché si verifica la condizione

```java
List<Integer> elementi = List.of(2,5,10,42,3,2,10);
List<Integer> reduced = l.stream().takeWhile(x->x<42).collect(toList());
// contiene [2,5,10]
```

Quindi una volta trovata una condizione falsa si fermano, anche 3,2,10 rispettano la condizione ma non sono stati presi dal takeWhile perché si è fermato al primo 42.

## anyMatch / allMatch / noneMatch 
Sono tutte operazioni terminali di matching che restituiscono un booleano relativo all'esito del matching.

_Esempi_

```java
boolean anyStartsWithA = l.stream().anyMatch(s->s.startsWith("a"));
System.out.println(anyStartsWithA);
boolean allStartsWithA = l.stream().allMatch(s->s.startsWith("a"));
boolean noneStartsWithZ = l.stream().noneMatch(s->s.startsWith("z"));
```

Quindi controllano rispettivamente:
- un elemento qualsiasi se rispetta il match
- se lo rispettano tutti
- se non lo rispetta nessuno

## findFirst, findAny
Sono operazioni terminali che ritornano il primo o un qualsiasi elemento dello stream

![[Pasted image 20240516131207.png|500]]

_Restituisci il doppio del primo valore in una lista di interi che sia pari e > 41_

![[Pasted image 20240516131241.png|500]]

## mapToInt e IntStream.summaryStatistics
Possiamo convertire uno Stream in un IntStream che possiede il metodo _summaryStatistics_ che restituisce un oggetto di tipo _IntSummaryStatistics_ che contiene informazioni su _min, max, media, conteggio_.

```java
List<Integer> p = List.of(2,3,4,5,6,7);
IntSummaryStatistics stats = p.stream().mapToInt(x->x)
.summaryStatistics();

System.out.println(stats.getMin());
System.out.println(stats.getMax());
System.out.println(stats.getAverage());
System.out.println(stats.getCount());
```

## flatMap
È un'operazione intermedia che permetti di unire gli stream in un unico stream, è la funzione che genera due stream che poi unisce, dobbiamo quindi fornire i supplier per crearli.

```java
Map<String, Long> letterToCount =
words.map(w -> w.split("")) // Restituisce String[]
.flatMap(Arrays::stream)
.collect(groupingBy(identity(), counting()));
```

![[Pasted image 20240516132642.png|500]]

Serve ad "appiattire" una collezione.
Trasformiamo gli elementi del nostro stream in altri stream e poi concatena questi stream creandone uno unico.

_Esempio_

![[Pasted image 20240516133434.png|500]]

_Esempio_

![[Pasted image 20240516133734.png|500]]

- Trasformiamo ogni linea in un array che contiene i token
  Abbiamo quindi uno stream di array
- Con flatmap creiamo degli stream da questi array e li uniamo ottenendo quindi uno stream di stringhe
- Eliminiamo i doppioni
- Stampiamo

_Esempio_

![[Pasted image 20240516134031.png]]

FlatMap prende gli array della seconda riga, li trasforma in stream e li concatena arrivando ad un unico stream di stringhe ovvero quello nella terza riga.

## IntStream, DoubleStream e LongStream
Questi si ottengono da altri Stream con i relativi metodi _mapToInt, mapToLong, mapToDouble_, e questi metodi sono disponibili anche nelle loro classi ma in più hanno _mapToObject_.
Un altro metodo aggiuntivo è _boxed_ che ci fa tornare da uno stream specializzato ad uno stream generico.
Ovviamente IntStream non avrà mapToInt.
Hanno 2 metodi statici:
- _range(inizio, fine):_ intervallo esclusivo (aperto a destra)
- _rangeClosed(inizio, fine):_ intervallo inclusivo (chiuso a destra)

_Esempio: Stampa in numeri dispari fino a 10_:

```java
IntStream.range(0, 10).filer(n->n%2==1)
.forEach(System.out::println);
```

_Esempio: IntStream ottenuto da stream di array di interi_

```java
Arrays.stream(new int[] {1,2,3}) //Restituisce un IntStream
.map(n->2*n+1)
.average() // Metodo di IntStream
.ifPresent(System.out::println); //5.0
```

_Esempio: Passaggio da Stream a IntStream, LongStream, DoubleStream_

![[Pasted image 20240521092924.png]]

- Ho uno stream di stringhe
- Lo trasformo in un intStream che contiene la lunghezza delle stringhe
- Lo trasformo in uno stream di Long
- Lo trasformo in uno stream di Double che contiene ogni valore / 42.0
- Con _boxed_ torniamo da una specializzazione come in questo caso _DoubleStream_ ad uno stream non specializzato quindi torniamo ad uno _Stream di Double_ **NON DOUBLESTREAM**.
- Lo trasformo in uno stream di Long dove ogni elemento diventa _1L_.
- Trasformo lo stream in uno stream di Stringhe vuote al posto dei _1L_.

**Ottenere uno Stream Infinito**
L'interfaccia Stream espone un metodo _iterate_ che partendo dal primo elemento dello stream restituisce uno stream infinito con i valori successivi applicando la funzione passata come argomento:

```java
Stream<Integer> numbers = Stream.iterate(0, n -> n + 10);
```

È possibile limitarlo con il metodo _limit:_

```java
numbers.limit(5).forEach(System.out::println);
```

**Iterazione mediante Stream**
L'interfaccia Stream espone un altro metodo iterate che partendo dal primo argomento restituisce uno stream dei valori successivi applicando la funzione passata come terzo argomento e uscendo quando il predicato del secondo argomento è false:

```java
Stream<Integer> numbers = Stream.iterate(0, n-> n < 50, n->n+10);
```

**Ordine delle Operazioni**
Come abbiamo già visto l'ordine delle operazioni è importante, se ad esempio dobbiamo eseguire delle operazioni e filtrare conviene prima filtrare lo stream e poi eseguire le operazioni.

_Esempi Ordine Operazioni:_

![[Pasted image 20240521094430.png]]

![[Pasted image 20240521094755.png]]

Le operazioni vengono eseguite una dopo l'altra su ogni elemento, quindi nel primo esempio per ogni elemento eseguiamo _map_ e poi _filter_ che in alcuni casi elimina gli elementi.
Nel secondo esempio prima filtriamo e quindi se l'elemento va eliminato non verrà eseguita la _map_ riducendo di molto le operazioni svolte.

![[Pasted image 20240521095141.png]]

In questo caso _sorted_ è un'operazione _stateful_ e quindi _bloccante_ questo significa che verrà eseguita su tutti gli elementi e poi andremo avanti con le successive sempre in modo parallelo, a meno che non ci siano operazioni bloccanti nel mezzo, _esempio successivo_.

![[Pasted image 20240521095635.png]]

In questo esempio sorted è posto tra filter e map, questo significa che queste due operazioni non possono essere eseguite in parallelo, prima viene eseguito tutto filter, poi il sorted e infine map.
Ovviamente se dopo map ci fossero stato altre operazioni non bloccanti queste sarebbero state eseguite in parallelo.

![[Pasted image 20240521100334.png]]

In questo caso abbiamo ottimizzato l'esecuzione con _limit_ perchè filter e map avrebbero aggiunto anche 6 e 8 allo stream ma con limit ci fermiamo al secondo elemento.
Abbiamo quindi eseguito le operazioni soltanto su 2 e 4.

## Fare Copie di Stream
Gli stream non sono riutilizzabili ma possiamo creare un builder di stream con una lambda.

```java
Supplier<Stream<String>> streamSupplier = () ->
	Stream.of("d2","a2","b1","b3","c")
		.filter(s -> s.startsWith("a"));
streamSupplier.get().anyMatch(s -> true);
streamSupplier.get().noneMatch(s -> true);
```

Al posto del Supplier possiamo usare una funzione che prende in input una Collection e e restituisce uno stream della collection.

## Stream Paralleli
Le operazioni suglie stream visti fino ad adesso sono sequenziali effettuate su singolo thread.
Per gli stream paralleli le operazioni sono effettuate su thread multipli e quindi eseguite in modo concorrente.

_Perchè creiamo uno Stream Parallelo?_

```java
int max = 1000000;
List<String> values = new ArrayList<>(max);
for (int i = 0; i < max; i++)
{
	UUID uuid = UUID.randomUUID();
	values.add(uuid.toString());
}
```

In questo caso dobbiamo quindi creare 1.000.000 UUID.
Cosa accade con uno stream sequenziale:

![[Pasted image 20240521101526.png]]

- Ordiniamo 1000000 di stringhe e le contiamo
- Tempo di esecuzione: 899ms

_Con uno Stream Parallelo?_

![[Pasted image 20240521101712.png]]

Eseguendo le stesse operazioni abbiamo impiegato 472ms quindi circa il 50%.

**In alcuni casi però uno stream parallelo può essere più lento di uno stream sequenziale**.

![[Pasted image 20240521101900.png]]

**Quando usiamo uno stream Parallelo?**
- Quando non abbiamo solo / molte operazioni bloccanti (lo stream è parallelizzabile), se invece abbiamo molte operazioni non bloccanti adiacenti vale la pena parallelizzare lo stream
- Quando possiamo utilizzare più risorse, core del processore
- La dimensione del problema giustifica il costo aggiuntivo dovuto alla parallelizzazione.

## Mappe e Stream
Le mappe non supportano gli stream ma sono state implementate delle funzioni per risolvere questo "problema".

```java
Map<Integer, String> map = new HashMap<>();
for (int i = 0; i < 10; i++) map.putIfAbsent(i, "val" + i);
map.forEach((id, val) -> System.out.println(val));
```

Da Java 9 possiamo creare mappe costanti con _Map.of_.

_Metodi_

_ComputeIfPresent_
- Se l'elemento è presente modifichiamo il valore associato utilizzando la BiFunction passata come secondo parametro
  
  ![[Pasted image 20240521102723.png|500]]

Quindi nel primo esempio se 3 è presente, il valore di 3 diventa val + key.

_Merge_
- Se l'elemento è presente, modifica il valore utilizzando il secondo parametro che è il nuovo valore e la funzione passata come terzo parametro.

	![[Pasted image 20240521103003.png|500]]

Quindi in questo caso se 9 è presente il suo valore diventa il precedente concatenato a "val9".

_Remove_
Ha due metodi uno se passiamo soltanto la chiave toglie la chiave se presente, se passiamo 2 parametri (key, val) elimina la chiave soltanto se questa ha il valore uguale a quello passato come parametro.

## API Data e Ora

![[Pasted image 20240521103255.png|500]]

_Esempio_

![[Pasted image 20240521103309.png|500]]

