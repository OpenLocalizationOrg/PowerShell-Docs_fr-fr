---
title: "Limiter l’accès à Skype entreprise Online | Microsoft Intune"
description: "Protéger et contrôler l’accès à Skype entreprise Online avec accès conditionnel."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1b2d7125-f63f-43cf-ac1e-94fbedf2a7e8
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: a0db4bd6d1ae55b5d82152f8d4910204e857cc85
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Limiter l’accès à Skype entreprise Online avec Microsoft Intune
Stratégie d’accès conditionnel pour **Skype entreprise Online** permet de contrôler l’accès à Skype entreprise Online.
Accès conditionnel comporte deux éléments :
- Stratégie de conformité d’appareil l’appareil doit respecter afin d’être considéré comme compatible.
- Stratégie d’accès conditionnelle que vous indiquer les conditions que l’appareil doit respecter pour accéder au service.
Pour en savoir plus sur comment conditionnelle access, consultez l’article [restreindre l’accès aux messages électroniques et services Office 365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) .

Lorsqu’un utilisateur ciblé tente d’utiliser Skype entreprise Online sur leur appareil, l’évaluation suivante se produit :

![Diagramme montrant les points de décision qui est utilisée pour déterminer si un appareil est autorisé à accéder à Skype entreprise Online ou bloqué](../media/ConditionalAccess_SkypeforBusiness.png)

**Avant de** configurer une stratégie d’accès conditionnel pour Skype entreprise Online, vous devez :
- Ont un **Skype entreprise Online abonnement** et affecter Skype entreprise Online licence aux utilisateurs.
- Posséder un abonnement pour **l’Entreprise mobilité Suite** ou **Azure Active Directory Premium**.
-   [Activer l’authentification moderne](https://docs.microsoft.com/en-us/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune) pour Skype entreprise Online.
-  Tous vos utilisateurs finaux doit être à l’aide de **Skype entreprise Online**. Si vous avez un déploiement avec Skype entreprise Online et Skype pour entreprise local, stratégie d’accès conditionnelle pas est appliquée aux utilisateurs finaux.

    Le périphérique nécessitant un accès à Skype entreprise Online doit :

-   Être un appareil **Android** ou **iOS** .

-   Être **inscrit** auprès de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

-   Être **compatibles** avec n’importe quel déployé [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] des stratégies de conformité.


L’état de l’appareil est stocké dans Azure Active Directory qui accorde ou bloque l’accès, en fonction des conditions que vous spécifiez.

Si une condition n’est pas remplie, l’utilisateur se voit avec l’un des messages suivants lors de la connexion :

-   Si l’appareil n’est pas inscrit avec [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], ou n’est pas enregistré dans Azure Active Directory, un message s’affiche avec des instructions sur la façon d’installer l’application portail d’entreprise et inscrire.

-   Si l’appareil n’est pas conforme, un message s’affiche et indique à l’utilisateur le [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] site Web du portail d’entreprise ou une application portail d’entreprise où ils peuvent trouver des informations sur le problème et explique comment convertir celui-ci.

## Configurer l’accès conditionnel pour Skype entreprise Online

### Étape 1 : Configurer les groupes de sécurité Active Directory
Avant de commencer, configurez des groupes de sécurité Azure Active Directory pour la stratégie d’accès conditionnelle. Vous pouvez configurer ces groupes dans le **Centre d’administration Office 365**. Ces groupes servira à cible, ou des agents utilisateurs à partir de la stratégie. Lorsqu’un utilisateur est ciblé par une stratégie, chaque périphérique qu’ils utilisent doit être conforme afin d’accéder à des ressources.

Vous pouvez spécifier deux types de groupe à utiliser pour la Skype pour la stratégie d’entreprise :

-   **Groupes cibles** – contient des groupes d’utilisateurs pour lequel la stratégie est appliquée.

-   **Groupes Exempted** – contient des groupes d’utilisateurs qui sont exemptés de la stratégie.

Si un utilisateur se trouve dans deux groupes, il sera exemptés de la stratégie.

### Étape 2 : Configurer et déployer une stratégie de conformité
[Créer](create-a-device-compliance-policy-in-microsoft-intune.md) et [déployer](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) une stratégie de conformité à tous les périphériques qui seront affectées par la stratégie. Il s’agit de tous les appareils qui sont utilisés par les utilisateurs dans les **groupes cibles**.

> [!NOTE]
> Tandis que les stratégies de conformité sont déployées à [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] les groupes, accès conditionnel stratégies destinées à des groupes de sécurité Azure Active Directory.


> [!IMPORTANT]
> Si vous n’avez pas déployé une stratégie de conformité, les appareils seront traités comme conformes.

Lorsque vous êtes prêt, passez à **l’étape 3**.

### Étape 3 : Configurer la Skype de stratégie entreprise Online
Ensuite, configurez la stratégie pour exiger que les appareils uniquement gérées et la conformité peuvent accéder Skype entreprise Online. Cette stratégie sera ne sera stocké dans Azure Active Directory.

####
1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), cliquez sur **stratégie** > **Accès conditionnel** > **Skype pour la stratégie d’entreprise en ligne**.

![Capture d’écran de Skype entreprise Online page de stratégie d’accès conditionnel](./media/conditional_access_SFBPolicy.png)

2.  Sélectionnez **Activer la stratégie d’accès conditionnelle**.

3.  Sous **accès aux applications**, vous pouvez choisir appliquer la stratégie d’accès conditionnel pour :

    -   **iOS**

    -   **Android**

4.  Sous **Destinée aux groupes**, cliquez sur **Modifier** pour choisir les groupes de sécurité Azure Active Directory à laquelle s’applique la stratégie. Vous pouvez choisir de cibler ce pour tous les utilisateurs ou simplement un groupe d’utilisateurs.

5.  Sous **Groupes exemptés**, si vous le souhaitez, cliquez sur **Modifier** pour choisir les groupes de sécurité Azure Active Directory qui sont pas soumis à cette stratégie.

6.  Lorsque vous avez terminé, cliquez sur **Enregistrer**.

Vous avez configuré accès conditionnel pour Skype entreprise Online. Vous n’êtes pas obligé de déployer la stratégie d’accès conditionnelle, il prend effet immédiatement.


## Surveiller les stratégies d’accès conditionnelle et conformité
Dans l’espace de travail **groupes** , vous pouvez afficher le statut d’accès conditionnelle de vos appareils.

Sélectionnez n’importe quel groupe de l’appareil mobile et puis, sous l’onglet **périphériques** , sélectionnez une des **filtres**suivants :

* **Appareils qui ne sont pas enregistrés avec AAD** – les appareils suivants sont bloqués à partir de Skype entreprise Online.

* **Appareils qui ne sont pas compatibles avec** les appareils suivants sont bloqués à partir de Skype entreprise Online.

* **Appareils qui sont enregistrés avec DAS et la conformité** – les appareils suivants peuvent accéder à Skype entreprise Online.
