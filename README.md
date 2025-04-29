# Projet Linux : Infrastructure de fichiers sécurisée avec Samba, LDAP et sauvegarde

Ce projet simule une infrastructure de fichiers d’entreprise composée de **4 machines virtuelles** sous Linux et Windows. Il met en œuvre des services essentiels pour une gestion efficace, centralisée et sécurisée des utilisateurs et des fichiers : annuaire LDAP, serveur Samba, quotas disques, sauvegardes automatiques, et test d’accès depuis un client Windows.

## Contexte

Dans un environnement professionnel, la gestion centralisée des utilisateurs et des ressources partagées est une nécessité. Ce projet a été conçu pour reproduire un cas d’usage concret en entreprise, tout en s’appuyant exclusivement sur des technologies open source.

## Objectifs

- Déployer une **infrastructure multi-serveurs réaliste** sous Linux.
- Centraliser les comptes utilisateurs avec **OpenLDAP**.
- Gérer des **partages de fichiers sécurisés** via **Samba**.
- Appliquer des **quotas disque** par utilisateur.
- Mettre en place une **sauvegarde automatique** quotidienne.
- Vérifier l’interopérabilité avec un **poste client Windows**.

## Architecture

| VM      | Rôle                  | OS         | Description                                 |
| ------- | --------------------- | ---------- | ------------------------------------------- |
| **VM1** | Serveur LDAP          | Debian 12  | Gère les utilisateurs et groupes            |
| **VM2** | Serveur Samba         | Debian 12  | Partages réseau sécurisés (connecté à LDAP) |
| **VM3** | Serveur de sauvegarde | Debian 12  | Réception des sauvegardes via `rsync`       |
| **VM4** | Poste client          | Windows 10 | Test des accès Samba avec comptes LDAP      |

Toutes les VMs sont interconnectées sur un **réseau interne VirtualBox** (192.168.100.0/24).

## Mise en œuvre

1. **Installation et configuration de OpenLDAP** avec arborescence `dc=entreprise,dc=local`.
2. **Création d'utilisateurs et de groupes LDAP** (RH, IT...).
3. **Installation de Samba** avec liaison à LDAP via PAM/NSS.
4. **Création de partages** Samba avec droits d'accès selon les groupes.
5. **Activation des quotas disques** (1 Go max par utilisateur).
6. **Rédaction d'un script de sauvegarde `rsync`**, lancé chaque nuit via `cron`.
7. **Test des accès depuis le poste Windows** : mappage des partages, tests de droits et quotas.

## Technologies utilisées

- **Debian 12**
- **OpenLDAP**
- **Samba**
- **rsync + cron**
- **quota**
- **Windows 10**
- **VmWare (réseau interne)**

## Résultats obtenus

- Authentification LDAP fonctionnelle via Samba
- Droits d’accès appliqués avec précision selon les groupes
- Blocage automatique des utilisateurs en dépassement de quota
- Sauvegarde automatisée transférée chaque nuit
- Accès aux partages validé depuis un poste Windows

## Pistes d'amélioration

- Ajout d’une interface Web d’administration (Webmin, Cockpit)
- Intégration d’un outil de supervision système (Netdata, Grafana)
- Automatisation du déploiement via **Ansible**
- Intégration à un Active Directory existant

## Auteur

Projet réalisé par **Marc.Khamchanh**
Avril 2025 – Dans le cadre d’un projet personnel en administration système et réseau.

# Projet Linux : Infrastructure de fichiers sécurisée avec Samba, LDAP et sauvegarde

Ce projet simule une infrastructure de fichiers d’entreprise composée de **4 machines virtuelles** sous Linux et Windows. Il met en œuvre des services essentiels pour une gestion efficace, centralisée et sécurisée des utilisateurs et des fichiers : annuaire LDAP, serveur Samba, quotas disques, sauvegardes automatiques, et test d’accès depuis un client Windows.

## Contexte

Dans un environnement professionnel, la gestion centralisée des utilisateurs et des ressources partagées est une nécessité. Ce projet a été conçu pour reproduire un cas d’usage concret en entreprise, tout en s’appuyant exclusivement sur des technologies open source.

## Objectifs

- Déployer une **infrastructure multi-serveurs réaliste** sous Linux.
- Centraliser les comptes utilisateurs avec **OpenLDAP**.
- Gérer des **partages de fichiers sécurisés** via **Samba**.
- Appliquer des **quotas disque** par utilisateur.
- Mettre en place une **sauvegarde automatique** quotidienne.
- Vérifier l’interopérabilité avec un **poste client Windows**.

## Architecture

| VM      | Rôle                  | OS         | Description                                 |
| ------- | --------------------- | ---------- | ------------------------------------------- |
| **VM1** | Serveur LDAP          | Debian 12  | Gère les utilisateurs et groupes            |
| **VM2** | Serveur Samba         | Debian 12  | Partages réseau sécurisés (connecté à LDAP) |
| **VM3** | Serveur de sauvegarde | Debian 12  | Réception des sauvegardes via `rsync`       |
| **VM4** | Poste client          | Windows 10 | Test des accès Samba avec comptes LDAP      |

Toutes les VMs sont interconnectées sur un **réseau interne VirtualBox** (192.168.100.0/24).

## Mise en œuvre

1. **Installation et configuration de OpenLDAP** avec arborescence `dc=entreprise,dc=local`.
2. **Création d'utilisateurs et de groupes LDAP** (RH, IT...).
3. **Installation de Samba** avec liaison à LDAP via PAM/NSS.
4. **Création de partages** Samba avec droits d'accès selon les groupes.
5. **Activation des quotas disques** (1 Go max par utilisateur).
6. **Rédaction d'un script de sauvegarde `rsync`**, lancé chaque nuit via `cron`.
7. **Test des accès depuis le poste Windows** : mappage des partages, tests de droits et quotas.

## Technologies utilisées

- **Debian 12**
- **OpenLDAP**
- **Samba**
- **rsync + cron**
- **quota**
- **Windows 10**
- **VmWare (réseau interne)**

## Résultats obtenus

- Authentification LDAP fonctionnelle via Samba
- Droits d’accès appliqués avec précision selon les groupes
- Blocage automatique des utilisateurs en dépassement de quota
- Sauvegarde automatisée transférée chaque nuit
- Accès aux partages validé depuis un poste Windows

## Pistes d'amélioration

- Ajout d’une interface Web d’administration (Webmin, Cockpit)
- Intégration d’un outil de supervision système (Netdata, Grafana)
- Automatisation du déploiement via **Ansible**
- Intégration à un Active Directory existant

## Auteur

Projet réalisé par **Marc.Khamchanh**
Avril 2025 – Dans le cadre d’un projet personnel en administration système et réseau.
