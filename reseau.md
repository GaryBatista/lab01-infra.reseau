# Bases Réseau

## Introduction

Ce document présente les fondamentaux des réseaux informatiques nécessaires à la compréhension des environnements systèmes et de la cybersécurité. Il sert à la fois de support théorique et de référence pour les labs pratiques présents dans ce dépôt.

L’objectif n’est pas d’être exhaustif, mais de poser des bases solides et opérationnelles, utiles en administration système, réseau et sécurité.

## Modèles OSI et TCP/IP

### Modèle OSI (7 couches)

Le modèle OSI est un modèle conceptuel qui permet de décomposer les communications réseau en 7 couches distinctes, afin de faciliter la compréhension, le dépannage et la conception des réseaux.

1. **Physique** : transmission électrique ou radio (câbles, ondes, connecteurs)
2. **Liaison de données** : communication locale, adresses MAC (switch)
3. **Réseau** : routage des paquets, adresses IP (routeur)
4. **Transport** : fiabilité et ports (TCP, UDP)
5. **Session** : gestion des sessions de communication
6. **Présentation** : format des données, chiffrement
7. **Application** : services utilisés par l’utilisateur (HTTP, FTP, DNS…)

Ce modèle est très utilisé en cybersécurité pour localiser précisément une attaque ou un dysfonctionnement.

### Modèle TCP/IP

Le modèle TCP/IP est plus pragmatique et utilisé dans les réseaux réels (Internet).

* Application
* Transport
* Internet
* Accès réseau

Il regroupe certaines couches du modèle OSI mais repose sur les mêmes principes.

---

## Adressage IP

### IPv4

Une adresse IPv4 est composée de 4 octets (32 bits), par exemple :

```
192.168.1.10
```

Elle est divisée en deux parties :

* la partie **réseau**
* la partie **hôte**

### Masque de sous-réseau et CIDR

Le masque de sous-réseau permet de déterminer quelle partie de l’adresse identifie le réseau.

Exemple :

```
192.168.1.0/24
```

* Réseau : 192.168.1.0
* Broadcast : 192.168.1.255
* Plage utilisable : 192.168.1.1 à 192.168.1.254

### Adresses privées et publiques

Les adresses privées sont utilisées dans les réseaux locaux et ne sont pas routables sur Internet.

Plages privées principales :

* 10.0.0.0/8
* 172.16.0.0/12
* 192.168.0.0/16

### Loopback

L’adresse `127.0.0.1` permet à une machine de communiquer avec elle-même. Elle est utilisée pour les tests et les services locaux.

---

## DHCP

Le **DHCP (Dynamic Host Configuration Protocol)** permet d’attribuer automatiquement les paramètres réseau aux machines clientes.

Paramètres fournis :

* Adresse IP
* Masque de sous-réseau
* Passerelle par défaut
* Serveur DNS

### Fonctionnement (DORA)

1. **Discover** : le client cherche un serveur DHCP
2. **Offer** : le serveur propose une configuration
3. **Request** : le client accepte l’offre
4. **Acknowledge** : le serveur confirme

En entreprise, le DHCP est essentiel pour centraliser la gestion réseau. En cybersécurité, un serveur DHCP mal contrôlé peut être exploité (DHCP rogue).

---

## DNS

Le **DNS (Domain Name System)** permet de traduire un nom de domaine en adresse IP.

Exemple :

```
www.example.com → 93.184.216.34
```

### Types de serveurs DNS

* **Récursif** : interroge d’autres serveurs pour obtenir la réponse
* **Autoritaire** : détient l’information officielle d’un domaine

### DNS et Active Directory

Active Directory repose entièrement sur le DNS pour :

* la localisation des contrôleurs de domaine
* l’authentification
* la réplication

Sans DNS fonctionnel, un domaine Active Directory est inutilisable.

---

## Équipements réseau

* **Hub** : répète les trames sur tous les ports (obsolète)
* **Switch** : communication locale basée sur les adresses MAC (couche 2)
* **Routeur** : interconnexion de réseaux IP (couche 3)
* **Firewall** : filtrage du trafic selon des règles
* **Point d’accès Wi-Fi** : accès réseau sans fil

---

## Protocoles essentiels

### TCP et UDP

* **TCP** : fiable, orienté connexion, contrôle des erreurs
* **UDP** : rapide, sans connexion, pas de garantie de livraison

### Autres protocoles courants

* **HTTP / HTTPS** : communication web
* **ICMP** : messages de contrôle (ping)
* **ARP** : résolution IP → MAC

ICMP est souvent filtré pour limiter la reconnaissance réseau.

---

## Lien avec la cybersécurité

La compréhension des réseaux est indispensable en cybersécurité, notamment pour :

* l’analyse du trafic
* le scan de réseaux (ex : Nmap)
* la segmentation réseau
* la mise en place de règles firewall

Ces notions sont mises en pratique dans les labs associés à ce dépôt.

---

## Labs associés

* Découverte d’un réseau local avec Nmap
* Analyse des services exposés
* Configuration réseau sous Linux
