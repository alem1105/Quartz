Uno stream è un flusso di dati derivata da dispositivi di input o output sequenziale, ad esempio uno stream di input riceve uno stream di caratteri uno alla volta.
Uno stream di output invece produce uno stream di caratteri.
Gli stream non si utilizzano soltanto per leggere i file ma anche per gestire flussi di dati da internet, trasmissioni, input / output ecc...
Possiamo trattare un file come uno stram di input / output.

**Classi per leggere scrivere**
- Leggere caratteri  - 16 bit alla volta `java.io.Reader/Writer`
- Leggere scrivere byte  - 8 bit alla volta `java.io.InputStream/OutputStream`
- L'accesso ai file di testo è stato semplificato con  `java.util.Scanner` che è più lento ma più potente.

**BufferedReader** permette una lettura bufferizzata dei caratteri di **FileReader**

```java
BufferedReader br = null;
try
{
	br = new BufferedReader(new FileReader(filename));
	while(br.ready())
	{
		String line = br.readLine();
	}
	catch(IOException e)
	{
	}
	finally
	{
		if (br != null)
			try {br.close();} catch(IOException e) { }
	}
}
```

Controllo se il flusso è rimasto aperto e lo chiudo nel `finally`.

**Try with resources**
Possiamo specificare dopo un try un elenco di istruzioni che definiscono risorse da chiudere automaticamente, separate da ;

```java
try(BufferedReader br = new BufferedReader(new FileReader(fileName)); BufferedReader br2 = new BufferedReader(new FileReader(fileName2)))
{
	while(br.ready()){
		String line = br.readLine();
	}
}
catch(IOException e) {}
```

**Chiudere automaticamente uno stream**
Tutti gli oggetti di classi che implementano `java.lang.AutoCloseable` che è estesa da `java.io.Closeable`.

```java
public interface AutoCloseable
{
	void close() throws Exception;
}
```

**Leggere file di testo**

![[Pasted image 20240509132022.png]]

**Scrivere su un file di testo**

![[Pasted image 20240509132040.png]]

**Scrivere un file di testo formattato**

```java
public class FormattaFile
{
	private String nome;
	private int valore;
	public void scrivi(String filename) throws IOException
	{
		Formatter output = new Formatter(filename);
		output.format("%s\t%d", nome, valore);
		//Scrive nome \t valore
		output.close();
	}
}
```

**Leggere un file di testo formattato**

![[Pasted image 20240509132626.png]]

Non utilizziamo più _File_ ma la classe _Path_ che rappresenta un percorso gerarchico

Per ottenere un path utilizziamo il metodo `Paths.get`

```java
Path p = Paths.get("/tmp/foo");
```

È importante non specificare in modo esplicito i separatori _\, /_ ma passare in sequenza le cartelle `Paths.get(cartella1, cartella2, cartella3, ..., file)`

Oppure lo costruiamo tramite _File.separator_

`Paths.get(cartella1 + File.separator + cartella2 + File.separator + file)`

Il percorso non deve quindi **obbligatoriamente esistere** nel filesystem, ma abbiamo un oggetto di tipo **path** che possiamo utilizzare nel codice.
Possiamo accedere a esso se esiste o crearlo nel filesystem e utilizzarlo.

Utilizziamo quindi Path e Files al posto di File

![[Pasted image 20240509133814.png]]

# Serializzare un Oggetto
Supponiamo di avere un'informazione da comunicare ad un altro dispositivo, possiamo serializzare l'oggetto e trasmetterlo, questo può essere letto e utilizzato da altri compilatori.

![[Pasted image 20240509134654.png]]

Cosa succede se un campo dell'oggetto da serializzare è un altro oggetto?
Anche questo oggetto deve essere serializzabile altrimenti genereremo degli errori.

Le classi infatti devono implementare **l'interfaccia serializable** che non ha metodi ma viene utilizzata come **marcatore** per indicare una caratteristica comune.

Tutti gli oggetti contenuti nell'oggetto serializzato vengono serializzati.

**È possibile rendere un campo non serializzabile con la parola chiave `transient`**.
I campi statici sono _transient_ di default.

**Serial Version UID**

È buona norma specificare un campo _static, final, long_ chiamato `serialVersionUID`.
Questo viene usato in fase di _deserializzazione_ per verificare se la versione della classe in uso è la stessa usata per serializzare.

![[Pasted image 20240509135429.png]]

Ad esempio se dopo un aggiornamento del software aggiungo un campo e decido di cambiare la UID, le versioni vecchie del codice non funzioneranno e genereranno un errore dato che le vecchie serializzazioni non sono più compatibili con il nuovo software.

**Leggere un oggetto serializzato: Deserializzazione**

![[Pasted image 20240509135914.png]]

Devo quindi sapere in che ordine ho salvato i campi del file(?).

