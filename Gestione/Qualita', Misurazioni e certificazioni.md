# La qualita'del software
Per misurare la qualita'del software viene utilizzato il modello di riferimento **ISO/IEC 25000**, il quale definisce sia le **caratteristiche** della qualita', che le **tecniche** per valutazione.  
Il documento e'diviso in **4 parti** principali:
- **ISO/IEC 2501n**: system and software quality models
- **ISO/IEC 2502n**: quality measurement framework
- **ISO/IEC 2503n**: quality requirements framework
- **ISO/IEC 2504n**: evaluation process

La prima sottoparte e'quindi identificata dalla sigla **ISO/IEC 2501n** (ovvero *Il modello delle qualita'del software*) ed indica il modello di riferimento basato sulla considerazione delle seguenti qualita':
- **qualita'esterne**: l'insieme delle funzionalita'che **offre** e delle **prestazioni** in relazione con l'ambiente in cui opera
- **qualita'interne**: indica la qualita'intrinsica del codice, della struttura logica, della documentazione e del livello di comprensione e modificabilita'del codice
- **qualita'd'uso**: indica quanto si mostra utile al cliente, quindi quanto e'**sicuro**, **affidabile** e **soddisfacente**

Per ognuna di queste qualita'sono specificati metodi di misurazione sottoforma di **componenti**, a loro volti divisi in **caratteristiche** e **sottocaratteristiche**.  

Per le qualita'interne ed esterne vengono utilizzate le seguenti:
- **funzionalita'**: il software deve fornire le funzioni implicite ed esplicite per cui e'stato realizzato
- **affidabilita'**: capacita'di mantenere sempre un determinato livello di prestazioni
- **usabilita'**: capacita'del software di essere compreso, utilizzato e configurato
- **efficienza**: capacita'di eseguire le funzioni nel minor tempo possibile
- **manutenibilita'**: capacita'del software di essere modificato, corretto o integrato
- **portabilita'**: capacita'del software di adattarsi ad ambienti tecnologici diversi, sia hardware che software

Per la qualita'd'uso vengono invece utilizzate le seguenti:
- **efficacia**: capacita'di consentire all'utente di ottenere i risultati ottenuti
- **produttivita'**: capacita'di ottenere un livello di gestione delle risorse (viste come tempo di utilizzo e costi di esercizio) conveniente
- **sicurezza**: capacita'di fornire un livello accettabile di rischio per i dati, le persone e l'attivita'economica correlata
- **soddisfazione**: grado di risposta positiva dell'utente nell'iterazione con il prodotto finale

# La misurazione del software
Per misurazione del software si intente la pratica di fornire una metrica del costo, della grandezza o della qualita'relativa ad un determinato pezzo di software.

Per fornire una misura effettiva del progetto c'e'il bisogno di utilizzare una **metrica**, che puo'essere valutata con valori **misurati**. Vengono detti valori di **soglia** i valori che rappresentano la qualita'minima o massima a seconda degli obiettivi del progetto.

L'esempio piu'semplice della misurazione del'efficienza software e'quella **M/L**, dove M e'il tempo necessario per l'elaborazione di una specifica operazione, mentre L e'il tempo obiettivo.

Un altro simile indicatore e'quello **S/N * 100**, dove S rappresenta il numero di utenti soddisfatti del prodotto e dove N e'il numero totale degli utenti intervistati. A questi valori si associa l'obiettivo (che normalmente e'posto al 90%).

La **scala Likert** e'un diverso metodo di misurazione per la qualita'del software. Si basa sul misurare quanto l'atteggiamento di un individuo sia positivo o negativo rispetto ad una determinata feature o caratteristica. Questo viene fatto con questionari a scelta multipla con 5 item per domanda, dove l'1 indica  una risposta molto negativa e il 5 ne indica una molto positiva. Tutto questo e'standardizzato nell'**ISO 9001**.

Il modello cocomo e'un modello per la misurazione dei tempi e costi. Vedi [[Metriche Costi Qualita'#Metodo COCOMO]].

# Metriche per il software
Per misurare il software nello specifico sono stati creati sistemi di misurazione efficienti, detti **metriche**. Questi ultimi sono divisi in piu'tipi:
- **dimensionali**: misurano la dimensione del codice
- **strutturali**: misurano la struttura del codice
- **funzionali**: misurano il funzionamento del codice

## Metriche dimensionali
Le metriche dimensionali misurano la dimensione del codice.

