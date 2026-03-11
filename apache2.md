#### Sommaire
- [Vérification de l'activité de Apache](#vérification-de-lactivité-de-apache)
- [Connexion sur Apache depuis l’hôte](#connexion-sur-apache-depuis-lhôte)



#### Objectifs 


---

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


## Connexion sur Apache depuis l’hôte

Pour se connecter via le navigateur sur la page web Apache, il faut :
- que la VM soit en bridge, 
- que le port 80 soit autorisé par UFW `sudo ufw status verbose`, 
- et que le service soit lancé.

En entrant l'adresse IP de la VM sur la machine hôte, nous pouvons nous connecter sur la page web gérée par le service Apache.

<p align="center">
  <img src="images/ApacheViaNavigateur.png" width="700">
  <br>
  <em>Connexion sur la page web du service Apache</em>
</p>

