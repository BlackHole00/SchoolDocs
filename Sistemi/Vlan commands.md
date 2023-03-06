### SWITCH
- `S1(config)# vlan {NUMERO VLAN}`: entra nella modalita'di modifica della vlan. Crea la vlan se non esiste ancora.
- `S1(config-vlan)# name {NOME VLAN}`: da'un nome alla vlan per riconoscerla facilmente.
- `S1(config)# interface {CATEGORIA}{NUMERI IDENTIFICATORI}`: entra nella modalita'di modifica della porta specificata.
Un esempio e'`interface FastEthernet0/24`
- `S1(config)# interface range {CATEGORIA} {PRIMO NUMERO IDENTIFICATORE}/{INIZIO SECONDO NUMERO}-{FINE SECONDO NUMERO}`:
Modifica tutte le interfacce nel range specificato.
- `S1(config-if)# switchport access vlan {NUMERO VLAN}`: setta la porta in modalita'VLAN, con accesso alla vlan 
specificata dal numero.
- `S1(config-if)# switchport mode trunk`: mette l'interfaccia in modalita'trunk.
- `S1# show vlan brief`: mostra le vlan
- `S1(config-if)# ip address 10.0.1.253 255.255.255.0`: setta l'indirizzo ip del router (per DHCP nella vlan)

### ROUTER
- `DG(config)# interface gigabitEthernet 0/0.11`: entra nella modalita'di configurazione della vlan 11 nell'interfaccia
gigabitEthernet 0/0
- `DG(config-subif)# encapsulation dot1Q 11`: dice di usare effettivamente la vlan 11
- `DG(config-subif)# ip address 10.0.11.254 255.255.255.0`: setta l'indirizzo ip
- `DG(config)# ip route 102.1.2.0 255.255.255.0 102.1.2.2`: setta una route statica. Dice che se bisogna  andare nella 
sottorete `102.1.2.0` bisognera' comunicare il server/router `102.1.2.2`.
- `DG(config)# ip route 0.0.0.0 0.0.0.0 102.1.2.2`: setta il gateway di last resort all'indirizzo `102.1.2.2`
- `DG# show ip routes`: mostra tutte le routes

### DHCP
- `S1(config)# ip dhcp excluded-address 10.0.0.1 10.0.0.10`: comando per DHCP per definire gli indirizzi non 
utilizzabili, quindi dal 10.0.0.1 al 10.0.0.10
- `S1(config)# ip dhcp pool vlan11`: crea una pool dhcp con nome vlan11.
- `S1(dhcp-config)# network 10.0.1.0 255.255.255.0`: setta la sottorete del pool dhcp
- `S1(dhcp-config)# default-router 10.0.1.254`: setta il default gateway
- `S1(dhcp-config)# dns-server 10.0.1.254`: setta il server dns
- `S1(dhcp-config)# option 150 ip 192.168.1.3`: setta l-indirizzo ip del server TFTP
- `S1(config)# show ip dhcp pool`: mostra la configurazione dhcp
- `S1(config)# show ip dhcp bindings`: mostra gli indirizzi dhcp assegnati

### NOTE:
- Nel router e'necessario ricordarsi di attivare anche la linea che contiene le vlan utilizzando `no shutdown`, sebbene
non siano stati assegnati indirizzi ip.