#### Sommaire

- [Installation du service Apache](#installation-du-service-apache)
  - [Vérification de l'activité de Apache](#vérification-de-lactivité-de-apache)
  - [Scan des ports à l'écoute](#scan-des-ports-à-lécoute)
  - [Connexion sur Apache depuis l’hôte](#connexion-sur-apache-depuis-lhôte)


# Installation du service Apache

```bash
sudo apt install apache2
```

Pour se connecter via le navigateur sur la page web Apache, il faut que la VM soit en bridge, que le port 80 soit autorisé par UFW `sudo ufw status verbose`, et que le service soit lancé.


## Vérification de l'activité de Apache

```bash
sudo systemctl status apache2
```
permet de vérifier que le service Apache est bien exécuté.
Le résultat de cette commande est le suivant :

```bash
apache2.service - The Apache HTTP Server
     Loaded: loaded (/usr/lib/systemd/system/apache2.service; enabled; preset: enabled)
     Active: active (running)
```


## Scan des ports à l'écoute
 
```bash
nmap 192.168.1.50 #IP de la VM
```
permet de connaitre les ports et services en écoute. La mention de http sur le port 80 désigne Apache.
Voici le prompt qui en résulte :
```bash
Starting Nmap 7.95 ( https://nmap.org ) at 2026-03-05 15:52 CET
Nmap scan report for masterDeb (192.168.1.50)
Host is up (0.00014s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT     STATE SERVICE
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2222/tcp open  EtherNetIP-1
```


## Connexion sur Apache depuis l’hôte

En entrant l'adresse IP de la VM sur la machine hôte, nous pouvons nous connecter sur la page web gérée par le service Apache.

<p align="center">
  <img src="images/ApacheViaNavigateur.png" width="700">
  <br>
  <em>Connexion sur la page web du service Apache</em>
</p>

```bash
sudo cat /var/log/apache2/access.log
```
 permet d'accéder aux logs d'accès de Apache, comme affichés-ci dessous.


<p align="center">
  <img src="images/LogApache.png" width="700">
  <br>
  <em>Logs d'accès de Apache</em>
</p>