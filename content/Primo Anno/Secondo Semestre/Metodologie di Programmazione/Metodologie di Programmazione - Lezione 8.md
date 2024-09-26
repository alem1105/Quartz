# Polimorfismo

Una variabile di un certo tipo può contenere un rifermento ad un oggetto del suo stesso tipo o di una sua qualsiasi sottoclasse

```java
Animale a = new Gatto();
a = new Chihuahua();
```

Quindi quando chiameremo dei metodi, il metodo chiamato avviene in base al tipo dell'oggetto contenuto nella variabile

```java
Animale a = new Gatto();
a.emettiVerso(); // Avremo un certo output
a = new Chihuahua();
a.emettiVerso(); // Cambio di output
```

**Non possiamo chiamare metodi esclusivi delle classi**, ad esempio se la classe _Gatto_ ha un metodo esclusivo la variabile _a_ di tipo _Animale_ non può chiamarlo anche se contiene un oggetto di tipo _Gatto_.

Il polimorfismo è quindi utile per utilizzare tanti oggetti diversi ma con caratteristiche in comune, possiamo infatti chiamare lo stesso metodo ma con implementazioni diverse e senza conoscerle.

## Binding statico e Dinamico

- Con il binding **statico** associamo una variabile al suo tipo, questo viene svolto dal _compilatore di Java_ prima di eseguire il codice.
- Il polimorfismo invece utilizza il binding **dinamico** infatti l'associazione tra variabile e metodo viene stabilita al tempo di esecuzione.

# Chiamare Metodi della Superclasse

![[Pasted image 20240326100931.png]]

![[Pasted image 20240326101146.png]]

In entrambe le classi abbiamo effettuato l'**override** del metodo _toString_, nella classe _StringaHackerataConStriscia_ abbiamo chiamato sia il costruttore della superclasse che il metodo _toString_.
Quindi creando un oggetto di tipo _StringaHackerataConStriscia_ passando una stringa e chiamando il metodo _toString_

![[Pasted image 20240326102351.png]]

# Conversione di Tipo fra sottoclasse e superclasse

Posso sempre convertire senza cast esplicito da un sottotipo ad un supertipo **upcasting**

```java
ImpiegatoStipendiato is1 = new ImpiegatoStipendiato("Mario", "imp1", 1500);
Impiegato i = is1;
```

Con un cast esplicito posso convertire da un supertipo ad un sottotipo **downcasting**

```java
ImpiegatoStipendiato is2 = (ImpiegatoStipendiato)i;
```

Quando effettuo l'**upcasting** non cancello l'oggetto ne creo di nuovi ma cambio soltanto i riferimenti.

---

**Campo Riferito ad un tipo Astratto**
Ad esempio con la classe Forma già vista possiamo utilizzare il polimorfismo per scrivere una cosa simile:

```java
Forma forma = new Cerchio();
```

---

# La superclasse Universale Object

Tutte le classi ereditano direttamente o indirettamente dalla classe _Object_, quando creiamo una classe senza estenderne un'altra, _implicitamente_ stiamo ereditando dalla classe Object

![[Pasted image 20240326111455.png]]

Quindi oltre alla classe _Object_ abbiamo una classe _Class_ infatti con il metodo _getClass()_ ci viene restituito la classe sottotipo della classe _Class_.

## Sovrascrivere il metodo equals

Il metodo _equals_ serve a confrontare due oggetti, la classe _Object_ però non conosce i suoi sottotipi che andremo a definire quindi è importante ridefinirlo se necesssario.

Implementazione standard di equals:

```java
public boolean equals(Object o) { return this == o; }
```

Nuova implementazione:

```java
public class Punto {
	private int x,y,z;
	
	@Override
	public boolean equals(Object o) {
	if (o == null) return false;
	if (getClass() != o.getClass()) return false;
	Punto p = (Punto)o
	return x == p.x && y = p.y && z = p.z;
	}
}
```

# Enum e Object

Una enumerazione ha tante istanze quante sono le costanti enumerative, le classi enumerative estendono la classe _Enum_ che a sua volte estende _Object_ dove il metodo equals restituisce _true_ solo se le costanti enumerative sono identiche.

Non possiamo creare nuove istanze ma possiamo creare istanze "costanti":

- Definiamo un costruttore non pubblico
- Si costruisce ciascuna costante con il rispettivo oggetto
- Possiamo creare altri metodi di accesso o modifica dei campi

![[Pasted image 20240327084032.png]]

_Altro Esempio_

![[Pasted image 20240327084213.png]]

# Metodi e classi Final

Quando dichiariamo una classe astratta e anche alcuni suoi metodi stiamo obbligando il programmatore a reimplementarli, se invece dichiariamo un metodo _final_ impediamo ai programmatori di sovrascriverli.
