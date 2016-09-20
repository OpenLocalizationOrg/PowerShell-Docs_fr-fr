---
title: "Utiliser la réinitialisation à distance verrouiller et le code secret | Microsoft Intune"
description: "Intune fournit des fonctionnalités de réinitialisation de verrouillage distant et le code secret."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
ms.reviewer: chrisgre
ms.openlocfilehash: 3a7c87d915abd6ef4090c1773af3e58b81366998
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Protéger vos appareils verrouiller et le code secret à réinitialisation à distance
Intune Microsoft fournit des fonctionnalités de réinitialisation verrouiller à distance et le code secret.

## Verrouiller un appareil à distance
Si un utilisateur perd son appareil que vous pouvez verrouiller le périphérique à distance. Le tableau ci-dessous répertorie distant works verrouillage sur différentes plateformes mobiles. Verrouiller à distance n’est pas pris en charge

|Plateforme|Verrouiller à distance|
|------------|---------------|
|iOS|Prise en charge|
|Android|Prise en charge|
|Windows 10 et Windows 10 Mobile|Prise en charge|
|Windows Phone 8 et Windows Phone 8.1|Prise en charge|
|Windows RT 8.1 et Windows RT|Prise en charge si l’utilisateur actuel de l’appareil est le même utilisateur qui inscrit l’appareil.|
|Windows 8.1|Prise en charge si l’utilisateur actuel de l’appareil est le même utilisateur qui inscrit l’appareil.|

Verrouillage distant n’est pas prise en charge pour les PC Windows inscrit avec le logiciel client Intune.

### Pour verrouiller un appareil mobile à distance via la console Intune

1.  Dans la [console d’administration Intune](https://manage.microsoft.com/), choisissez **groupes** &gt; **Tous les périphériques** &gt; **Tous les appareils mobiles**.

2.  Choisissez **Tous les périphériques gérés directe** pour les périphériques inscrits dans Intune ou **Tous les Exchange ActiveSync gérées périphériques**.

    > [!TIP]
    > Vous pouvez également accéder à un appareil par utilisateur. Sélectionnez **tous les utilisateurs**. Sur la page de propriétés de l’utilisateur, sélectionnez **périphériques**, puis le nom de l’appareil mobile que vous voulez réinitialiser.

3.  Dans la liste, sélectionnez l’ou les périphériques que vous voulez verrouiller. Dans la barre des tâches, cliquez sur **Tâches à distance**, puis sélectionnez **Verrouiller à distance**.

## Réinitialiser le code secret sur un appareil
Si un utilisateur oublie son code secret, vous pouvez les aider en supprimant le code secret d’un appareil ou en forcer un nouveau mot de passe temporaire sur un appareil. Le tableau ci-dessous répertorie le code secret réinitialiser fonctionne sur différentes plateformes mobiles.

|Plateforme|Réinitialisation du code secret|
|------------|------------------|
|iOS|Prise en charge désactivant le code secret d’un appareil. Ne crée pas un nouveau mot de passe temporaire.|
|Android|Prise en charge et un code secret temporaire est créé.|
|Windows 10 Mobile|Prise en charge|
|Windows Phone 8 et Windows Phone 8.1|Prise en charge|
|Windows RT 8.1 et Windows RT|Non pris en charge|
|Windows 8.1|Non pris en charge|

Réinitialisation du code secret n’est pas prise en charge pour les PC Windows inscrit avec le logiciel client Intune.

### Réinitialiser un code secret

1.  Dans la [console d’administration Intune](https://manage.microsoft.com/), choisissez **groupes** &gt; **Tous les périphériques** &gt; **Tous les appareils mobiles**.

2.  Choisissez **Tous les périphériques gérés directe** pour les périphériques inscrits dans Intune ou **Tous les Exchange ActiveSync gérées périphériques**.

    > [!TIP]
    > Vous pouvez également accéder à un appareil par utilisateur. Cliquez sur **tous les utilisateurs**. Sur la page de propriétés de l’utilisateur, cliquez sur **périphériques**, puis cliquez sur le nom de l’appareil mobile que vous voulez réinitialiser.

3.  Dans la liste, sélectionnez l’ou les périphériques que vous voulez verrouiller. Dans la barre des tâches, cliquez sur **Tâches à distance**, puis sélectionnez **Réinitialisation du code secret**.


### Voir aussi
[Retirer appareils](retire-devices-from-microsoft-intune-management.md)
[Windows à distance sélectif pour via la gestion des données](http://technet.microsoft.com/library/dn486874.aspx)
