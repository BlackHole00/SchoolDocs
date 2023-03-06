# DNS
- Internet non funziona con URL, ma con indirizzi IP. Il DNS converte un URL in
indirizzo IP (www.poste.it -> 123.121.231.213)
- Il DNS e'costituito da una gerarchia di server, che sono molti e sparsi in 
tutto l'internet. Questa architettura distribuita consiente migliore gestione 
del traffico e meggiore tolleranza ai guasti.

## Hostname
- Gli hostname sono formati da nodi, ogniuno corrispondente ad ogni parte, nei quali quelli verso la fine sono piu'vicini alla radice (www.test.org = org->test->www). Non sempre ci sono solo 3 nodi in un indirizzo (www.test.gov.it).
- I nodi si identificano per livelli (www.test.org = org:primo, test:secondo, www:terzo)

## Gerarchia DNS
- Root server contiene gli indirizzi dei server con nodi primari (it, en, gov, com), i quali contengono i server con i nodi secondari etc.
- Ogni server conosce chi sta sopra e sotto di lui.

## Local Name Server
- Ogni ISP possiede un name server locale, che riceve le richieste DNS e soddisfa quelle interne alla rete.

## Suddivisione in zone
- Lo spazio dei nomi DNS e'diviso in zone.
- Ogni zona ha un server primario ed uno o piu'server secondari (che prendono le informazioni dal secondario).

## Servizi DNS
- record SOA: record univoco che contiene le informazioni sulla zona DNS, come, per esempio, il nome del server DNS principale, la mail dell'amministratore, il numero seriale ed altro ancora.
- record A (o AAAA per IPv6): da hostname ad indirizzo IP
- record CNAME: alias hostname
- record MX: fornisce i server di posta
- recond NS: correla dominio e name server
- record PTR: utilizzato per reverse lookup
- distribuzione del carico: un hostname puo'avere associati piu'indirizzi IP

## Authoritative name server
- E'il server, in una zona, che contiene i record riguardanti gli host di tale zona e ne e'il referente ufficiale.
- Caching DNS: il server DNS, se non ha la risoluzione presente nei record puo' chiedere al suo superiore la risoluzione e salvarla nella sua cache.
- Ogni campo cached ha un campo TTL, che indirca il tempo che quest'ultimo puo'essere valido

## Ricerche
- I server per ricercare la risoluzione possono utilizzare i seguenti metodi:
	- Ricerca ricorsiva: un host o server A richede al server il nome B, il quale ritorna il risultato della richiesta da un altro server ad A.
	- Ricerca iterativa: utilizzato quando il server B non puo'richieder ad un altro server, ma ne ha l'indirizzo, quindi ritornera'ad A l'indirizzo del nuovo server da contattare. Viene utilizzato normalmente per i root server.

## Protocollo DNS
- E'unp procollo dello strato applicazione
- utilizzato in supporto di altri protocolli (HTTP, SMTP, FTP)
- Utilizza UDP, nella porta 53.
- Lavora a livello 7 (Application)

# ARP
- Arp sta per address resolution protocol, viene utilizzato per ottenere l'indirizzo mac di una macchina della quale si conosce solo l'indirizzo ip.
- per vedere la cache arp e'possibile utilizzare `arp -a`.
- Lavora al livello 2 (Data Layer), ma utilizza un frame di livello 3 
(Network).

## Esempi di funzionamento
- Primo caso: A e B sono nella stessa sottorete:
	- A deve conoscere l'inirizzo MAC di B
	- A manda in broadcast l'indirizzo Ip di B, con la netmask.
	- B riconosce l'indirizzo e risponde ad A inviando il proprio indirizzo MAC. B sa di sapere di essere sulla stessa sottorete grazie alla netmask.
	- ARP ha lavorato solo a livello datalink, ma il pacchetto ARP viene incapsulato come frame di protocollo di livello 3.
	- Non e'stato interpelato nessun router.
- Secondo caso: A e B non sono nella stessa sottorete:
	- A deve conoscere l'inirizzo MAC di B
	- A manda in broadcast l'indirizzo Ip di B, con la netmask.
	- Il router vede che l'indirizzo di B e'al di fuori della sottorete e risponde ad mandando il suo indirizzo.

## Ottimizzazioni
- Ogni host ha una cache che contiene le corrispondenze tra indirizzi logici e fisici. Viene controllata prima di spedire una richiesta ARP. Non si intasa la rete.
- Il pacchetto ARP contiene anche indirizzo fisico e logico del mittente, quindi anche gli host non interessati possono aggiornare le loro cache ARP.

