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
- **chosen plaintext** (testo in chiaro a scelta): il crittoanalista e'a conoscenza di parte del testo in chiaro ed e'in grado di intercettare il corrispondente crittogramma con la chiave segreta. Questo attacco e'in genere causato da un grande numero di testo in chiaro che viene studiato per trovare eventuali vulnerabilita' dovute a comportamenti non casuali.
- **chosen ciphertext** (crittogramma a scelta): il crittoanalista e'in grado di ottenere un testo in chiaro con la chiave segreta conoscendo il crittogramma che lo ha generato
- **opek key model**: il crittoanalista ha una conoscenza limitata della chiave o della sua struttura, quindi sfrutta queste conoscienze per ottenere i testi in chiaro

Si nota che la soluzione piu'comune e'quando il crittoanalista conosce solo il crittogramma e l'algoritmo di cifratura utilizzato. In mancanza di altre informazioni viene utilizzato un **attacco esaustivo** (anche detto **forza bruta**), privando ad utilizzare tutte le possibile chiavi. Questo approccio e'generalmente poco produttivo.

## Crittosistemi
Un **sistema crittografico** ha le seguenti ulteriori caratteristiche:
- l'algoritmo di cifratura deve essere abbastanza **resistente** da resistere ad attacchi di tipo **chipertext only** e **known plaintext**
- deve avere un meccanismo sicuro per l'ottenimento della chiave, che deve rimanere segreta

Un sistema crittografico viene detto **incondizionalmente sicuro** quando il testo cifrato **non** contiene abbastanza informazioni perche'un crittoanalista sia in grado di **risalire** al **testo in chiaro**, indipendentemente dalle risorse utilizzate. In pratica **non esistono** sistemi incondizionalmente sicuri, esistono solo sistemi **computazionalmente sicuri**, il quale tempo di decriptazione e'maggiore del tempo di utilita'del testo in chiaro.

Un esempio di sicurezza, definito da *Claude Shannon*, e'che in un testo cifrato non si riflettessero le statistiche di frequenza dell'utilizzo delle lettere nella lingua utilizzata.

Il cifrario robusto deve quindi utilizzare due metodi:
- **diffusione**: la struttura statistica del testo in chiaro viene diffusa nel crittogramma, facendo in modo che il cambiamento di una cifra nel testo in chiaro causi il cambiamento di molte cifre nel crittogramma. Questo effetto viene detto **effetto valanga**
- **confusione**: la relazione tra chiave e crittogramma deve essere molto complessa, rendendo difficile ricostruire la chiave.

## Stream cipher e Block Cipher
I cifrari possono essere divisi in due gruppi a seconda della modalita'di criptazione:
- **Stream cipher**: cifrario a base simmetrica, in cui le cifre di testo in **chiaro** sono **combinate** con un flusso di cifre di cifratura **pseudocasuale**. Come funzionamento si basa sul cifrare ogni singolo bit o byte del flusso di dati. Le cifre pseudocasuali vengono generate attraverso valori iniziali, che utilizzano registri a scorrimento delle cifre. Si nota che lo stream cipher utilizza una chiave diversa per ogni byte. 
- **Block cipher**: metodo di crittografia che applica un algoritmo **deterministico** per crittografare un testo di lunghezza conosciuta, al posto di crittografare ogni singolo bit. Il testo viene generalmente diviso in **blocchi** da 64 o 128 byte ed ogniuno di questi viene criptato separatamente.

## Stream cipher
Un esempio di un algoritmo di criptazione a stream e'quello che cripta il singolo byte combinando (con l'operazione logica **XOR**) il byte in chiaro con il **keystream**/ Il keystream viene generato in maniera pseudocasuale utilizzando una **chiave**. Quest'ultimo viene anche detto algoritmo di **sostituzione**, in quanto sostituisce ogni byte con il corrispondente criptato.

## Block cipher
Gli algoritmi di cifratura simmetrica a blocchi sono divisi a loro volta a seconda del funzionamento:
- **per sostituzione**: mappano ogni elemento del testo in chiaro con un nuovo elemento criptato
- **per trasposizione**: distribuiscono gli elementi del testo in chiaro in ordine diverso

### Il codice di cesare
Il codice di cesare e'un algoritmo di criptazione a blocchi che associa ogni singola lettera ad un suo equivalente statico. Utilizza quindi un algoritmo per **sostituzione**.

Il codice di cesare e'vulnerabile ad attacchi di **forza bruta**, specialmente se si tiene in considerazione la **frequenza** dell'apparizione delle singole lettere in una determinata lingua.

