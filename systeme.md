À inclure :

## Gestion des utilisateurs / groupes

### "user n'est pas dans le dossier sudoers"

`su -`
(le tiret permet une connexion complète de root)

`usermod -aG sudo user`



Fonctionnnement de usermod :
[...]
Dans la commande précédente :

- `-a` = append (ne supprime pas les autres groupes)
- `G` = groupes

---




### Permissions (chmod, chown)

### Services (systemctl status)

### Processus (ps, top)

### Logs (/var/log/auth.log)