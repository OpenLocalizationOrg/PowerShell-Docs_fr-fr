---
title: "Protéger des applications métier sur appareils ne pas inscrits | Microsoft Intune"
description: "Cette rubrique décrit comment vous pouvez préparer votre trait personnalisé des applications d’entreprise pour que vous puissiez appliquer des stratégies de gestion de l’application mobile qui peuvent vous aider à éviter la perte de données."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 00219467-a62e-43b6-954b-3084f54c45ba
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: 05b7755798963005a894a9f4a72442672bbe0a68
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Protéger la ligne de données sur les appareils ne pas inscrits dans Microsoft Intune et applications métiers

Stratégies de gestion des (MAM) application mobile protéger vos données d’entreprise en limitant le déplacement de données à copier et coller ou en empêchant les utilisateurs d’enregistrer des documents de l’entreprise vers un emplacement personnel.   Pour appliquer des stratégies de MAM pour iOS et ou Android ligne des applications d’entreprise, vous devez tout d’abord renvoyer l’application avec Microsoft Intune application Wrapping outil.  Habillage de l’application est le processus de l’application d’une couche de gestion pour une application mobile sans avoir besoin de toute modification apportée à l’application sous-jacente.  Une fois que l’application est encapsulée, vous pouvez lui appliquer des stratégies MAM et distribuer à vos utilisateurs finaux.  

Cette rubrique décrit les étapes nécessaires pour appliquer des stratégies de MAM pour les appareils qui sont gérés par une **solution de gestion (périphériques mobiles) appareil mobile tiers**et applications qui sont accessibles sur **employé appartenant appareils qui ne sont pas gérés**.  Pour préparer votre ligne d’applications d’entreprise qui s’exécutent sur les **appareils qui sont inscrits dans Intune**, voir [déterminer comment préparer des applications pour la gestion des applications mobiles avec Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).
##  Étape 1 : Préparation de l’application
Avant d’appliquer des stratégies MAM à une application, vous devez tout d’abord renvoyer l’application avec l’outil Microsoft Intune application Wrapping.  Les instructions pour installer et utiliser l’outil d’habillage application sont incluses dans le téléchargement.  
>[!IMPORTANT]  
>Cette version de l’outil d’habillage application, qui prend en charge des appareils ne pas inscrits dans Intune est disponible dans la version d’évaluation. Si vous souhaitez participer à la version d’évaluation, vous pouvez télécharger l’outil à partir de [cette page github](https://github.com/msintuneappsdk/intune-app-wrapper-ios-preview) pour iOS et [ce site github](https://github.com/msintuneappsdk/intune-app-wrapper-android-preview) pour Android.

## Étape 2 : Ajouter l’application

Pour associer votre application métier de stratégies MAM, vous devez ajouter les détails de l’application à votre abonnement/client Intune procédant comme suit :

1. Dans le [portail Azure](https://portal.azure.com/), accédez à **Gestion des applications mobiles Intune > Paramètres**, cliquez sur **applications métier de**.

  ![Capture d’écran de la cuillère paramètres avec ligne de l’option d’entreprise](../media/mam-azure-portal-lob-on-settings.png)

2. Dans la carte de la **ligne des applications métiers** , cliquez sur **Ajouter une application personnalisée**.

  ![Capture d’écran de la ligne de carte d’applications d’entreprise avec le bouton application personnalisée ajouter en haut](../media/mam-azure-portal-add-lob-app-action.png)
3.  Indiquez un nom pour l’application, l’identificateur de groupe dans le champ Identificateur de l’application et la plateforme (iOS ou Android).

  ![Capture d’écran de l’ajouter une carte application personnalisée ](../media/mam-azure-portal-add-app-details.png) cette étape permet de créer une liste unique de votre application.  L’application également être apparaîtra dans la liste des applications cibles pour une stratégie MAM pour votre client, comme décrit dans l’étape suivante.

## Étape 3 : Appliquer des stratégies de MAM
Une fois que les métadonnées de l’application sont téléchargée dans le service, l’application apparaît dans la liste des applications.  Vous pouvez maintenant [créer une nouvelle stratégie ou une stratégie existante](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) et l’appliquer à la ligne de l’application métier ajoutée à l’étape 2.

>[!IMPORTANT]
>Vous devez cibler la stratégie MAM aux utilisateurs pour lesquels vous envisagez d’utiliser l’application renvoyé à la ligne.  Les utilisateurs qui n’ont pas cette stratégie déployée leur ne seront pas en mesure d’utiliser l’application.


  ![Capture d’écran de la liste de cibles de cuillère applications avec la nouvelle ligne de l’application d’entreprise affichée](../media/mam-azure-portal-lob-on-targeted-app-list.png)
## Étape 4 : Distribuer l’application
Vous pouvez déployer des applications à vos utilisateurs finaux des façons suivantes :
* Pour les appareils inscrits dans une solution de la gestion des périphériques tiers, vous pouvez distribuer les applications via votre solution de périphériques mobiles.
* Pour les appareils ne pas gérés par n’importe quelle solution périphériques mobiles, vous avez besoin d’une solution personnalisée. Les utilisateurs finaux doivent télécharger et installer l’application sur leur appareil.

## Modifier les métadonnées
Si vous devez modifier les détails de l’application tel que le nom de l’application, ou l’identificateur de groupe, vous devez [Supprimer l’application](#remove-apps)et [Ajoutez-le](#step-2-add-the-app) avec les nouvelles métadonnées.

##  Supprimer des applications
Vous pouvez supprimer une ligne de l’application d’entreprise à partir de la liste des applications.  Cela sera supprimer l’application de la liste et supprimer l’association avec les stratégies MAM, mais pas supprimer ou désinstaller l’application à partir de l’appareil de l’utilisateur final.  

1.  Dans le [portail Azure](https://portal.azure.com/), accédez à **gestion de l’application mobile Intune > Paramètres**.  Dans la carte de **paramètres** , sélectionnez **secteur d’activité** pour ouvrir la liste des applications existantes.  
2.  Sélectionnez l’application que vous voulez supprimer, puis sélectionnez le menu **contextuel (...)** .

  ![Capture d’écran de la ligne de carte d’applications d’entreprise avec les points de suspension](../media/mam-azure-portal-lob-context-menu.png)
3.  Choisissez **Application supprimer** pour supprimer l’application.

  ![Capture d’écran de la ligne de carte de visite avec l’option d’application delete](../media/mam-azure-portal-delete-app.png)

  Cela supprime applications de la liste des applications métiers existantes et la liste cibles des applications dans la stratégie MAM.
