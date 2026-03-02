Chaque action a été realisé dans l'ordre d'écriture du document. 

### Désactiver la connexion de root en SSH

L’accès SSH direct au compte `root` a été désactivé afin de réduire la surface d’attaque et d’améliorer la traçabilité des actions d’administration. Il faut utiliser la commande suivante pour parvenir à cela :
`sudo nano /etc/ssh/sshd_config`

puis rechercher la ligne PermitRootLogin, et lui indiquer le paramètre `no` de cette manière :
`PermitRootLogin no`

A chaque tentative de connexion en SSH via le compte de root, la permission sera refusée.

## Changement de port SSH 

Avec la commande `sudo nano /etc/ssh/sshd_config`, il faut remplacer le `Port 22` par un port choisi soi-même. J'ai décidé de prendre 2222. J'ai décommenté la ligne, et modifié le port. 

Note : c'est dans ce fichier que l'on paramètre la permission de connexion en root via SSH.

Après redémarrage du service, via la commande `sudo systemctl restart ssh`, on peut vérifier la réussite du processus en utilisant la commande : 
`ss -tulpen | grep ssh`
où l'on témoigne que le résultat passe de :
`LISTEN 0 128 0.0.0.0:22` -> `LISTEN 0 128 0.0.0.0:2222`.



## UFW
### Installation et configuration de UFW
`sudo apt install ufw`  permet d'installer UFW
`sudo ufw default deny incoming` permet de renseigner la règle selon laquelle le trafic entrant est filtré par UFW, sauf contre-indication.
`sudo ufw default allow outgoing` permet de renseigner une seconde règle, définissant que le trafic sortant est autorisé par UFW.
`sudo ufw allow 2222/tcp` permet d'autoriser la connexion en SSH sur ce port, précédemment défini sur 2222.
`sudo ufw enable` permet d'activer le service et de mettre en rigueur les règles précédemment définies.
`sudo ufw status numbered` permet d'assigner des numéros aux règles définies.

### Explication de la commande "ufw status numbered"

```bash
sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
2222/tcp                   ALLOW IN    Anywhere
2222/tcp (v6)              ALLOW IN    Anywhere (v6)
```

Logging: on (low)
: Le pare feu est actif; "low" désigne le fait que le journal tenu est de faible intensité, si l'on peut définir cela ainsi. Les paramètres medium, high et full sont des paramètres respectivement qui journalisent plus mais qui sont plus lourds. Low convient très bine pour une surveillance strandard, et notamment pour un lab comme le notre.

Default: deny (incoming), allow (outgoing)
: Les règles par défault ajoutées précédemment.

2222/tcp ALLOW IN Anywhere
: Seul SSH est autorisé, sur le port qui a été modifié.

Tous les autres ports sont bloqués, ce qui est la bonne pratique conformément au principe du moindre privilège.


### Où vérifier les tentatives de connexion