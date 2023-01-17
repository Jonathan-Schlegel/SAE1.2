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
ip route add default via @ip_gw dev interface | |route ADD 0.0.0.0 MASK 0.0.0.0 192.168.1.254|
ip route add @ip_reseau/CIDR via @ip_gw dev interface|ip r a @ip_reseau/CIDR via @ip_gw dev interface|route add @reseau mask masque @ip|
ip route del @ip_gateway dev interface| ip r del @ip_gateway dev interface|route delete @reseau mask masque @ip|
ip route flush default dev interface| |route delete 0.0.0.0|
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

Utilisation
-----------

### ip addr show/ipconfig

Ces commandes renseignent sur la configuration réseau

Sur Linux:

```
ip addr show
```
Elle affiche:

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether f8:b4:6a:91:25:a0 brd ff:ff:ff:ff:ff:ff
    inet 10.213.0.219/16 brd 10.213.255.255 scope global dynamic noprefixroute enp1s0
       valid_lft 52396sec preferred_lft 52396sec
    inet 10.213.0.52/16 brd 10.213.255.255 scope global secondary dynamic enp1s0
       valid_lft 52398sec preferred_lft 52398sec
    inet6 fe80::2b93:dbe1:98d8:f5f0/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp2s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether d0:ab:d5:ec:e6:7c brd ff:ff:ff:ff:ff:ff
4: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:c8:83:00 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
```

Sur Windows:


```
ipconfig
```

```

```
### ip addr add @ip/masque dev interface /

Ces commandes ajoute une adresse IP 

Sur Linux:

```
ip addr add 10.213.4.1/16 dev eno1
```

Sur Windows:

```

```

### ip addr flush dev interface

Ces commandes suppriment les adresses IP

Sur Linux:

```
ip addr flush dev enp1s0
```

Ce qui donne:

```
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether f8:b4:6a:91:25:a0 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::e332:3b3d:9bd7:efef/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```

Sur Windows:

```
```


### ip addr del @ip dev interface

Ces dommandes suppriment une adresse IP

Sur Linux:

```
ip addr del 10.213.0.52 dev enp2s0
```

Ce qui donne:

```
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether f8:b4:6a:91:25:a0 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::e332:3b3d:9bd7:efef/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```

Sur Windows:

```
```

### ip link show /

Ces commandes renseignent sur l'état de la carte réseau

Sur Linux:

```
ip link show
```

Ce qui donne:

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether f8:b4:6a:91:25:a0 brd ff:ff:ff:ff:ff:ff
3: wlp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default qlen 1000
    link/ether d0:ab:d5:ec:e6:7c brd ff:ff:ff:ff:ff:ff
4: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default qlen 1000
    link/ether 52:54:00:c8:83:00 brd ff:ff:ff:ff:ff:ff
```

Sur Windows:

```
```
Ce qui donne:

```
```

### ip link set up dev interface /  

Sur Linux:

```
ip link set up de enp1s0
```

Ce qui donne:

```
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether f8:b4:6a:91:25:a0 brd ff:ff:ff:ff:ff:ff
    inet 10.213.0.219/16 brd 10.213.255.255 scope global dynamic noprefixroute enp1s0
       valid_lft 57077sec preferred_lft 57077sec
    inet6 fe80::2b93:dbe1:98d8:f5f0/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```

Sur Windows:

```
```

Ce qui donne:

```

```


### ip link set down dev interface / 

Sur Linux:

```
ip link set down dev enp1s0
```

Ce qui donne:

```
2: enp1s0: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether f8:b4:6a:91:25:a0 brd ff:ff:ff:ff:ff:ff
    inet 10.213.0.219/16 brd 10.213.255.255 scope global dynamic noprefixroute enp1s0
       valid_lft 57011sec preferred_lft 57011sec
    inet6 fe80::e332:3b3d:9bd7:efef/64 scope link tentative noprefixroute 
       valid_lft forever preferred_lft forever
```

Sur Windows:

```
```

Ce qui donne:

```

```


### ip neighbour / 

Sur Linux:

```
ip neighbour
```

Ce qui donne:

```
10.213.0.219 dev wlp2s0  FAILED
104.199.65.124 dev wlp2s0  FAILED
51.144.164.215 dev wlp2s0  FAILED
35.186.224.40 dev wlp2s0  FAILED
35.186.224.25 dev wlp2s0  FAILED
10.213.255.254 dev enp1s0 lladdr d0:7e:28:2d:84:8c REACHABLE
142.250.200.194 dev wlp2s0  FAILED
151.101.242.248 dev wlp2s0  FAILED
35.186.224.18 dev wlp2s0  FAILED

```

