## Gestion des utilisateurs et groupes
### "user n'est pas dans le dossier sudoers"

`usermod -aG sudo user` permet de donner les droits d'élévation de privilèges temporaires à user
- `-a` = append (ne supprime pas les autres groupes)
- `G` = groupes

### Permissions (chmod, chown)
chmod et chown valent pour "change mode" et "change owner".
`chmod` permet de changer les droits d'accès d'un fichier ou d'un répertoire.
`chown` permet de changer le propriétaire d'un ficheir ou d'un répertoire.


### Services (systemctl status)
CF securite.md



### Processus (ps, top)

### Logs (/var/log/auth.log)

Ce fichier n'existe pas initialement.