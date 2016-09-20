---
title: "Mettre à jour des applications | Microsoft Intune"
description: "Utilisez les informations dans cette rubrique pour comprendre comment mettre à jour des applications lorsqu’une nouvelle version est requise."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: cefe90cdb0cda5ada259576af7cf477642860446
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Mettre à jour des applications à l’aide de Microsoft Intune
Microsoft Intune peut vous aider à gérer les mises à jour de l’application. Utilisez les informations dans cette rubrique pour comprendre comment mettre à jour des applications lorsqu’une nouvelle version est requise.

## Comment mettre à jour des applications
Lorsque vous relâchez une nouvelle version d’une application que vous avez déployé Intune vous permet de mettre à jour et déployer la version la plus récente de l’application. Vous ne pouvez remplacer un déploiement avec une version plus récente de l’application même (qui a le même identifiant). Vous ne pouvez pas utiliser mises à jour de l’application pour mettre à jour un déploiement avec un package d’application différents.

### Identificateurs de l’application
L’identificateur de l’application est une propriété qui identifie de façon unique une application. Vous ne pouvez pas installer plusieurs copies d’une application avec le même identificateur. Voici quelques exemples d’identificateurs d’application :

- **iOS** - ID de l’ensemble de guides (par exemple : com.microsoft.excel)
- **Android** - ID de Package (par exemple : com.microsoft.excel)
- **Windows Phone** - utilisation (xap installer) ID de produit (GUID)
- **Windows** - (appx/appxbundle), utilisez le nom complet du Package



> [!IMPORTANT]
> Lorsque vous déployez une application avec une action de déploiement de **Installer requis** et toute modification ultérieure l’action de déploiement d' **installation disponible**, mises à jour de l’application ne sont pas installés automatiquement sur les appareils dont l’application installée avant que la modification de déploiement a été effectuée. Pour résoudre ce problème, vous pouvez procédez comme suit :
>
> -   Demandez à l’utilisateur de l’appareil accédez à l’application portail d’entreprise, sélectionnez l’application installée et puis sélectionnez **installer**.
> -   Modifier l’action de déploiement à **désinstaller**, puis après la désinstallation de l’application, redéployez l’application avec une action de déploiement **d’installation disponible**.

### Mettre à jour une application

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), cliquez sur **applications** &gt; **applications**.

2.  À partir de la liste **d’applications** , sélectionnez l’application que vous souhaitez mettre à jour, puis **Modifier**.

3.  Dans l’Assistant **Modifier le logiciel** , fournissent tous les nouveaux détails pour le package d’application.

4.  Lorsque vous avez terminé, cliquez sur **mettre à jour**.

Lorsque les périphériques Consultez ensuite applications disponibles, l’application se verra automatiquement vers la dernière version.
Pour les applications installées à partir d’un package d’application (ligne des applications d’entreprise), l’application passeront automatiquement pour les déploiements obligatoires et disponibles, dans la mesure où l’application a le même identificateur.

Pour les applications déployées en tant qu’un lien vers un magasin, la mise à jour est gérée par la banque d’informations à l’origine de l’application.
