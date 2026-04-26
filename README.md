## Infrastructure Automation & Security Lab

Ce dépôt contient les scripts d'automatisation Ansible utilisés pour déployer et sécuriser mon infrastructure réseau personnelle (HomeLab). L'objectif est de simuler un environnement d'entreprise robuste en isolant les services et en centralisant l'administration.
Architecture du Lab

L'infrastructure est virtualisée sous VirtualBox et segmentée derrière un firewall **pfSense**.

    SVR-ADMIN (Debian) : Centre de contrôle Ansible.

    SVR-PROXY (Debian) : Reverse Proxy Nginx (Point d'entrée unique).

    SVR-WEB-01 (Debian) : Serveur d'application (Isolé du flux direct).

    SVR-AD-01 (Windows Server 2022) : Contrôleur de domaine Active Directory.

## Fonctionnalités implémentées
**1. Automatisation via Ansible**

    Hardening Système : Mise à jour automatique, configuration SSH sécurisée (désactivation du login root), et installation d'outils de monitoring.

    Déploiement Dynamique : Utilisation de templates Jinja2 pour générer des rapports d'état serveur en temps réel.

    Idempotence : Scripts conçus pour garantir un état système stable et reproductible.

**2. Sécurité Réseau & Reverse Proxy**

    Masquage d'Infrastructure : Le serveur web est dissimulé derrière un Reverse Proxy Nginx.

    Sécurisation des Headers : Implémentation de directives de sécurité (X-Frame-Options, X-XSS-Protection) pour prévenir les attaques de type Clickjacking et XSS.

    Segmentation : Flux réseau contrôlés pour limiter la surface d'attaque.
