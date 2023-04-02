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
		- `(2 + 3)(3 + 2)
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
Kotlin è un linguaggio nuovo che sta prendendo piede negli ultimi anni. E'retrocompatibile con codice Java precedentemente scritto, in quanto non è in grado di interfacciarsi con esso, ma 