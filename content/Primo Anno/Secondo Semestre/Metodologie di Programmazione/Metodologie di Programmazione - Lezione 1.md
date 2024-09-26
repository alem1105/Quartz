# La Programmazione ad Oggetti
Tutto può essere pensato come un **oggetto**, questi hanno:
- **Uno stato**
- **Delle Operazioni**

_Esempio:_
L'oggetto computer ha gli stati **accesso/spento** e può svolgere determinate operazioni.

Quando dobbiamo effettuare una richiesta ad un oggetto gli si invia un messaggio ovvero una richiesta di **chiamata a una funzione (metodo)** che appartiene all'oggetto.

Ogni oggetto ha una propria memoria **costituita da altri oggetti (incapsulamento)** infatti un nuovo tipo di oggetto può essere creato utilizzando oggetti già esistenti.

Ogni oggetto **è istanza di una classe**, questa è identificata dai **messaggi(metodi)** che essa possiede.

![[Pasted image 20240302195555.png]]

# Ereditarietà
Quando delle classi hanno funzionalità molto simili evitiamo di crearne di completamente nuove ma utilizziamo una parte di quelle già esistenti

![[Pasted image 20240302195743.png]]

# Polimorfismo
É possibile utilizzare la classe base, senza dover conoscere necessariamente la classe specifica di un oggetto.
Permette di scrivere codice che non dipende dalla classe specifica, ad esempio se consideriamo una classe madre “FiguraGeometrica” e due classi figlie “Cerchio” e “Quadrato”, entrambe con un metodo “calcolaArea”, il metodo può essere chiamato sulle istanze di entrambe le classi, ma verrà eseguito in modo diverso a seconda del tipo di oggetto.

# Java
Java è un linguaggio di programmazione **orientato agli oggetti** costruito per essere **"sicuro", cross-platform e internazionale.**
Un grande vantaggio è anche la sua portabilità sui vari sistemi operativi: **WORA (write once, run anywhere)**, Java infatti al contrario di altri linguaggi non viene compilato su una macchina ma nel **bytecode di una macchina virtuale**

## Tipi di dato di base (primitive)
Questa tipologia di dati sono **built-in** ovvero già di base nel linguaggio, è importante sapere quali tipi sono di base e quali non per questioni di **efficienza e allocazione della memoria**.
I tipi primitivi in Java possiamo distinguerli dal modo in cui sono scritti, infatti iniziano per una lettera minuscola (int, float, double, ecc...)

- **Interi** - 27
- **Reali** - 27.5
- **Booleani** - true o false
- **Caratteri** - 'c'
- **Stringhe** - "Sono una stringa" **Attenzione non è realmente un primitivo**

I tipi di dato comprendono anche delle operazioni che possiamo svolgere su di essi:

| Tipo    | Dominio                  | Operatori | Esempio            |
| ------- | ------------------------ | --------- | ------------------ |
| int     | interi                   | + - * / % | 27 + 1             |
| double  | Numeri in virgola mobile | + - * / % | 3.14 * 5.01e23     |
| boolean | valori booleani          | && \|\| ! | true \|\| false    |
| char    | caratteri                | + -       | 'a'                |
| String  | Sequenza di caratteri    | +         | "Hello" + " World" |
> [!bug] Operatore + nei caratteri
> L'operatore + nei caratteri non li concatena come avviene nelle stringhe ma restituisce l'intero dato dalla somma del loro valore Unicode dei caratteri sommati.
> Esempio: 'a' + 'b' = 195

| Tipo    | Intervallo                                                                   | Dimensione |
| ------- | ---------------------------------------------------------------------------- | ---------- |
| double  | parte intera: 10308, parte frazionaria: 15 cifre                             | 8 byte     |
| long    | -9223372036854775808...9223372036854775807                                   | 8 byte     |
| int     | -2147483648...2147483647                                                     | 4 byte     |
| float   | parte intera: ±1038, parte frazionaria: circa 7 cifre decimali significative | 4 byte     |
| boolean | true, false                                                                  | 1 byte     |
| char    | Tutti i caratteri codificati con Unicode                                     | 2 byte     |
| short   | -32768...32767                                                               | 2 byte     |
| byte    | -128...127                                                                   | 1 byte     |
## Variabili, dichiarazioni e assegnazioni
Una **variabile** è un nome usato per riferirsi a un valore di un tipo di dati, una variabile si crea mediante una **dichiarazione**:

