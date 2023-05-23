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

# Metriche per il software: LOC
Per misurare il software nello specifico sono stati creati sistemi di misurazione efficienti, detti **metriche**. Questi ultimi sono divisi in tre tipi:
- **dimensionali**: misurano la dimensione del codice
- **strutturali**: misurano la struttura del codice
- **funzionali**: misurano il funzionamento del codice

Il LOC e'il metodo piu'semplice per la misurazione della qualita'del software. Vedi [[Metriche Costi Qualita'#Mole di software]]. Il LOC ha molti problemi in quanto e'una misura che dipende molto dal linguaggio utilizzato, dallo stile di codice e da molto altro. Il LOC non e'quindi oggettivo e viene praticamente utilizzato solo per misure statistiche come:
- **la probabilita'di errori**
- **il tempo di realizzazione**
- **la produttivita'ed i compensi**: conoscendo il numero di lavoratori e la paga
- **densita'del commento del codice**

# Metriche per il software: numero ciclomatico
