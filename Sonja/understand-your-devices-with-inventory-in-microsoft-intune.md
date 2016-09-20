---
title: "Comprendre vos périphériques en stock | Microsoft Intune"
description: "Intune permet d’afficher des informations sur le matériel des appareils que vous gérez."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: a195ca39169d2288d76b1337a003db8a0ae11997
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Comprendre vos périphériques en stock dans Microsoft Intune
Microsoft Intune vous permet d’afficher l’inventaire des appareils inscrits et ordinateurs Windows qui s’exécutent le logiciel client Intune.
Intune collecte généralement inventaire de périphériques gérés tous les 7 jours. Pour cette raison, il peut y avoir un délai avant de rapports affichent les résultats de toute récente des modifications aux périphériques, par exemple, une modification de l’espace de stockage gratuit ou nom appareil.

## Que sont collecté à partir d’appareils inscrits ?
Pour afficher le stock qui est collecté par les appareils mobiles, exécutez les [Rapports d’inventaire appareil Mobile](understand-microsoft-intune-operations-by-using-reports.md). Intune collecte l’inventaire suivante à partir d’appareils inscrits :

|Propriété|Collectées par|
|------------|-----------------------|
|**Nom**|Tous les périphériques|
|**Système d'exploitation**|Tous les périphériques|
|**Fabricant**|Tous les périphériques|
|**Modèle**|Tous les périphériques|
|**Gestion des canaux**|Tous les périphériques|
|**AAD enregistré**|Tous les périphériques à l’exception de Mac OS X|
|**Respecter les exigences**|Tous les périphériques|
|**EAS activé**|Tous les périphériques à l’exception de Mac OS X|
|**ID de l’Activation EAS**|Tous les périphériques à l’exception de Mac OS X|
|**Heure d’Activation EAS**|Tous les périphériques à l’exception de Mac OS X|
|**État de gestion**|Tous les périphériques|
|**Adresse de messagerie**|Tous les périphériques|
|**Exchange ActiveSync ID**|Tous les périphériques|
|**Jailbroken ou associés à une racine**|appareils iOS et Android uniquement|
|**ID d’appareil unique**|Tous les périphériques à l’exception d’Exchange ActiveSync|
|**Numéro de série**|appareils iOS, Mac OS X, Android, Windows 8.1 et Windows 10|
|**Espace de stockage total**|iOS, Mac OS X, Windows 8.1 et appareils Windows 10|
|**Espace de stockage disponible**|iOS, Mac OS X, Windows 8.1 et appareils Windows 10|
|**Numéro de téléphone**<br>Téléphones classés comme d’entreprise sont identifiés par leur numéro de téléphone complet (par exemple, lorsque vous exécutez un rapport d’inventaire appareil mobile). BYOD téléphone nombres sont masqués avec & #42 ; et uniquement les quatre derniers chiffres sont affichent.|iOS, Android et Windows Phone appareils|
|**IMEI**|Appareils Exchange ActiveSync, iOS, Android et Windows Phone|
|**MEID**<br>Identificateur d’appareil mobile|uniquement les appareils iOS|
|**Wi-Fi MAC**|Tous les périphériques à l’exception d’Exchange ActiveSync|
|**Opérateur d’abonné**|appareils iOS et Android uniquement|
|**Technologie cellulaire**|appareils iOS et Android uniquement|
|**Contrôlés**|uniquement les appareils iOS|
|**État de verrouillage d’activation**|uniquement les appareils iOS|
|**Date inscrit**|Tous les périphériques|
|**Dernière mise à jour**|Tous les périphériques|
|**Ethernet MAC**|Uniquement les périphériques de Mac OS X|
|**Verrouiller l’activation activé**|uniquement les appareils iOS|
|**Chiffrement est activé**|Tous les périphériques|

## Que sont collecté à partir d’ordinateurs Windows ?
> [!IMPORTANT]
> Cette section s’applique uniquement à Windows PC qui exécutent le logiciel client PC Windows Intune.

Pour afficher le stock qui est collecté par les PC Windows, exécutez les [Rapports d’inventaire ordinateur](understand-microsoft-intune-operations-by-using-reports.md). Intune collecte l’inventaire suivant à partir d’ordinateurs Windows :

-   **Nom**

-   **Type de boîtier**

-   **Fabricant**

-   **Modèle**

-   **Système d'exploitation**

-   **Version de plateforme sécurisée**

-   **Espace disque total**

-   **Espace disque utilisé**

-   **Espace disque disponible**

-   **Nom du système d’exploitation disque**

-   **Espace disque du système d’exploitation**

-   **Système d’exploitation espace disque disponible**

-   **Mémoire physique**

-   **Nom du processeur**

-   **Architecture du processeur**

-   **Vitesse du processeur**

-   **Adresse IP**

-   **Numéro de série**

-   **Dernier utilisateur à une session**

-   **Utilisateur affecté**

-   **Dernière mise à jour**

<!-- this section below belongs in the planning journey
### See Also
[Monitoring and reports with Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
-->
