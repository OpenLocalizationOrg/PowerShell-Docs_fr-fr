---
title: Supprimer des applications | Microsoft Intune
description: "Découvrez comment désactiver ou désinstaller des applications à l’aide Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6fbf0805-1144-4e08-bafd-4f181d932bf2
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: 33ff2a202a8317319b6f8ef0a0e5fa10b4335ff3
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Supprimer des applications à l’aide de Microsoft Intune

Pour désactiver une application, vous simplement le désinstaller. Lorsque vous déployez et gérer les applications avec Intune, le processus de désinstallation de l’application est le même pour les appareils mobiles et ordinateurs Windows. L’application doit prendre en charge le processus de désinstallation pour cette procédure réussir.

## Désinstaller une application

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), cliquez sur **applications** &gt; **applications**.

2.  Sélectionnez l’application que vous voulez désinstaller (celui qui a été déployé précédemment), puis **Gérer le déploiement**.

3.  Dans la page **Action de déploiement** , sélectionnez **désinstaller** à partir de la colonne **approbation** .

Lorsque l’appareil ou l’ordinateur suivant vérifie les applications, l’application sera désinstallée.

### Voir aussi
[Ajouter des applications dans Microsoft Intune](add-apps.md)
