---
title: "Paramètres de la stratégie Exchange ActiveSync | Microsoft Intune"
description: "Utilisez la stratégie Intune Exchange ActiveSync à configurer les paramètres qui vous permettent de que contrôler les fonctionnalités et les fonctionnalités sur les périphériques gérés par Exchange ActiveSync."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9cbb826-b155-4df6-abf3-60c6f05b2783
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 21f4e16787a3f5aa1970fbf7d22214018bc8c69c
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Paramètres de stratégie Exchange ActiveSync dans Microsoft Intune
Utilisez la stratégie Intune Microsoft **Exchange ActiveSync** pour configurer les paramètres qui contrôlent une grande variété de fonctionnalités sur les périphériques qui sont gérés par Exchange ActiveSync.


## Paramètres de mot de passe

|Nom du paramètre|Plus d’informations
|----------------|---|
|**Demander un mot de passe pour la déverrouiller les appareils mobiles**|Détermine si les appareils doivent être verrouillés à l’aide d’un mot de passe.<br>(non applicable aux appareils exécutant Windows RT).|
|**Obligatoires type de mot de passe**|Spécifie le type de mot de passe qui sera requis, par exemple numérique uniquement ou alphanumérique.|
|**Longueur minimale**|Spécifie le nombre minimal de caractères requis dans le mot de passe.|
|**Autoriser les mots de passe simples**|Indique si vous pouvez utiliser des mots de passe simples, qui incluent '0000' et « 1234 ».|
|**Nombre d’échecs de signe répétés autorisé avant que l’appareil est sélective**|Spécifie le nombre de fois qu’un utilisateur peut entrer un mot de passe avant de l’appareil est sélective.|
|**Expiration du mot de passe (jours)**|Spécifie le nombre de jours après lequel le mot de passe doit être modifié.
|**N’oubliez pas de l’historique de mot de passe**|Spécifie s’il faut ne pas autoriser l’utilisation de mots de passe utilisés précédemment.|
|**Historique de mot de passe mémoriser** : **éviter la réutilisation des mots de passe précédents**|Spécifie le nombre de mots de passe précédemment utilisés ne peuvent pas être utilisés à nouveau.|
|**Minutes d’inactivité avant de mot de passe est nécessaire**|Spécifie la durée pendant laquelle un appareil devant être inactif avant que l’écran est verrouillé.

## Paramètres de chiffrement

|Nom du paramètre|Plus d’informations|
|----------------|---|
|**Exiger le chiffrement sur appareil mobile**<sup>1</sup>|Exige que les données sur un appareil d’être chiffrées lors de la prise en charge.<br><br>Pour les appareils Windows Phone 8, vous devez définir sur **Oui**.<br /><br />Pour activer le chiffrement sur les appareils iOS, activer le paramètre **Exiger un mot de passe pour la déverrouiller les appareils mobiles** .|
|**Exiger le chiffrement sur les cartes de stockage**|Nécessite des données qui sont trouve sur le stockage externe tel qu’une carte SD à chiffrer (sur les appareils mobiles pris en charge).
<sup>1</sup> des informations supplémentaires pour les appareils exécutant Windows 8.1

-   Si vous souhaitez appliquer le chiffrement sur les appareils qu’exécuter Windows 8.1, vous devez installer le [décembre 2014 MDM mise à jour du client pour Windows](http://support.microsoft.com/kb/3013816) sur chaque appareil.

-   Si vous activez ce paramètre pour les appareils Windows 8.1, tous les utilisateurs de l’appareil doivent avoir un compte Microsoft.

-   Si vous souhaitez que le chiffrement pour l’utiliser pour les appareils Windows 8.1, le périphérique doit respecter les exigences de certification Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) matériel.

-   Si vous appliquez le chiffrement sur un appareil Windows 8.1, la clé de récupération est uniquement accessible à partir de compte Microsoft de l’utilisateur, qui est accessible à partir du compte d’utilisateur OneDrive. Vous ne pouvez pas récupérer cette touche au nom d’un utilisateur.

## Paramètres de messagerie

|Nom du paramètre|Plus d’informations
|----------------|---|
|**Permettre aux utilisateurs de télécharger des pièces jointes**|Indique si des pièces jointes pouvant être téléchargés à l’appareil.|
|**Période de synchronisation de messagerie**|Spécifie le nombre de jours de message électronique reçu qui seront synchronisés avec le périphérique.
|**Autoriser les périphériques mobiles qui ne prennent entièrement en charge les paramètres Exchange ActiveSync à la synchronisation avec Exchange**|Indique si vous voulez autoriser l’accès Exchange sur les appareils qui ne prennent pas en charge un ou plusieurs paramètres Exchange ActiveSync.

## Paramètres du navigateur

|Nom du paramètre|Plus d’informations
|----------------|---|
|**Autoriser le navigateur web**|Indique si le navigateur web sur l’appareil peut être utilisé.<br>(Non disponible pour Windows RT ou Windows Phone).

## Paramètres de matériel

|Nom du paramètre|Plus d’informations
|----------------|---|
|**Autoriser l’appareil photo**|Indique si la caméra sur l’appareil peut être utilisée.<br>(Non disponible pour Windows RT ou Windows Phone).



### Voir aussi
[Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
