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
Si nota che questo tipo di firewall e'stato rimpiazzato dallo `Statefull Packet Inspection`, in quanto porta problemi con l'accuratezza delle analisi effettuate.

Per capire quali pacchetti scartare, vengono analizzati gli header di ogni pacchetto e controlla che quest'ultimo rispetti le proprie regole e parametri. Nel particolare vengono analizzati:
- Il procollo utilizzato _(TCP o UDP)_
- Gli indirizzi sorgenti e di destinazione
- La porta sorgente e di destinazione _(questo permette di riconoscere il protocollo a livello applicativo - HTTP, SSH, HTTPS...)_

Questi parametri vengono filtrati controllandoli con una serie di regole. Le quali portanno decidere se effettuare una delle seguenti operazioni:
- **DROP/DISCART**: scarta il pacchetto senza dire nulla al mittente
- **ACCEPT/ALLOW**: accetta il pacchetto e permette la connessione
- **DENY**: scarta il pacchetto e invia al mittente un messaggio ICMP per comunicare lo scarto celo
- 