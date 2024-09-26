# Metodi Statici
I metodi statici non hanno accesso ai campi di istanza (oggetti) ma hanno accesso soltanto ai campi di classe (static) infatti sono detti **metodi di classe**

# Lettura Input da Console
Dobbiamo utilizzare la classe _java.util.Scanner_

```java
public class Input() {
	public static void main(String[] args) {
		java.util.Scanner scanner = new java.util.Scanner(System.in);
		System.out.println("Come ti chiami?");
		String nome = scanner.nextLine();
		System.out.println("Ciao " + nome);
	}
}
```

É più comodo importare direttamente il package invece di specificare ogni volta che utilizziamo una sua classe.
Possiamo anche importare tutto il package direttamente invece che una sola classe:

```java
import java.util.Scanner; // Importo soltanto la classe Scanner
import java.util.*; // Importo l'intero package
public class Input() {
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		System.out.println("Come ti chiami?");
		String nome = scanner.nextLine();
		System.out.println("Ciao " + nome);
	}
}
```

# Istruzioni di Controllo
Per ora abbiamo controllato l'esecuzione del programma tramite l'ordine in cui abbiamo scritto le istruzioni.
Possiamo prendere decisioni ad esempio con l'istruzione _if_ ed _else_:

```java
if (<espressione booleana>)
{
	<istruzioni>
}
// Oppure
if (<espressione booleana>) <singola istruzione>


if (x < 0) x = -x;
if (x < y)
{
	int t = x;
	x = y;
	y = t;
}

int max = 0;
if (x > y) max = x;
else max = y;
```

**Operatore Ternario**

```java
//Sintassi
// condizione ? valoreCasoVero : valoreCasoFalso
int abs = x < 0 ? -x : x
int max = x > y ? x : y;
String testaCroce = Math.random() < 0.5 ? "Testa" : "Croce";
```

# Operatore Switch
Per confrontare più valori invece di utilizzare tanti _if else_ annidati possiamo utilizzare il costrutto _switch_

```java
switch(<espressione intera>)
{
	case <valore1>: <istruzioni>; break;
	case <valore2>: <istruzioni>; break;
	case <valore>: >istruzioni>; break;
	default: <istruzioni> //Viene eseguito se non rientriamo in altri casi
}

// Con la freccia -> possiamo omettere il break
switch(<espressione intera>)
{
	case 0 -> metodo1();
	case 1 -> metodo2();
	case 2 -> metodo3();
	default -> "ciao";
}

String s = switch(c)
{
	case 'a': case 'o' : case 'c' : s = "Ciao"; break;
	//Da Java 13 in poi
	case 'a','o','c' -> "ciao";
}

```

Il _break_ infatti non è obbligatorio ma se non lo inseriamo dopo essere entrati in un caso, il compilatore continuerà a controllare anche gli altri.
Da Java 13 in poi lo _switch_ è diventato quindi un vero e proprio _operatore_ con il quale possiamo assegnare variabili:

```java
String s = switch(c) {
	case 'k': yield "kappa";
	case 'a': case 'b': yield "ciao";
};
```

# Istruzioni Iterative
- _while_
- _do while_
- _for_

**While**

```java
while (<espressione booleana>)
{
	<istruzioni>
}
```

Le istruzioni all'interno vengono ripetute finché la condizione booleana è vera, l'espressione viene controllata all'inizio di ogni iterazione.

**Do While**

```java
do
{
	<istruzione>
} while (<espressione booleana>)
```

In questo costrutto eseguiamo almeno una volta le istruzioni nel blocco _do_ e a fine blocco controlliamo l'espressione booleana.
L'espressione viene sempre controllata _alla fine_ e il blocco viene eseguito _almeno una volta_ prima di controllare l'espressione

**For**

```java
for (<inizializza controllo>; <espressione booleana>; <incremento>)
{
	<istruzioni>
}

int somma = 0;
for (int i = 0; i < N; i++)
{
	somma += i;
}
```

Con il ciclo for controlliamo l'epsressione booleana a fine blocco e incrementiamo o decrementiamo il controllo di quanto specificato nel costrutto.