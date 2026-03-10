#### Sommaire
- [Configuration réseau](#configuration-réseau)
- [Commandes utiles pour le diagnostic réseau](#commandes-utiles-pour-le-diagnostic-réseau)
- [Tests de connectivité depuis la VM](#tests-de-connectivité-depuis-la-vm)

# Configuration réseau

La VM est configurée en **mode Bridge**. Cela permet :  
- À la VM d’obtenir une adresse IP sur le même réseau local que l’hôte.  
- À l’hôte et aux autres machines du réseau local d’accéder directement à la VM.  
- De simplifier (/permettre) les tests de services (SSH, HTTP) depuis l’hôte.  

> Le mode NAT aurait permis à la VM d’accéder à Internet, mais l’hôte ne peut pas se connecter directement aux services exposés.


# Commandes utiles pour le diagnostic réseau

| Commande | Description |
|----------|-------------|
| `ip a` | Liste les interfaces réseau et leurs adresses IP. |
| `ip route` | Affiche la table de routage, utile pour vérifier la passerelle par défaut. |
| `ss -tulpen` | Liste les ports ouverts et les services en écoute.<br>Paramètres :<br>- t : TCP<br>- u : UDP<br>- l : listening<br>- p : montre le PID et le nom du processus<br>- e : informations étendues<br>- n : sans résolution DNS |
| `ping <IP>` | Teste la connectivité avec une autre machine ou une passerelle. |
| `curl http://<IP>` | Teste l’accès à un service HTTP depuis la VM. |


# Tests de connectivité depuis la VM

`ping 8.8.8.8` vérifie la connexion Internet
`ping 192.168.1.1` vérifie la connexion à la passerelle locale
`curl http://192.168.1.50` vérifie que le service Apache répond.