### Cifrari polialfabeti
Per risolvere la debolezza del codice di cesare venne creato un cifrario a sostituzione **polialfabetica**, il quale usa una **piu'** diversi algoritmi di associazione delle lettere, i quali vengono utilizzati un un **determinato ordine** definito dalla chiave. La lunghezza della chiave definisce quindi anche la complessita'del cifrario. Utilizzando una chiave breve, il messaggio sara'piu'facilmente decriptabile.
Si nota che i cifrari standard, come quello di cesare, vengono considerati **monoalfabetici**.

Un esempio di cifrario **polialfabetico** fu quello di **Vignere** che venne utilizzato estensivamente nel 1800.

### Algoritmo DES
Inventato dalla IBM negli anni '60, il DES (Data Encryption Standard) e'un algoritmo di **cifratura simmetrica a blocchi**, che codifica **blocchi di 64 bit** con una **chiave di 56 bit**.

Si nota che il DES **non viene piu'utilizzato** dal 2001, quando e'stato scoperto che puo'essere soggetto ad attacchi di **forza bruta**.

Il blocco viene permutato inizialmente da un **permutazione iniziale** $P_i$ e subisce una **trasformazione** $F$ 16 volte utilizzando la chiave ed infine subisce una **permutazione finale** $P_f$ inversa di $P_i$. 

Con il termine **permutazione** si intende lo **scambio** delle posizioni dei **bit** stessi. Si nota che le permutazioni iniziali e finali **non hanno valenza crittografica**, ma vennero create per facilitare l'input con l'hardware dell'epoca.

Prima di ogni **trasformazione** ogni blocco viene diviso in **due parti** da 32 bit, che vengono elaborate alternamente. Vengono inoltre generate 16 **sottochiavi** di 48 bit utilizzando la chiave principale utilizzando la permutazione dello **shift a sinistra**, una utilizzata per ogni trasformazione.

Le **trasformazioni** quindi lavorano con blocchi di 32 bit e consistono nei seguenti passaggi:
- **expansion**: il blocco viene **ridimensionato** a **48 bit**, utilizzando un algoritmo deterministico. Meta'dei bit sono quindi duplicati. Questa operazione viene fatta dal **blocco E**
- **key mixing**: il blocco viene messo a **XOR** con la sottochiave corrispondente alla trasformazione
- **substitution**: i 48 bit risultanti vengono divisi in parti da 6 bit, i quali vengono utilizzati come indici di una **tabella di lookup** che ritorna 4 bit. Viene creato quindi un blocco da **32 bit**. Ogni tabella di lookup viene detta **S-box**
- **permutation**: i 32 bit vengono mescolati da una permutazione predefinita. Questa operazione viene fatta dal **blocco P**

L'utilizzo delle **S-box** e dei **blocchi E e P** causano **diffusione** e **conclusione**, rendendo sicuro l'algoritmo.

### Algoritmo AES
Quando il DES venne violato nel 2001 venne creato un algoritmo piu'robusto, chiamato **AES** (Advanced Encryption Standard). Quest'ultimo e'un cifrario a blocchi della famiglia *Rjindael*.

AES utilizza quindi blocchi e chiavi di lunghezza diversa, generalmente i blocchi sono di 128 bit, mentre le chiavi possono essere di 128 bit, 192 bit e 256 bit. La modalita'di funzionamento e'simile a quella del DES.

### Algoritmo 3-DES
Questo algoritmo fu creato come successore del DES ed **alternativa all'AES**, con l'obiettivo di continuare ad essere compatibile con l'hardware designato per il DES e consiste nell'applicare il **DES tre volte**, utilizzando una **chiave di 168 bit**. Il 3-DES e'comunque meno sicuro (sebbene sia comunque computazionalmente sicuri), quindi si e'mantenuto l'AES.

## Modalita'operative per i cifrari a blocchi
Gli algoritmi per la cifratura sono in grado di criptare un blocco di lunghezza determinata di $n$ bit. Se un messaggio e'piu'lungo di un blocco deve essere **diviso** in piu'parti grandi come un blocco, ogniuno dei quali viene elaborato a se'.

Sorgono allora alcuni **problemi**, in quanto i cifrari visti danno sicurezza solo sul singolo blocco, cio'porta a problemi di sicurezza, in quanto ci sono molti blocchi cifrati con la **stessa chiave**.

Per risolvere questo problema sono state definite delle modalita'di applicazione ripetuta degli algoritmi di cifratura, dette **modalita'operative**, le quali sono indipendenti dal cifrario utilizzato.

