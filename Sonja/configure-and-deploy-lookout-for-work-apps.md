---
title: "Déployer affût travail application | Microsoft Intune"
description: "Configurer et déployer affût pour les applications de travail pour Android."
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
ms.openlocfilehash: c43104ff199e1800bfded35154d2be0cfd0c40f3
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Configurer et déployer affût pour les applications de travail
Dans cette version, affût pour utiliser l’application sur les appareils Android 4.1 en cours d’exécution et version ultérieure est pris en charge.
## Android
Cette section explique comment configurer et déployer l’affût de travail de votre application pour les appareils Android inscrit dans Intune.  
* Étape 1 : Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), accédez à **applications** et cliquez sur **Ajouter des applications**.   
* Étape 2 : Dans la page **D’installation du logiciel** de l’éditeur, cliquez sur **lien externe**et spécifiez l’URL suivante : https://play.google.com/store/apps/details?id=com.lookout.enterprise
>[!NOTE]
>Ne cliquez pas sur la zone d’exigence d’un navigateur géré.

* Étape 3 : dans la **description de logiciel** page, renseignez les informations suivantes :
  * **Publisher :** Sécurité Mobile affût
  * **Nom :**   Affût du travail
  * **Description :**  Affût offre la meilleure protection contre les menaces pour protéger votre appareil mobiles. Lorsque l’application affût est installée sur l’appareil, l’application protège votre appareil des menaces et vous informe vous et votre administrateur de la société, s’il en existe.
  * **Catégorie :** Gestion de l’ordinateur
* Étape 4 : En cas de réussite vous voyez un message **télécharger des données à Microsoft Intune bien été effectuée**.

Dans la Intune Console lorsque vous cliquez sur les **applications** vous verrez maintenant l’affût application de travail dans la liste ![capture d’écran de la page d’applications Intune admin console affichant l’affût pour les applications de travail dans la liste](../media/mtp/lookout-app-listed-intune-console.png)

Étape 5 : À ce point Intune sait comment déployer l’affût application android de travail.   Vous pouvez déployer l’application à des utilisateurs, en sélectionnant l’affût application travail indiqué dans l’écran ci-dessus et sélectionnez **Gérer le déploiement**.

Vous devez sélectionner les mêmes utilisateurs ajoutés à l’option de gestion de l’inscription dans la console affût le plan de référence.  Consultez l’étape 3 dans la [configuration de votre abonnement avec la section de plan de référence affût](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) pour plus d’informations sur l’ajout de groupes d’utilisateurs à l’affût le plan de référence.
>[!IMPORTANT]
> Le déploiement de l’application Intune Assistant n’a pas connaissance des groupes d’utilisateurs Azure AD et utilise les groupes d’utilisateurs Intune à la place. Si vous devez créer un groupe d’utilisateurs Intune basé sur le groupe d’utilisateurs Azure AD inscrit dans la console de plan de référence affût comme décrit dans [cette](plan-your-user-and-device-groups.md)rubrique.

Étape 6 : Choisissez l’option **Requise Installation** afin d’exiger que l’application affût soient installés sur le périphérique l’utilisateur.

### Activation du périphérique
Avec l’option **Installer requis** pour le déploiement, Intune fera à l’affût de travail de votre application à l’appareil.   

Lorsque l’utilisateur ouvre l’affût pour le travail sur le périphérique ils êtes invités à activer l’application, puis choisissez le connectez-vous avec l’option Azure Active Directory. Vous trouverez une procédure pas à pas détaillées avec le flux de l’utilisateur final dans les rubriques suivantes :

* [Vous êtes invité à installer affût pour le travail sur votre appareil Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [Vous avez besoin résoudre une menace trouvant affût pour le travail sur votre appareil Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## Étapes suivantes
* [Activer la règle de protection de menace appareil dans la stratégie de conformité](enable-device-threat-protection-rule-in-compliance-policy.md)
