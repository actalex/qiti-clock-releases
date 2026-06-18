# QiTi Clock — Guide Utilisateur

> Documentation officielle du firmware QiTi Clock.
> Contact support : support@gatto.fr

---

## Table des matières

1. [Prise en main](#1-prise-en-main)
2. [Connexion Wi-Fi](#2-connexion-wi-fi)
3. [Mise à jour firmware (OTA)](#3-mise-à-jour-firmware-ota)
4. [Modèles d'affichage](#4-modèles-daffichage)
5. [Alarmes](#5-alarmes)
6. [Paramètres système](#6-paramètres-système)
7. [Réinitialisation usine](#7-réinitialisation-usine)
8. [Dépannage](#8-dépannage)
9. [Support](#9-support)

---

## 1. Prise en main

### Premier démarrage

À la première mise sous tension, le QiTi Clock démarre en **mode Point d'Accès (AP)** :

1. Repérez le réseau Wi-Fi `QiTi_XXYYZZ` (les 6 caractères correspondent au suffixe MAC de votre appareil).
2. Connectez-vous à ce réseau depuis votre téléphone ou ordinateur.
3. Ouvrez un navigateur et accédez à [http://192.168.4.1](http://192.168.4.1).
4. L'interface de configuration s'affiche.

### Navigation dans l'interface

L'interface embarquée comporte plusieurs onglets :

| Onglet | Description |
|--------|-------------|
| Horloge | Vue principale — heure, modèle actif |
| Paramètres | Configuration Wi-Fi, modèle, alarmes, système |
| ? | Cette aide |

---

## 2. Connexion Wi-Fi

### Se connecter à un réseau existant

1. Onglet **Paramètres** → section **Réseau**.
2. Cliquez sur **Scanner les réseaux** pour lister les réseaux disponibles.
3. Sélectionnez votre réseau et entrez le mot de passe.
4. Cliquez sur **Connecter**.

L'appareil redémarre et se connecte à votre réseau. Une fois connecté, il est accessible via son nom d'hôte `QiTi_XXYYZZ.local` ou via l'adresse IP attribuée par votre box (visible dans les paramètres réseau de votre box).

### Mode AP (Point d'Accès)

Si la connexion Wi-Fi échoue ou si l'appareil n'a pas encore été configuré, il reste accessible en mode AP (`QiTi_XXYYZZ` / IP : `192.168.4.1`).

---

## 3. Mise à jour firmware (OTA)

Les mises à jour sont distribuées via GitHub Releases et peuvent être installées directement depuis l'interface.

### Mise à jour depuis l'interface

1. Onglet **Paramètres** → section **Système** → bouton **Vérifier les mises à jour**.
2. Si une mise à jour est disponible, une fenêtre de confirmation s'affiche avec la version cible.
3. Cliquez sur **Mettre à jour** pour lancer le téléchargement et l'installation.
4. L'appareil redémarre automatiquement après la mise à jour.

> **Note** : L'appareil doit être connecté à Internet (mode STA) pour télécharger la mise à jour.

---

## 4. Modèles d'affichage

Le QiTi Clock supporte plusieurs modèles d'affichage selon le matériel connecté.

| Modèle | Description | LEDs requises |
|--------|-------------|---------------|
| `inline` | Affichage linéaire 25 LEDs — chiffres en ligne | 25 × WS2812B |
| `lixie` | Affichage Lixie 6 colonnes × 20 LEDs | 120 × WS2812B |
| `minimal` | Aucun rendu LED — mode débogage / test | — |

### Changer de modèle

1. Onglet **Paramètres** → section **Modèle**.
2. Sélectionnez le modèle dans la liste déroulante.
3. Cliquez sur **Appliquer**.

Le changement prend effet immédiatement sans redémarrage.

---

## 5. Alarmes

### Créer une alarme

1. Onglet **Paramètres** → section **Alarmes** → **Ajouter une alarme**.
2. Définissez l'heure, les jours de répétition, et activez/désactivez l'alarme.
3. Validez.

### Arrêter une alarme en cours

Utilisez le bouton **Arrêter l'alarme** affiché dans l'interface principale lorsqu'une alarme est active, ou via l'API REST.

---

## 6. Paramètres système

### Informations appareil

La section **Informations** (onglet Paramètres) affiche :
- **Appareil** : nom de l'appareil (ex. `QiTi_AABBCC`)
- **Firmware** : version installée
- **IP** : adresse IP courante

### Nom de l'appareil

Le nom par défaut est `QiTi_XXYYZZ` (générés depuis le suffixe MAC). Vous pouvez le personnaliser dans les paramètres Wi-Fi.

### Redémarrage

Bouton **Redémarrer l'appareil** → une confirmation s'affiche dans une fenêtre modale avant exécution.

---

## 7. Réinitialisation usine

> **Attention** : cette opération efface toutes vos configurations (Wi-Fi, alarmes, préférences).

1. Onglet **Paramètres** → section **Système** → bouton **Réinitialisation usine**.
2. Confirmez dans la fenêtre modale.
3. L'appareil redémarre en mode AP avec la configuration par défaut.

---

## 8. Dépannage

| Symptôme | Cause probable | Solution |
|----------|----------------|----------|
| L'interface n'est pas accessible | Connexion au mauvais réseau | Se connecter au réseau `QiTi_XXYYZZ` ou vérifier l'IP sur la box |
| Les LEDs ne s'allument pas | Modèle non compatible avec le matériel | Vérifier le modèle sélectionné dans Paramètres → Modèle |
| La mise à jour échoue | Pas de connexion Internet | Vérifier la connexion Wi-Fi (mode STA actif) |
| L'heure est décalée | Fuseau horaire non configuré ou NTP non synchronisé | Vérifier Paramètres → Heure → Fuseau horaire |
| L'appareil ne se connecte plus au Wi-Fi | Credentials invalides ou SSID changé | Se connecter en mode AP (`192.168.4.1`) et reconfigurer le Wi-Fi |
| L'appareil démarre en Safe Mode | Boot loop détectée ou configuration corrompue | Attendre la stabilisation ou effectuer une réinitialisation usine |

---

## 9. Support

Pour toute question ou signalement de problème :

**Email** : [support@gatto.fr](mailto:support@gatto.fr)

**Releases & historique des versions** : [https://github.com/actalex/qiti-clock-releases](https://github.com/actalex/qiti-clock-releases)

---

*QiTi Clock — Documentation utilisateur. Dernière mise à jour : 2026-06-18.*