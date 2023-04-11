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
- *proprietari*: non pubblici, relativi ad una singola organizzazione. Sono quindi i piu'difficili da accettare. Un esempio e'il metodo di *Putnam e *SLIM*
- *non proprietari*: pubblica, spesso definita da uno standard ed utilizzabile da chiunque

I metodi basati sui modelli specifici si dividono invece a loro volta in:
- *data driven*: a seconda del tipo si basano su piu'dati e modelli matematici, che vengono analizzati attraverso una formula fissa (nel caso di quelli *parametrici*) o su di una non precisa (nel caso dei *non parametrici*). Utilizzano un valore di produttivita'detto *KDSI (Kilo Delivered Source Instruction)*, che conteggia le linee di codice consegnate effettivamente al cliente, quindi escludendo test e commenti.
- *composti*: realizzati attraverso l'utilizzo di tecniche data driven combinate con l'opinione di esperti.

#### Metodo SLIM
Inventato da Putnam. Viene applicato a progetti superiori a 70000 righe.
Utilizza due equazioni che descrivono la relazione tra lo sforzo di sviluppo e la pianificazione sotto forma di mano d'opera.

#### Metodo di Putnam
Il metodo sul quale si basa il metodo SLIM. Utilizza una curva (*curva di Raleigh-Norden*) per descrivere l'andamento dello sforzo necessario nel corso del progetto. La curva viene ottenuta utilizzando lo sforzo totale e il mese attuale.

#### Metodo COCOMO
Il metodo cocomo e'un modello proprietario sviluppato da *Barry Boehm*. Viene utilizzato nei progetti con le seguenti caratteristiche:
- La progettazione deve essere a cascata seguendo le fasi di pianificazioni, progettazione, sviluppo e di testing.
- I requisiti devono essere stabilito
- Il mese di lavoro e'composto da 19 giorni, ovvero la totalita'delle ore di lavoro al mese di ogni singolo individuo.

Questo metodo, basandosi su LOC e FP, permette di creare una stima tenendo conto di molti fattori, anche esterni al progetto, e permette di effettuare una stima del preventivo.

Secondo questo modello, a seconda della scala del progetto, bisogna effettuare diversi calcoli. I progetti possono essere:
- Semplici, utilizzando il modello base
- Intermedio, utilizzando il modello intermedio
- Complesso, utilizzando il modello avanzato

Il metodo COCOMO quindi si divide in:
- *base*: utilizza solo le LOC per ottenere lo sforzo in mesi-persona
- *intermedio*: utilizza le stesse tecniche del modello base, ma implementa 15 fattori correttivi per le categorie di attributi del prodotto, del calcolatore, del personale, del progetto
- *avanzato*: simile al modello intermedio, anche se i miglioramenti di stima sono molto inferiori rispetto a quelli tra il metodo base e quello intermedio. Rispetto al livello intermedio, in quello avanzato, vengono analizzati altri fattori di correzione dipendenti dalla fase del progetto.

#### Metodo COCOMO II
Il metodo COCOMO II e'un'evoluzione del metodo COCOMO ed e'la versione attualmente utilizzata.

Rispetto a COCOMO I, i progetti sono divisi per tipologia. Ogni tipologia, come anche nella prima versione, definisce un nuovo metodo di calcolo.
- *End-User Programming*, che utilizza il modello *Application Composition Model*
- *Application Composition*, che utilizza il modello *Early Design*
- *Application Generators & Composition Aids*, che utilizza il modello *Post-Architecture*

L'idea generale, per tutte le sottocategorie, e'l'utilizzo di una nuova modalita'di calcolo che considera l'impegno complessivo per il progetto non in modalita'proporzionale al lavoro necessario per sviluppare il software.