Sur Windows:

```
```

Ce qui donne:

```

```
### ip neighbour flush all	/ 

Sur Linux:

```
ip neighbour flush all
```

Ce qui donne:

```
Rien
```

Sur Windows:

```
```

Ce qui donne:

```
Rien
```
### ip route show/ 

Sur Linux:

```
ip route show
```

Ce qui donne:

```
default via 10.213.255.254 dev enp1s0 proto dhcp metric 100 
default dev wlp2s0 scope link metric 1003 linkdown 
10.213.0.0/16 dev enp1s0 proto kernel scope link src 10.213.0.219 metric 100 
169.254.0.0/16 dev wlp2s0 proto kernel scope link src 169.254.16.188 linkdown 
169.254.0.0/16 dev virbr0 scope link metric 1000 linkdown 
192.168.122.0/24 dev virbr0 proto kernel scope link src 192.168.122.1 linkdown
```

Sur Windows:

```
```

Ce qui donne:

```

```

### ip route add default via @ip_gw dev interface /

Sur Linux:

```
ip route add default via 10.213.0.254 dev enp1s0
```

Ce qui donne:

```
default via 10.213.0.254 dev enp1s0 
default via 10.213.255.254 dev enp1s0 proto dhcp metric 100 
10.213.0.0/16 dev enp1s0 proto kernel scope link src 10.213.0.219 metric 100 
169.254.0.0/16 dev virbr0 scope link metric 1000 linkdown 
192.168.122.0/24 dev virbr0 proto kernel scope link src 192.168.122.1 linkdown 
```

Sur Windows:

```
```

Ce qui donne:

```

```

### ip route add @IP_reseau/masque via @IP_gw dev interface / 

Sur Linux:

```
ip route add 192.168.1.0/24 via 10.213.250.250 dev enp1s0
```

Ce qui donne:

```
default via 10.213.0.254 dev enp1s0 
default via 10.213.255.254 dev enp1s0 proto dhcp metric 100 
10.213.0.0/16 dev enp1s0 proto kernel scope link src 10.213.0.219 metric 100 
169.254.0.0/16 dev virbr0 scope link metric 1000 linkdown 
192.168.1.0/24 via 10.213.250.250 dev enp1s0 
192.168.122.0/24 dev virbr0 proto kernel scope link src 192.168.122.1 linkdown 
```

Sur Windows:

```
```

Ce qui donne:

```

```

### ip route del @IP_reseau/masque via @IP_gw dev interface / 

Sur Linux:

```
sudo ip route del 192.168.1.0/24 via 10.213.250.250 dev enp1s0
```

Ce qui donne:

```
default via 10.213.255.254 dev enp1s0 proto dhcp metric 100 
default dev wlp2s0 scope link metric 1003 linkdown 
10.213.0.0/16 dev enp1s0 proto kernel scope link src 10.213.0.219 metric 100 
169.254.0.0/16 dev wlp2s0 proto kernel scope link src 169.254.16.188 linkdown 
169.254.0.0/16 dev virbr0 scope link metric 1000 linkdown 
192.168.122.0/24 dev virbr0 proto kernel scope link src 192.168.122.1 linkdown 
```

Sur Windows:

```
```

Ce qui donne:

```

```

### ip route flush default dev interface /

Sur Linux:

```
ip route flush default dev enp1s0
```

Ce qui donne:

```
default dev wlp2s0 scope link metric 1003 linkdown 
169.254.0.0/16 dev wlp2s0 proto kernel scope link src 169.254.16.188 linkdown 
169.254.0.0/16 dev virbr0 scope link metric 1000 linkdown 
192.168.122.0/24 dev virbr0 proto kernel scope link src 192.168.122.1 linkdown 
```

Sur Windows:

```
```

Ce qui donne:

```

```

### ip route flush dev interface / 

Sur Linux:

```
ip route flush dev enp1s0
```

Ce qui donne:

```
default dev wlp2s0 scope link metric 1003 linkdown 
169.254.0.0/16 dev wlp2s0 proto kernel scope link src 169.254.16.188 linkdown 
169.254.0.0/16 dev virbr0 scope link metric 1000 linkdown 
192.168.122.0/24 dev virbr0 proto kernel scope link src 192.168.122.1 linkdown 
jojo@PC-Jojo:~$ 

```

