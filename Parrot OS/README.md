# Parrot OS - analyse réseau et sécurisation de Debian

## Objectif

J’ai utilisé Parrot OS pour analyser une machine Debian sur le même réseau VMware.

## Environnement

- Parrot OS : machine d’analyse
- Debian : machine cible
- Réseau VMware : NAT
- Parrot : `192.168.39.130`
- Debian : `192.168.39.129`

## Test de connexion

J’ai vérifié la communication entre Parrot et Debian avec `ping`.

## Scan avec Nmap

Avant la sécurisation, j’ai lancé :

```bash
nmap -sV 192.168.39.129
```

Résultat principal :

```text
22/tcp open ssh OpenSSH 10.0p2
999 ports TCP fermés
```

## Connexion SSH

Depuis Parrot, je me suis connectée à Debian avec :

```bash
ssh ninar@192.168.39.129
```

Sur Debian, j’ai vérifié la connexion avec :

```bash
ss -tn | grep :22
```

## Sécurisation SSH

J’ai désactivé la connexion SSH directe avec le compte root :

```text
PermitRootLogin no
```

Avant d’appliquer la configuration, j’ai vérifié qu’il n’y avait pas d’erreur avec :

```bash
sudo sshd -t
```

## Pare-feu UFW

J’ai activé UFW sur Debian.

Configuration :

- connexions entrantes bloquées par défaut ;
- connexions sortantes autorisées ;
- port `22/TCP` autorisé pour SSH.

## Scan après sécurisation

Après l’activation du pare-feu, j’ai lancé :

```bash
nmap -Pn -sV 192.168.39.129
```

Résultat :

```text
22/tcp open ssh
999 ports TCP filtered
```

Le port SSH reste accessible et les autres ports sont filtrés par le pare-feu.

## Analyse avec Wireshark

J’ai observé la connexion SSH entre Parrot et Debian avec Wireshark.

Filtre utilisé :

```text
tcp.port == 22
```

J’ai identifié :

- le handshake TCP : SYN, SYN/ACK, ACK ;
- le début de la connexion SSH ;
- l’échange de clés ;
- le trafic chiffré.

## Ce que j’ai appris

- utiliser Nmap pour scanner des ports ;
- utiliser SSH entre deux machines Linux ;
- vérifier une connexion TCP ;
- sécuriser SSH ;
- configurer UFW ;
- comparer un scan avant et après sécurisation ;
- analyser une connexion SSH avec Wireshark.