Il modello quindi terra'conto dei seguenti parametri:
- *PREC (Precedentedness)*: se il progetto ha precedenti di difficolta'nota
- *FLEX (Development FLEXibility)*: indica la flessibilita'delle specifiche del progetto (es. standard di sviluppo)
- *REAL (Architecture/Risck RESolution)*: relativo ai rischi trattati ed affrontati
- *TEAM (TEAM Cohesion)*
- *PMAT (Process MATurity)*

Come anche il COCOMO I, COCOMO II utilizza i fattori di aggiustamento, sotto il nome di *moltiplicatori di sforzo (EM)*, che vengono utilizzati per aggiustare la stima dei mesi/persona e sono divisi in 4 categorie:
- *prodotto*
- *piattaforma*
- *personale*
- *progetto*

#### Modelli di Doty, Walston-Felix e Bailey-Basili
Modelli basati sul data driven. Utilizzano formule fisse.

#### Modello COBRA
Il modello COBRA *(COst Estimation Benchmarking and Rick Assessment)* e'un metodo composto che fornisce una stima per analogia attraverso due componenti:
- un modello matematico che fornisce la stima dei costi utilizzando un insieme di fattori acquisito mediante gli esperti.
- l'utilizzo dei dati dei progetti passati con richieste simili.

COBRA fornisce molteplici vantaggi:
- puo'essere applicato a piu'ambienti, anche con poci dati
- vengono riutilizzate le conoscenze passate
- viene accettato facilmente
Ma fornisce anche alcuni svantaggi:
- bisogna avere dispobibilita'di esperti e dati passati

#### Metodo Delphi Standard
Questo metodo non e'basato su un modello. La stima viene offerta attraverso la consultazione di piu'esperti, sotto la supervisione di un supervisore. Si nota che gli esperti consultati non saranno in collegamento tra di loro, per ottenere una stima eterogenea, che poi verra'"normalizzata" e rifatta analizzare dagli esperti.

#### Metodo Delphi Wideband
Questo metodo non e'basato su un modello. E'simile al modello delphi standard.

#### Metodo della Stima alla Parkinson
Questo metodo non e'basato su un modello. Si basa sull'idea che il progetto consumera'tutto il budget. Quindi generera'sovrastime e portera'all'aggiunta di funzionalita'aggiuntive e di consumo ad esaurimento delle risorse. 

#### Metodo dell Stima Price-to-win
Questo metodo non e'basato su un modello. Viene utilizzato per aggiudicarsi una gara o un contratto. Porta quindi a molti problemi di processo ed ad una qualita'inferiore del prodotto.

### Dimensioni del software
Ci sono due dimensioni del software che vengono considerate:
- *dimensione interna*: misurata in LOC, viene anche detta *strutturale*. Vengono utilizzate perche'sono facilmente definibili, misurabili ed intepretabili, ma hanno lo svantaggio di non avere una definizione standard, in quanto il conteggio non tiene conto del linguaggio utilizzato, dallo stile di programmazione e delle funzionalita'delle linee di codice.
- *dimensione esterna*: misurata in FP, viene detta anche *funzionale*. I suoi vantaggi sono gli svantaggi dei quella interna e viceversa. Oltre a questi ultimi, l'utilizzo degli FP porta ad ulteriori svantaggi, ovvero la difficile definizione delle funzionalita'del progetto, in quanto la determinazione dei FP e dello schema dei pesi utilizzato e'soggettivo

# Qualita'
Per qualita'si intende l'insieme degli attributi che definiscono la "bonta'"di un prodotto. Ovviamente l'obiettivo del produttore e'quello di ottenere un prodotto con buona qualita'che rispetti le specifiche definite dal cliente.

Si nota che gli *utilizzatori* si aspettano qualita'correlata ad *efficienza, usabilita' ed affidabilita'*. Gli sviluppatori invece si aspettano *riusabilita', comprensibilita', testabilita' e mantenibilita'*.

Per standardizzare la qualita'vengono utilizzati modelli. In genere questi ultimi funzionano a livelli e definiscono la qualita'da diversi punti di vista. Ogni livello analizza in modo qualitativo piu'attributi utilizzando una scala di riferimento.

