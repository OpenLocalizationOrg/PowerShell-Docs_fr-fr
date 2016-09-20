---
title: "Limiter l’accès de messagerie vers Exchange local | Microsoft Intune"
description: "Protéger et contrôler l’accès à la messagerie d’entreprise sur Exchange en local avec access conditionnelle."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a55071f5-101e-4829-908d-07d3414011fc
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 9a6455ded35bf77fbd5da1d4f345759836f38c7f
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Limiter l’accès de messagerie Exchange en local et dédié Online héritées Exchange avec Intune


Si vous disposez d’un environnement Exchange Online dédié et que vous devez déterminer si elle est dans la nouvelle ou de configuration héritées, veuillez contacter votre responsable de compte.


Pour contrôler l’accès de messagerie vers Exchange local ou à votre environnement Exchange Online dédié hérité, configurer l’accès conditionnelle vers Exchange local dans Intune.
Pour en savoir plus sur comment conditionnelle access, consultez l’article [restreindre l’accès aux messages électroniques et services Office 365]( restrict-access-to-email-and-o365-services-with-microsoft-intune.md) .

**Avant de** pouvoir configurer l’accès conditionnelle Vérifiez les points suivants :

-   Votre version d’Exchange doit être **Exchange 2010 ou version ultérieure**. Groupe de serveur d’accès au Client (CAS) Exchange server est pris en charge.

