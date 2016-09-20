---
title: Connecteur Exchange pour Exchange Online | Microsoft Intune
description: "Connecter Intune au service Office 365 Exchange pour prendre en charge Exchange ActiveSync (périphériques mobiles) de gestion des appareils mobiles."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: muhosabe
ms.suite: ems
ms.openlocfilehash: 1aabf820170483eacc83bec5e2b275e84dc07ffd
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Configuration du connecteur de service à service Intune pour Exchange Online

Utiliser ces informations pour vous connecter Microsoft Intune et Exchange Online ou nouveau service Exchange Online dédié. Pour déterminer si votre environnement Exchange Online dédié est de **Nouveau** ou **hérité**, contactez votre responsable de compte. Intune prend uniquement en charge une connexion de connecteur Exchange de n’importe quel type par abonnement.

## Configuration requise pour le lien de service à service
Le **connecteur de Service à Service** prend en charge uniquement Exchange Online ou nouveau Exchange Online dédié et n’a aucune configuration requise pour l’infrastructure en local.

|Configuration requise|Plus d’informations|
|---------------|--------------------|
|Exchange Online configuré et en cours d’exécution|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Autorité de gestion des appareils mobiles| [Définir l’autorité de gestion des périphériques mobiles à Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)|
|Version de Microsoft Exchange|Exchange Online ou nouveau service Exchange Online dédié|
|Synchronisation Active Directory|Avant de pouvoir utiliser le connecteur Intune, vous devez [configurer la synchronisation Active Directory](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) afin que vos utilisateurs locaux et les groupes de sécurité sont synchronisés avec votre instance d’Azure Active Directory.|

### Configuration requise pour Exchange applet de commande

Vous devez également créer un compte d’utilisateur qui est utilisé par le connecteur Exchange Intune Exchange Online. Le compte doit disposer des autorisations pour utiliser la console d’administration Intune et exécuter ces applets de commande Windows PowerShell Exchange requis :

 - Get-ActiveSyncOrganizationSettings, jeu ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, nouvelle-MobileDeviceMailboxPolicy, supprimer MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, nouvelle-ActiveSyncDeviceAccessRule, supprimer ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## Configurer le connecteur de service à service

1. Ouvrez la [console d’administration Microsoft Intune](http://manage.microsoft.com) avec un compte d’utilisateur avec des droits d’administrateur Exchange et les autorisations pour les applets de commande [ci-dessus](#exchange-cmdlet-requirements). Microsoft Intune utilise l’adresse de messagerie de l’utilisateur connecté pour configurer la connexion.

2.  Dans le volet Raccourcis espace de travail, cliquez sur **administrateur**, puis accédez **Gestion des appareils mobiles** > **Microsoft Exchange** > **Configurer la connexion Exchange**.
![Configurer la page de service de connecteur](../media/intunesa5cservicetoserviceconnector.png)

3.  Dans la page **Configurer la connexion Exchange** , sélectionnez **Définir Service au connecteur de Service**.


Le lien de Service à Service automatiquement configurer et synchroniser avec votre Exchange Online ou un nouvel environnement Exchange Online dédié.

## Valider votre connexion Exchange

Une fois que vous avez correctement configuré le connecteur Exchange, dans la [console d’administration Microsoft Intune](http://manage.microsoft.com) sélectionnez l' **administrateur** , puis accédez **Gestion des appareils mobiles** > **Microsoft Exchange** et valider que les détails que vous avez fourni s’affichent sous **Informations de connexion Exchange**.

Vous pouvez également vérifier l’heure et la date de la dernière tentative de synchronisation.
