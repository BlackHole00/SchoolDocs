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

Le risorse vengono intoltre classificate nelle segenti categorie:
- **lavoro**: diviso in **diretto** (utilizzato per la produzione) **indiretto** (a supporto della produzione) ed **amministrativo** (per la contabilita'e l'amministrazione, che sono comunque richieste al progetto).
- **materiali**: tutti gli elementi che fanno parte del prodotto finito
- **attrezzature**: tutti gli elementi che servono per il prodotto finito.
- **altro**: risorse in genere associabili ai costi fissi _(come l'energia elettrica)_

Per eseguire la **stima della risorsa** vengono utilizzate le seguenti tecniche:
- **per analogia**: il calcolo si basa su risorse simili gia'utilizzate in progetti precedenti
- **parametrica**: il calcolo si basa su informazioni oggettive ricavate generalmente dal mercato ed adattare alle condizioni del progetto
- **a tre punti**: utilizzo di un calcolo probabilistico basato sul costo **minimo**, **massimo** e **probabile**

# Costi
L'**analisi dei costi** e'l'ultimo elemnto che bisogna tenere in considerazione durante la progettazione. Quest'ultima e'altamente **correlata** all'analisi dei tempi e delle risorse ed e'la fase piu'critica della pianificazione.

L'intera analisi e'basata in relazione al **budget di progetto**, ovvero la previsione di spesa dell'intero progetto.