-   Vous devez utiliser le **Connecteur Exchange local**, qui se connecte [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Microsoft Exchange en local. Cela vous permet de gestion des appareils via la [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] console. Pour plus d’informations sur le connecteur, voir [Intune locaux connecteur Exchange](intune-on-premises-exchange-connector.md).

    -   Le connecteur d’Exchange locaux disponible dans la console Intune est spécifique à votre client Intune et ne peuvent pas être utilisé avec n’importe quel autre client. Vous devez également vous assurer que le connecteur exchange pour votre client est installée **sur un seul ordinateur**.

        Ce connecteur doit être téléchargé à partir de la console d’administration Intune.  Pour une procédure pas à pas sur la configuration du connecteur Exchange en local, voir [configurer le connecteur Exchange en local pour local ou Exchange hébergé](intune-on-premises-exchange-connector.md).

    -   Le connecteur peut être installé sur n’importe quel ordinateur tant que cet ordinateur est en mesure de communiquer avec le serveur Exchange.

    -   Le connecteur prend en charge **l’environnement Exchange CAS**. Vous pouvez techniquement installer le connecteur sur le serveur Exchange CAS directement si vous le souhaitez, mais il n’est pas recommandé, car cela améliore la charge sur le serveur.
    Lorsque vous configurez le connecteur, vous devez le configurer pour communiquer à un des serveurs Exchange CAS.

-   **Exchange ActiveSync** doit être configuré avec l’authentification par certificat ou d’une entrée d’informations d’identification utilisateur.

Lorsque les stratégies d’accès conditionnelle sont configurées et destinées à un utilisateur, avant d’un utilisateur peut se connecter à leur messagerie, **périphérique** qu’ils utilisent doit être :

-  Soit **inscrite** avec [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ou est un domaine rejoint PC.

-  **Enregistré dans Azure Active Directory**. En outre, le client Qu'exchange ActiveSync ID doit être enregistré avec Azure Active Directory.

  DRS AAD est activée automatiquement pour les clients Intune et Office 365. Clients qui ont déjà déployé le Service d’enregistrement de périphérique ADFS ne verront pas les appareils inscrits dans leurs locale d’Active Directory. **Cela ne s’applique pas à Windows PC et appareils Windows Phone**.

-   **Compatible** avec n’importe quel [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] des stratégies de conformité déployés sur cet appareil.

Le diagramme suivant illustre le flux est utilisé par les stratégies d’accès conditionnel pour Exchange local pour évaluer la nécessité d’autoriser ou bloquer les appareils mobiles.

![Diagramme montrant les points de décision qui déterminent si un appareil est autorisé à accéder à Exchange locaux ou bloqué](../media/ConditionalAccess8-2.png) si une stratégie d’accès conditionnelle n’est pas remplie, l’utilisateur se voit avec l’un des messages suivants lors de la connexion :

- Si l’appareil n’est pas inscrit avec [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], ou n’est pas enregistré dans Azure Active Directory, un message s’affiche avec des instructions sur la façon d’installer l’application portail d’entreprise, inscrire l’appareil et activer compte de messagerie. Ce processus associe également Exchange ActiveSync ID du périphérique avec l’enregistrement de périphérique dans Azure Active Directory.

-   Si l’appareil n’est pas conforme, un message s’affiche et indique à l’utilisateur le [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] site Web du portail d’entreprise, ou l’application portail d’entreprise où ils peuvent trouver des informations sur le problème et comment plus.

## Prise en charge pour les appareils mobiles
-   Windows Phone 8 et versions ultérieur

-   Application de messagerie native sur iOS.

-   Application de messagerie native sur Android 4 ou version ultérieure
> [!NOTE]
> Application Microsoft Outlook pour Android et iOS n’est pas pris en charge.

## Prise en charge pour les PC

L’application de **messagerie** sur Windows 8 et versions ultérieures (lorsque inscrite avec [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)])

##  Configurer une stratégie d’accès conditionnel

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **stratégie** > **Accès conditionnel** > **Exchange local stratégie**.
![IntuneSA5aSelectExchOnPremPolicy](../media/IntuneSA5aSelectExchOnPremPolicy.png)

2.  Configurer la stratégie avec les paramètres que vous avez besoin : ![capture d’écran de l’échange locaux page Stratégie](../media/IntuneSA5bExchangeOnPremPolicy.png)

  - **Empêche les applications de messagerie à partir de l’accès à Exchange local si l’appareil n’est pas inscrit à Microsoft Intune ou non conformes :** Lorsque vous sélectionnez cette option, les périphériques qui ne sont pas gérés par [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], ou est pas compatible avec une conformité stratégie sont bloqués depuis l’accès aux services Exchange.

  - **Par défaut règle substitution - toujours autoriser les périphériques inscrits et respecter les exigences pour accéder à Exchange :** Lorsque vous activez cette option, appareils qui sont inscrits dans Intune et la conformité avec les stratégies de respecter les exigences sont autorisés à accéder à Exchange.  
  Cette règle remplace la **Règle par défaut**, ce qui signifie que même si vous définissez la **Règle par défaut** pour mettre en quarantaine ou bloquer l’accès, inscrit et appareils compatibles toujours seront en mesure d’accéder à Exchange.

  - **Destinée aux groupes :** Sélectionnez le [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] groupes d’utilisateurs qui doivent s’inscrire leur appareil avec [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] avant de pouvoir accéder Exchange.

  - **Exemptés groupes :** Sélectionnez le [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] groupes d’utilisateurs sont exemptés de la stratégie d’accès conditionnelle. Les utilisateurs de cette liste seront agents même s’ils sont également dans la liste **Destinée aux groupes** .

  - **Plateforme Exceptions :** Cliquez sur **Ajouter une règle** pour configurer une règle qui définit les niveaux d’accès pour appareil mobile spécifié familles et les modèles. Étant donné que les appareils suivants peuvent être de n’importe quel type, vous pouvez également configurer des types de périphériques qui ne sont pas pris en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

  - **Règle par défaut :** Pour un appareil n’est pas traité par une des autres règles, vous pouvez choisir pour lui permettre d’accéder à Exchange, bloquer ou mettre en quarantaine. Lorsque vous définissez la règle pour autoriser l’accès, pour les périphériques qui sont inscrits et conformes, accès à la messagerie est automatiquement accordé pour iOS, Windows et Samsung KNOX appareils. L’utilisateur final n’a pas à passer par n’importe quel processus pour recevoir leur courrier.  Sur les appareils Android qui ne sont pas exécutées Samsung KNOX, les utilisateurs finaux obtenez un message électronique de mise en quarantaine qui inclut une procédure guidée pour vérifier l’inscription et conformité avant de pouvoir accéder messagerie. Si vous définissez la règle à bloquer l’accès ou mettre en quarantaine, tous les périphériques ne peuvent pas accéder à exchange indépendamment si elles sont déjà inscrit dans Intune ou non. Pour éviter les périphériques inscrits et respecter les exigences ne soient pas affectés par cette règle, vérifiez la **par défaut règle substituer.**
>[!TIP]
>Si votre intention est d’abord bloquer tous les périphériques avant d’accorder l’accès à la messagerie, sélectionnez la bloquer l’accès ou la règle de mise en quarantaine. La règle par défaut s’appliquent à tous les types de périphérique, afin que les types d’appareils configuré comme exceptions de plateforme et qui ne sont pas pris en [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] sont également affectés.

  - **Notification de l’utilisateur :** Outre le message de notification électronique envoyé à partir d’Exchange, Intune envoie un message électronique qui contient des étapes pour débloquer le périphérique. Vous pouvez modifier le message par défaut à personnaliser selon vos besoins. Étant donné que le message de notification Intune contenant les instructions de conversion est remis à la boîte aux lettres de l’utilisateur Exchange, dans le cas où le périphérique de l’utilisateur est bloqué avant qu’ils reçoivent le message électronique, ils peuvent utiliser un périphérique non bloqué ou une autre méthode pour accéder à Exchange et afficher le message. Cela est particulièrement vrai lorsque la **Règle par défaut** est défini sur Bloquer ou mettre en quarantaine.  Dans ce cas, l’utilisateur final a accéder à leur app store, téléchargez l’application portail d’entreprise Microsoft et inscrire leur appareil. Il s’agit applicable aux iOS, Windows et Samsung KNOX appareils.  Pour les périphériques qui ne sont pas exécutées Samsung KNOX, vous devez envoyer le message de mise en quarantaine à un compte de messagerie de secours, lequel l’utilisateur final a pour copier sur leur appareil bloqué pour terminer le processus d’inscription et conformité. |
  > [!NOTE]
  > Dans l’ordre pour Exchange pour pouvoir envoyer le message électronique de notification, vous devez spécifier le compte qui doit être utilisé pour envoyer le message électronique de notification.
  >
  > Pour plus d’informations, voir [configurer le connecteur Exchange en local pour local ou Exchange hébergé](intune-on-premises-exchange-connector.md).

3.  Lorsque vous avez terminé, cliquez sur **Enregistrer**.

-   Vous n’êtes pas obligé de déployer la stratégie d’accès conditionnelle, il prend effet immédiatement.

-   Une fois que l’utilisateur configure un profil Exchange ActiveSync, il peut prendre à partir de 1 à 3 heures pour le périphérique pour être bloqué (si elle n’est pas géré par [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]).

-   Si un utilisateur bloqué s’inscrit alors l’appareil avec [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] et les répare non-conformité), accès à la messagerie sera déblocage dans les 2 minutes.

-   Si l’utilisateur désactiver-s’inscrit à partir de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] peut prendre de 1 à 3 heures pour le périphérique pour être bloqué.

**Pour voir des exemples de scénarios de comment vous voulez configurer stratégie d’accès conditionnel pour restreindre l’accès des appareils, voir [limiter les scénarios d’exemple accès messagerie](restrict-email-access-example-scenarios.md).**

## Étapes suivantes
[Limiter l’accès à SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

[Limiter l’accès à Skype entreprise Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
