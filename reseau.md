#### Sommaire
- [Diagnostic réseau](#diagnostic-réseau)
    - [Configuration réseau](#configuration-réseau)
  - [Commandes importantes pour le diagnostic](#commandes-importantes-pour-le-diagnostic)
  - [Tests de connectivité depuis la VM](#tests-de-connectivité-depuis-la-vm)
- [Scan réseau grâce à nmap](#scan-réseau-grâce-à-nmap)


# Diagnostic réseau
### Configuration réseau

Comment mentionné dans le document installation.md, la VM est configurée en **mode Bridge**. 
Cela permet :  
- À la VM d’obtenir une adresse IP sur le même réseau local que l’hôte.  
- À l’hôte et aux autres machines du réseau local d’accéder directement à la VM.  
- De simplifier (/permettre) les tests de services (SSH, HTTP) depuis l’hôte.  

Le mode NAT aurait permis à la VM d’accéder à Internet, mais l’hôte ne peut pas se connecter directement aux services exposés.


## Commandes importantes pour le diagnostic

| Commande | Description |
|----------|-------------|
| `ip a` | Liste les interfaces réseau et leurs adresses IP. |
| `ip route` | Affiche la table de routage, utile pour vérifier la passerelle par défaut. |
| `ss -tulpen` | Liste les ports ouverts et les services en écoute.<br>Paramètres :<br>- t : TCP<br>- u : UDP<br>- l : listening<br>- p : montre le PID et le nom du processus<br>- e : informations étendues<br>- n : sans résolution DNS |
| `ping <IP>` | Teste la connectivité avec une autre machine ou une passerelle. |
| `curl http://<IP>` | Teste l’accès à un service HTTP depuis la VM. |


## Tests de connectivité depuis la VM

`ping 8.8.8.8` vérifie la connexion Internet :
<p align="center">
  <img src="images/ping8888.png" width="700">
  <br>
  <em>`ping 8.8.8.8`</em>
</p>

`ping 192.168.1.1` vérifie la connexion à la passerelle locale. Elle est dans notre cas au début de la plage d'adresses.
<p align="center">
  <img src="images/pingPasserelle.png" width="700">
  <br>
  <em>`ping 192.168.1.1`</em>
</p>

`curl http://192.168.1.50` vérifie que le service Apache répond :
<p align="center">
  <img src="images/curlLocalhost.png" width="700">
  <br>
  <em>`curl http://192.168.1.50`</em>
</p>


# Scan réseau grâce à nmap
 
```bash
nmap 192.168.1.50 #IP de la VM
```
permet de connaitre les ports et services en écoute. La mention de http sur le port 80 désigne Apache.
Voici le prompt qui en résulte :
```bash
Starting Nmap 7.95 ( https://nmap.org ) at 2026-03-11 22:43 CET
Nmap scan report for masterDeb (192.168.1.50)
Host is up (0.000093s latency).
Not shown: 998 closed tcp ports (conn-refused)
PORT     STATE SERVICE
80/tcp   open  http
2222/tcp open  EtherNetIP-1
```

Le scan Nmap montre que l’hôte 192.168.1.50 est actif sur le réseau et expose 2 ports TCP ouverts. (`nmap scan report for masterDeb (192.168.1.50)`)

`Not shown: 998 closed tcp ports (conn-refused)` indique que la grande majorité des ports (998) sont fermés, ce qui signifie que les connexions sont refusées.

`80/tcp   open  http` désigne le port correspondant au service web HTTP. Il est utilisé ici par Apache2. 
Cela permet :
- d’héberger un site web,
- de tester les logs Apache,
- d’observer les connexions dans access.log.

`2222/tcp open  EtherNetIP-1` correspond au port SSH que j'ai modifié en amont. 