## Sicurezza
- Il protocollo ARP non e'sicuro e non e'protetto. (E' possibile rispondere ad una richiesta ARP con un indirizzo fittizio)
- ARP Poisoning:
	- Reindirizzare il traffico per intenti malevoli. Permette attacchi di tipo man-in-the-middle (impersonando un altro host) o deny-of-service (impersonando un gateway che non rispondera'a nessun paccketto).
	- Prevenuto attraverso il Dynamic ARP Inspection, una feature presente su switch e router avanzati. Ogni pacchetto viene analizzato e deve avere una valida mappatura IP-to-MAC, quindi deve avere gli indirizzi IP e MAC registrati in un database attendibile.

# NEIGHBOR DISCOVERY - IPV6
- Equivalente IPv6 dell'ARP, sfrutta tuttavia il protocollo ICMPv6
- Si ricorda che IPv6 non ha funzionalita'di broadcast, solo di multicast:
	- utilizza come destinazione un indirizzo chiamato solicited-node multicast address':
	- indirizzo utilizzato: `FF02:0:0:0:0:1:FFxx:xxxx`, dove le ultime 6 cifre sono quelle dell'indirizzo desiderato
	- questo indirizzo verra'inoltrato a tutti i dispositivi con indirizzo IPv6 che termina con le 6 cifre specificate.
- Permette, tra le altre cose, la STATELESS CONFIGURATION, una configurazione automatica di ottenimento dell'indirizzo IPv6, senza il bisogno di un server DHCP. Permette anche di determinare se un vicino e'ancora disponibile e di determinare se un indirizzo esiste gia'nella rete.


## Esempio di funzionamento
- A deve conoscere l'indirizzo MAC di B. A ha indirizzo l'IPv6 `2001:db8:1:2==18/64`. B ha indirizzo `2001:db8:1:2==33/64`
- A invia in multicast con l'indirizzo solicited-node multicast relativo di destinazione, quindi per esempio `FF02::1:FF00:33`. Viene specificato anche l'indirizzo di A ed l'indirizzo che si vuole ottenere. Questo frame viene detto NEIGHBOR SOLECITATION.
- B riconosce il suo indirizzo IPv6, quindi risponde con un frame NEIGHBOR ADVERTISEMENT. Utilizza come destinazione l'indirizzo di A in multicast e come indirizzo di partenza il suo specificato. Include anche il suo indirizzo MAC.


# DHCP
- Dhcp sta per Dynamic host configuration protocol e si occupa di assegnare un indirizzo logico ai computer che ne sono sprovvisti. In genere si occupa anche di configurare la subnetmask, il gateway predefinito ed il server DNS.
- E'un evoluzione del protocollo BOOTP, ora non piu'utilizzato. Si basa su questo principio:
	- l'host che vuole un indirizzo manda una richiesta in broadcast col suo indirizzo fisico ed il server risponde direttamente all'indirizzo mac con il nuovo indirizzo.
- Utilizza la porta 67 per il server e la porta 68 per il client
- Lavora nel layer 7 (Application)

## Procedimento DHCP
- Client invia pacchetto DHCPDISCOVER, con indirizzo di origine 0.0.0.0 e di destinazione 255.255.255.255. IL pacchetto contiene l'indirizzo fisico del client.
- Il server risponde con un pacchetto DHCPOFFER, con indirizzo di origine l' indirizzo del server ed indirizzo di destinazione 255.255.255.255. Il pacchetto contiene ancora l'indirizzo fisico del client, ma viene settato un field con l'indirizzo IP che il server sta offrendo. Nella parte opzionale del pacchetto e'presente la subnetmask, il gateway predefinito, il tempo di lease (quanto e'valido l'indirizzo), l'indirizzo del server WINS ed il tipo di nodo NetBIOS.
- Il client risponde con un pacchetto DHCPREQUEST, con indirizzo di origine 0.0.0.0 (il client non ha ancora ricevuto la conferma dal server) e con indirizzo di destinazione 255.255.255.255. Questo pacchetto viene trasmesso per informare eventuali server DHCP aggiuntivi che il client ha avuto una risposta. Il pacchetto contiene comunque l'indirizzo offerto e l'identificatore dell' indirizzo DPHCP.
- Il server risponde con DHCPACK, con indirizzo di orgine il proprio indirizzo e con destinazione 255.255.255.255, contenendo sempre l'indirizzo fisico e logico del client.

## Rinnovo dell'indirizzo
- tipicamente, a meta'del tempo di lease, il client richede la prologa del lease con un paccketto DHCPREQUEST.
- il server risponde con un pacchetto DHCPACK o DHCPNACK (e quindi il client otterra'unnuovo indirizzo con il procedimento standard).

## Sicurezza DHCP
- Si nota che il DHCP non prevede autorizzazioni
- Gli attacchi tipici sono:
	- DHCP Address Starvation: una macchina fa molte richieste DHCP ed usaurisce gli indirizzi disponibili
	- DHCP rogue server: un finto server DHCP che invia configurazioni non corrette ai client.

## APIPA
- Tecnologia microsoft
- Se un host non riesce ad ottenere un indirizzo con DHCP, si autoconfigura con l'indirizzo 169.254.0.0/16, inviando ARP request per verificare confilitti.
- La soluzione e'solo temporanea, in quanto il client continua ad inviare DHCPDISCOVER.
- Gli host che usano APIPA possono comunicare solo tra di loro.

# Domande
## DNS
- Un server web e un mail server di una stessa compagnia possono avere lo stesso alias?  
  SI', in quanto vengono salvati come record di tipo diverso (tipo A vs tipo MX).
- Discuti sull’efficacia di un attacco di tipo DDoS su un Authoritative Server di zona. Sarebbe possibile impedire il servizio e creare disagi agli utenti che si vogliono connettere ai server di quella zona?  
  SI', il server autoritativo e'quello che contiene i record riguardanti gli host della zona, quindi, se non sono presenti server di riserva, e'possibile impedire il servizio.
- L’attacco DNS poisoning consiste nell’iniettare record dns fasulli nella cache di un server o di un host. In che modo potrebbe essere effettuato?  
  Attraverso il caching: una volta che un server chiede al server autoritario l'indirizzo di un host, l'hacker puo'rispondere al posto del server ponendo un indirizzo malevolo, quindi quando la vittima vuole accedere a tale host, verra'indirizzata al server fasullo.