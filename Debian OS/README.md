# Debian OS - réseau et SSH

## Objectif

J’ai installé Debian dans VMware et configuré le réseau pour pouvoir communiquer avec une autre machine virtuelle.

## Configuration réseau

L’interface réseau utilisée est `ens33`.

Debian a reçu une adresse IPv4 avec DHCP :

```text
192.168.39.129/24
```

La machine utilise le réseau NAT de VMware.

## Vérification du réseau

J’ai utilisé :

```bash
ip a
```

pour vérifier l’adresse IP et l’état de l’interface réseau.

## Service SSH

J’ai vérifié que le serveur SSH était actif avec :

```bash
systemctl status ssh
```

Le service était :

```text
active (running)
```

## Vérification du port SSH

J’ai utilisé :

```bash
sudo ss -tulpn | grep :22
```

pour vérifier que le port `22` était en écoute.

Le port `22/TCP` est utilisé par SSH.

## Test de connexion SSH

Depuis Parrot OS, j’ai testé une connexion SSH vers Debian avec :

```bash
ssh ninar@192.168.39.129
```

La connexion a fonctionné correctement.

## Ce que j’ai appris

- vérifier une adresse IP sous Linux ;
- comprendre le rôle de DHCP ;
- vérifier l’état d’un service avec `systemctl` ;
- vérifier un port avec `ss` ;
- utiliser SSH entre deux machines Linux.