La **crittografia** e'la scienza che studia ed elabora metodi finalizzati al nascondere le informazioni a chi non e'autorizzato al loro accesso. La parola deriva dal greco *cryptos* (nascosto).

Storicamente la crittografia ha avuto utilizzi **diplomatici**, **militari**. Attualmente viene utilizzata per la **protezione del segreto industriale**, per la **privacy del cittadino** e per le **transazioni economiche per via telematica**.

Dal punto di vista pratico la crittografia si occupa di **convertire** dati da un formato **leggibile** ad uno **codificato**, che puo'essere letto o interpretato solo dopo essere stato decrittato solo da persone **autorizzate**.  
In *generale* per far cio'si utilizzano **sistemi crittografici** che hanno in comune due elementi:
- una **trasformazione** del messaggio per garantire la sicurezza (comunemente la  *cifratura*)
- una **informazione segreta** nota solo agli **attori** (trasmettitore e ricevitore) della comunicazione (in genere la *chiave*)

Si nota che i sistemi crittografici sono distinti in:
- **sistemi simmetrici** o *a chiave privata*: la chiave utilizzata per cifrare e decifrare il messaggio e'la **stessa**, ovvero avviene una **criptazione simmetrica**
- **sistemi asimmetrici** o *a chiave pubblica*: vengono utilizzate due chiavi **distinte** per la criptazione (che utilizza la chiave **pubblica**) e la decriptazione (che utilizza la chiave **privata**), ovvero avviene una **criptazione asimmetrica**

## Crittografia Simmetrica
Questo metodo di criptazione, come detto prima utilizza un'unica chiave. Si basa sulla funzione matematica del **cifrario**, la quale viene utilizzare per criptare e decriptare ed e'**iniettiva** ed **invertibile**. La chiave viene utilizzata come parametro applicato al cifrario.
$$
	Plain \rightarrow f_{key}() \rightarrow Crypted
$$
$$
Crypted \rightarrow f^{-1}_{key}() \rightarrow Plain
$$
La criptazione simmetrica ha quindi le seguenti caratteristiche:
- fonda la segretezza sulla **segretezza della chiave**
- mittente e destinatario devono essere in **possesso** della **chiave**, che deve essere **distribuita**
- comprende algoritmi che impiegano sia **sostituzioni** che **trasposizioni**
- comprende codici cifrati sia a **flusso** che a **blocchi**

## Crittografia Asimmetrica
Questo metodo di criptazione, come detto in precedenza utilizza due chiavi distinte.=, una **pubblica** per cifrare ed una **privata** per decifrare.
$$
Plain \rightarrow f_{publicKey}() \rightarrow Crypted
$$
$$
Crypted \rightarrow f_{privateKey}() \rightarrow Plain 
$$

Si nota che e'**impossibile derivare una chiave dall'altra**, quindi essendo a conoscenza della chiave pubblica non e'possibile ottenere quella privata e viceversa.

## Crittoanalisi
Per crittoanalisi si intende lo studio dei **metodi di decriptazione** per ricostruire un messaggio in chiaro. Si dice **crittoanalista** colui che prova a decriptare un messaggio.

Quest'ultimo puo'provare diversi **tipi di attacco** a seconda delle informazioni che ha a disposizione sull'**algoritmo di cifratura** e sul **crittogramma**.  
Alcune situazioni in cui si puo'provare sono:
- **ciphertext only** (solo crittogramma): la situazione piu'difficile per il crittoanalista
- **known plaintext** (testo in chiaro noto): si conosce il testo in chiaro con il corrispondente crittogramma e chiave segreta
- **chosen plaintext** (testo in chiaro a scelta): il crittoanalista e'a conoscenza di parte del testo in chiaro ed e'in grado di intercettare il corrispondente crittogramma con la chiave segreta. Questo attacco e'in genere causato da un grande numero di testo in chiaro che viene studiato per trovare eventuali vulnerabilita' dovute a comportamenti non casuali. Questa tecnica fu utilizzata nelle *bombe* durante la seconda guerra mondiale
- **chosen ciphertext** (crittogramma a scelta): il crittoanalista e'in grado ti ottenere un crittogramma con la chiave segreta conoscendo il testo in chiaro che lo ha generato
- **opek key model**: il crittoanalista ha una conoscenza limitata della chiave o della sua struttura, quindi sfrutta queste conoscienze per ottenere i testi in chiaro