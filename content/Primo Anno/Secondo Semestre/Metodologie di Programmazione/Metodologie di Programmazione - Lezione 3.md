# java.lang.String
É la classe fondamentale per utilizzare il tipo _String_, per questo tipo di dato è stato anche riscritto l'operatore _+_ (concatenazione di stringhe).

## Metodi
- _.length()_
- _toLowerCase()_
- _toUpperCase()_
- _charAt(i)_ Restituisce il carattere alla posizione i
- _substring(startIndex, endIndex)_ Restituisce sottostringa
	  `String s = "ciao"; System.out.println(s.substring(1,3))`
	  Stamperà "ia".
- _startsWith - endsWith_ Verificano la presenza di prefissi e post
- _replace_ Sostituire tutte le occorrenze di un carattere o stringa all'interno di un'altra

```java
String min = "Ciao".toLowerCase(); //ciao
```

Notiamo che non abbiamo bisogno di chiamare il costruttore String.

### Concatenazione fra stringhe
- Possiamo effettuarla con il semplice _+_
- Possiamo utilizzare il metodo _.concat()_

```java
String s3 = s1+s2;
String s4 = s1.concat(s2); //Metodo più efficiente
```

Se devo concatenare molte stringhe è bene usare la classe **StringBuilder**

```java
StringBuilder sb = new StringBuilder;
sb.append(s1).append(s2);
String s5 = sb.toString();
```

### Cercare caratteri
Utilizziamo il metodo _indexOf(c)_:
- Restituisce un intero positivo corrispondente alla **prima posizione** del carattere
- Restituisce -1 se il carattere non è presente nella stringa

```java
int k = "happy happy happy".indexOf('a');
```

Restituisce 1 perché è la prima _a_ che troviamo

### Spezzare le stringhe
Il metodo _split_ prende in input un'espressione regolare s (una semplice stringa) e restituisce un array di sottostringhe separate s.

```java
String[] parole = "uno due tre".split(" ");
//parole contiene l'array new String[] { "uno" , "due" , "tre" }
```

## Confronto tra oggetti
Gli oggetti in generale vanno **sempre confrontati** con il metodo **equals**

- L'operatore _= =_ confronta il riferimento (indirizzo in memoria) quindi sarà _true_ se e solo se si confrontano gli stessi oggetti
- L'operatore _equals_ confronta la stringa carattere per carattere e restituisce _true_ se sono tutti uguali.

# Tipi di dato in Java: Primitivi e Oggetti
- Valori primitivi: int, char, boolean, float, double ecc..
- Oggetti: Istanze delle classi

Cambia come Java rappresenta nella memoria
- Valori primitivi: memoria allocata automaticamente nella **compilazione**
- Oggetti: memoria allocata durante **l'esecuzione del programma**

Al momento della creazione di un oggetto i suoi campi sono **inizializzati automaticamente**, questo avviene automaticamente per le classi ma **non** per le **variabili locali di un metodo**

| Tipo del campo | Inizializzato a |
| -------------- | --------------- |
| int, long      | 0, 0L           |
| float, double  | 0.0f, 0.0       |
| char           | '\0'            |
| boolean        | false           |
| classe X       | null            |

Possiamo dichiarare gli interi in notazione esadecimale o binario:

```java
int val = 0x2A;
int val = 0b101;
```

Per i double possiamo usare la notazione scientifica:

```java
double val = 0.425e2;
// Possiamo rappresentare il suo equivalente float
float val = 42.5f;
```

Il valore di questi 8/4 byte sarà sempre lo stesso.

## Riferimenti e Oggetti
Un riferimento è un indirizzo di memoria ma di cui non conosciamo il valore numerico dell'indirizzo, gli oggetti quindi **non  sono memorizzati direttamente** ma tramite il loro **riferimento**.
Le variabili quindi possono contenere o tipi di dati primitivi oppure **riferimenti ad oggetti** ma non gli oggetti stessi.

**Creazione di un oggetto**
- *Menu menu* = new Menu() - Dichiarazione
- Menu menu = *new Menu()* - Creazione
- Menu menu *=* new Menu() - Assegnazione

## Memoria
Esistono due tipi di memoria:
- **heap**: Vengono allocate le aree di memoria per la _creazione dinamica_ (oggetti)
- **stack**: Vengono allocate le variabili locali

![[Screenshot 2024-03-07 alle 13.35.24.png]]
![[Screenshot 2024-03-07 alle 13.35.33.png]]
![[Screenshot 2024-03-07 alle 13.35.41.png]]

- **MetaSpace**: Qui vengono allocati i campi di tipo static relativi all'intera classe, nel caso di un oggetto non static invece abbiamo una locazione di memoria diversa per ogni oggetto creato.

Quando viene avviato un programma il compilatore di Java esegue queste azioni:
- Tramite il **ClassLoader** carica la classe e vede se c'è un metodo main eseguibile.
- Alloca nel **MetaSpace** i campi statici se ci sono
- Inizia ad eseguire il main riservandogli una locazione di memoria nello **stack** e copiando **nell'heap** i valori presenti nella lista args, anche se vuota.
- Va avanti nella compilazione del programma allocando locazioni di memoria di variabili, oggetti e metodi mano a mano che li troviamo.

I valori dei parametri di un metodo vengono sempre copiato e non passati per riferimento, se troviamo un nuovo metodo questo viene allocato ad un livello superiore nello stack.