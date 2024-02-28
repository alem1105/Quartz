Una variabile contiene un valore nel tempo ed è la base di ogni linguaggio di programmazione.
Per dichiarare una variabile in Java ci sono vari step:
- **Dichiarazione**
- **Assegnazione**
- **Inizializzazione**

```java
public class Main {
	public static void main(String[] args) {
		int x; //dichiarazione
		x = 45; //assegnazione
		int y = 34; //inizializzazione -> dichiarazione e assegnazione
	}
}
```

Una variabile può **contenere soltanto i dati del tipo dichiarato**, quindi un intero (int) non può contenere stringhe di testo o numeri con la virgola (double), quindi ogni volta dobbiamo dichiarare il giusto tipo di variabile.
Una volta inizializzata una variabile possiamo usarla per svolgere operazione o anche mandarla in output sulla console:

```java
public class Main {
	public static void main(String[] args) {
		int x = 5;
		String y = "Alessio";
		double z = 9.72;

		System.out.println(x);
	}
}
```

Una variabile può ovviamente anche **anche cambiare valore** durante il programma ma **non tipo di dato**:

```java
public class Main {
	public static void main(String[] args) {
		int x;
		x = 45;
		x = 195;
	}
}
```


> [!NOTE] Notazioni
> - Gli identificatori non possono iniziare con delle cifre
> - Sono case-sensitive e si utilizza la notazione a cammello

