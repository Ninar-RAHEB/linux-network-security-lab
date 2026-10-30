# Linux Network Security Lab

Projet personnel réalisé avec deux machines virtuelles Linux sous VMware :

- Debian
- Parrot OS

L’objectif est de créer un petit laboratoire réseau pour pratiquer Linux, SSH, Nmap, Wireshark et la sécurisation d’un serveur Debian.

## Réseau

Les deux machines utilisent le même réseau NAT VMware :

- Debian : `192.168.39.129`
- Parrot OS : `192.168.39.130`

## Travail réalisé

- installation et configuration de Debian et Parrot OS ;
- configuration du réseau entre les deux machines ;
- test de connexion avec `ping` ;
- connexion SSH de Parrot vers Debian ;
- scan des ports et services avec Nmap ;
- désactivation de la connexion SSH directe de root ;
- configuration du pare-feu UFW ;
- comparaison des scans Nmap avant et après sécurisation ;
- analyse du trafic SSH avec Wireshark.

## Organisation

### Debian OS

Configuration réseau et mise en place du serveur SSH.

### Parrot OS

Tests réseau, scans Nmap, sécurisation de Debian et analyse Wireshark.

## Outils utilisés

- VMware Workstation
- Debian
- Parrot OS
- SSH
- Nmap
- Wireshark
- UFW
- Git / GitHub