# Design Patterns

## Strategy Pattern
- Trova gli aspetti che variano e separali (incapsulandoli) da quelli che rimangono uguali, questi aspetti possono quindi cambiare in modo indipendente dal progetto.
  Cancelliamo questi metodi e li modelliamo a parte
- Per ogni comportamento implementiamo un'interfaccia funzionale e ne implementiamo una per ogni possibile tipo di comportamento costruendo una gerarchia di interfacce.

![[Pasted image 20240521111819.png]]

La classe _Anatra_ adesso non implementa direttamente i comportamenti ma li delega alle interfacce.

![[Pasted image 20240521112049.png|500]]

Nel costruttore di ciascuna classe definiamo il comportamento specifico per ogni sottoclasse di Anatra

```java
public class AnatraDomestica extends Anatra
{
	public AnatraDomestica() 
	{
		compVolo = new VoloConAli();
		compStarnazzo = new Starnazzo();
	}
}
```

**Metodi Personalizzabili**
Grazie all'incapsulamento individuale di ogni comportamento possiamo adesso personalizzarli come vogliamo, possiamo quindi aggiungere elementi alla classe Anatra.

```java
protected void setComportamentoDiVolo(ComportamentoDiVolo c)
{
	compVolo = c;
}
protected void setComportamentoDiStarnazzo(ComportamentoDiStarnazzo c)
{
	compStarnazzo = c;
}
```

Le implementazioni dei metodi possono essere fornite come input di espressioni lambda o riferimenti ai metodi:

```java
ComportamentoDiStarnazzo st;
st = Starnazzo::starnazza;
st = Squittio::starnazza;
st = Muto::starnazza;
```

**UML Strategy**

![[Pasted image 20240521112453.png]]

_Esempi di utilizzo del pattern Strategy_
- Ordinamento quando non sappiamo quale algoritmo utilizzare.
- Giochi, quando dobbiamo inserire dei "potenziamenti" al personaggio, magari inizialmente può soltanto camminare e saltare e successivamente eseguire altre azioni come nuotare volare o altro.
- Produrre output: Produrre una stringa che rappresenti un oggetto oppure anche dei file XML, JSON, CSV ecc..
- Validazione, verificare gli elementi in base a delle regole, ma successivamente potremmo voler aggiungere altre regole.

**27 - 05 - 2024**

## Builder Pattern
Si utilizza quando ci sono più costruttori "in cascata" che si chiamano a vicenda per costruire l'oggetto.
Ad esempio quando utilizziamo operazioni intermedie negli stream stiamo creando altri stream.


- Creare una nuova Classe di solito _"\<Classe\> Builder"_, può anche essere annidata all'interno della classe stessa (in questo caso la chiamiamo soltanto _Builder_).
- Tutti i costruttori di classe vengono resi _privati_
- La classe Builder ha metodi per impostare i valori dei campi dell'oggetto, quindi ogni metodo imposta il valore iniziale di ogni campo.
  Questi funzionano come le operazioni intermedie quindi ci restituiranno un'istanza del builder.
- Alla fine avremo un metodo build che restituisce l'istanza di _Classe_
- La Classe Builder può anche avere un costruttore che ci obbliga a impostare dei valori iniziali dell'oggetto.

## Singleton

Rende una classe istanziabile una sola volta

- Privatizzare tutti i costruttori (anche il default)
- Dichiarare campo statico _istance_ del tipo della Classe (sarà l'unico oggetto di quella classe)
- Creiamo un metodo _getIstance_ che restituisce l'unica istanza, se _istance_ è vuoto creiamo un nuovo oggetto e lo restituiamo altrimenti restituiamo _istance_.

## Decorator Pattern

Aggiungiamo delle funzionalità ad un oggetto durante la fase di runtime, senza che questo "se ne accorga".

![[Pasted image 20240527124530.png|500]]

In questo esempio possiamo aggiungere la rappresentazione grafica delle auto a runtime.

- Decorator estende la classe astratta dell'oggetto (Automobile)
- Si costruisce con *un'istanza concreta della classe astratta* dell'oggetto, quindi una sottoclasse
- Inoltra le richiesti di tutti i comportamenti dell'oggetto
- Effettua azioni aggiuntive (rappresentazione grafica in questo caso)

![[Pasted image 20240527124846.png]]

Componente è la classe Astratta.
Quindi creo un oggetto concreto e lo passo come parametro per creare un oggetto concreto di decorator che eseguirà operazioni aggiuntive senza che l'oggetto originale lo sappia.

## Command / Callback pattern

È necessario fare richieste ad oggetti senza sapere nulla sull'operazione, questa potrà essere eseguita in futuro quando necessario.
Dobbiamo rendere l'operazione modulare in modo che possa essere associata ad un oggetto, potranno essere eseguite anche diverse associazioni in seguito.

- Creiamo un'interfaccia funzionale che espone il metodo generale, questo metodo chiama la funzionalità da associare.


## Template Method