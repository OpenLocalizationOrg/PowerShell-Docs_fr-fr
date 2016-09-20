---
title: "S’inscrire avec le Gestionnaire d’inscription device | Microsoft Intune"
description: "Le compte du responsable (DEM) inscription d’un appareil peut gérer un grand nombre d’appareils mobiles partagés, appartenant à l’entreprise avec un seul compte d’utilisateur."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 585ce92b0f0159060d9a8f1960b4c7b05eafdee7
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# S’inscrire périphériques appartenant à l’entreprise avec le Gestionnaire d’inscription device dans Microsoft Intune
Organisations peuvent utiliser Intune pour gérer un grand nombre d’appareils mobiles avec un seul compte d’utilisateur. Le compte *le Gestionnaire de périphériques d’inscription* (DEM) est un compte Intune spécial qui peut s’inscrire jusqu'à 1 000 appareils. Nous vous conseillons d’utiliser appareils inscrits via ce compte en tant que périphériques partagés plutôt que vos périphériques personnels (« BYOD »). Les utilisateurs ne seront pas en mesure d’utiliser les applications de messagerie « native », par exemple.

Par exemple, vous pouvez affecter un responsable d’inscription appareil compte d’utilisateur à un responsable de magasin ou un responsable lui permettre de :

-   Inscription des appareils dans Intune.

-   Se connecter à l’application portail d’entreprise pour obtenir des applications d’entreprise.

-   Installer et désinstaller le logiciel.

-   Configurer l’accès aux données de la société.


**Un scénario de responsable d’inscription appareil :** Un restaurant souhaite tablettes point de vente pour son attente personnel et ordre des moniteurs pour son personnel de cuisine. Les employés doivent jamais accéder aux données de la société ou connectez-vous en tant qu’utilisateurs. L’administrateur Intune crée un compte du Gestionnaire d’inscription appareil et s’inscrit les appareils appartenant à l’entreprise à l’aide de ce compte. Par ailleurs, l’administrateur peut donner au Gestionnaire de l’inscription appareil informations d’identification pour un gestionnaire de restaurant qui permet du Gestionnaire de s’inscrire et gérer les appareils.

L’administrateur ou le gestionnaire pouvez déployer des applications spécifiques au rôle sur les appareils restaurant. Un administrateur peut également sélectionner le périphérique dans la console Intune et retirer gestion des appareils mobiles avec la console d’administration.

Appareils sont inscrit auprès d’un compte du Gestionnaire d’inscription appareil possèdent les restrictions suivantes :
  - Aucun périphérique spécifique « utilisateurs », par conséquent, il n’existe aucun accès aux données de messagerie ou de la société. Toutefois VPN, par exemple, peut toujours fournir applications appareil d’accéder aux données.
  - Il n’existe aucun accès conditionnelle, car il s’agit des scénarios par utilisateur.
  - Vous ne pouvez pas réinitialiser les appareils suivants à partir du portail d’entreprise.
  - Seul le périphérique local s’affiche dans l’application portail d’entreprise ou au site Web.
  - Ils ne peuvent pas utiliser les applications de Apple Volume achat programme (VPP) en raison de la configuration requise par utilisateur identifiant Apple pour la gestion de l’application.
  - (iOS) Ils ne peuvent pas être également inscrits avec Apple le programme de configuration ou le programme d’inscription Apple appareil (PED), mais DEP ou Apple le programme de configuration des équipements peuvent être inscrit sans affinité utilisateur.

> [!NOTE]
> Pour déployer des applications d’entreprise sur appareils qui sont gérés par le Gestionnaire d’inscription d’un appareil, déployer l’application portail d’entreprise comme un **Obligatoire installer** au compte d’utilisateur du responsable d’inscription appareil.
> Pour améliorer les performances, l’affichage de l’application portail d’entreprise sur un appareil DEM affiche uniquement le périphérique local. Gestion à distance d’autres appareils DEM peut uniquement faire à partir de la console d’administration Intune.

