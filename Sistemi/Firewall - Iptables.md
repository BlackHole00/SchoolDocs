## Concetti chiave:

### Table
Ci sono 3 `tables` principali con diverse regole. Queste sono:
- **filter**: table di default. Utilizzata per filtrare i pacchetti;
- **nat**: fa in modo che il servizio di NAT funzioni. Determina se e come modificare gli indirizzi;
- **mangle**: modifica gli headers dei pacchetti;

Ci sono altre 2 `tables` secondarie:
- **raw**: utilizzata per tracciare le connessioni;
- **security**: utilizzata per sicurezza su sistemi linux;

### Chains
Stagi del processo del pacchetto dove vengono applicate le `rules`.
Ne esistono 5:
- **prerouting**: la prima chain. Viene processata prima che venga deciso dove inoltrare il pacchetto;
- **input**: Il pacchetto è entrato nel sistema, dopo la decisione di routing;
- **forward**: Applicata ad un pacchetto che passa nel computer, ma non ne è il destinatario
- **output**: Applicata ai pacchetti creati dal computer che stanno uscendo, prima della decisione di inoltrare il pacchetto;
- **postrouting**: Dopo la decisione di inoltro di un pacchetto uscente.

Esempi di percorso di pacchetto *(le tables sono date tra parentesi)*:
- **passante per il computer**: prerouting(nat) ➡️ forward(filter) ➡️ postrouting(nat);
- **destinato al computer**: prerouting(nat) ➡️ input(filter);
- **generato dal computer**: output(nat) ➡️ output(filter) ➡️ postrouting(nat);

### Rules
Comandi per manipulare il traffico. Per ogniuno vi è una parte di controllo, che utilizza una condizione, che, se vera, può far eseguire un salto ad un target.
I target possono essere:
- **accept**:
- **drop**:
- **queue**:
- **redirect**: reindirizza il pacchetto alla macchina stessa, passando per il sistema un'ulteriore volta
- **return**: ritorna alla catena da cui quest'ultima è stata chiamata
- **dnat**: applica il nat dinamico
- **snat**: applica il nat statico
- **masquerade**: applica il nat overload. Richiede di specificare un `--to-ports`

## Comando

### Switches generali:
- `-t --table`: specifica la tabella. 
	- `iptables -t nat ...` 
	- `iptables -t filter ...`
- `-P --policy`: determina la policy di default per una chain.
	- `iptables -P FORWARD DROP`
- `-A --append`: aggiungi una condizione in una chain (append).
	- `iptables -A INPUT ...`
- `-j --jump`: salta ad un target (o chain).
	- `iptables -A INPUT -j ACCEPT`
	- `iptables -t nat -A POSTROUTING -j SNAT --to-source 192.168.1.20-192.168.1.25`
- `-R --replace`: rimpiazza un elemento di una chain
	- `iptables -R INPUT 1 ...`
- `-I --insert`: inserisce un elemento in una chain nella posizione specificata. Uguale a `-A` se nessuna posizione è specificata
	- `iptables -I INPUT 1 ...`
- `-F --flush`: rimuove tutte le regole in una catena
	- `iptables -F INPUT`
- `-X --delete-chain`: rimove una catena
	- `iptables -X INPUT`
- `-N --new-chain`: crea una nuova catena
	- `iptables -N TEST` 
- `-E --rename-chain`: rinomina una catena
	- `iptables -E TEST TESTBUTBETTER`
- `-p --protocol`: specifica un protocollo
	- `iptables -A INPUT -p tcp ...`
- `-s --source`: specifica l'indirizzo di partenza
	- `iptables -A INPUT -s 98.43.2.3 ...`
	- `iptables -A INPUT -s 192.168.0.0/24 ...`
	- `iptables -A INPUT -s www.facebook.com ...`
- `-d --destination`: specifica l'indirizzo di destinazione
	- `iptables -A INPUT -d 192.168.0.1 ...`
	- `iptables -A INPUT -d 192.168.0.0/24 ...`
	- `iptables -A OUTPUT -d www.facebook.com ...`
- `--dport --destination-port`: specifica la porta di destinazione
	- `iptables -A INPUT --dport 80 ...`
- `--sport --source-port`: specifica la porta sorgente
	- `iptables -A INPUT --sport 80 ...`