### Electronic CodeBook
L'ECB e'una modalita'operativa. E'molto semplice in quanto divide il messaggio in blocchi e completa con bit casuali quelli che non sono "pieni". Questo porta alla **mancanza di diffusione**, quindi nei messaggi lunghi rivelera'eventuali irregolarita'presenti nel messaggio originale.

### Cipher Block Chaining
Il CBC utilizza il crittogramma risultante dal blocco precendente in **XOR** con il blocco da in chiaro da cifrare. Nel primo blocco viene utilizzato quello che si definische **vettore di inizializzazione** $V_i$.  
Il messaggio otterra'sicuramente diffusione, ma non potra'essere criptato in parallelo.

### Counter
La modalita'CTR utilizza, come input dell'algoritmo di criptazione, passa, al posto del testo in chiaro, un **nonce**, ovvero un numero casuale utilizzato solo una volta nel messaggio, ed un **contatore**.  
Al risultato ottenuto viene messo in **XOR** il testo in chiaro, per generare il crittogramma.   
Per decifrare viene utilizzata l'operazione opposta.

I vantaggi sono numerosi:
- **efficienza hardware**: permette la parallelizzazione
- **efficienza software**: permette la parallelizzazione
- **sicurezza**
- **elaborazione a priori**: i blocchi possono essere pre calcolati, per poi essere messi in XOR col messaggio in chiaro solo quando serve
- **semplicita'**
- **accesso in lettura casuale**

## Crittografia a chiave pubblica/privata
I crittosistemi simmetrici hanno una grande **debolezza** difficile da superare: lo **scambio delle chiavi**, cosa che richiede un canale sicuro di comunicazione, che e'difficile da creare senza, appunto, le chiavi.

Per risolvere il problema vennero scoperti i **crittosistemi asimmetrici**, i quali utilizzano due chiavi distinte. Questi si basano quindi su funzioni matematiche e non piu'sostituzioni e permutazioni.

I **requisiti** per un crittosistema asimmetrici sono:
- facilita'di generare una coppia di chiavi
- facilita'computazionale per il mittente di generare il crittogramma
- impossibilita'computazionale di dedurre la chiave privata conoscendo quella pubblica
- facilita'computazionale per un destinatario di risalire al messaggio in chiaro
- impossibilita'computazionale di dedurre il messaggio in chiaro conoscendo la solo chiave pubblica
- possibilita'di applicare le due chiavi in entrambi gli ordini (opzionale)

In genere in un sistema crittografico asimmetrico vi sono i seguenti **passaggi**:
- ogniuno deve avere una chiave pubblica e privata
- ogni persona deve rendere presente al prossimo la propria chiave pubblica
- il mittente cifra il messaggio con la chiave pubblica del destinatario
- il destinatario decifra il messaggio utilizzando la chiave privata

Se anche l'ultimo dei requisiti e'soddisfatto e'anche possibile **decifrare** messaggi cifrati con la chiave privata. Cio'puo'garantire l'**autenticita'** del mittente. In questo caso vengono utilizzati ulteriori passaggi:
- prima di cifrare il messaggio con la chiave pubblica del destinatario, il mittente lo decifra con la propria chiave privata
- dopo di aver decifrato il messaggio, il destinatario utilizza la chiave pubblica del mittente per decifrare il messaggio. Se il messaggio risulta allora in chiaro si puo'essere sicuri che il destinatario sia autentico.

Si nota infine che i crittosistemi asimmetrici sono vulnerabili ad attacchi di **forza bruta**. Per una maggiore protezione e'consigliato aumentare le dimensioni della chive, tuttavia il tempo di criptazione e decriptazione aumenta non in maniera lineare, ma piu'velocemente, all'aumentare della lenghezza della chiave. Questo richiede di trovare un **compromesso** tra velocita'e sicurezza.

Praticamente, tuttavia, questo compromesso **non esiste**, e per fornire tale sicurezza non e'possibile avere un sistema puramente simmetrico. Viene quindi utilizzato un sistema **ibrido**, che utilizza la criptazione asimmetrica per condividere la chiave simmetrica, con la quale avverra'la normale comunicazione. La chiave simmetrica viene generalmente cambiata ad ogni messaggio e viene detta quindi **chiave di sessione**.

### Algoritmo RSA
L'algoritmo RSA e'stato creato nel 1977 ed e'ancora oggi quello piu'diffuso ed utilizzato per la cifratura asimmetrica.