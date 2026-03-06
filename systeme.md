# Permissions
## chmod, chown

chmod et chown valent pour "change mode" et "change owner".
```bash
chmod
```
permet de changer les droits d'accès d'un fichier ou d'un répertoire.

```bash
chown
```
permet de changer le propriétaire d'un fichier ou d'un répertoire. `chown` permet d'avoir un contrôle plus fin, notamment en terme de monitoring : définir et compter plutôt sur les droits d'un propriétaire plutôt que d'un groupe permet d'améliorer la tracabilité des actions.

## "user n'est pas dans le dossier sudoers"

Si l’utilisateur n’est pas dans le groupe `sudo`, il ne peut pas exécuter de commandes avec élévation de privilèges.
```bash
usermod -aG sudo user
``` 
permet de donner les droits d'élévation de privilèges temporaires à user.
- `-a` = append (ne supprime pas les autres groupes)
- `G` = groupes
En utilisant la commande `groups` à la suite, sudo apparait dans la liste de résultats, ce qui indique que le compte user peut utiliser cette commande.

# Processus
### ps

```bash
ps aux
```
permet d'afficher tous les processus en cours.

### top et htop
```bash
top
htop
```
permettent de voir tous les processus en cours, classés en fonction de ceux qui consomment le plus de ressources sur la machine. 
`htop` est un paquet à installer **qui est plus complet et moderne que top.**

<p align="center">
  <img src="images/htop.png" width="700">
  <br>
  <em>Visualisation des processus avec htop</em>
</p>

`ps aux | grep ssh` permet d'afficher uniquement les processus concernant SSH parmis l'entièreté des processus.

#### Verification pratique avec Apache

```bash
ps aux | grep apache2
```

<p align="center">
  <img src="images/psaux-grepapache2.png" width="700">
  <br>
  <em>Affichage des processus contenant "apache2"</em>
</p>

### Kill
`sudo kill <PID>` permet de terminer un service.
`sudo kill -9 <PID>` permet de terminer un service **de force**. Cela implique une potentielle corruption de fichiers, ou une perte de donnnées.

PID
: Processus IDentifier.

