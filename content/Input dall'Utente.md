Per usare gli input da terminale dell'utente dobbiamo importare una libreria chiamata **java.util.Scanner** in questo modo:

```java
import java.util.Scanner;
```

Adesso possiamo creare un **oggetto** di tipo Scanner, vediamo la sintassi anche se la studieremo più avanti con la **programmazione a oggetti**.

```java {5}
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
		Scanner og_scanner = new Scanner(System.in);
	}
}
```

> [!example] Analizziamo per punti cosa fa questa riga:
> - **Scanner:** Indica il tipo di variabile che stiamo creando, è lo stesso procedimento che utilizziamo per, ad esempio, gli interi le stringhe ecc..
> - **og_scanner:** Indica il nome della variabile
> - **new Scanner(System.in):** stiamo chiamando il metodo costruttore della classe Scanner, questo lo vedremo più nel dettaglio nella programmazione a oggetti

--- 

Adesso vediamo come fare delle domande all'utente e associare le sue risposte a delle variabili all'interno del nostro codice

```java
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
		Scanner og_scanner = new Scanner(System.in);

		System.out.println("Ciao! Come ti chiami?");
		String nome = scanner.nexLine();
	}
}
```

Possiamo adesso utilizzare questo dato nel codice, ad esempio per mandarlo in output insieme ad altri valori.

```java
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
		Scanner og_scanner = new Scanner(System.in);

		System.out.println("Ciao! Come ti chiami?");
		String nome = scanner.nexLine();

		System.out.println("Ciao " + nome);
	}
}
```

**Vediamo come prendere valori numerici**

```java
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
		Scanner og_scanner = new Scanner(System.in);

		System.out.println("Ciao! Come ti chiami?");
		String nome = scanner.nexLine();
		
		System.out.println("Quanti anni hai?");
		int eta = scanner.nextInt();
		
		System.out.println("Qual e' il tuo cognome?");
		String cognome = scanner.nexLine();
	}
}
```


> [!bug] scanner.nextInt()
> Quando leggiamo l'età con **scanner.nextInt()** questo non posizionerà il cursore in una nuova linea ma rimarrà alla fine di quella con l'intero appena letto creando problemi per le linee successive, infatti provando questo programma crasherà dopo aver inserito l'età.

**Vediamo una soluzione:**

```java
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
		Scanner og_scanner = new Scanner(System.in);

		System.out.println("Ciao! Come ti chiami?");
		String nome = scanner.nexLine();
		
		System.out.println("Quanti anni hai?");
		int eta = scanner.nextInt();
		scanner.nextLine();
		
		System.out.println("Qual e' il tuo cognome?");
		String cognome = scanner.nexLine();
	}
}
```

Ci basta infatti posizionare manualmente il cursore nella prossima linea facendo leggere allo scanner ma senza assegnare il valore appena letto.