```java
int contatore;
```

Dopo aver dichiarato una variabile gli assegniamo un valore tramite una **assegnazione**:

```java
contatore = 0;
```

Possiamo eseguire queste due operazioni in un solo step tramite **un'inizializzazione:**

```java
int contatore = 0;
```

Il nome assegnato ad una variabile è detto **identificatore** ovvero una sequenza di lettere, cifre, _ e $ la prima delle quali non è una cifra.
Gli identificatori sono case-sensitive, non si possono utilizzare le **parole riservate** (public, static, int, ecc...)
Si utilizza la **notazione a cammello (Camel Case)**: nomeVariabileIntera, secondaVariabile.
I nomi devono **essere sensati**.
Un'altra notazione usata per le variabile è mettere una lettere minuscola iniziale per specificare il tipo di dato, per esempio un intero: iContatore.

### Distinguere costanti intere e in virgola mobile
- Interi:
  Le costanti di tipo _int_ sono semplicemente numeri nell'intervallo $[-2, +2]$ miliardi.
  Le costanti tipo _long_ vengono specificate con con il suffisso _l o L_ dopo il numero (ad esempio, 1000000000000L)

- Numeri in virgola mobile:
  Le costanti di tipo _double_ sono semplicemente numeri con la virgola.
  Le costanti di tipo _float_ hanno il suffisso _f o F_ (ad esempio 10.5F)

In tutti i casi si può utilizzare il trattino basso per separare le cifre:
100_000 indica 100000, 1_234 indica 1234.

Possiamo ottenere degli interi anche dalla loro rappresentazione binaria:
Ad esempio 0b101 vale 5.

## Letterali
Un letterale è una rappresentazione a livello di codice sorgente del valore di un tipo di dati:
- 27 o 32 sono letterali per gli interi
- 3.14 è un letterale per i double
- true o false sono gli unici due letterali per il tipo di booleano
- "Ciao mondo" è un letterale per il tipo String

## Espressioni
Un'espressione è un letterale, una variabile o una sequenza di operazioni su letterali e/o variabili che producono un valore.
Possiamo, ad esempio, assegnare il valore di un'espressione a una variabile:

```java
c = a*2+b;
```

**Precedenza degli operatori aritmetici**

| Operatori | Operazioni                        | Precedenza                                     |
| --------- | --------------------------------- | ---------------------------------------------- |
| * / %     | Moltiplicazione, Divisione, Resto | Valutati per primi, da sinistra verso destra   |
| + -       | Addizione, Sottrazione            | Valutati per secondi, da sinistra verso destra |

## Caratteri e Stringhe
Un _char_ è un carattere alfanumerico o un simbolo racchiuso da apici ('a', 'b', '0', '1', ecc...)

_Caratteri di escape:_
- Tab: \\t
- A capo: \\n
- Backslash: \\\
- Apice: \\'
- Virgolette: \\"

Una _Stringa_ è una sequenza di caratteri

## Tipi di Booleani
Il tipo _booleano_ ha solo due valori possibili: true (vero) e false (falso), gli operatori disponibili sono && (and), || (or), ! (not) e seguono le tabelle di verità dell'**algebra di boole.**

## Operatori di confronti
Definiti sui tipi numerici primitivi, producono un valore booleano:
- Uguaglianza: ==
- Diversità: !=
- Minore: <
- Minore uguale: <=
- Maggiore: >
- Maggiore uguale: >=


| Operatori                         | Operazioni                              | Significato                                          |
| --------------------------------- | --------------------------------------- | ---------------------------------------------------- |
| post-incremento e post-decremento | var++ var--                             | Utilizza la variabile e poi la incrementa/decremeta  |
| pre-incremento e pre-decremento   | ++var --var                             | Incrementa/decrementa la variabile e poi la utilizza |
| Operatori moltiplicativi          | * / %                                   |                                                      |
| Operatori Additivi                | + -                                     |                                                      |
| Shift                             | << >> >>>                               |                                                      |
| Relazionali                       | < > <= >= istance of                    |                                                      |
| Confronto                         | == !=                                   |                                                      |
| AND bit a bit                     | &                                       |                                                      |
| OR esclusivo bit a bit (XOR)      | ^                                       |                                                      |
| OR inclusivo bit a bit            | \|                                      |                                                      |
| AND logico                        | &&                                      |                                                      |
| OR logico                         | \|\|                                    |                                                      |
| Operatore ternario                | ?:                                      |                                                      |
| lambda                            | ->                                      |                                                      |
| Assegnazione                      | = += -= *= /= %= &= ^= \|= <<= >>= >>>= |                                                      |

