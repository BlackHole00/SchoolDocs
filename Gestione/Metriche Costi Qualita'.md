# Metriche
Le **metriche del software** sono strumento che forniscono misure quantitative del prodotto e delle sue componenti. Esse sono importante sia dal **punto di vista del produttore** che da quello **dell'utilizzatore finale**.

Le metriche vengono utilizzate per qualificare e quantificare:
- **i prodotti dell'ingegneria del software**: progetti, sorgenti e casi di test
- **i processi dell'ingegneria del software**: attivita'di analisi, progettazione e codifica
- **gli "attori" del software**: efficienza collaudatori e progettisti.

Le metriche vengono divise in piu'tipi:
- **metrica primitiva**: anche detta diretta,
- **metrica calcolata**: anche detta indiretta,

Oltre alla tipologia, le metriche vengono anche divise in piu'gruppi:
- **metriche del prodotto**
- **metriche di processo**
- **metriche di qualita'**

### Mole di software
La **Mole di software** e' quantita'di software da produrre. Viene spesso Misurata in *tempo/persona* (quindi *giorni/uomo*). Utilizzato per stimare la quantita'di lavoro.

Le **linee di codice (LOC)** sono *primo* metodo di misura per la valutazione della quantita' del software. Piu'semplice. Comprende il alternativa:
	- *Non Comment LOC (NLOC),*
	- *Non Comment Non Blanck (NCNB)*
	- *Solo Commenti (CLOC)*
	- *Solo Codice Eseguibile (EXEC)*

### Function Points FP
I **Funtion Points (FP)** sono un metodo alternativo per la valutazione della quantita'di lavoro. Da questi ultimi e'possibile ottenere le *linee di codice (LOC)*. Introdotto da *Allan Albrecht* nel 1979, per rendere piu'adeguate le stime create utilizzando solo le LOC. Tiene conto di nuovi linguaggi e tecniche di programmazione (assembly comincia ad non essere l'unico linguaggio). 
Si basa sull'analisi del software dal punto di vista della richiesta dell'utente, analizzando le *features* che un programma deve fornire, senza analizzare il late tecnico.
I functions points quindi forniscono una misura oggettiva che pero'non tiene conto della difficolta'reale dell'algoritmo.
Dagli FP e'possibile ottenere le LOC utilizzando un'apposita tabella, che contiene, dato il linguaggio scelto, le linee di codice per function point. Per far cio'si utilizza la tecnica di *backfiring*.
Il conteggio dei function points avviene in piu'situazioni durante il ciclo di vita di ogni diverso progetto:
- **progetto di sviluppo**: fornito prima della realizzazione del progetto e durante il suo sviluppo.
- **progetto di manutenzione**: fornito al momento della richiesta di aggiornamento, di aggiunta o di rimozione di features.
Gli FP ha anche l'ulteriore vantaggio di poter essere calcolato in fase preventiva.

#### Calcolo degli FP
Il calcolo degli FP avviene attraverso il *metodo standard IFPUG*. Avviene attraverso 7 fasi:
- **Pianificazione del conteggio ed identificazione del tipo**
- **Racconta della documentazione**
- **Inventario delle funzioni e calcolo FP non pesati**
- **Classificazione dei componenti**
- **Esaminazione delle 14 caratteristiche generali del sistema (GSC) e determinazione del fattore di aggiustamento (VAF)**
- **Tabulazione dei risultati**
- **Convalida dei risultati**

#### Tecnica di backfiring
La tecnica di backfiring permette di ottenere le LOC conoscendo gli FP. Questo avviene utilizzando una tabella, che, data la complessita'del progetto ed il linguaggio utilizzato, permette di ottenere il valore di conversione LOC/FP.
Per calcolare la complessita'del progetto viene utilizzato un coefficiente *Ct*, che tiene conto delle complessita'del *problema*, dei *dati* e del *codice*. Il *Ct* per essere utilizzato viene trasformato di *BAF* attraverso una formula di conversione. Dal *BAF* e'possibile ottenere il *coefficiente dell'applicazione* utilizzando la tabella e, solo da quest'ultimo, e'possibile ottenere la dimensione dell'applicazione sotto forma di *LOC*.

# Costi
### Concetto di stima dei costi
La stima del costo di un progetto si basa su tre aspetti fondamentali:
- **tempo di sviluppo**
- **quantita'di lavoro richiesta in ore-uomo**
- **quantita'di persone**

Si nota che la progettazione del software richiede una progettazione particolare, in quanto e'molto diversa dai progetti normali, in quanto in questi ultimi il costo e'facilmente prevedibile e subisce piccole variazioni. Il costo del software invece e'caratterizzato da un *alto costo sottoforma di sforzo iniziale*, che e'in genere maggiore a quello relativo alla fine del progetto.
E'anche necessario considerare che il costo di *manutenzione* e'*sempre piu'alto* di quello di sviluppo.

La stima dei costi e'richiesta per la quasi totalita'di progetti software, grazie ai seguenti benefici:
- possibilita'di stipulare contratti sensati dal punto di vista del costruttore e dell'acquirente
- previsione dei tempi di sviluppo
- corretto dimensionamento del team di sviluppo

Come menzionato in precedenza in genere il costo di un'applicazione dipende dallo *sforzo* imposto su quest'ultima. Lo sforzo viene definito dai seguenti fattori:
- *dimensione del software*
- *fattori umani*: la specializzazione ed esperienza richiesta
- *complessita'dell'applicazione*
- *stabilita'dei requisiti*
- *vincoli extra richiesti dall'applicazione*, che richiedono l'utilizzo di piu'risorse
- *ambiente di sviluppo*: l'organizzazione interna all'azienda

### Classificazione dei metodi di stima
Secondo la classificazione definita da *Barry Boehm*, i metodi di stima sono divisi in:
- *basati su modelli generici*
- *basati su modelli specifici*
- *non basati su modelli*: si basano sull'esprienza di un tecnico che offre una stima. Richiede ovviamente piu'opinioni e confronti.

I metodi basati sui modelli generici si dividono a loro volta in:
- *proprietari*: non pubblici, relativi ad una singola organizzazione
- *non proprietari*: pubblica, spesso definita da uno standard ed utilizzabile da chiunque

I metodi basati sui modelli specifici si dividono invece a loro volta in:
- *data driven*: a seconda del tipo si basano su piu'dati, che vengono analizzati attraverso una formula fissa (nel caso di quelli *parametrici*) o su di una non precisa (nel caso dei *non parametrici*)
- *composti*: realizzati attraverso l'utilizzo di tecniche data driven combinate con l'opinione di esperti.

### Dimensioni del software
Ci sono due dimensioni del software che vengono considerate:
- *dimensione interna*: misurata in LOC, viene anche detta *strutturale*. Vengono utilizzate perche'sono facilmente definibili, misurabili ed intepretabili, ma hanno lo svantaggio di non avere una definizione standard, in quanto il conteggio non tiene conto del linguaggio utilizzato, dallo stile di programmazione e delle funzionalita'delle linee di codice.
- *dimensione esterna*: misurata in FP, viene detta anche *funzionale*. I suoi vantaggi sono gli svantaggi dei quella interna e viceversa. Oltre a questi ultimi, l'utilizzo degli FP porta ad ulteriori svantaggi, ovvero la difficile definizione 

### Modello COCOMO II

### Modello COBRA