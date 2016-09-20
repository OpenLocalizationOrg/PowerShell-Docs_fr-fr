---
title: "Déployer des applications | Microsoft Intune"
description: "Cette rubrique décrit les concepts que vous devez comprendre avant de commencer le déploiement des applications avec Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: ef042e24af2300250cf2bd1bf9803678e252b773
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Déployer des applications avec Microsoft Intune

Cette rubrique explique certains des concepts que vous devez savoir avant de commencer le déploiement des applications avec Microsoft Intune.


## Actions de déploiement d’application
Lorsque vous déployez des applications, vous pouvez choisir parmi les actions de déploiement suivantes :

-   **Installer requis** – l’application est installé sur l’appareil sans intervention de l’utilisateur.

    > [!TIP]
    > Pour les appareils iOS qui ne sont pas en mode contrôlé ou pour tous les appareils Android, l’utilisateur doit accepter l’offre d’application avant qu’il est installé.
    >
    >  Si un utilisateur a désinstallé une application que vous avez déployée comme une installation requise, Intune automatiquement permet de réinstaller l’application après le cycle d’inventaire suivant, qui se produit généralement tous les sept jours.

-   **Installer disponible** – l’application est affiché dans le portail d’entreprise et les utilisateurs peuvent l’installer à la demande.

-   **Désinstaller** : l’application est désinstallé de l’appareil.

-   **Non applicable** – l’application n’est pas affichée dans le portail d’entreprise et n’est pas installé sur les périphériques.

#### Comprendre les actions de déploiement sont disponibles pour chaque type d’installation

|Type d’installation|Installer requis|Installer disponible|Désinstaller|Non applicable|
|------------------|--------------------|---------------------|-------------|------------------|
|Package d’application Windows (déployé sur un groupe d’utilisateurs)|Oui|Oui|Oui|Oui|
|Package d’application Windows (déployé sur un groupe de périphériques)|Oui|N°|Oui|Oui|
|Package d’application pour les appareils mobiles (déployé sur un groupe d’utilisateurs)|Oui|Oui|Oui|Oui|
|Package d’application pour les appareils mobiles (déployé sur un groupe de périphériques)|Oui|N°|Oui|Oui|
|Windows Installer (déployé sur un groupe d’utilisateurs)|N°|Oui|N°|Oui|
|Windows Installer (déployé sur un groupe de périphériques)|Oui|N°|Oui|Oui|
|Lien externe (déployé sur un groupe d’utilisateurs)|N°|Oui|N°|Oui|
|Lien externe (déployé sur un groupe de périphériques)|N°|N°|N°|N°|
|Gèrent application iOS à partir de l’app store (déployé sur un groupe d’utilisateurs)|Oui|Oui|Oui|Oui|
|Gèrent application iOS à partir de l’app store (déployé sur un groupe de périphériques)|Oui|N°|Oui|Oui|
> [!TIP]
> Lorsque vous déployez des applications, si vous sélectionnez des utilisateurs et groupes de périphériques, vous pouvez déployer uniquement l’application comme une **installation disponible**.

## Conflits de déploiement
Lorsque les deux déploiements avec la même action de déploiement sont reçues par un périphérique, les règles suivantes s’appliquent :

-   Déploiements à un groupe de périphériques priment sur les déploiements à un groupe d’utilisateurs. Toutefois, si une application est déployée sur un groupe d’utilisateurs avec une action de déploiement de **disponible**, et l’application même est également déployée sur un groupe de périphériques avec une action de déploiement de **Ne s’applique pas**, l’application seront disponible dans le portail d’entreprise pour les utilisateurs à installer.

-   Une action d’installation est prioritaire sur une action désinstaller.

-   Si un requis et une installation disponible sont reçues par un périphérique, les actions sont combinées. En d’autres termes, l’utilisateur peut installer l’application disponible à partir du portail d’entreprise avant le début de l’installation requise.


## Étapes suivantes

Découvrez comment [déployer des applications dans Microsoft Intune](deploy-apps-in-microsoft-intune.md).
