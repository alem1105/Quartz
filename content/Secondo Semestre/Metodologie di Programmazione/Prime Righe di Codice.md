Il nostro file principale è _main.java_ ovvero da dove inizia il nostro programma, più nello specifico il programma inizia dalla **funzione main**:

```java
public class Main {
	public static void main(String[] args) {
		// Codice
	}
}
```

La classe ovvero il file può chiamarsi come vogliamo in questo caso _Main_ ma la funzione **main** deve chiamarsi così per far capire a Java che è dove inizia il programma.
- Con **//** indichiamo dei commenti, ovvero linee di codice ignorate in compilazione
- Possiamo anche scrivere commenti su più linee aprendolo con **/\*** e chiudendolo con **\*/**

```java
// Commento su singola linea

/* Commento
* su
* piu'
* linee
*/
```

**Mandare in output sulla console**:
```java
public class Main {
	public static void main(String[] args) {
		System.out.print("Hello World!");
		System.out.println("Nuova Riga");
		Sytem.out.print("\nCiao!");
	}
}
```

- **print:** Stampa sulla console posizionandosi all'ultimo carattere
- **println:** Stampa ogni volta una nuova linea andando quindi a capo
- Per andare a capo possiamo utilizzare anche i caratteri speciali come _'\\n'_