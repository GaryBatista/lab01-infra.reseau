#### Sommaire
- [Lab 01 — Infrastructure \& Réseaux](#lab-01--infrastructure--réseaux)
  - [Objectifs](#objectifs)
  - [Architecture du lab01](#architecture-du-lab01)
    - [Les axes principaux du lab](#les-axes-principaux-du-lab)


# Lab 01 — Infrastructure & Réseaux
## Objectifs

Ce premier laboratoire a pour objectif de mettre en place un environnement de travail virtualisé et d'explorer les bases d'un système Linux dans une perspective de cybersécurité.

L'objectif est de comprendre :
- les fondamentaux Linux
- l'installation et l'analyse d'un service réseau
- l'observation des processus et logs système
- la découverte réseau à l'aide d'outils de scan

Ce laboratoire constitue la base des labs suivants, notamment l'implémentation d'une infrastructure Active Directory et l'analyse de sécurité.

Les VM utilisés ici dans les labs sont des clones de VM master. Les configurations indiquées valent également pour les clones.

## Architecture du lab01

Host Machine
      │
VirtualBox
      │
Ubuntu VM
      │
Apache Web Server


### Les axes principaux du lab

1. Exploration du système Linux grâce aux commandes `ls`, `tree` (je ne mentionnerai pas ou peu `cd` ou `find`).
2. Observation de l'activité du système grâce aux commandes `ps` et `htop`.
3. Gestion des permissions grâce à `chmod`, `chown`, `usermod`




