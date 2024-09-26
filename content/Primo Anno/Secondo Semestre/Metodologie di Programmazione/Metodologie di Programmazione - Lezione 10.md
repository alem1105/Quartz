# Interfacce Notevoli

![[Pasted image 20240409092600.png]]

- **Comparable**: Ci obbliga a implementare il metodo _compareTo_ dove definiamo un metodo di comparazione fra due oggetti della classe.
- **Cloneable**: Effettua una clonazione _campo a campo_ questo significa che se come campo abbiamo una stringa e creiamo un nuovo oggetto clonato, quest'ultimo si riferirà alla stessa stringa già in memoria.
- **Serializable**: Possiamo ottenere una rappresentazione a stringa dell'oggetto per memorizzarlo su un file, un programma potrebbe quindi riutilizzare questo oggetto salvato durante un'altra runtime.
- **Runnable**: Ha un metodo _run_ dove specifichiamo un metodo che verrà eseguito su un thread.

> [!info] Metodo Clone
> L'operatore di assegnazione non _copia_ l'oggetto ma copia il suo riferimento.
   Per creare una copia abbiamo bisogno del metodo _clone()_ che crea un nuovo oggetto ma non richiama il costruttore della classe, infatti copia campo a campo e questo funziona bene quando i campi sono tutti primitivi mentre se i campi sono riferimenti viene **copiato soltanto il riferimento**.
   Possiamo sovrascrivere il metodo _clone_ che è protetto quindi la nostra classe dovrà necessariamente **implementare** _cloneable_.
   Per effettuare una **deep clone** invece posso utilizzare clone per i tipi primitivi e poi richiamare clone su tutti i campi che sono riferimenti

![[Pasted image 20240409100855.png]]

Quindi faccio il _downcasting_ da Object per clonare l'oggetto e se ho bisogno di clonare dei campi con riferimento, richiamo _.clone()_ anche sul campo.

![[Pasted image 20240409093908.png]]

# Classi Annidate e Classi Interne
Le classi utilizzate fino ad ora vengono dette **top-level** perché si trovano più in alto di tutte le altre e non sono contenute in altre, queste classi infatti hanno bisogno di un file _.java_ con lo stesso nome.

**Classi Annidate**
- Possiamo scrivere classi all'interno di altre classi, **Classi Annidate** e ci sono di due tipi:
- **Static (Nested Class)**
- **Non Static (Inner Class)**

Prima di poter creare un oggetto della classe interna dobbiamo istanziare un oggetto della classe esterna, infatti ciascuna classe interna ha un riferimento all'oggetto della classe che la contiene.
Dalla classe interna possiamo accedere a tutti i campi e metodi della classe esterna e come tutti i campi o metodi le classi interne posso essere dichiarate _public, private o protected_.

## Inner Class
Per togliere ambiguità quando utilizziamo _this_ ci stiamo riferendo alla classe interna mentre con _TopClass.this_ ci stiamo riferendo alla classe di livello superiore.
Dalla classe esterna per istanziare un oggetto della classe interna ci basta utilizzare _new_ mentre dall'esterno si usa la sintassi

```java
riferimentoOggettoClasseEsterna.new ClasseInterna();
```

## Nested Class
Se la classe interna è statica, questa non richiede un oggetto della classe esterna e non contiene nemmeno un riferimento a essa.
Come per i metodi statici questa non può accedere allo stato dei singoli oggetti, _campi non statici_.
A livello di comportamento una classe statica annidata è **equivalente a una classe top-level** scritta all'interno di un'altra top-level.
Sono accessibili con la sintassi:

```java
new ClasseEsterna.ClasseAnnidataStatica();
```

**A cosa servono:**
- Raggruppamento logico delle classi
- Aumenta l'incapsulamento infatti una classe B annidata in A può accedere ai membri di A anche se privati, ma B viene **nascosta all'esterno**.
- Codice più leggibile

# Classi Anonime
Possiamo definire classi senza nome che implementano un'interfaccia o estendono una classe, queste vengono utilizzate per creare un'unica istanza.
Vengono utilizzate in contesti specifici per utilizzi veloci come ad esempio creare un iteratore.

_Sintassi:_

```java
TipoDaEstendere unicoRiferimentoAOggetto = new TipoDaEstendere()
{
	//Codice della classe anonima (implementazione dell'interfaccia
	// o estensione della classe)
};
```

_Esempio_

```java
public interface Formula
{
	double calculate(int a);
	default double sqrt(int a) { return Math.sqrt(a) }
}

//In un altro file posso usare

Formula formula = new Formula()
{
@Override
public double calculate(int a) {
		return sqrt(a * 100)
	}
};
formula.calculate(100); //100.0
formula.sqrt(16) //4.0
```

# Interfacce Funzionali
Possiamo utilizzare l'annotazione _@FunctionalInterface_, questa garantisce che l'interfaccia sia dotata di **un solo metodo astratto**

```java
@FunctionalInterface
public interface Runnable
{
	void run();
}
```

# Espressioni Lambda
Possiamo utilizzare le **espressioni lambda** per compattare il codice;
Queste espressioni creano oggetti anonimi assegnabili a riferimenti a **interfacce funzionali compatibili con l'intestazione** della funzione creata.
_(Infatti l'interfaccia funzionale ha un solo metodo)_

Posso dichiarare un metodo in questo modo:

```java
() -> { System.out.println("hello, lambda!"); }
```

Quindi abbiamo soltanto le parentesi per i parametri se presenti e seguita dalla freccia l'implementazione del metodo.

_Esempio utilizzo:_

```java
Runnable r = () -> { System.out.println("hello, lambda!"); };
r.run(); // Stampa "hello, lambda!"
```

_Sintassi specifica:_

```java
(tipo nomeParametro) -> { codice della funzione }
```

- Il tipo dei parametri è **opzionale** perché si ricava dal contesto dell'interfaccia a cui facciamo riferimento
- Le parentesi tonde sono **opzionali** se in input abbiamo un solo parametro
- Le parentesi graffe sono **opzionali** se il codice è costituito da una sola riga
- **Non è necessario nessun return** se il codice è dato dall'espressione di ritorno

_Esempi sintassi:_

![[Pasted image 20240409112332.png]]
![[Pasted image 20240409112408.png]]

# Single Abstract Method (SAM) type

Le interfacce funzionali sono di tipo **SAM**, a ogni metodo che accetta un'interfaccia SAM si può passare un'espressione lambda compatibile con l'unico metodo dell'interfaccia SAM.

# Differenze tra classi anonime ed espressioni lambda

Abbiamo differenze nell'utilizzo della parola chiave _this_:
- Nelle classi anonime si riferisce all'oggetto anonimo
- Nelle espressioni lambda si riferisce all'oggetto della classe che lo racchiude
Differenze nella compilazione:
- Le classi anonime sono compilate come classi interne
- Le espressioni lambda sono compilate come metodi privati.

