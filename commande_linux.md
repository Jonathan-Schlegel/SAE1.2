Guide pratique de l'administrateur réseau
========================================

Ce document à pour but de connaître les commandes réseaux des différents systèmes d'exploitations que sont Linux et Windows.

Voici un bref aperçu de celles-ci dans un tableau:

| Linux              | Racourci         | Windows           |
|--------------------|------------------|-------------------|
|ip addr show        | ip a             | ip config         |
|ip addr add @ip/masque dev interface|ip a a @ip/CIDR dev interface|netsh interface ip set address name="interface" static @ip masque @DNS
|ip addr flush dev reseau|ip a f dev interface|ipconfig/release
|ip addr del @ip dev interface|ip a d @ip interface|
