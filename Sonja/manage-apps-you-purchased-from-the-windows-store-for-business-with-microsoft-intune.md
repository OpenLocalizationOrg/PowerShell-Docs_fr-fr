---
title: "Gestion du Windows Store pour les applications métier | Microsoft Intune"
description: "Se connecter Microsoft Intune vers le Windows Store pour les entreprises si vous voulez gérer et déployer des applications acheté volume à partir de la console Intune"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: 077029a962797a18fab27c3f1f5340eae6edfe04
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Gérer les applications que vous avez acheté auprès du Windows Store pour les entreprises avec Microsoft Intune
Le [Windows Store pour les entreprises](https://www.microsoft.com/business-store) vous propose un emplacement pour rechercher et acheter des applications pour votre organisation, individuellement ou en volume. En vous connectant à la banque à Microsoft Intune, vous pouvez gérer les applications acheté volume depuis la console Intune. Par exemple :
* Vous pouvez synchroniser la liste des applications que vous avez acheté à partir du magasin avec Intune.
* Applications qui sont synchronisées apparaissent dans la console d’administration Intune, et vous pouvez déployer ces comme toutes les autres applications.
* Vous pouvez suivre le nombre de licences disponibles et combien est utilisés dans la console d’administration Intune.
* Intune bloque déploiement et installation des applications s’il existe un nombre insuffisant de licences disponibles.

## Avant de commencer
Passez en revue les informations suivantes avant de commencer la synchronisation et le déploiement des applications à partir du Windows Store pour les entreprises :
* Vous devez configurer Intune comme l’autorité de gestion des périphériques mobiles pour votre organisation. Pour plus d’informations, voir [préparer d’inscription des appareils dans Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md).
* Vous devez avoir connecté pour un compte sur le Windows Store pour les entreprises.
* Une fois que vous avez associé un compte d’entreprise du Windows Store Intune, vous ne pouvez pas modifier ultérieurement vers un autre compte.
* Applications achetées à partir du magasin ne peut pas être ajoutées à ou supprimées de Intune manuellement. Ils peuvent uniquement être synchronisés avec le Windows Store pour les entreprises.
* Intune synchronise les applications sous licence uniquement en ligne que vous avez acheté à partir du Windows Store pour les entreprises.
* Appareils doivent être joints aux Services de domaine Active Directory ou rejoint poste de travail, pour utiliser cette fonctionnalité.
* Appareils inscrits doivent être à l’aide de la version 1511 de Windows 10.

## Associer votre du Windows Store pour le compte d’entreprise Intune
Avant d’activer la synchronisation dans la console Intune, vous devez configurer votre compte store pour utiliser Intune comme un outil de gestion :
1. Vérifiez que vous vous connectez dans le magasin d’entreprise à l’aide de la même compte client que vous utilisez pour vous connecter à Intune.
2. Dans le magasin d’entreprise, choisissez **paramètres** > **Outils de gestion**.
3. Dans la page Gestion des outils, cliquez sur **Ajouter un outil de gestion**, puis sélectionnez **Microsoft Intune**.

Vous pouvez maintenant continuer et configuré la synchronisation dans la console Intune.

## Configurer la synchronisation

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **administrateur**.
2. Dans l’espace de travail **Administration** , développez **Gestion des appareils mobiles**et choisissez **Store pour les entreprises**.
3. Dans la page **Du Windows Store pour les entreprises** , procédez comme suit :
 * Si vous n’avez pas déjà fait, cliquez sur le lien pour vous inscrire pour le Windows Store pour les entreprises.
 * Une fois que vous êtes connecté à distance, cliquez sur **Configurer la synchronisation**.
4. Dans la boîte de dialogue **Configurer du Windows Store pour la synchronisation de l’application d’entreprise** , sélectionnez **Activer Windows Store pour la synchronisation de l’entreprise**.
5. Dans la liste déroulante **langue** , sélectionnez la langue dans laquelle les applications à partir du Windows Store pour les entreprises seront affichera dans la console Intune. Quelle que soit la langue dans lequel elles sont affichées, elles seront installés dans la langue de l’utilisateur final lorsqu’elles sont disponibles.
6. Cliquez sur **OK**.

## Synchroniser des applications

1. Dans la page **Du Windows Store pour les entreprises** , sélectionnez **Synchroniser maintenant** pour synchroniser les applications que vous avez acheté à partir de la banque avec Intune.
2. Dans l’espace de travail **applications** , sélectionnez **Logiciels gérés** > **Logiciel sous licence** pour afficher les applications disponibles et vérifiez que vos applications que vous avez achetées ont été correctement importées. Les applications de ce nœud sont affichées avec le nombre total de licences que vous êtes propriétaire et le nombre de licences dont vous disposez.

## Déployer des applications

Déployer des applications à partir du magasin de la même façon que vous déployez une autre application Intune. Pour plus d’informations, voir [déployer des applications dans Microsoft Intune](deploy-apps-in-microsoft-intune.md).
Lorsque vous déployez du Windows Store entreprise App, une licence est utilisée par chaque utilisateur qui installe l’application. Si vous utilisez toutes les licences disponibles pour une application déployée, vous ne serez pas en mesure de déployer davantage de copies. Vous devez effectuer une des actions suivantes :
* Désinstaller l’application à partir de certains appareils.
* Réduire l’étendue du déploiement actuel afin de cibler uniquement les utilisateurs que vous avez suffisamment de licences pour.
* Acheter davantage de copies de l’application Windows Store pour les entreprises.

> [!Important]
> Applications déployées ne sont disponibles à l’utilisateur inscrit à l’origine de l’appareil. Aucun autre utilisateur ne peut accéder à l’application.


### Voir aussi
[Ajouter des applications pour les appareils mobiles dans Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)
