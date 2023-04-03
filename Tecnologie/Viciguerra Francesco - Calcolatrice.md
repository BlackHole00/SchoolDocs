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

# Struttura logica
L'applicazione è divisa in due parti fondamentali indipendenti le une dalle altre: un _frontend_ ed un _backend_.
## Frontend
Questa parte è dedicata all'interfaccia grafica e codice strettamente correlato con Android.

In Android ogni "schermata" con il quale l'utente può interagire viene detta _Activity_. Ogni activity può utilizzare un _intent_ per richiedere al sistema operativo di mostrare un nuova attività, la quale verrà logicamente piazzata "al di supra" di quella corrente, in una modalità simile ad uno stack.
La terminazione dell'attività chiamata dall'intent (attraverso l'utilizzo del pulsante _indietro_ o attraverso il metodo `finish`) porterà alla riapparizione della precedente activity (quindi avviene effettivamente un "pop" dello stack delle activity).

### MainActivity
Questa activity è la principale e permette di inserire l'espressione utilizzando i pulsanti, che verranno disabilitati a seconda dello stato dell'espressione attuale, per evitare che l'utente possa fare molti errori.
Come è possibile notare non sono presenti le parentesi graffe e quadre. Questo perché la parentesi nell'espressione sono automaticamente convertite nel corretto formato a seconda del numero di parentesi utilizzate dall'utente.
![[MainActivity.png]]
### GraphViewActivity
Questa activity mostra lo studio della funzione mostrando il grafico di quest'ultima. Viene chiamata  dalla MainActivity a seguito della pressione del pulsante _uguale_ nel caso nell'espressione sia presente il simbolo _x_. 
L'utente può ulteriormente specificare l'intervallo di suo interesse ed il grafico verrà automaticamente aggiornato.
![[GraphViewActivity.png]]

## Backend
Il backend è la parte di software strettamente dedicata alla logica interna dell'applicazione. 
Fornisce quindi classi per la conversione di un'eventuale espressione nella corrispondente notazione polacca e per il calcolo di quest'ultima, supportando anche la sostituzione dell'incognita.
Inoltre il backend fornisce varie classi ed estensioni di supporto che vengono utilizzate anche nel frontend.
Il backend fornisce le varie classi e tipi presentati in seguito.

### ExpressionToken
Questa classe, seconda la stretta definizione teorica, è un cosiddetto [_Tipo di dato algebrico (algebraic data type)_](https://en.wikipedia.org/wiki/Algebraic_data_type). Un dato algebrico è una tipo composto che è formato dalla combinazione di più tipi diversi.
Logicamente, comparandolo con il linguaggio C, è possibile considerarlo come una variante di un enumerato che, oltre al valore dell'enum contiene anche ulteriori dati, a modo simile di un union. Si nota tuttavia che il linguaggio C (e CPP) non supporta direttamente questi tipi di dato. 
Per avere un semplice esempio è possibile vedere il linguaggio di programmazione rust, che implementa questi tipi [direttamente nei suoi enum](https://doc.rust-lang.org/book/ch06-01-defining-an-enum.html).

Segue l'esempio di un tipo di dato algebrico. Ogni variabile di tipo `IpAddr` potrà essere di tipo `V4` (e contenere 4 valori unsigned ad 8 bit), di tipo `V6` (contenendo una stringa) oppure di tipo `None` (non contenendo nulla).
```rust
enum IpAddr {
	None,
    V4(u8, u8, u8, u8),
    V6(String),
}
```

Kotlin di per se'non supporta direttamente i tipi di dati algebrici, ma è possibile, ed è anche l'alternativa consigliata, utilizzando una combinazione di `sealed class` e di `data class`, in modo da creare un 

### ExpressionTokenizer
```kotlin
class ExpressionTokenizer(private val expression: String) {  
    fun tokenize(): ArrayList<ExpressionToken> { ... }
}
```

# Algoritmi e Logica di Implementazione