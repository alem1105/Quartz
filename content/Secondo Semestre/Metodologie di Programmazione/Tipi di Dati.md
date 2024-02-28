I tipi di dati in Java si dividono in **Primitive** e **Reference**.
Vediamo i principali tipi, che dati possono contenere e quanto spazio occupano:

| Tipo    | Valori                        | Peso    |
| ------- | ----------------------------- | ------- |
| boolean | true : false                  | 1 bit   |
| byte    | -128 : 127                    | 1 byte  |
| short   | -32768 : 32767                | 2 bytes |
| int     | -2 miliardi : 2 miliardi      | 4 bytes |
| long    | -9 quintilioni : 9 quintilioni      | 8 bytes |
| float   | numero con 6-7 cifre decimali | 4 bytes |
| double  | numero con 15 cifre decimali  | 8 bytes |
| char    | singolo carattere             | 2 bytes |
| String  | sequenza di caratteri         | variabile        |

**Possiamo ottenere anche un numero decimale da una rappresentazione binaria, esempio: 0b101 = 5**.

**Variabili numeriche:**
Quando inizializziamo una variabile di tipo **long** o **float** va inserita alla fine del numero rispettivamente una **'L'** o una **'F'**, maiuscole o minuscole non fa differenza
Notare anche che per scrivere numeri lunghi possiamo utilizzare gli underscore per renderli più leggibili.
```java
public class Main {
	public static void main(String[] args) {
		long numeroLong = 123_456_789_123_456_789L;
		// oppure
		long numeroLong = 123_456_789_123_456_789l;
		
		float numeroFloat = 3.123456F;
		// oppure
		float numeroFloat = 3.123456f;
	}
}
```

**Variabili alfanumeriche**:
Quando inizializziamo variabili di tipo **char o String** dobbiamo fare attenzione agli apici che utilizziamo, infatti per i char usiamo i singoli apici mentre per le Stringhe i doppi.
```java
public class Main {
	public static void main(String[] args) {
		char carattere = 'a';
		String stringa = "Ciao";
	}
}
```

- _La Stringa infatti è un insieme di caratteri_

> [!HELP]- Qual è quindi la differenza tra primitiva e reference?
> Le primitive sono quei tipi di dato che ci vengono forniti direttamente da Java, li possiamo distinguere facilmente perché iniziano con una lettera minuscola (**es. int, boolean, float**), mentre le reference sono tipi di dato più complessi creati da noi ma in questo caso ad esempio la **String** ci viene fornita direttamente da Java.
> Le reference infatti portano con loro una serie di **attributi** e **metodi** che possiamo utilizzare per manipolarli.


