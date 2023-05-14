Progetto e progettazione sono due elementi fondamentali di un'impresa.
Le attivita'eseguite da un'azienda sono divise nelle seguenti categorie:
- **attivita'ordinarie**: operazioni svolte periodicamente con obiettivi impliciti e definiti, utilizzando costi e risorse standard
- **progetto**: e'un operazione univoca, con obiettivi espliciti e originali, con durata pianificabile e temporanea
- **programma**: un gruppo di progetti collegati tra di loro con un obiettivo comune.

Tutte le attivita'hanno a che fare con **tempi**, **costi** e **risorse**, elementi collegati tra di loro che vanno studiati e bilanciati.

# Il progetto
Il progetto viene definito come *uno sforzo temporaneo per creare un prodotto, un servizio o un risultato con caratteristiche di univocita'*.
Nel particolare un progetto ha le seguenti caratteristiche:
- ha uno scopo ben definito
- ha un inizio ed una fine
- ha dei vincoli da rispettare e dei rischi da valutare
- termina quando lo scopo e'raggiunto

Spesso per supportare un progetto viene ricercato uno **sponsor**. 

# WBS
Per pianificare un progetto viene utilizzata una **Work Breakdown Structure**. Con questo termine si intende una rappresentazione in forma **grafica** che enfatizza **la gerarchia** delle attivita'del progetto. 

Spesso la WBS e'composta in un modello ad albero, dove la **radice** indica l'interita'del progetto e dove le **foglie** indicano il **Work Package**, ovvero un' **attivita'minima** con un responsabile ed una durata.

Per creare il WBS vengono utilizzate piu'regole, una delle quali e'la regola del **100%**, la quale indica che il WBS deve contenere **tutto il lavoro** necessario al completamento del progetto.
E'anche buona norma creare un WBS in modo **strutturato**, creando una gerarchia accurata.

Dal WBS e'possibile ottenere la lista ordinata dei Work Packages, detta **Activity list**. Grazie a quest'ultima si riorganizza il progetto utilizzando una nuova struttura: l'**OBS (Organization Breakdown Structure)**, una simile rappresentazione gerarchia ad albero che definisce la gerarchia dei lavoratori (ovvero quindi chi comanda chi) ed il ruolo nel progetto.

Utilizzando l'OBS e'allora possibile creare la matrice di responsabilita'del progetto (**tabella RACI**).

Nel dettaglio il work package riporta: _(copiati dal libro)_
- un titolo dell'attivita ed un'eventuale descrizione
- date di inizio e dine del lavoro
- la responsabilita'
- gli input necessari per effettuare il lavoro
- la descrizione dei risultati attesi
- le risorse necessarie
- il livello di qualita' e dettaglio delle prestazioni
- gli output del lavoro
- il budget assegnato

# Tempi
I **tempi** del progetto sono un importante parametro da tenere in considerazione durante la progettazione di un'attivita'.

Una volta completato il WBS e'possibile cominciare a **schedulare nel tempo** il progetto. 

Per far cio'e'necessario adottare un modello di schedulazione. Il piu'diffuso e'il **CPM (Critical Path Method)**, ovvero un modello reticolare che usa in grafo nel quale i **nodi** rappresentano le **attivita'** e gli **archi** descrivono le **relazioni** tra di loro (anche dette **AON**, ovvero **Activity On Node**). Questo grafo e'anche caratterizzato da avere un **nodo iniziale** ed un **nodo finale**.

Si nota che, ovviamente, il grafo deve contenere **tutte le attivita'** del progetto.

Ogni attivita'e'caratterizzata da una o piu' **dipendenze** dalle altre attivita'a lei collegate, che possono essere di diversi tipi:
- **FS (Finish to Start)**: l'attivita'puo'iniziare solo se la precedente e'stata terminata
- **SS (Start to Start)**: l'attivita'puo'iniziare solo se la precedente e'gia'iniziata
- **FF (Finish to Finish)**: l'attivita'puo'terminare solo se quella precedente e'gia'stata terminata
- **SF (Start to Finish)**: l'attivita'puo'terminare solo se quella precedente e'gia'stata iniziata

Utilizzando il grafo allo stato attuale e'possibile calcolare la durata totale del progetto. Cio'permettera'anche di determinare le attivita'da terminare **al piu'presto** ed **al piu'tardi**, insieme alle attivita'dette **critiche**, ovvero quelle operazioni il quale **ritardo** porta a quello dell'**intero progetto**.

Un altro strumento molto efficace per rappresentare l'evoluzione temporale del progetto e'il **diagramma di Gantt**, che e'un grafico strutturata in maniera simile ad un calendario utilizzando barre orizzontali, la cui lunghezza e'**proporzionale** alla durata della corrispondente attivita'nel tempo. Le barre possono essere "sovrapposte" nel tempo, cio'rappresenta piu'attivita'che vengono svolte nello stesso momento.

# Risorse
La **pianificazione delle risorse** e'un altro elemento importante da tener conto in fase di pianificazione, ma questa volta il processo generalmente adottato e'di difficile standardizzazione, in quanto va **reiterato piu'volte** durante la vita del progetto e si basa sull'analisi del progresso ed alla stima di esso.

In generale pero'la pianificazione delle risorse si occupa di definire il **tipo**, la **quantita'**, le **persone**, le **attrezzature** e le **forniture** necessarie per **ciascuna attivita'** del progetto.

