# 🛡️ Network Security & Automation Lab

Ce projet présente l'automatisation et la sécurisation d'une infrastructure réseau virtualisée via **Ansible**. L'objectif est de démontrer la mise en place d'une architecture résiliente, segmentée et protégée par un Reverse Proxy.

##  Architecture du Réseau
L'infrastructure est déployée sur **VirtualBox** avec une segmentation réseau via **pfSense**.

* **SVR-ADMIN** : Station d'administration et nœud de contrôle Ansible.
* **SVR-PROXY** : Reverse Proxy Nginx agissant comme unique point d'entrée (DMZ).
* **SVR-WEB-01** : Serveur d'application isolé du flux internet direct.
* **SVR-AD-01** : Contrôleur de domaine Active Directory pour la gestion des identités.

---

##  Fonctionnalités Clés

###  Sécurité Offensive & Défensive
* **Masquage d'Infrastructure** : Le serveur web est invisible depuis l'extérieur ; seul le Proxy est exposé.
* **Hardening Nginx** : Implémentation de headers de sécurité (`X-Frame-Options`, `X-XSS-Protection`) via Ansible.
* **Segmentation Réseau** : Configuration de règles de pare-feu pour limiter les déplacements latéraux.

###  Automatisation (Infrastructure as Code)
* **Déploiement Idempotent** : Configuration reproductible des serveurs Linux (Debian/Ubuntu).
* **Dynamic Templating** : Utilisation de **Jinja2** pour générer des tableaux de bord d'état système en temps réel.
* **Gestion des Clés SSH** : Automatisation de la confiance entre le nœud d'administration et les serveurs.

---

##  Aperçu des Playbooks
* `deploy_web.yml` : Installation de Nginx et déploiement du tableau de bord personnalisé.
* `deploy_proxy.yml` : Configuration du rôle Reverse Proxy et durcissement des politiques HTTP.

##  Résultats obtenus
Le système permet de servir du contenu dynamique tout en protégeant l'identité du serveur source. En cas de compromission du Proxy, le serveur web reste protégé derrière les règles de filtrage internes.
