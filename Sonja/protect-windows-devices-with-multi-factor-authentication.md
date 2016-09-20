---
title: "L’authentification multifacteur pour Windows | Microsoft Intune"
description: "Intune s’intègre à l’authentification multifacteur (MFA) pour vous aider à protéger vos ressources d’entreprise."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 09/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36
ms.reviewer: vinaybha
ms.suite: ems
ms.openlocfilehash: e9eef5c0589fa2d75a5ba2e677ca2d3c29e305af
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Protéger les périphériques de Windows avec l’authentification multifacteur
Microsoft Intune s’intègre à l’authentification multifacteur (MFA) pour vous aider à protéger vos ressources d’entreprise. L’authentification Multifacteur nécessite facteurs d’authentification comme l’authentification en texte en plus de noms d’utilisateur et les mots de passe. Intune prend en charge l’utilisation de l’authentification Multifacteur lors de l’inscription de Windows 8.1 ou version ultérieure, Windows Phone 8.1 ou Windows 10 bureau Mobile périphériques.

## Exigences de l’infrastructure pour ADFS MFA local
Pour configurer l’authentification multifacteur, vous devez :

-   Inscription automatique, comme décrit dans [configurer la gestion des appareils Windows](set-up-windows-device-management-with-microsoft-intune.md).
-   **Un domaine Active Directory auquel le serveur ADFS est joint.**

-   **Active server Directory Federation Services (ADFS), configuré pour l’authentification Multifacteur.** Un serveur qui exécute Windows Server 2012 R2 et est configuré comme un serveur ADFS. Pour plus d’informations, voir : [sécuriser les ressources de cloud et en local à l’aide de serveur de l’authentification multifacteur Azure avec Windows Server 2012 R2 AD FS](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/)

Les serveurs doivent présenter la configuration système [requise](http://technet.microsoft.com/library/dn303418.aspx)et Installation informations pour Windows Server 2012 R2.

 


#### Authentification Multifacteur avec Intune
Si votre organisation possède un local l’infrastructure informatique qui inclut un domaine Active Directory avec Active Directory Federation Services (ADFS), vous pouvez configurer l’authentification Multifacteur sur votre serveur de fédération, puis activez l’authentification Multifacteur pour l’inscription Intune. En configurant l’authentification Multifacteur sur Intune, les utilisateurs peuvent authentifier une seule fois, lors de l’inscription, puis utilisez les ressources d’entreprise sans remplacer de chaque fois que le processus de l’authentification Multifacteur.

>[!NOTE]
>L’authentification Multifacteur peut être tenu sur une base par utilisateur ou par groupe sur le serveur ADFS.  

#### Authentification Multifacteur sans Intune
Si vous configurer l’authentification Multifacteur sur votre serveur de fédération, mais vous n’activez pas l’authentification Multifacteur pour l’inscription dans Intune, les utilisateurs devront utiliser l’authentification Multifacteur chaque fois qu’ils accèdent aux ressources d’entreprise (et pas seulement à l’inscription d’un appareil).

Vous pouvez également utiliser l’authentification Multifacteur Azure Active Directory (AD Azure) afin d’exiger l’authentification Multifacteur sur une base par utilisateur chaque fois que les utilisateurs accéder aux ressources d’entreprise. L’authentification Multifacteur AD Azure est un cloud service qui ne nécessite pas les locaux infrastructure informatique. Pour savoir comment configurer l’authentification Multifacteur de Azure Active Directory, voir [prise en main l’authentification multifacteur Azure dans le nuage.](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/).

## Pour demander une ADFS MFA lors de l’inscription des appareils Windows
Pour plus d’informations sur l’activation de l’authentification Multifacteur dans ADFS, voir [Gérer les risques grâce à l’authentification multifacteur supplémentaires pour les Applications sensibles](http://technet.microsoft.com/library/dn280949.aspx).

## Configurer l’authentification Multifacteur dans Intune inscription d’un appareil
>[!Important]  
>Activer l’authentification Multifacteur dans votre environnement Azure AD client ou locaux avant que vous exigez l’authentification Multifacteur pour l’inscription des appareils Windows Intune. Si vous n’est pas, les utilisateurs qui essaient inscrire leur appareil Windows ou essayez de jointure Azure AD leurs appareils obtenez un message d’erreur lors de l’inscription automatique pendant Azure AD jointure a été configurée.

1.  Dans la console d’administration Intune, choisissez **administrateur** &gt; **Gestion des appareils mobiles** &gt; **l’authentification multifacteur**.

2.  Sélectionnez **Configuration de l’authentification multifacteur**, puis **Activer l’authentification multifacteur**.
