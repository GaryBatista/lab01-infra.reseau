## Objectif 
Ce document décrit l’installation de l’environnement nécessaire au lab
L’objectif est de disposer d’une machine Linux fonctionnelle, accessible en SSH, servant de base aux manipulations réseau et sécurité.

### Matériel

- Hôte : Windows 11
- Hyperviseur : VMware Workstation
- ISO : Ubuntu Server 22.04 LTS
- Accès Internet

## Création de la machine virtuelle

- Type : Linux
- Version : Ubuntu (64-bit)
- Mémoire : 2 Go
- CPU : 2 vCPU
- Disque : 20 Go (VDI, allocation dynamique)
- Carte réseau : NAT
Le mode NAT permet à la VM d’accéder à Internet tout en restant isolée du réseau local.

## Installation du système

- Langue : Anglais
- Installation minimale
- Fuseau horaire : Europe/Paris
- Création d’un utilisateur non-root
- Installation du serveur OpenSSH : Oui

![Installation réussie via VMware](images\VMware.png)

## Mise à jour du système

`sudo apt update && sudo apt upgrade -y`


## Vérifications

- Version du système :
`lsb_release -a`
`ip a`


## Problèmes rencontrés

## Difficultés rencontrées


## Conclusion
