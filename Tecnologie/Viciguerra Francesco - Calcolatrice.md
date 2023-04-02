# Consegna
Creare un'applicazione android che consenta di:
- Risolvere un'espressione matematica con operazioni elementari e parentesi.
- Mostrare lo studio di una funzione con l'incognita.
Ulteriori punti da considerare:
- Utilizzare il minimo ammontare di codice esterno e di librerie aggiuntive

# Ipotesi
Durante la creazione del progetto sono stati ipotizzatati i seguenti punti:
- l'espressione analizzata deve essere matematicamente valida. Le seguenti espressioni, che possono essere considerate casi limite. devono essere gestibili e calcolabili senza errori:
	- mancanza dell'operatore di moltiplicazione:
		- `8(3 + 2)`
		- `(2 + 3)(3 + 2)`
		- `8x`
		- `(3 + 2)x2`
	- casi particolari di precedenza:
		- `-3^2`, _risultato: -9_
		- `(-3)^2`, _risultato: 9_
		- `-x^2`, _valutato come: -(x^2)_
		- `(-x)^2`
- l'espressione analizzata è un'espressione matematica standard, quindi è fornita con al massimo tre livelli di parentesi, supportando i tipi _graffa_, _quadra_ e _tonda_. Vengono successivamente elencati alcuni esempi di espressione con le parentesi:
	- `{[12 + 2][3 + (2 * 4)]}`
	- `{[(3 * 4) ^ 2] - 2}`
- lo studio della funzione con l'incognita avviene attraverso la visualizzazione sul grafico della funzione che permette quindi di mostrare il dominio della funzione. L'utente ha il controllo anche sull'intervallo che vuole visualizzare.
- L'applicazione deve essere in grado di riconoscere divisioni per zero (quindi sia _impossibili_ che _indeterminate_) e fornire un adeguato messaggio d'errore.
- Per motivi legati alla logica computazionale dei computer alcune operazioni possono causare un overflow nella computazione (ovvero l'ottenimento di un numero double _infinity_). L'applicazione deve tenere conto di questo e fornire adeguati messaggi d'errore.

# Tecnologie utilizzate
## Android studio
Android studio è l'IDE utilizzato per l'applicazione, la quale è nativa Android. La tecnologia android si basa prevalentemente sull'utilizzo di:
- file di configurazione XML: per descrivere l'applicazione e crearne l'interfaccia in modo statico
- codice Java: per creare la logica e dare funzionalità all'applicativo.
La spiegazione nel preciso dell'intero funzionamento della programmazione Android è oltre lo scopo di questo documento. Verranno spiegate, qualora opportuno, specifici funzionamenti aggiuntivi.

## Kotlin
Kotlin è un linguaggio nuovo che sta prendendo piede negli ultimi anni. E'retrocompatibile con codice Java precedentemente scritto, in quanto non è in grado di interfacciarsi con esso, ma Kotlin può essere compilato direttamente in bytecode JVM.
Grazie a queste caratteristiche, il linguaggio sta quindi lentamente sostituendo Java ed è già il linguaggio ufficialmente raccomandato per la creazione di nuove applicazioni Android.

Dal punto di vista delle features Kotlin fornisce:
- una sintassi più moderna e flessibile
- i tipi primitivi sono classi 
- null-safety
- migliori strutture per l'astrazione come:
	- `sealed classes`: migliori classi astratte
	- `getters, setters e properties`
	- `data class`: equivalente al `record` di Java 14
	- `objects e companion objects`: equivalente a `static`
	- `extensions`: la possibilità di aggiungere metodi a tipi o classi già precedentemente definite

Il motivo della scelta dell'utilizzo di Kotlin è puramente didattico, in quanto è stato voluto imparare un nuovo linguaggio.

## GraphView
GraphView è una libreria Java per Android sviluppata da Jjoe64 ed è la più utilizzata per la creazione di schemi e grafici. 
Sebbene sia tecnicamente possibile implementare una propria versione utilizzando una view Android custom e sovrascrivendo il metodo virtuale `onDraw`, questo metodo non è stato utilizzato perché la libreria è adeguatamente flessibile per le esigenze del progetto e la parte di analisi della funzione è di importanza secondaria.
E'stato comunque necessario imparare ad utilizzare la libreria, utilizzando la [documentazione ufficiale](https://github.com/jjoe64/GraphView/wiki/Documentation).

# Tecniche utilizzate
## Reverse Polish Notation
La reverse polish notation (abbreviazione RPM), anche detta _notazione postfissa_, è un metodo di rappresentazione di una espressione matematica che permette le rimozione delle parentesi ed è facilmente calcolabile da un computer.
La notazione normalmente utilizzata in matematica viene detta invece _notazione infissa_.
Quando nella notazione infissa l'operatore (quindi _più, meno, per, diviso_...) viene posto tra i due operandi, in quella postfissa, l'operatore viene posto dopo gli operatori, facendo riferimento agli ultimi _n_.
> Per esempio _(infissa -> postfissa)_:
> - `3 + 2` -> `3 2 +`:
> 	Nella notazione postfissa, l'operatore _più_ fa riferimento agli ultimi due numeri, quindi 3 e 2
> - `3 + 2 * 4` -> `3 2 4 * +`:
> 	Nella notazione postfissa, l'operatore _per_ fa riferimento agli operatori 2 e 4, mentre l'operatore _più_, non potendo far più riferimento a 2 e 4, farà riferimento al risultato dell'operatore _per_ e a 3.

Come anche accennato in precedenza, la notazione postfissa rende possibile rimuovere le parentesi.
> Per esempio _(infissa -> postfissa)_:
> - `(3 + 2) * 4` -> `3 2 + 4 *`:
> 	Nella notazione postfissa, l'operatore _più_ fa riferimento a 3 e 2, mentre l'operatore _per_ fa riferimento al risultato dell'operazione _più_ e a 4.

La notazione polacca è facilmente calcolabile da un computer utilizzando una semplice struttura a stack, in quanto, diversamente dalla notazione infissa, le operazioni vengono eseguite a seconda del loro ordine nell'espressione, indipendentemente dalla normale priorità di questi ultimi.

L'applicazione quindi dovrà convertire l'espressione infissa in postfissa per calcolare il risultato in modo semplice. Entrambi gli algoritmi verranno successivamente spiegati ed analizzati.

Si nota che la notazione polacca viene anche utilizzata nello studio della funzione.