I registri sono un insieme di Flip Flop e possono svolgere due operazioni:
- Memorizzazione dell'informazione
- Caricamento dell'informazione

Li rappresentiamo in questo modo:
![[Pasted image 20231204220514.png]]
Dove ogni quadratino rappresenta un Flip Flop
### Caricamento
Il caricamento di un'informazione può avvenire in due modi:
- *Parallelo:* Tutti gli FF ricevono il valore nello stesso momento
- *Seriale:* Ogni FF riceve il valore in momenti diversi

**Caricamento in parallelo con registro da 4 FF**
![[Pasted image 20231204220823.png]]

Nel caso in cui volessimo usare degli SR:
![[Pasted image 20231204221008.png]]

Possiamo effettuare il caricamento anche con una linea di controllo *load*, quando questa vale 1 effettuiamo il caricamento altrimenti no
![[Pasted image 20231204221307.png]]

La linea di load può essere anche collegata insieme al clock, vediamo due esempi sia con SR che con D FF
![[Pasted image 20231204221509.png]]

![[Pasted image 20231204221601.png]]

Un ultimo modo per effettuare il caricamento:
![[Pasted image 20231204221809.png]]

Ricapitolando abbiamo quindi:
- *Caricamento parallelo*
	- *Con FF D*
	- *Con FF SR*
- *Caricamento*
	- *Load sugli ingressi*
		- *FF D*
		- *FF SR*
	- *Load sul clock*
		- *FF D*
		- *FF SR*

### Caricamento Seriale
Per il caricamento seriale usiamo dei registri chiamati anche a scorrimento o *shif register*, infatti si riempiranno in questo modo:
![[Pasted image 20231204222307.png]]

Vediamo come realizzare il circuito:
![[Pasted image 20231204222416.png]]

Quando avrò finito di inserire i dati in input imposterò la linea di load a 0 bloccando così lo stato dei flip flop.
