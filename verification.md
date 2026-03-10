- [x] compte root désactivé
- [x] connexion en root via SSH désactivée
- [x] port 22 > port 2222
  - [x] SSH okay
- [x] Installation de Apache faite
  - [x] port 80 accessible
- [x] UFW installé
  - [x] Ports non nécessaires fermés  
  - [x] Firewall activé 

- [ ] Expliquer les différences entre journalctl et les logs classiques (/var/log).

Permissions

- [ ] Ajouter exemples pratiques pour chmod et chown sur fichiers et dossiers (par exemple Apache ou dossier utilisateur).

- [ ] Vérifier les permissions des fichiers critiques (ex : /etc/ssh/sshd_config).

RESEAU.MD

Tu viens de l’avoir réécrit, mais assure-toi que :

- [x] Les tests ping/curl/SSH depuis l’hôte et la VM sont inclus.

- [x] Explication du choix Bridge vs NAT est claire (tu l’as fait).

INSTALLATION.MD

- [ ] Expliquer clairement le problème du navigateur avec Apache quand NAT était utilisé, et comment Bridge corrige ça.
- [ ] Vérifier que toutes les captures d’écran sont présentes et accessibles.
SECURITE.MD

- [ ] Tu peux ajouter une mini-section sur fail2ban si tu veux montrer comment limiter les tentatives SSH échouées. Ce n’est pas obligatoire, mais c’est un bon complément sécurité pour un lab.

SERVICES.MD

- [x] Supprimer Nginx si non utilisé.

- [ ] Ajouter petit rappel : après chaque installation, vérifier le service (systemctl status) et le port (ss -tulpen ou nmap).

VERIFICATION.MD

Ajouter une vérification finale :

- [x] sudo ufw status verbose pour confirmer que seules les règles voulues sont actives.

- [x] Test final SSH + HTTP depuis l’hôte pour s’assurer que tout fonctionne après toutes les configurations.

2️⃣ Points techniques à vérifier pour la complétude

- [ ] Les droits sudo pour ton utilisateur (groups) sont bien appliqués.

- [ ] Les logs Apache et journaux SSH montrent bien ce que tu attends.

- [x] Tous les ports inutiles sont fermés par UFW.

- [x] Les services critiques sont actifs (Apache, SSH).

- [x] Les images et captures sont à jour et bien nommées.