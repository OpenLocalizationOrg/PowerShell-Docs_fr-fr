---
title: "Comment déployer des applications | Microsoft Intune"
description: "Utilisez les informations dans cette rubrique pour vous aider à déployer des applications avec Microsoft Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b42019e-73da-4538-a496-212f11d5bf9b
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: 904b89a92cef870f4672e5f40e6ac91ece10d3b7
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Déployer des applications dans Microsoft Intune

Utilisez les informations dans cette rubrique pour vous aider à déployer des applications avec Microsoft Intune.


## Déployer une application
Dans cette procédure, vous allez déployer une application à des groupes sélectionnés des appareils ou des utilisateurs.

### Déployer une application

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), cliquez sur **applications** &gt; **applications** pour afficher la liste des applications que vous gérez.

2.  Sélectionnez l’application que vous voulez déployer, puis cliquez sur **Gérer le déploiement**.

3.  Dans la * &lt;nom de l’application&gt; * boîte de dialogue, dans la page **Sélectionner des groupes** , sélectionnez les groupes d’utilisateur ou un appareil auquel vous voulez déployer l’application.

4.  Dans la page **Action de déploiement** , configurez les éléments suivants :

    - **Approbation** - Indiquez si le déploiement est :
        - **Obligatoire** (installation obligatoire)
        - **Disponible** (les utilisateurs installer à partir du portail d’entreprise à la demande)
        - **Non Applicable** (l’application n'est pas installée ou affichée dans le portail d’entreprise)
        - **Désinstaller** (l’application est désinstallée à partir d’appareils cibles)
    - **Date d’échéance** - pour les installations requises, choisissez comment bientôt déployer l’application. Vous pouvez choisir parmi des valeurs prédéfinies, ou vous pouvez sélectionner **personnalisée** pour configurer votre propre échéance.

5. Si l’application que vous déployez peut être configurée par une stratégie de gestion des applications mobiles, la page de **Gestion de l’application Mobile** s’affiche. Dans cette page, sélectionnez la stratégie de gestion des applications mobiles que vous voulez associer à cette application.

    [Déterminer quelles applications Microsoft sont compatibles avec les stratégies de gestion des applications mobiles.](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)

6. Si l’application que vous déployez est compatible avec les profils Intune VPN, la page de **Profil VPN** s’affiche. Dans cette page, vous pouvez choisir associer un profil VPN que vous avez déployé des applications iOS. La connexion VPN s’ouvre automatiquement lorsque l’application est lancée. Pour rendre un profil VPN, il doit avoir le paramètre de profil **par application VPN** activé.
 Pour plus d’informations sur la façon de configurer les profils VPN, y compris des informations sur la façon d’associer des profils d’applications, voir [connexions VPN dans Microsoft Intune](vpn-connections-in-microsoft-intune.md).

## Exemple

Dans cet exemple, vous avez déployé l’application en tant que **disponible** sur un appareil iOS.
L’application s’affiche sur les périphériques des utilisateurs dans le portail d’entreprise et les utilisateurs pouvez l’installer à partir de là.

Par exemple, dans cette capture d’écran, le Bing application iOS a été déployé en utilisant le type d’installation **Lien externe** avec une icône personnalisée. L’option **Afficher comme une application proposée et mettre en surbrillance dans le portail d’entreprise** a été activée.  
![application disponible iOS](./media/available-install-on-iOS.png)

Si vous avez déployé l’application comme **obligatoire** sur un appareil iOS, l’utilisateur recevra une notification indiquant qu’une application est prête à installer. Par exemple, dans cette capture d’écran, les dossiers de travail pour une application iOS a été déployé en utilisant le type d’installation de **l’application iOS gérés à partir de l’app store** .  
![application requis iOS](./media/iOS-Required-install.PNG)

## Étapes suivantes

Une fois que vous déployez une application, vous souhaiterez surveiller sa progression. Pour plus d’informations, voir [surveiller des applications dans Microsoft Intune](monitor-apps-in-microsoft-intune.md).