Sur Windows:

```
```

Ce qui donne:

```

```

### ping @IP / ping @IP

Sur Linux:

```
```

Ce qui donne:

```
jojo@PC-Jojo:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=110 time=6.85 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=110 time=6.13 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=110 time=6.16 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=110 time=11.1 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=110 time=15.6 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=110 time=5.89 ms
64 bytes from 8.8.8.8: icmp_seq=7 ttl=110 time=6.35 ms
^C
--- 8.8.8.8 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6007ms
rtt min/avg/max/mdev = 5.886/8.296/15.632/3.433 ms
```

Mais il est nécessaire de renseigner un nombre de ping car par défault il est illimité. On fait ainsi avec l'option -c et un argument 3 par exemple: 

```
ip ping 8.8.8.8 -c 3
```

Sur Windows:

```
```

Ce qui donne:

```

```

### traceroute @IP / ping @IP

Sur Linux:

```
traceroute 8.8.8.8

Ce qui donne:

```
jojo@PC-Jojo:~$ traceroute 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  _gateway (10.213.255.254)  4.019 ms  3.937 ms  4.350 ms
 2  gw.iutbeziers.fr (194.199.227.254)  1.776 ms  1.749 ms  1.722 ms
 3  100.75.85.254 (100.75.85.254)  17.434 ms  17.409 ms  17.383 ms
 4  100.74.101.65 (100.74.101.65)  18.004 ms  17.978 ms  17.951 ms
 5  100.75.1.13 (100.75.1.13)  17.924 ms 100.75.1.9 (100.75.1.9)  17.251 ms  17.870 ms
 6  100.77.255.109 (100.77.255.109)  17.757 ms  16.155 ms  16.087 ms
 7  100.77.255.110 (100.77.255.110)  16.679 ms  9.545 ms  9.460 ms
 8  193.55.200.138 (193.55.200.138)  3.506 ms  3.384 ms  3.324 ms
 9  xe-0-0-15-marseille1-rtr-131.noc.renater.fr (193.51.177.138)  5.908 ms xe-0-0-16-ren-nr-marseille1-rtr-131.noc.renater.fr (193.51.180.193)  5.879 ms  5.852 ms
10  xe-0-0-15-marseille2-rtr-131.noc.renater.fr (193.51.180.116)  5.472 ms xe-1-0-10-marseille2-rtr-131.noc.renater.fr (193.51.180.120)  5.800 ms xe-0-0-6-marseille2-rtr-131.noc.renater.fr (193.51.177.185)  5.772 ms
11  72.14.218.132 (72.14.218.132)  5.746 ms  5.718 ms  5.692 ms
12  74.125.244.209 (74.125.244.209)  5.800 ms 108.170.252.241 (108.170.252.241)  6.831 ms  6.575 ms
13  142.251.78.81 (142.251.78.81)  5.719 ms 216.239.35.161 (216.239.35.161)  6.159 ms 142.250.46.97 (142.250.46.97)  6.523 ms
14  dns.google (8.8.8.8)  5.226 ms  5.392 ms  5.361 ms

```

Sur Windows:

```
```

Ce qui donne:

```

```

### cd / cd

Sur Linux:

```
```

Ce qui donne:

```
```

Sur Windows:

```
```

Ce qui donne:

```

```

### mkdir / mkdir

Sur Linux:

```
```

Ce qui donne:

```
```

Sur Windows:

```
```

Ce qui donne:

```

```

### cp / 

Sur Linux:

```
```

Ce qui donne:

```
```

Sur Windows:

```
```

Ce qui donne:

```

```

### rm /

Sur Linux:

```
```

Ce qui donne:

```
```

Sur Windows:

```
```

Ce qui donne:

```

```

### man /

Sur Linux:

```
```

Ce qui donne:

```
```

Sur Windows:

```
```

Ce qui donne:

```

```

### pwd /

Sur Linux:

```
```

Ce qui donne:

```
```

Sur Windows:

```
```

Ce qui donne:

```

```

### cat /

Sur Linux:

```
```

Ce qui donne:

```
```

Sur Windows:

```
```

Ce qui donne:

```

```

### touch /

Sur Linux:

```
```

Ce qui donne:

```
```

Sur Windows:

```
```

Ce qui donne:

```

```

### ls /

Sur Linux:

```
```

Ce qui donne:

```
```

Sur Windows:

```
```

Ce qui donne:

```

```
