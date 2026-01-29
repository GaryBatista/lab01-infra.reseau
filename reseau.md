À inclure :

- Configuration réseau (NAT, IP)

Commandes utilisées :

- `ip a`
: permet de lister les cartes réseaux et le paramétrage réseau du système
- `ip route`
- `ss -tulpen`
  - permet de lister les ports ouverts et les services en écoute du système. Concernant les paramètres `tulpen`, ils définissent chacun un service.
    - t = TCP
    - u = UDP
    - l = listening
    - p = processus
    - e = inforamtions étendues
    - n = sans résolution DNS

Tests de connectivité

Ouverture des ports

Port | Service | État  | Justification
22   | SSH     | Ouvert| Administration distante
80   | HTTP    | Ouvert| Test de service web