## Hello World

```java
public class HelloWorld //Dichiarazione di una classe
{
	public static void main(String[] args)
	{
		System.out.print("Hello, World");
		System.out.println();
	}
}
```

_public, class, static, void_ sono parole chiave

Il programma (_la classe_) Java risiede in un file che ha lo stesso nome della classe creata (HelloWorld) più l'estensione .java (HelloWorld.java)

In questo caso la classe contiene un **metodo chiamato main**.

**String[] args** sono gli argomenti del metodo

I corpi della classe e del metodo sono definite dalle **{ }**.
Ogni riga indica un'istruzione che termina con un **;**

## Create, Compile, Run

![[Pasted image 20240302222730.png]]

## Input presi in fase di esecuzione

```java
public class BotSemplice
{
	public static void main(String[] args)
	{
		System.out.print("Ciao ");
		System.out.print(args[0]);
		System.out.print(". Come va?");
	}
}
```

- _Compila_: javac BotSemplice.java
- _Esegui_: java BotSemplice Alessio
- _Output_: Ciao Alessio. Come va?

## Funzioni Matematiche Utili (class Math)

– double abs(double a)
– double max(double a, double b)
– double min(double a, double b)
– double sin(double theta)
– double cos(double theta)
– double tan(double theta)
– double exp(double a)
– double log(double a)
– double pow(double a, double b)
– long round(double a)
– double random()
– double sqrt(double a)

**Costanti**

double E
double PI

## Da Stringhe a Dati Primitivi
Supponiamo di voler utilizzare l'input di un programma per effettuare calcoli, come convertiamo questi dati da stringa a intero?

```java
public class SommaInteri
{
	public static void main(String[] args)
	{
		int a = Integer.parseInt(args[0]);
		int b = Integer.parseInt(args[1]);
		System.out.print("La somma vale: ");
		System.out.println(a+b);
	}
}
```

E in double?

```java
public class SommaInteri
{
	public static void main(String[] args)
	{
		Double a = Double.parseDouble(args[0]);
		Double b = Double.parseDouble(args[1]);
		System.out.print("La somma vale: ");
		System.out.println(a+b);
	}
}
```

## Da Dati primitivi a Stringhe
Java definisce l'operatore + sul tipo di dato "built-in" String.
Quando usiamo + con almeno un operando String, Java _converte automaticamente l'altro operando_ a String, restituendo una stringa:

```java
public class PensieroProfondo
{
	public static void main(String[] args)
	{
		String s = "Ciao io ho ";
		int anni = 21;
		String risposta = s+anni+" anni".
		System.out.println(risposta);
	}
}
```

## Conversioni di tipo
- **Conversione esplicita:** 
  Utilizzando un metodo che prende in ingresso un argomento di un tipo e restituisce un valore di un altro tipo
  Integer.parseInt(), Double.parseDouble()
  
- **Cast esplicito:**
  Anteponendo il tipo desiderato tra parentesi:
  (int)2.71828 produce un intero di valore 2.
  Se il tipo di partenza è più preciso (double), le informazioni aggiuntive vengono eliminate nel modo più ragionevole (passando ad un intero ad esempio viene troncata la parte decimale)

- **Cast implicito:**
  Se il tipo di partenza è meno preciso, Java converte automaticamente il valore al tipo più preciso.
  double d = 2; otteniamo 2.0

### Regole per il cast implicito
Il cast implicito **avviene in fase di assegnazione**:
- byte, short, char possono essere promossi a int
- int può essere promosso a long
- float può essere promosso a double

Oppure in **fase di calcolo**:
- se uno dei due operandi è double, l'intera espressione è promossa a double
- se uno dei due operandi è float, l'intera espressione è promossa a float

![[Pasted image 20240302225419.png]]

