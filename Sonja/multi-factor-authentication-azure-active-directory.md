---
title: "L’authentification multifacteur à l’aide d’Azure AD | Microsoft Intune"
description: "Comment demander l’authentification multifacteur dans Azure AD pour inscription d’un appareil."
keywords: 
author: nbigman
manager: angerobe
ms.date: 08/17/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: NOINDEX,NOFOLLOW
ms.openlocfilehash: 90f05f63e5df7776d6c6fde4de60731ccf1cddf0
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Authentification multifacteur pour Intune Microsoft

Intune s’intègre à l’authentification multifacteur Azure Active Directory (MFA) pour l’inscription d’un appareil pour vous aider à protéger vos ressources d’entreprise. L’authentification Multifacteur nécessite facteurs d’authentification comme l’authentification en texte en plus de noms d’utilisateur et les mots de passe. Ceci est pris en charge pour iOS, Android, Windows 8.1 ou version ultérieure, ou Windows Phone 8.1 ou générations ultérieures.

> [!NOTE]
>
> Dans les anciennes versions du Gestionnaire de Configuration (antérieures à la version 1610), vous verrez toujours le paramètre de l’authentification Multifacteur dans la console d’administration du Gestionnaire de Configuration. N’essayez pas de configurer l’authentification Multifacteur dans la console d’administration du Gestionnaire de Configuration, qu’il ne fonctionnera pas. Configurer l’authentification Multifacteur comme décrit dans cette rubrique.

### Configuration Intune afin d’exiger l’authentification multifacteur en inscription d’un appareil
Pour exiger l’authentification Multifacteur en inscription d’un appareil, procédez comme suit :

1. Se connecter à votre [portail Microsoft Azure](https://manage.windowsazure.com) avec vos informations d’identification d’administration.
2. Choisissez votre client.
2. Sélectionnez l’onglet **applications** . Vous verrez une liste des services pour lesquels vous pouvez configurer les fonctionnalités de sécurité Azure AD.
3. Choisissez **l’inscription Intune Microsoft**.
4. Cliquez sur **configurer**. 
5. Sous **l’authentification multifacteur et règles d’accès basé sur un emplacement** , vous pouvez :
    -  Activer les règles d’accès
    -  Indiquez si vous souhaitez appliquer les règles à tous les utilisateurs ou à Azure spécifique groupes de sécurité AD.
    -  Nécessite l’authentification multifacteur pour l’inscription de tous les périphériques.
    -  Exiger l’authentification multifacteur pour l’inscription lorsque l’appareil n’est pas au travail.
    -  Cliquez sur **Bloquer l’accès aux ressources d’entreprise** pour empêcher l’inscription d’un appareil lorsqu’il n’est pas connecté au réseau d’entreprise. 
4. Vous pouvez également cliquer sur le lien à **définir/modifier votre emplacement réseau de travail**, pour configurer les besoins en connectivité réseau pour l’inscription de l’appareil.
> [!IMPORTANT]
> 
> Ne configurez pas **les règles d’accès basés sur des périphériques** pour Microsoft Intune d’inscription.
