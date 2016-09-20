---
title: Valider la configuration de votre MAM | Microsoft Intune
description: "Cette rubrique décrit comment vous pouvez tester et valider si votre stratégie MAM est configuré correctement et fonctionne comme prévu."
keywords: 
author: karthikaraman
manager: angerobe
ms.date: 08/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 41d82597-e13e-4c3e-9151-e71392236ca0
ms.reviewer: joglocke
ms.openlocfilehash: dab40df81c26b403aa3f2ae5524ff1297e2a7963
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Validation de vos paramètres de gestion des applications mobiles

Cette rubrique fournit des informations sur la vérification des problèmes après avoir configuré la gestion des applications mobiles (MAM). Ce guide s’applique aux stratégies MAM dans le portail Azure.

### Vérification des problèmes
Les utilisateurs peuvent probablement pas pour signaler des problèmes dans la mesure où MAM est un outil de protection des données. S’il existe un problème de configuration MAM l’utilisateur sera illimitée access, comme c’est sans MAM et serait pas savoir qu’il existe un problème. Pour cette raison, que nous vous recommandons valider votre configuration MAM en appliquant vos stratégies MAM avec un petit groupe d’utilisateurs qui permet de tester délibérément les restrictions MAM. 


### Points à vérifier 

Si le test montre que votre comportement d’une stratégie MAM est ne pas comme prévu, nous vous recommandons de que vous vérifiez les points suivants :

- Sont les utilisateurs autorisés à ouvrir MAM ?
- Sont les utilisateurs de licence pour Office 365 ?
- L’état de chacune des applications MAM utilisateurs. Les statuts possibles pour les applications sont **archivées** et **pas archivé**.

#### État MAM utilisateur
1. Dans le portail Azure choisissez **Gestion des applications mobiles Intune** > **paramètres** > **gestion application** > **tous les paramètres** > **application rapports par utilisateur** > **utilisateurs**.

2. Choisissez un utilisateur dans la liste ou recherchez et sélectionnez un utilisateur, puis choisissez **Sélectionner utilisateur**. En haut de la colonne **application de création de rapports** , vous verrez si l’utilisateur est sous licence pour MAM. Sous qui s’affiche si l’utilisateur est sous licence pour Office 365 et l’état de l’application pour tous les périphériques de l’utilisateur.

![Application statuts pour MAM](..\media\ts-mam-use-apps.png) 

### Procédure à suivre
Voici les actions à prendre en fonction de l’état de l’utilisateur :

- Si l’utilisateur n’est pas autorisé à MAM, attribuer une licence Intune à l’utilisateur comme décrit dans la zone [Intune gérer les licences](..\get-started\start-with-a-paid-subscription-to-microsoft-intune).
- Si l’utilisateur n’a pas de licence pour Office 365 obtenir une licence pour l’utilisateur.
- Si l’application d’un utilisateur est répertoriée comme **pas archivé**, vérifiez si vous avez correctement configuré une stratégie MAM pour cette application.
- Assurez-vous que ces conditions sont appliquées sur tous les utilisateurs auxquels vous voulez appliquer des stratégies MAM.

### Voir aussi
[Préparez-vous à configurer des stratégies de gestion de l’application mobile avec Microsoft Intune](..\deploy-use\get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

[Protéger les données d’application à l’aide de stratégies de gestion de l’application mobile avec Microsoft Intune](..\deploy-use\protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
