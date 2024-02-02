#base2
Per rappresentare le informazioni abbiamo bisogno di un alfabeto di supporto e di una [[Funzioni Matematiche|funzione]] di codifica, ovvero una funzione che associa l'informazione *"I"* a parole nell'insieme *"C"* detto **codice** $f:I\rightarrow C$
Indichiamo con $N_I$ la cardinalità di I e con $N_C$ la [[Cardinalità ed Enumerabilità degli Insiemi|cardinalità]] di C, possono verificarsi 3 casi:
- $N_I < N_C$ - **Codifica ridondante**, abbiamo più modi per codificare un'informazione
- $N_I>N_C$ - **Codifica ambigua**
- $N_I=N_C$ - Codifica ideale, per ogni informazione esiste una sola codifica, se ci troviamo in questa situazione abbiamo anche una [[Funzioni Matematiche#^bdc88c|funzione di decodifica]] $g:C\rightarrow I$ 

## Requisiti di una buona Rappresentazione
1) Economicità: Usare il minor numero possibile di caratteri per la codifica
2) Semplicità di codifica e decodifica
3) Semplicità di elaborazione

## Come rappresentare l'informazione
Prendiamo come esempio un'informazione numerica, i [[Insiemi Numerici#Numeri Naturali|Numeri Naturali]]. Se ci troviamo in base 10 avremo che ogni cifra è associata alla relativa potenza di 10
$$2348=2*10^3+3*10^2+4*10^1+8*10^0$$
Avendo a disposizione 10 simboli diversi e 4 cifre posso rappresentare in totale $10^4$ valori. Analogamente in base due posso rappresentare $2^n$ valori.
Nel mondo dell'informatica le basi più utilizzate sono 2, 8, 16. Per capire di quanti bit avrò bisogno per rappresentare un numero in una base si utilizza il logaritmo con parte intera maggiore:
$$N\rightarrow\lceil log_2 N\rceil$$

## Conversione da base 10 a base b
Dato N in base 10, per convertirlo in una qualsiasi altra base b, ci basta dividere N per b e segnare i resti in ordine opposto, quindi:

| 62  | 0   |
| --- | --- |
| 31  | 1   |
| 15  | 1   |
| 7   | 1   |
| 3   | 1   |
| 1   | 1   |
| 0    |     |
Quindi leggendo i resti nel senso opposto a come li abbiamo ottenuti $62_{10} = 111110_2$