## Créer des comptes de gestionnaire d’inscription d’un appareil
Comptes du Gestionnaire de périphériques d’inscription sont des comptes d’utilisateurs avec des autorisations d’inscription grand nombre de périphériques appartenant à l’entreprise. Seuls les utilisateurs de la console Intune peuvent être responsables d’inscription d’un appareil.

#### Ajouter un responsable d’inscription d’un appareil à Intune

1.  Accédez au [portail de compte Microsoft Intune](http://go.microsoft.com/fwlink/?LinkId=698854) et se connecter à votre compte d’administrateur.

2.  Sélectionnez **Ajouter un utilisateur**.

3.  Vérifiez que le compte d’utilisateur qui sera un responsable d’inscription d’un appareil est répertorié. Si elle n’est pas le cas, ajoutez l’utilisateur en choisissant **Nouveau** et terminer le processus **d’Ajouter un utilisateur** . Une licence avec abonnement est nécessaire pour chaque utilisateur qui accède au service. Le Gestionnaire d’inscription d’un appareil ne peut pas être administrateur Intune. Vérifier si vous avez besoin d’ajouter des licences supplémentaires avant d’utiliser cette fonctionnalité.

4.  Se connecter à la [console d’administration Microsoft Intune](http://manage.microsoft.com) avec vos informations d’identification d’administration.

5.  Dans le volet de navigation, choisissez **administrateur**, accédez à la **Gestion de l’administrateur**et sélectionnez **Le Gestionnaire de périphériques d’inscription**. La page **Responsables d’inscription d’un appareil** s’ouvre.

6.  Cliquez sur **Ajouter**. La boîte de dialogue **Ajouter le Gestionnaire de périphériques d’inscription** s’ouvre.

7.  Entrez l' **ID d’utilisateur** du compte Intune, puis cliquez sur **OK**. L’utilisateur Gestionnaire d’inscription d’un appareil ne peut pas être administrateur Intune.

8.  Le Gestionnaire de l’inscription périphériques pouvez vous inscrire maintenant les appareils mobiles à l’aide de la même procédure que celle qu’un utilisateur final utilise pour un scénario BYOD dans le portail d’entreprise.

## Supprimer un responsable d’inscription d’un appareil de Intune

1.  Connectez-vous au [portail d’administration Microsoft Intune](http://manage.microsoft.com) avec vos informations d’identification d’administration.

2.  Dans le volet de navigation, choisissez **administrateur**, accédez à la **Gestion de l’administrateur**et sélectionnez **Le Gestionnaire de périphériques d’inscription**. La page **Responsables d’inscription d’un appareil** s’ouvre.

3.  Sélectionnez le périphérique d’inscription gestionnaire **utilisateur** que vous voulez supprimer, puis **Supprimer**. Cet utilisateur n’est pas supprimé à partir de Intune, et les appareils que gère cet utilisateur restera inscrits dans Intune. Suppression d’un responsable d’inscription appareil empêche l’inscription des appareils plus dans Intune cet utilisateur.

4.  Cliquez sur **Oui** pour confirmer que vous voulez supprimer le Gestionnaire d’inscription d’un appareil.

Suppression d’un responsable d’inscription appareil n’affecte pas les appareils inscrits. Lorsqu’un responsable d’inscription d’un appareil est supprimé :

-   Aucun périphérique inscrits n’est affectées.

-   Appareils inscrits continuent à être gérés complètement.

-   Les informations d’identification de compte de la gestionnaire appareil supprimés d’inscription restent valides pour vous connecter au portail d’entreprise pour accéder aux applications.

-   Les informations d’identification de compte de la gestionnaire appareil supprimés d’inscription ne peut pas toujours à distance ou retirer des appareils mobiles.

-   Relation de l’appareil supprimés d’inscription Gestionnaire de compte à inscrit reste appareils, mais aucun autre périphérique ne peut être inscrit.
