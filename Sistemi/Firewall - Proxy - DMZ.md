# Firewall
E' un sistema dedicato alla difesa **perimetrale** di una rete. Controlla i pacchetti che riceve.

Ha 3 principi fondamentali:
- Il firewall e' l'**unico** punto di contatto tra la rete interna e quella esterna
- Solo il traffico **autorizzato** puo'attraversare il firewall
- Il firewall stesso deve essere un sistema altamente **sicuro**

I firewall possono essere classificati in 3 metodi.
Il primo metodo e'in base al tipo di protezione offerto:
- **ingress firewall**: controlla i collegamenti dall'esterno all'interno della LAN (collegamenti incoming)
- **egress firewall**: controlla i collegamenti dall'interno all'esterno della LAN (collegamenti outgoing)

Il secondo metodo e'in base al numero di host protetti:
- **personal firewall**: proteggono un singolo host
- **network firewall**: protegge tutta una LAN e la divide dall'internet

Il terzo metodo e'in base alla modalita'di operazione:
- **filtri di pacchetto IP**: bloccano o consentono il traffico analizzando i pacchetti (e quindi i protocolli utilizzati, gli indirizzi e porte sorgenti e di destinazione e altro)
- **server proxy**: server intermediario _(vd. Proxy)_

## Stateless firewall
E'un tipo di firewall nel quale un pacchetto viene analizzato singolarmente per poi essere scartato o meno.
Si nota che questo tipo di firewall e'stato rimpiazzato dallo `Statefull Firewall`, in quanto porta problemi con l'accuratezza delle analisi effettuate.

Per capire quali pacchetti scartare, vengono analizzati gli header di ogni pacchetto e controlla che quest'ultimo rispetti le proprie regole e parametri. Nel particolare vengono analizzati:
- Il protocollo utilizzato _(TCP, UDP, ICMP...)_
- Gli indirizzi sorgenti e di destinazione
- La porta sorgente e di destinazione _(questo permette di riconoscere il protocollo a livello applicativo - HTTP, SSH, HTTPS...)_

Questi parametri vengono filtrati controllandoli con una serie di regole. Le quali sono eseguite secondo un ordine preciso e potranno decidere se effettuare una delle seguenti operazioni:
- **DROP/DISCART**: scarta il pacchetto senza dire nulla al mittente
- **ACCEPT/ALLOW**: accetta il pacchetto e permette la connessione
- **DENY**: scarta il pacchetto e invia al mittente un messaggio ICMP per comunicare lo scarto

Si nota che le regole possono essere divise in 2 categorie:
- **inside**: provengono dall'interno della LAN e sono diretti verso l'esterno
- **outside**: provengono dall'esterno della LAN e sono diretti verso l'interno

## Statefull firewall
Firewall piu'innovativo che si basa sull'analisi della **cominicazione** tra sorgente e destinatario e non piu'del singolo pacchetto. Per identificare la connessione vengono sempre analizzati gli header dei pacchetti per ottenere il protocollo utilizzato e gli indirizzi e porte sorgenti e di destinazione. Nel caso delle comunicazioni **TCP** vengono anche analizzati i **numeri della sequenza dei pacchetti ed i flag _(SYN, SYN-ACK, ACK, FIN)_  dello stato di connessione**. 

Lo statefull firewall permette quindi di controllare solo i primi pacchetti di una comunicazione _(handshake)_ ed accettare tutti i pacchetti della comunicazione corrispondente.

Ovviamente per gestire i primi pacchetti di una comunicazione vengono sempre utilizzare le regole come nello `stateless firewall`. Lo stesso vale per le comunicazioni non TCP.

Lo stato di una connessione viene salvato nella **SPI Table**.  
Le connessioni possono essere di 3 tipi:
- **ESTABLISHED**: accettata dal firewall. Il _three-way handshake_ e'avvenuto correttamente 
- **CLOSED**: a seguito del termine di una connessione _(chiusura con pacchetti FIN)_
- **NEW**: una nuova connessione, generalmente ancora nello stato di _handshake_


# Proxy
Il proxy e'un servizio che labora a livello di **applicazione** o di **sessione/trasporto** a seconda del tipo. E'in grado di analizzare i pacchetti a livello del loro contenuto _(quindi non piu'solo di header)_.

A livello di funzionamento un server proxy funziona in modalita'simile a quella di un firewall e quindi funziona come "middleware" tra sorgente e destinatario. Quindi ricevera'i pacchetti, ne controlla il contenuto e lo invia al destinatario.

Il proxy viene utilizzato per motivi di:
- **caching**: memorizza comuni dati remoti richiesti dagli utenti e ne tiene una copia in cache dopo la prima richiesta. Questo rende alcune connessioni non piu'necessarie e rende la rete quindi piu'veloce.
- **controllo**: applicando piu'regole e'in grado di decidere se limitare o meno la comunicazione di un client a seconda della banda disponibile o delle limitazioni del client.
- **monitoraggio**: tiene traccia delle operazioni effettuati da ogni indirizzo IP/account.

## Application Proxy
Questo tipo di firewall lavora a livello **applicazione**. Filtra i pacchetti a seconda del loro contenuto.

Ha le seguenti caratteristiche:
- Siccome lavora a livello applcativo questo tipo di proxy e'estremamente specifico e funziona solo per **una sola specifica applicazione**
- Questo filtraggio e'pesante ed ha un **grande overhead ad ogni comunicazione**
- Questo filtraggio e'**piu'sicuro**
- 

# Note varie
- I pacchetti ICMP possono essere di piu'tipi:
	- **0 - ECHO REPLY**: risposta a una richiesta _(tipo 8)_ - **PONG**
	- **3 - DESTINATION UNREACHABLE**: la destinazione non e'raggiungibile
	- **8 - ECHO REQUEST**: richiesta di una risposta _(tipo 0)_ - **PING**
	- **11 - TIME EXCEEDED**: il TTL non ha permesso al pacchetto di arrivare a destinazione
	- ...