- `-m --match`: specifica ulteriori dati da controllare:
	- `--state`: controlla lo stato (`state`) della connessione. Può essere `NEW`, `ESTALISHED`, `RELATED` (creazione di una nuova connessione "collegata" ad un altra connessione, es. icmp error)...
		- `iptables -A INPUT -m state --state NEW, ESTABLISHED ...`
	- `--mac-source`: controlla l'indirizzo mac sorgente (`mac`).
		- `iptables -A INPUT -m mac --man ff:ff:ff:ff:ff:ff ...`
	- `--ip-range`: controlla il range degli indirizzi sorgente (`iprange`)
		- `iptables -A INPUT -m iprange 192.168.1.0-192.168.1.255 ...`
	- `--connlimit-above`: controlla che il pacchetto sia oltre il limite di connessioni (`connlimit`) determinato. Utilizzato solo per connessioni tcp.
		- `iptables -A INPUT -p tcp -m connlimit --connlimit-above 3 ...` 
- `--syn`: controlla che il pacchetto tcp(`tcp`) contenga in flag SYN, ACK, RST, FINSYN
- `-i --in-interface`: specifica l'interfaccia di ingresso. Se omesso ogni interfaccia viene considerata valida. Solo per `INPUT`, `FORWARD` e `PREROUTING`.
	- `iptables -A INPUT -i eth0 ...`
- `-o --out-interface`: specifica l'interfaccia di uscita. Se omesso ogni interfaccia viene considerata valida. Solo per `FORWARD`, `OUTPUT`, `POSTROUTING`.
	- `iptables -A OUTPUT -i eth0 ...`
- `--icmp-type`: specifica il tipo di icmp, utilizzabile solo con `-p icmp`. Accetta valori `echo-request` (ovvero codice 8, richiede l'icmp), `echo-reply` (ovvero codice 0, risposta al codice 8), `destination-unreachable` (ovvero codice 3), `time-exceeded` (ovvero codice 11)  e altri.
	- `iptables -A INPUT -p icmp --icmp-type echo-request`
- `--to-ports`: specifica la porta nel quale reindirizzare il messaggio dopo di aver fatto `-j REDIRECT`
	- `iptables ... -j REDIRECT --to-ports 8080`
- `--to-source`: specifica un nuovo indirizzo sorgente dopo di aver fatto `-j SNAT`, nella tabella `nat` e chain `POSTROUTING`
	- `iptables ... -j SNAT --to-source 11.11.11.11`

### Note:
- un indirizzo di tipo `0/0` indica qualsiasi indirizzo.

## Esempi generici:
- `iptables -L -n -v`: mostra tutte le liste
- `service iptables stop`
- `service iptables start`
- `service iptables restart`
- `iptables-save > /root/my.active.firewall.rules`: salva le regole
- `iptables-restore < /root/my.active.firewall.rules`: ripristina le regole

-  `iptables --policy INPUT DROP`
-  `iptables --policy FORWARD DROP`
-  `iptables --policy OUTPUT DROP`
- `iptables --policy PREFORWARD DROP`
- `iptables --policy POSTFORWARD DROP`
- `iptables --append INPUT --match state --state NEW, ESTABLISHED --protocol tcp --destination-port 22 --jump ACCEPT`
- `iptables -t nat --append PREROUTING --source 0/0 --destination 192.168.1.1 --protocol tcp --destination-port 80 -j REDIRECT --to-ports 8080`
- `iptables --append OUTPUT --destination www.facebook.com -j DROP`
- `iptables --append INPUT --source 1.1.1.1 -j DROP`
- `iptables --append INPUT --match mac --mac-source ff:ff:ff:ff:ff:ff -j DROP`
- `iptables --append INPUT --in-interface eth1 --match iprange --ip-range 192.168.0.0-192.168.255.255 -j DROP`
- `iptables --append INPUT --p tpc --destination-port 80 --match connlimit --connlimit-above 20 -j DROP`

## Utility varie
- `host -t a www.facebook.com`: ottieni l'indirizzo IP di facebook
- `whois 89.213.12.3 | grep CIDR`: ottieni la sottorete dell'indirizzo


## Sources:
- https://www.youtube.com/watch?v=vbhr4csDeI4
- https://wiki.archlinux.org/title/iptables
- https://www.frozentux.net/iptables-tutorial/iptables-tutorial.html#TRAVERSINGOFTABLES
- https://linux.die.net/man/8/iptables
- https://www.cyberciti.biz/tips/linux-iptables-examples.html