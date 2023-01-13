Guide pratique de l'administrateur réseau
========================================

Ce document à pour but de connaître les commandes réseaux et leurs utilisations dans différents systèmes d'exploitations.

Tableaux
--------

### Réseaux


|Linux|Racourci|Windows|
|-----|--------|-------|
ip addr show|ip a|ip config|
ip addr add @ip/masque dev interface|ip a a @ip/CIDR dev interface|netsh interface ip set address name="interface" static @ip masque @DNS|
ip addr flush dev reseau|ip a f dev interface|ipconfig/release|
ip addr del @ip dev interface|ip a d @ip interface| ipconfig/release|
ip link show|ip l|ipconfig/all|
ip link set up dev interface|ip l s up dev interface|netsh interface set interface "interace" enable|
ip link set down dev inteface|ip l s down dev interface|netsh interface set interface "interface" disable|
ip neighbour|ip n|arp|
ip neighbour flush all|ip n f all|arp -d|
ip route|ip r|ipconfig|
ip route add default via @ip_gateway dev interface_reseau| |route ADD 0.0.0.0 MASK 0.0.0.0 192.168.1.254|
ip route add @ip_gateway dev interface|ip r a @ip_gateway dev interface|route add @reseau mask masque @ip|
ip route del @ip_gateway dev interface| ip r del @ip_gateway dev interface|route delete @reseau mask masque @ip|
ip route flush @ip_gateway dev interface| |route delete 0.0.0.0|
ip route flush dev interface| | |
ping @ip|| ping @ip|
traceroute @ip|| tracert @ip|
netstat||netstat|
telnet||telnet|

<br>

### OS
|Linux|Windows|
|-----|-------|
cd|cd|
mkdir|mkdir|
cp fichier_source fichier_cible|copy fichier_source fichier_cible|
rm|del|
man commande|commande /?|
pwd|chdir|
cat fichier|type fichier|
touch fichier|type nul > fichier|
ls|dir|


