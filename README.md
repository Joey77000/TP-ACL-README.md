# TP-ACL-README.md
# TP ACL – Filtrage du trafic réseau

## Objectif

Mettre en place des ACL sur un routeur Cisco afin de contrôler les communications réseau.

## Contexte

Les ACL permettent d’autoriser ou de bloquer certains flux selon l’adresse IP source, l’adresse IP destination, le protocole ou le port.

Elles sont utilisées pour sécuriser les accès et limiter les communications non autorisées.

## Exemple de besoin

Autoriser le LAN à accéder au Web, mais bloquer tout le reste.

## Commandes principales

```bash
ip access-list extended ACL_LAN_IN
 permit tcp 192.168.1.0 0.0.0.255 any eq 80
 permit tcp 192.168.1.0 0.0.0.255 any eq 443
 permit icmp 192.168.1.0 0.0.0.255 any echo
 deny ip any any log

interface GigabitEthernet0/0
 ip access-group ACL_LAN_IN in
