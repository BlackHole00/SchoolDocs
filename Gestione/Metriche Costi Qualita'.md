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

### Classificazione dei metodi di stima

### Modello COCOMO II

### Modello COBRA