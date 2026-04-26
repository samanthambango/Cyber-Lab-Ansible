# Projet : Automatisation et Sécurisation d'Infrastructure (HomeLab)

Ce projet documente la mise en place d'une architecture réseau virtualisée, segmentée par un pare-feu et automatisée avec Ansible.
## 1. Schéma de l'Architecture

L'infrastructure est isolée dans un réseau interne VirtualBox derrière un **firewall pfSense**.

    [METTRE ICI TON SCHÉMA RÉSEAU (Excalidraw ou autre)]
    ![Schéma Architecture](docs/schema_reseau.png)

Détails des VM :

    Gateway : pfSense (Pare-feu & Routage)

    Contrôleur : SVR-ADMIN (Debian 12) - Nœud de contrôle Ansible

    DMZ : SVR-PROXY (Debian 12) - Reverse Proxy Nginx

    LAN : SVR-WEB-01 (Debian 12) - Serveur d'application isolé

    IAM : SVR-AD-01 (Windows Server 2022) - Active Directory

## 2. Automatisation avec Ansible

Utilisation de l'Infrastructure as Code (IaC) pour déployer les services de manière reproductible.
Tâches réalisées :

    Hardening système (SSH, mises à jour, outils de base).

    Déploiement du serveur Web avec template dynamique Jinja2.

    Configuration du rôle Reverse Proxy sur le nœud frontal.

    [METTRE ICI UNE CAPTURE DE TON TERMINAL APRÈS LE LANCEMENT DU PLAYBOOK (les lignes OK/CHANGED en couleur)]
    ![Console Ansible](docs/capture_ansible.png)

## 3. Sécurisation (Reverse Proxy)

Mise en place d'un Reverse Proxy pour masquer l'infrastructure interne et durcir les échanges HTTP.

    Masquage d'IP : Le serveur web n'est pas accessible directement depuis l'extérieur.

    Headers de sécurité : Ajout de directives X-Frame-Options et X-XSS-Protection.

    [METTRE ICI LA CAPTURE D'ÉCRAN DE TON DASHBOARD FINAL (ton navigateur avec l'IP du Proxy)]
    ![Résultat Dashboard](docs/capture_web.png)

## 4. Structure du dépôt

    ansible/ : Contient les playbooks YAML et l'inventaire des hôtes.

    ansible/templates/ : Fichiers Jinja2 pour la génération de pages dynamiques.

    docs/ : Schémas et preuves de fonctionnement.
