Con la parola chiave _super_ possiamo richiamare il costruttore della superclasse, ogni sottoclasse deve esplicitamente definire un costruttore se la superclasse non definisce un costruttore senza argomenti.

**Quindi se la superclasse non ha un costruttore senza argomenti allora le sottoclassi devono avere obbligatoriamente un costruttore.**

![[Pasted image 20240321123346.png]]

Se non esplicitiamo un costruttore in una sottoclasse in automatico chiamiamo il supercostruttore di default della superclasse.

![[Pasted image 20240321123501.png]]

In questo caso non possiamo effettuare la chiamata di defualt perchè la classe X non ha un costruttore di defualt e necessita obbligatoriamente di un paramentro.

**Quindi se scrivo un costruttore nuovo, automaticamente elimino quello di default, e dovrò creare un secondo costruttore con meno argomenti se ne ho bisogno**.

# Overriding e Overloading

L'overriding consiste nel ridefinire un metodo con la stessa intestazione che è presente in una superclasse.
Nell'overriding devo mantenere gli stessi argomenti e anche tipi di ritorno compatibili, non posso ridurre la visibilità (_private, public, ec..._).
Se ridefinisco i tipi di ritorno per essere compatili il nuovo tipo di ritorno deve essere un **sottotipo** del tipo di ritorno del metodo nella classe super.

L'overloading consiste nel creare un metodo con lo stesso nome ma intestazione diversa come ad esempio numero e/o tipo di parametri differente.
Nell'overloading posso avere tipi di ritorno diversi e posso anche variare la visibilità del metodo.

# Visibilità

![[Pasted image 20240321131116.png]]

Se non scrivo il tipo di visibilità di base avrò **Default**.

# Rappresentazioni UML

- **Is-a**: Rappresenta l'ereditarietà, un oggetto di una sottoclasse è infatti un oggetto della superclasse
- **Has-a**: Rappresenta la composizione, un oggetto contiene come membri riferimenti ad altri oggetti.

![[Pasted image 20240321132326.png]]
![[Pasted image 20240321132519.png]]