Per definire questi parametri viene effettuata un'**analisi** sul WBS e sui singoli Work Package per ottenere il tempo richiesto in unita'**ore/uomo**, **ore/macchina** e **materiale** requisito. Questi dati vengono immessi in un documento detto **Requirement Breakdown Structure (RBS)**, che e'simile ad un WBS, ma riporta anche la stima delle risorse.

Le risorse vengono inoltre classificate nelle seguenti categorie:
- **lavoro**: diviso in **diretto** (utilizzato per la produzione) **indiretto** (a supporto della produzione) ed **amministrativo** (per la contabilita'e l'amministrazione, che sono comunque richieste al progetto).
- **materiali**: tutti gli elementi che fanno parte del prodotto finito
- **attrezzature**: tutti gli elementi che servono per il prodotto finito.
- **altro**: risorse in genere associabili ai costi fissi _(come l'energia elettrica)_

Per eseguire la **stima della risorsa** vengono utilizzate le seguenti tecniche:
- **per analogia**: il calcolo si basa su risorse simili gia'utilizzate in progetti precedenti
- **parametrica**: il calcolo si basa su informazioni oggettive ricavate generalmente dal mercato ed adattare alle condizioni del progetto
- **a tre punti**: utilizzo di un calcolo probabilistico basato sul costo **minimo**, **massimo** e **probabile**

# Costi
L'**analisi dei costi** e'l'ultimo elemento che bisogna tenere in considerazione durante la progettazione. Quest'ultima e'altamente **correlata** all'analisi dei tempi e delle risorse ed e'la fase piu'critica della pianificazione.

L'intera analisi e'basata in relazione al **budget di progetto**, ovvero la previsione di spesa dell'intero progetto, come l'analisi delle risorse anche l'analisi dei costi va **reiterata** piu'volte durante la realizzazione del progetto, spesso a seguito di predeterminate **scadenze temporali** dette **timenow**.

La previsione dei costi avviene **riutilizzando le stime** dell'analisi delle risorse, ottenendo i costi delle singole operazioni ed ottenendo quindi i costi delle fasi di livello superiore. Questo tipo di stima viene detto **Bottom-Up**.

Un altro tipo meno utilizzato viene detto **Top-Bottom**, nella quale si predispone un budget per ogni livello superiore che viene diviso tra le singole operazioni attraverso molteplici stime.

Queste stime, sia nel modello bottom-up che top-bottom sono divise in categoria a seconda del livello di approssimazione:
- **Ballpack**: si hanno poche certezze e la stima va approfondita. Accuratezza tra il -25% ed il +75%  del valore reale
- **Budget**: accuratezza tra il -10% ed il +25%
- **Definitivo**: precisa, ottenuta alla fine del progetto

Utilizzando tutte le stime infine e'possibile determinare per ogni risorsa iesima la **stima delle quantita'** ($q_i$) ed il **prezzo unitario** ($pu_i$). Da qui sara'possibile ottenere il **costo unitario** ($c_i$).
Quindi: $c_i=q_i*pu_i$

La somma di tutti i **costi unitari** di ogni risorsa $c_i$ dara'il **costo totale** dell'attivita'.

# Earned Value
I tempi ed i costi durante la realizzazione di un progetto si discostano spesso da quelli previsti durante la fase di progettazione. Per controllare lo **stato** di un progetto in **esecuzione** viene quindi utilizzato un modello denominato **Earned Value Method**.

Quest'ultimo opera sul tre valori visti come costo relativo ad una data prefissata:
- **PV - Planned Value**: valore pianificato, la somma di tutti i costi stimati fino al tempo corrente. Anche detto _BCWS_
- **AC - Actual Cost**: la somma di tutti i costi effettivamente sostenuti fino al tempo corrente. Anche detto _ACWP_
- **EV - Earned Value**: il valore guadagnato riferito all rapporto tra l'AC ed il completamento del progetto in percentuale. Anche detto _BCWP_

Una volta ottenuti questi valori e'possibile determinare se il progetto sta rientrando sul budget e se il progetto sta rispettando i tempi. E'anche possibile stimare il costo e la durata totale del progetto.

Per rendere questa operazione piu'semplice vengono utilizzati diversi indici:
- **CPI - Cost Performance Index**: Ottenuto da **EV/AC**. Un valore minore all'1 indica che il progetto sta uscendo da buget, mentre un valore superiore all'1 indica per quest'ultimo ne rientra.
- **SPI - Schedule Performance Index**: Ottenuto da **EV/PV**. UN valore minore all'1 indica che il progetto e'in ritardo, mentre uno maggiore dell'1 indica che quest'ultimo e'in anticipo
- **EAC - Estimated Cost At Completion**: Ottenuto da **AC + (BT-EV)/CPI)** Anche detto _BT - Budget totale_
- **SAC - Schedule At Completion**: Indica il tempo necessario per il completamento del progetto. Ottenuto da **Durata pianificata / SPI**

# Sigle e nomi notevoli
- WBS
- Work Package
- Activity List
- OBS
- Tabella RACI
- CPM
- AOM
- SF
- FF
- SS
- FS
- Diagramma di Gantt
- RBS
- Bellpack
- Budget
- Definitivo
- Earned Value Method
- PV
- AC
- EV
- CPI
- SPI
- EAC
- SAC