Il LOC e'il metodo piu'semplice per la misurazione della qualita'del software. Vedi [[Metriche Costi Qualita'#Mole di software]]. Il LOC ha molti problemi in quanto e'una misura che dipende molto dal linguaggio utilizzato, dallo stile di codice e da molto altro. Il LOC non e'quindi oggettivo e viene praticamente utilizzato solo per misure statistiche come:
- **la probabilita'di errori**
- **il tempo di realizzazione**
- **la produttivita'ed i compensi**: conoscendo il numero di lavoratori e la paga
- **densita'del commento del codice**

## Metriche strutturali
Le metriche di tipo strutturali si occupano di misurare la struttura logica interna, estrapolando la complessita'di realizzazione, insieme al livello di comprensione e facilita'di modifica.

La metrica strutturale piu'diffusa e' quella del **numero ciclomatico**, che calcola il numero di percorsi logici che il "flusso di esecuzione" del programma puo'seguire, tenendo in conto i punti decisionali (ad es. if-else). Si nota che tale cosa e'possibile se il programma e'strutturato e puo'essere ridotto ad un grafo (il flowchart).  
Viene quindi detto numero ciclomatico il conteggio di tutti i possibili cammini del programma.

Evitando di utilizzare la forza bruta si sa che in un grafo (come il flowchart) la complessita'viene indicata come $V(g)=numeroArchi-numeroNodi=2p$. Si nota che $p$ e'sempre 1 nel caso del flowchart.  
In alternativa, utilizzando direttamente il diagramma di flusso, viene detto $\pi$ il numero di punti decisionali presente in quest'ultimo. Il numero ciclomatico vale $\pi + 1$.

Si nota quando il numero ciclomatico e'alto, la qualita'e'bassa, software tende ad essere soggetto ad errore e tende ad essere meno comprensibile.

## Metriche funzionali
Le metriche funzionali si occupano del misurare un software dal punto di vista delle funzionalita'che offre all'utente che deve utilizzarlo. Si nota che in questi casi il misuramento del software puo'essere fatto senza essere a conoscenza del sorgente ed addirittura senza aver sviluppato il progetto (quindi anche in fase di analisi).

Il metodo piu'diffuso e'quello dei **Function Points**, che, attraverso una operazione di **function point analisys**, portano al dimensionamento del progetto in **function points**. Vedi [[Metriche Costi Qualita'#Function Points FP]].  
Un vantaggio aggiuntivo a questo metodo e'la possibilita'di prevedere la dimensione del software di manutenzione di un software gia'esistente. Questo viene fatto calcolando i seguenti valori:
- **MEV**: manutenzione evolutiva
- **MAC**: manutenzione correttiva
- **MAM**: manutenzione migliorativa
- **MAD**: manutenzione adeguativa

Il conteggio dei function points avviene attraverso procedure standard emanate dall'**IFPUG**, il quale prevede di individuare e scomporre il programma in 5 tipologie:
- **ILF** (Internal Logical File): archivi utilizzati internamente al programma
- **EIF** (External Interface File): archivi scambiati dal programma con altri programmi
- **EI** (External Input): permettono all'utente di fornire input al software
- **EO** (External Output): forniscono l'output dell'applicazione
- **EQ** (External Query): forniscono l'output senza interagire con dati
Si nota che le prime due voci sono relative ai **dati**, mentre le ultime tre sono relative alle **elaborazioni**.

Da queste tipologie si possono poi ottenere i parametri seguenti:
- **RET e DET**: relativi ai dati
- **FTR e DET**: relativi alla elaborazione

Questi parametri possono poi essere utilizzati per definire il numero di function point (che prendono il nome di **FP unadjusted**).  
Questi FP possono essere quindi aggiustati (e diventare **FP adjusted**) con un fattore detto **VAF** (Value Adjustement Factor) per ottenere un eventuale LOC preciso.

# Certificazioni ICT
Le certificazioni vengono utilizzate per garantire che una persona, un prodotto, un processo o un'azienda possano dimostrare un determinato livello di qualita'.

Le prime certificazioni furono quelle stabilite dalla norma **ISO 9000**, sebbene siano ora obsolete. All'interno di queste certificazioni apparirono per la prima volta i concetti di **Sistema di Gestione della Qualita'** (SGQ) e **Qualita'Totale** (TQM). Si nota che la norma **ISO 9000** e'basata sulla tecnica del **BSI** (British Standards Institution). La sua ultima forma/evoluzione e'la norma **ISO 9001:2015**.

Si nota che la linea di norme ISO 9000 fornisce solo norme generali, quindi sono state formate certificazioni piu'specifiche. Un esempio e' la **IAF**, che riguarda il mondo dell'IT.

L'IAF, si nota, si occupa anche di internazionalizzare i meccanismi di certificazione attraverso gli accordi **MLA**. Questo e'importante in quanto solo una azienda certificata e'autorizzata a produrre a sua volta certificati (processo dett)