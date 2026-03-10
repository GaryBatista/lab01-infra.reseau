#### Sommaire
- [Objectifs](#objectifs)
  - [Matériel](#matériel)
- [Paramétrage de la machine virtuelle](#paramétrage-de-la-machine-virtuelle)
- [Installation du système](#installation-du-système)
- [Mise à jour du système](#mise-à-jour-du-système)
- [Installation des différents services](#installation-des-différents-services)
- [Problèmes rencontrés](#problèmes-rencontrés)

## Objectifs

Ce document décrit l’installation de l’environnement nécessaire au lab.
L’objectif est de disposer d’une machine Linux fonctionnelle, accessible en SSH, nmap, Apache et d'autres services servant de base aux manipulations réseau et sécurité.

---
### Matériel

- Hôte : Windows 11
- Hyperviseur : VMware Workstation
- ISO : Ubuntu Server 22.04 LTS
- Accès Internet


## Paramétrage de la machine virtuelle

- Logiciel : VMware Wokstation
- Type : Linux
- Version : Debian 13.3.0
- Mémoire : 2 Go
- CPU : 2 vCPU
- Disque : 20 Go (VDI, allocation dynamique)
- Carte réseau : **Bridge**
  - Ce mode permet ensuite de se connecter à un service Apache à partir de la machien hôte de la VM.


## Installation du système

- Langue : Anglais
- CLI (**sans GNOME ni environnement de bureau**)
- Fuseau horaire : Europe/Paris
- Installation du serveur OpenSSH : Oui

<p align="center">
  <img src="images/VMware.png" width="700">
  <br>
  <em>Installation réussie via VMware</em>
</p>


## Mise à jour du système

```bash
sudo apt update && sudo apt upgrade -y
```
permet de mettre à jour l'OS.

```bash
lsb_release -a
ip a
```
sont des commandes qui respectivements permettent de témoingner de la version de l'OS utilisé, ainsi que de l'adresse IP de la machine virtuelle.


## Installation des différents services

```bash
apt install -y nmap curl git sudo ufw
```
permet d'installer les services suivants :
- nmap 
- curl 
- git 
- sudo
- **ufw**
- **apache2**

Ces services seront utiles dans ce lab ou ultérieurement grâce à des clones de cette machine.

## Problèmes rencontrés

> *Le navigateur n'arrive pas à se connecter au serveur Apache, alors que la commande curl parvient malgré tout à récupérer le contenu HTML.*

La carte réseau était fixée sur **NAT**, et non pas sur **Bridge**.
Le mode Bridge intègre la VM dans le réseau comme étant une machine à part entière, et non plus "cachée" derrière la machine hôte. Une machine configurée en NAT n'accepte pas les connexions entrantes. Une connexion sur le serveur Apache via l'interface web de la machine hôte est voué à l'échec, sauf si du port forwarding est réalisé.