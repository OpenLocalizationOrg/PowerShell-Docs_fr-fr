---
title: "Limiter l’accès de messagerie à Dynamics CRM Online | Microsoft Intune"
description: "Protéger et contrôler l’accès à Dynamics CRM online avec accès conditionnel."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f1c4522b-5a34-4f5a-89d2-7809c4352af7
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: dd322ff1a699da9444598135a6614f5e2d24ccc5
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Limiter l’accès de messagerie à Dynamics CRM Online avec Intune
Vous pouvez contrôler l’accès à Microsoft Dynamics CRM Online à partir d’appareils iOS et Android avec accès conditionnel Intune Microsoft.  Accès conditionnel Intune comporte deux éléments :
* [Stratégie de conformité appareil](introduction-to-device-compliance-policies-in-microsoft-intune.md) l’appareil doit respecter afin d’être considéré comme compatible.
* [Stratégie d’accès conditionnelle](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) que vous indiquer les conditions que l’appareil doit respecter pour accéder au service.

Pour en savoir plus sur comment conditionnelle access, consultez l’article [restreindre l’accès à la messagerie, 0365, ainsi que d’autres services](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) .

Lorsqu’un utilisateur ciblé tente d’utiliser l’application Dynamics CRM sur leur appareil, l’évaluation suivante se produit :

![Diagramme affiche les points de décision utilisées pour déterminer si un appareil est autorisé à accéder à un service ou est bloqué](../media/mdm-ca-dynamics-crm-flow-diagram.png)

Le périphérique nécessitant un accès à Dynamics CRM Online doit :
* Être un appareil **Android** ou **iOS** .
* Être **inscrit** avec Microsoft Intune.
* **Respecter les exigences** en avec les stratégies de conformité Microsoft Intune déployés.

L’état de l’appareil est stocké dans Azure Active Directory qui accorde ou bloque l’accès, en fonction des conditions que vous spécifiez.

Si une condition n’est pas remplie, l’utilisateur se voit avec l’un des messages suivants lors de la connexion :
* Si l’appareil n’est pas inscrit avec Microsoft Intune ou n’est pas enregistré dans Azure Active Directory, un message s’affiche avec des instructions sur la façon d’installer l’application portail d’entreprise et inscrire.
* Si l’appareil n’est pas conforme, un message s’affiche qui indique l’utilisateur au site portail d’entreprise Intune Microsoft ou l’application portail d’entreprise où il peut trouver des informations sur le problème et comment convertir celui-ci.

## Configurer l’accès conditionnel pour Dynamics CRM Online  
### Étape 1 : Configurer les groupes de sécurité Active Directory

Avant de commencer, configurez des groupes de sécurité Azure Active Directory pour la stratégie d’accès conditionnelle. Vous pouvez configurer ces groupes dans le **Centre d’administration Office 365**. Ces groupes servira à cible, ou des agents utilisateurs à partir de la stratégie. Lorsqu’un utilisateur est ciblé par une stratégie, chaque périphérique qu’ils utilisent doit être conforme afin d’accéder à des ressources.

Vous pouvez spécifier deux types de groupe à utiliser pour la stratégie de Dynamics CRM :
* **Groupes cibles** – contient des groupes d’utilisateurs pour lequel la stratégie est appliquée.
* **Groupes Exempted** – contient des groupes d’utilisateurs qui sont exemptés de la stratégie.

Si un utilisateur se trouve dans deux groupes, il sera exemptés de la stratégie.

### Étape 2 : Configurer et déployer une stratégie de conformité
[Créer](create-a-device-compliance-policy-in-microsoft-intune.md) et [déployer](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) une stratégie de conformité à tous les périphériques qui seront affectées par la stratégie. Il s’agit de tous les appareils qui sont utilisés par les utilisateurs dans les groupes cibles.

> [!NOTE]
> Tandis que les stratégies de conformité sont déployées aux groupes Microsoft Intune, les stratégies d’accès conditionnelle destinées à des groupes de sécurité Azure Active Directory.

> [!IMPORTANT]
> Si vous n’avez pas déployé une stratégie de conformité, les appareils seront traités comme conformes.

Lorsque vous êtes prêt, passez à l’étape 3.
### Étape 3 : Configurer la stratégie de Dynamics CRM
Ensuite, configurez la stratégie pour exiger que les appareils uniquement gérées et la conformité peuvent accéder Dynamics CRM. Cette stratégie sera ne sera stocké dans Azure Active Directory.

1.  Dans la console d’administration Microsoft Intune, choisissez **stratégie > accès conditionnel > Dynamics CRM Online stratégie**.

  ![Capture d’écran de la page de stratégie d’accès conditionnel Dynamics CRM Online](../media/mdm-ca-dynamics-crm-policy-configuration.png)

2.  Sélectionnez **Activer l’accès conditionnelle** stratégie.
3.  Sous **accès aux applications**, vous pouvez choisir appliquer la stratégie d’accès conditionnel pour :
  * **iOS**
  * **Android**
4.  Sous **Destinée aux groupes**, cliquez sur **Modifier** pour sélectionner les groupes de sécurité Azure Active Directory à laquelle s’applique la stratégie. Vous pouvez choisir de cibler ce pour tous les utilisateurs ou simplement un groupe d’utilisateurs.
5.  Sous **Groupes exemptés**, si vous le souhaitez, cliquez sur **Modifier** pour sélectionner les groupes de sécurité Azure Active Directory qui sont pas soumis à cette stratégie.
6.  Lorsque vous avez terminé, cliquez sur **Enregistrer**.

Vous avez configuré accès conditionnel pour Dynamics CRM. Vous n’êtes pas obligé de déployer la stratégie d’accès conditionnelle, il prend effet immédiatement.
##  Surveiller les stratégies d’accès conditionnelle et conformité

Dans l’espace de travail **groupes** , vous pouvez afficher le statut d’accès conditionnelle de vos appareils.

Sélectionnez n’importe quel groupe de l’appareil mobile et puis, sous l’onglet **périphériques** , sélectionnez une des **filtres**suivants :
* **Appareils qui ne sont pas enregistrés avec AAD** – les appareils suivants sont bloqués depuis Dynamics CRM.
* **Appareils qui ne sont pas compatibles avec** les appareils suivants sont bloqués depuis Dynamics CRM.
* **Appareils qui sont enregistrés avec DAS et la conformité** – les appareils suivants peuvent accéder à Dynamics CRM.

##  Étapes suivantes
[Limiter l’accès à Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)

[Limiter l’accès à Exchange locaux](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
[restreindre l’accès à SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

[Limiter l’accès à Skype entreprise Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