### Modello McCall-Boehm
Il uno dei primi modelli per la standardizzazione della qualita'e'stato il *modello McCall-Boehm*.
La qualita'del software viene definita da questo modello come l'insieme delle caratteristiche che incidono sulla capacita'di soddisfare requisiti impliciti od espliciti.

Il modello McCall-Bohem utilizza un'architettura a tre livelli:
- *fattori*: descrivono il software dal punto di vista esterno, dell'utente. Ne prevede 11
- *criteri*: descrivono il software dal punto di vista degli sviluppatori. Ne prevede 23
- *metriche*: controlla che il software sviluppato corrisponda alle richieste dell'utente

Il modello utilizza quindi una visione gerarchica ed un approccio top-down.  

I requisiti dell'utente (fattori) sono i seguenti:
- *servizio*:
	- *correttezza*: il software deve essere tracciabile, coerente e completo
	- *affidabilita'*: il sfotware deve tollerare l'errore, essere coerente, essere accurato ed  essere semplice
	- *efficienza*: sia in esecuzione che in memorizzazione
	- *integrita'*: provvede controllo e revisione degli accessi
	- *usabilita'*: il software deve essere operabile, attraverso un addestramento conoscendo il volume e la velocita'dell'I/O
- *manutenzione*
	- *mantenibilita'*: il software deve essere coerente, semplice, coinciso, modulare e con documentazione automatica
	- *flessibilita'*: il software deve essere generale ed espandibile
	- *testabilita'*
- *migrazione a nuovi sistemi*:
	- *portabilita'*: il software deve essere modulare, auto documentante, indipendente dalla macchina e dal software
	- *riusabilita'*, legata alla portabilita'e flessibilita'
	- *interoperabilita'*: il software deve essere modulare ed utilizzare standard di comunicazione e di dati.
Si nota che alcuni fattori hanno sinergia tra di loro, mentre altri sono in conflitto.

### Modello ISO/IEC 9126
Conosciuto anche come *Software engineering - Product quality*, e'un altro modello per definire la qualita'del software. Si basa sul definire caratteristiche e sottocaratteristiche, per le quali sono indicati vari descrittori. Questo modello viene utilizzato in piu'fasi di vita del progetto ed e'destinato sia al team di sviluppo, che agli utenti che ai gestori del sistema (a tutte le persone a contatto col progetto).

Per definire la qualita', a seconda della categoria, vengono utilizzati diversi metodi, cambiando le caratteristiche, le sottocaratteristiche ed i descrittori.

Le categorie sono:
- *qualita'interna*: misurata direttamente dal codice sorgente, tiene in considerazione i requisiti dell'utente e le specifiche tecniche.
- *qualita'esterna*: misurata attraverso le prestazioni del prodotto dal punto di vista delle sue funzionalita'.
- *qualita'in uso*: misurata attraverso la percezione dell'utilizzatore del prodotto.

La qualita'interna ed esterna vengono definite dai seguenti attributi:
- *functionalita'*
- *affidabilita'*
- *usabilita'*
- *efficienza*
- *mantenibilita'*
- *portabilita'*

La qualita'd'uso viene definita dalle caratteristiche:
- *efficacia*
- *produttivita'*
- *sicurezza*
- *soddisfazione*

Dal punto di vista effettivo, la qualita'del codice viene raggruppata in tre categorie:
- *errori*
- *difetti*
- *malfunzionamenti*

Tuttosommato, per migliorare la qualita'e'necessario migliorare:
- la competenza delle persone
- i processi maturi
- metriche, metodi, tecniche e strumenti

### ISO/IEC 15504
E'un modello utilizzato per i processi software, fornendo un approccio strutturato. E'anche conosciuto come *SPICE (Software Process Improvement and Capacity Determination)*. E' una sottosezione dell'ISO 9126.