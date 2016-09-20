---
title: "S’inscrire appareils | Microsoft Intune"
description: "Gestion des appareils mobiles (MDM) utilisant d’inscription pour importer des appareils dans gestion et autoriser l’accès aux ressources."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
ms.openlocfilehash: 4dbf5123fc909d5372a0ca29c22d0df6d0eef26b
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# S’inscrire appareils pour la gestion des Intune
Vous pouvez vous inscrire appareils, y compris les PC Windows, pour activer la gestion des périphériques mobiles (périphériques mobiles) avec Microsoft Intune. Cette rubrique décrit les différentes façons d’inscription des appareils mobiles dans Intune gestion. Comment appareils inscrire appareils varie selon le type d’appareil, la propriété et le niveau de gestion de vos besoin. « Mettre votre propre périphérique » inscription (BYOD) permet aux utilisateurs de s’inscrire leur téléphone personnel, tablettes ou PC. Inscription d’un appareil appartenant à l’entreprise (CR) permet de gestion des scénarios comme réinitialisation à distance, périphériques partagés ou affinité utilisateur pour un appareil.

Si vous utilisez [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune), localement ou hébergées dans le cloud, vous pouvez activer la gestion de Intune simple sans d’inscription. PC Windows peuvent également être gérés à l’aide du [logiciel client Intune](#manage-windows-pcs-with-intune).

## Vue d’ensemble des méthodes d’inscription d’un appareil

Le tableau suivant indique les méthodes d’inscription de Intune avec leurs fonctions pris en charge. Ces fonctionnalités sont les suivantes :
- **Réinitialiser** - réinitialiser usine l’appareil, supprimer toutes les données. [Retirer des appareils mobiles](retire-devices-from-microsoft-intune-management.md)
- **Affinité** - appareils Associates avec des utilisateurs. Requis pour la gestion des applications mobiles (MAM) et conditionnelle accès aux données de la société. [Affinité utilisateur](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices)
- **Verrouillage** Empêche les utilisateurs de supprimer le périphérique de la gestion. les appareils iOS, mode Supervised est nécessaire pour verrouiller. [Verrouiller à distance](retire-devices-from-microsoft-intune-management.md#block-access-a-device)

**méthodes d’inscription iOS**

| **Méthode** |  **Réinitialiser** |  **Affinité**    |   **Verrouillage** | **Plus d’informations** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | N°|    Oui |   N° | [plus](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management)|
|**[DEM](#dem)**|   N° |N° |N°  | [plus](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   Oui |   Facultatif |  Facultatif|[plus](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| Oui |   Facultatif |  N°| [plus](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB Direct](#usb-direct)**| N° |    N°  | N°|[plus](ios-direct-enrollment-in-microsoft-intune.md)|

**Windows et les méthodes d’inscription Android**

| **Méthode** |  **Réinitialiser** |  **Affinité**    |   **Verrouillage** | **Plus d’informations**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | N°|    Oui |   N° | [plus](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management)|
|**[DEM](#dem)**|   N° |N° |N°  |[plus](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

Pour une série de questions qui vous permettent de vous trouvez la bonne méthode, voir [Choisir la procédure d’inscription des appareils mobiles](/intune/get-started/choose-how-to-enroll-devices1).

## BYOD
Les utilisateurs « Mettre votre propre périphérique » installer l’application portail d’entreprise et inscrire leur appareil. Cela peut permettre aux utilisateurs de se connecter au réseau d’entreprise, rejoindre le domaine ou Azure Active Directory. L’activation BYOD inscription est indispensable pour de nombreux scénarios de remboursement pour la plupart des plates-formes. Voir [Configuration requise pour l’inscription de l’appareil](prerequisites-for-enrollment.md). ([Revenir à la table](#overview-of-device-enrollment-methods))

## Périphériques appartenant à l’entreprise
Périphériques appartenant à l’entreprise (CR) peuvent être gérés grâce à la console Intune. les appareils iOS peuvent être inscrit directement par le biais d’outils fournis par Apple. Tous les types de périphérique peuvent être inscrit par un administrateur ou le Gestionnaire de l’utilisation du Gestionnaire d’inscription d’un appareil. Appareils avec un numéro IMEI peuvent également être identifiés et marqués comme appartenant à l’entreprise CR permettre à.

[S’inscrire périphériques appartenant à l’entreprise](manage-corporate-owned-devices.md)

### DEM
Le Gestionnaire de périphériques d’inscription est un Intune spécial compte utilisé pour s’inscrire et gérer plusieurs périphériques appartenant à l’entreprise. Responsables peuvent installer le portail d’entreprise et inscrire utilisateur moins grand nombre d’appareils. Apprenez-en davantage sur [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Revenir à la table](#overview-of-device-enrollment-methods))

### DEP
Gestion Apple appareil inscription d’un programme (PED) vous permet de créer et déployer une stratégie de « via l’air » pour les appareils iOS acheté et gérées avec logicielle. L’appareil est inscrit lorsque l’utilisateur se transforme sur le périphérique pour la première fois et s’exécute à l’Assistant de configuration iOS. Cette méthode prend en charge en mode **iOS Supervised** qui à son tour permet de :
  - Inscription verrouillée
  - Accès conditionnel
  - Détection jailbreak
  - Gestion des applications mobiles

En savoir plus sur [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Revenir à la table](#overview-of-device-enrollment-methods))

### USB-SA
Port USB, l’inscription Assistant de configuration. L’administrateur crée une stratégie Intune et exporte à configuration d’Apple. Appareils connectés USB, appartenant à l’entreprise sont prêtes Intune stratégie. L’administrateur doit s’inscrire chaque appareil manuellement. Les utilisateurs reçoivent les périphériques et exécutez l’Assistant de configuration, inscrire leur appareil. Cette méthode prend en charge en mode **iOS Supervised** qui à son tour permet de :
  - Accès conditionnel
  - Détection jailbreak
  - Gestion des applications mobiles

En savoir plus sur [l’Assistant de configuration d’inscription avec Apple le programme de configuration](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Revenir à la table](#overview-of-device-enrollment-methods))

### USB Direct
Inscription directe. L’administrateur crée une stratégie Intune et exporte à configuration d’Apple. Appareils connectés USB, appartenant à l’entreprise sont inscrits directement sans exiger une réinitialisation factory. L’administrateur doit s’inscrire chaque appareil manuellement. Appareils sont gérées comme dispositifs utilisateur sans. Ils ne sont pas verrouillées ou contrôlés et non pris en charge accès conditionnel, détection jailbreak, gestion des applications mobiles. Apprenez-en davantage sur [directe d’inscription avec Apple le programme de configuration](ios-direct-enrollment-in-microsoft-intune.md). ([Revenir à la table](#overview-of-device-enrollment-methods))

## Gestion des appareils mobiles avec Exchange ActiveSync et Intune
Les appareils mobiles qui ne sont pas inscrit, mais qui se connectent à Exchange ActiveSync (EAS) peuvent être gérés par Intune à l’aide de la stratégie EAS MDM. Intune utilise un connecteur Exchange pour communiquer avec EAS, localement et hébergé sur le nuage.

[Gestion des appareils mobiles avec Exchange ActiveSync et Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Gérer des PC Windows avec Intune  
Vous pouvez également utiliser Microsoft Intune pour gérer des PC Windows à l’aide du logiciel client Intune. PC gérés par le client pouvant Intune :

 - Rapport matérielle et logicielle stocks
 - Installer des applications de bureau (par exemple les fichiers .exe et .msi)
 - Paramètres du pare-feu

PC géré avec le logiciel client Intune ne peut pas être nettoyé et ne peut pas tirer parti de nombreuses fonctionnalités de gestion Intune tels qu’accès conditionnel, paramètres VPN et Wi-Fi ou le déploiement des certificats et des configurations de messagerie.

[Gérer des PC Windows avec Intune](manage-windows-pcs-with-microsoft-intune.md)

##  Plateformes d’appareil pris en charge

Intune peut gérer les plateformes d’appareil suivants :

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Étapes suivantes
- [Conditions préalables pour l’inscription d’un appareil](prerequisites-for-enrollment.md)
- [Gestion des appareils appartenant à l’entreprise](manage-corporate-owned-devices.md)
- [Ordinateurs et appareils mobiles pris en charge](../get-started/supported-mobile-devices-and-computers.md)
