---
title: "Gérer les applications iOS acheté volume | Microsoft Intune"
description: "Utiliser Intune pour gérer les applications ce volume vous acheté auprès d’Apple par importer les informations de licence de l’app store, le suivi du nombre de licences que vous avez utilisée et empêchent d’installer plus de copies de l’application que vous êtes propriétaire."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1dafc28a-7f8b-4fe0-8619-f977c93d1140
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: a5c37c470f937c682d9138a636d1211f641da784
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Gérer les applications iOS que vous avez acheté via un programme d’achat de volume avec Microsoft Intune
L’app store d’iOS vous permet d’acheter plusieurs licences pour une application que vous voulez exécuter dans votre entreprise. Cela vous permet de réduire la charge administrative de suivi de plusieurs copies que vous avez achetées d’applications.

Magasin de Microsoft Intune permet de que gérer les applications que vous avez acheté via ce programme en important les informations de licence de l’application, le suivi du nombre de licences que vous avez utilisée et empêchent d’installer plus de copies de l’application que vous appartient.

> [!Important]
> Pour l’instant, Intune affecte iOS Volume programme d’achat de licences d’applications métier (VPP) à des utilisateurs et dispositifs pas. Pour cette raison, les utilisateurs doivent entrer leur mot de passe pour installer l’application.

## Gérer les applications acheté en volume pour les appareils iOS
Vous achetez plusieurs licences pour les applications iOS via le [Programme d’achat en Volume Apple pour les entreprises](http://www.apple.com/business/vpp/). Cela implique la configuration d’un compte Apple VPP depuis le site Web Apple et de télécharger le jeton VPP Apple sur Intune.  Vous pouvez synchroniser vos informations d’achat de volume avec Intune et suivre l’utilisation de votre application acheté en volume.

## Avant de commencer
Avant de commencer, vous devez obtenir un jeton VPP à partir de Apple et procéder au téléchargement à votre compte Intune. En outre, vous devez comprendre les éléments suivants :

* Chaque organisation peut contenir qu’un seul compte VPP et jeton.
* Une fois que vous associez un compte Apple VPP au Intune, vous ne peut pas associer un autre compte ultérieurement. Pour cette raison, il est très important que plusieurs personnes contient les détails du compte que vous utilisez.
* Si vous avez utilisé un jeton VPP avec un autre produit, vous devez générer un à utiliser avec Intune.
* Chaque jeton est valide pendant un an.
* Par défaut, Intune est synchronisé avec le service Apple VPP deux fois par jour. Vous pouvez démarrer une synchronisation manuelle à tout moment.
* Une fois que vous avez importé le jeton VPP dans Intune, ne pas importer le même jeton pour toute autre solution de gestion des périphériques. Cela peut entraîner la perte des enregistrements d’une affectation et utilisateur licence.
* Avant de commencer à utiliser iOS VPP avec Intune, supprimez les comptes d’utilisateur VPP existantes créées avec d’autres fournisseurs de gestion des (périphériques mobiles) appareil mobile. Intune synchroniseront pas ces comptes d’utilisateurs dans Intune une mesure de sécurité. Intune synchronisera uniquement les données à partir du service de Apple VPP Intune créé.
* Vous ne pouvez pas déployer iOS VPP applications aux périphériques qui ont été inscrite à l’aide du protocole d’inscription appareil (PED).

## Pour obtenir et télécharger un jeton VPP Apple

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **administrateur** &gt; **iOS et Mac OS X** &gt; **Programme d’achat en Volume**.  

2.  Cliquez sur le lien **Apple VPP compte** . Si vous n’avez pas déjà, s’inscrire au programme d’achat en Volume pour les entreprises. Une fois que vous vous inscrivez, téléchargez le jeton VPP Apple pour votre compte.

3.  Dans la page **Programme Apple Volume achat gérer (VPP)** de la console Intune, sélectionnez **Télécharger le jeton VPP**.

4.  Dans la boîte de dialogue **Télécharger le jeton VPP** , entrez ou collez le nom du jeton VPP et votre identifiant Apple et puis cliquez sur **Télécharger**.

5.  Dans la boîte de dialogue Avertissement, cochez la case pour indiquer que vous avez compris que vous ne pouvez pas modifier ultérieurement vers un autre compte VPP et puis cliquez sur **Oui**.

Dans la page **Programme d’achat en Volume** , vous pouvez à présent afficher des informations sur le jeton VPP Apple, y compris quand elle a été dernière mise à jour, lorsqu’il arrive à expiration et lors de la dernière synchronisation avec Intune.

Vous pouvez synchroniser les données contenues dans Apple avec Intune à tout moment en choisissant **Synchroniser maintenant**.

## Pour déployer une application acheté en volume

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), cliquez sur **applications** &gt; **Logiciels gérés** &gt; **applications acheté en Volume**. Cette liste affiche toutes les applications qui ont été synchronisées à partir du service VPP Apple.

2.  Sélectionnez l’application que vous voulez déployer, choisissez **Gérer le déploiement**, puis suivez les instructions dans la rubrique [applications déployer dans Microsoft Intune](deploy-apps-in-microsoft-intune.md) pour téléchargement, la création et déploiement de l’application.

> [!TIP]
> Vous devez choisir une action de déploiement de **obligatoire**. Installations disponibles ne sont actuellement pas pris en charge.

Lorsque vous déployez l’application comme une installation **obligatoire** , chaque utilisateur qui installe l’application utilise une licence.

Pour libérer une licence, vous devez redéfinir l’action de déploiement sur **désinstaller**. La licence est récupérée après la désinstallation de l’application.

Lorsqu’un utilisateur avec un appareil éligible tente tout d’abord installer une application VPP, il seront invité à participer au programme d’Apple Volume d’achat. Ils doivent faire ceci avant le démarrage de l’installation de l’application.

> [!TIP]
> Examinez la colonne **État de termes VPP** pour afficher l’état d’acceptation pour chaque utilisateur auquel l’application a été déployée.

Si aucune licence supplémentaire n’est disponible, le déploiement échouera.

## Pour surveiller des applications VPP Apple
Vous pouvez contrôler quelles applications VPP déployées et combien de licences est utilisées, à partir de l’espace de travail **applications** du **Logiciel Managed** &gt; nœud **Volume-Purchased applications** .

> [!TIP]
> Vous pouvez également utiliser l’application de **filtres** pour examiner l’état de chaque installation de l’application.

### Voir aussi
[Déployer des applications dans Microsoft Intune](deploy-apps-in-microsoft-intune.md)
