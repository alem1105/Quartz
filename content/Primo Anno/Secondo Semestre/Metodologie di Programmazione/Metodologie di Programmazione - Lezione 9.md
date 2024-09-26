# Le Interfacce
Consentono a più classi di implementare un insieme di metodi comuni
La differenza con le classi astratte è che le interfacce specificano soltanto il comportamento di un oggetto all'esterno mentre l'implementazione di queste operazioni rimane non definito.
Nelle interfacce quindi non possiamo stabilire dei costruttori.

- È possibile specificare delle implementazioni di default di metodi non statici
	- Si utilizza la parola chiave **default**
- E implementazione di metodi statici
	- Sono metodi associati alle singole istanze

Si possono definire metodi privati all'interno di un'interfaccia

![[Pasted image 20240404122334.png]]

Un'interfaccia è una classe che può contenere soltanto:
- Costanti
- Metodi Astratti
- Implementazione di default di metodi e metodi statici
- Metodi privati usati tipicamente nei metodi di default
- Tutti i metodi sono _public abstract_
- Tutti i campi sono _public static final_
- Tranne nel caso di metodi _default o statici_ non è possibili specificare l'implementazione

_Esempio Dichiarazione Interfaccia_

![[Pasted image 20240404122558.png]]

_Esempio Implementazione in una classe_

![[Pasted image 20240404122809.png]]

L'utilità delle interfacce è quindi quella di modellare comportamenti comuni a classi che non sono necessariamente in relazione gerarchica.

**Esempio, Interfaccia Iterabile**

```java
public interface Iterabile
{
	boolean hasNext();
	Object next();
	void reset();
}
```

Possono quindi implementare questi metodi sulle mie classi che voglio rendere "iterabili".

Esiste un'interfaccia già implementata in Java, l'interfaccia **Iterable** oppure **Iterator**.

![[Pasted image 20240404125037.png]]

Quindi la classe _Iterable_ restituisce un oggetto di tipo _Iterator_ che ci fornisce un puntatore per accedere agli elementi.
Questo è utile nel caso di cicli annidati dove con lo stesso oggetto potremmo ottenere iterabili diversi ma con lo stesso puntatore.

**Contratto della classe con il compilatore**

![[Pasted image 20240404132430.png]]

L'utilità è quindi di poter implementare più di un'interfaccia dato che una classe può invece ereditare soltanto una classe per volta.
Possiamo anche estendere una classe e implementare più di una interfaccia

Anche per le interfacce vale il polimorfismo quindi possiamo scrivere cose come:

```java
SupportoRiscrivibile supporto = new Nastro();
supporto.leggi();
```

E possiamo quindi utilizzarlo come se fosse di tipo _SupportoRiscrivibile_ e abbiamo quindi visibilità limitata ai soli metodi dell'interfaccia SupportoRiscrivibile