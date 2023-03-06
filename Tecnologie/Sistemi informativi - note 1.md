# TECNOLOGIE - UDA 01, Francesco Viciguerra, Novembre 2022

- **Sistema informativo centralizzato**: dati ed informazioni risiedono in un 
unico nodo informativo.
- **Sistema informativo distribuito**: quando avviene l'**elaborazione
distribuita** o quando **la base dei dati e'distruita**. E'quindi costituito da
un insieme di applicazioni logicamente indipendenti che collaborano per il
perseguimento di obiettivi comuni attraverso una infrastruttura di comunicazion
hardware e software. Le applicazioni hanno i seguenti ruoli:
  - **client**: quando e-utilizzatore di servizi messi a disposizione da altre
	applicazioni.
  - **server**: quando fornisce servizi.
  - **actor**: quando assume sia ruolo di cliente che di servente.    
- I sistemi distribuiti sono di tre tipi:
  - **di calcolo distribuiti**: per calcolo ad alte prestazioni (grid computing
	e cloud computing)
  - **informativi distribuiti**: il web 
  - **distribuiti pervasivi**: sistemi connessi tipicamente in modo wireless,
  come sistemi domestici, PAN ed altro. Sono fatti ad hoc, hanno facile 
  configurazione, condividono molti dati e sono pronti per molti contesti.
- **Benefici della distribuzione**:
  - affidabilita'
  - integrazione
  - trasparenza
  - economicita'
  - apertura
  - connettivilita'
  - prestazioni e scalabilita'
  - tolleranza ai guasti
- **Svantaggi della distribuzione**:
  - produzione di software
  - complessita'
  - sicurezza
  - comunicazione
- **Classificazione archietture distribuite hardware**: 
  - SISD: La macchina di von Newmann
  - SIMD: Piu'processori che fanno la stessa cosa (stesso instruction stream),
  ma con dati diversi (piu'data stream). Compute shaders in GPU.
  - MISD: Piu'processori che fanno cose diverse con gli stessi dati.
  - MIMD: Piu'processori che fanno code diverse lavorano su dati diversi, che 
  vengono condivisi. Sono divise in:
    - a memoria fisica condivisa: muliprocessori, utilizzano variabili condivise
    e meccanismi di sincronizzazione.
    - a memoria fisica privata: multi computer  
- E sono interconnessi nei seguenti metodi:
    - con mezzo condiviso
    - su canale diretto
> |                     | DATI SINGOLI | DATI MULTIPLI |  
> |---------------------|--------------|---------------|  
> | ISTRUZIONI SINGOLE  | SISD         | SIMD          |  
> | ISTRUZIONI MULTIPLE | MISD         | MIMD          |  
- **Cluster computing**: un sistema costituito da un insieme di nodi, 
interconnessi tramite una rete locale ad alta velocita'. I nodi sono omogenei 
(stesso OS, stesso HW, stessa rete). Questi sistemi possono essere ad 
organizzazione gerarchica, con un nodo principale o con organizzazione Single
System Image.
- **Grid computing**: sistema altamente decentralizzato, con molti nodi 
eterogenei.
- **Architetture distribuite Software**: Possono essere di tipo:
  - **A terminali remoti**: le applicazioni sono solo sul server
  - **Client server**: sia il client che il server hanno applicazioni e dati.
  - **Web centric**: spostamento applicazioni sul server. Host meno importanti,
  ma comunque con applicazioni
  - **Cooperativa**: entita'esterne richiedono servizi.
  - **Completamente distribuita**
- **Architettura a livelli**: Alleggerisce il carico dei server, utilizza i
**middleware**, il quale spesso fornisce un'API