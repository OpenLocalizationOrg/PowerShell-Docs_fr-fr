---
title: "Protéger les données d’application à l’aide de stratégies MAM | Microsoft Intune"
description: "Cette rubrique explique comment mobile application Gestion des stratégies permettent de protéger vos données d’entreprise, éviter la perte de données et conserver les informations personnelles et Professionnel séparément."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: a3b6cb54c5b6c7bee084482f5c73c250574b182f
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Protéger les données d’application à l’aide de stratégies de gestion de l’application mobile avec Microsoft Intune

## Comment vous pouvez protéger les données d’application
Vos employés utilisent les appareils mobiles pour des tâches personnelles et Professionnel.  Si en prenant soin de vos employés peut être productif, vous souhaitez également éviter la perte de données voulu et accidentel.  En outre, que vous souhaitez effectuer la possibilité de protéger vos données société accessibles à l’aide d’appareils même dans le cas où ils ne sont pas gérés par vous.

Vous pouvez utiliser les stratégies de gestion des (MAM) de l’application mobile Intune protéger les données de votre société. Étant donné que les stratégies Intune MAM peuvent être utilisés **indépendamment de toute solution de gestion des appareils mobiles (périphériques mobiles)**, vous pouvez l’utiliser pour protéger vos données de votre entreprise avec ou sans inscription des appareils dans une solution de gestion des périphériques. En mettant en œuvre les **stratégies au niveau de l’application**, vous pouvez limiter l’accès aux ressources de l’entreprise et conserver les données dans le cadre de votre service informatique.

Stratégies MAM peuvent être configurés pour l’application en cours d’exécution sur les périphériques qui sont :

- **Inscrit dans Microsoft Intune :** Les périphériques de cette catégorie sont généralement d’entreprise appartenant appareils.

-   **Inscrit dans une solution de gestion (MDM) appareil Mobile tiers :**   Les périphériques de cette catégorie sont généralement d’entreprise appartenant appareils.

  > [!NOTE]
  > Stratégies de gestion de l’application mobile ne doivent pas être utilisés avec la gestion de l’application mobile tiers ou solutions conteneur sécurisé.

-   **Ne pas inscrit de toute solution de gestion des périphériques mobiles :**  Les périphériques de cette catégorie sont généralement employé appartenant périphériques qui ne sont pas gérés ou inscrit dans Intune ou d’autres solutions de périphériques mobiles.

> [!IMPORTANT]
> Stratégies de gestion des applications mobiles Office qui se connectent aux services Office 365, vous pouvez créer une application mobile. Stratégies MAM ne sont pas prises en charge pour les applications qui se connectent à Exchange en local, Skype entreprise ou SharePoint services.

**Sont les avantages de l’utilisation des stratégies MAM importantes**

-   Protection des données de votre société au niveau de l’application.  Étant donné que la gestion de l’application mobile ne nécessite pas de gestion des périphériques, vous pouvez protéger les données d’entreprise sur appareils gérés et. La gestion est centrée sur l’identité utilisateur qui supprime la nécessité de gestion des appareils.

-   Cela n’affecte pas la productivité des utilisateurs et les stratégies ne sont pas appliquées lors de l’utilisation de l’application dans un contexte personnel.  Les stratégies sont appliquées uniquement dans un contexte de travail, vous donnant ainsi la possibilité de protéger les données de la société sans toucher aux données personnelles.

Il existe des avantages supplémentaires à l’aide de la gestion des périphériques avec les stratégies MAM et entreprises peuvent utiliser les deux MAM avec et sans la gestion des périphériques en même temps. Par exemple, un employé peut utiliser un téléphone émis à l’entreprise, ainsi qu’une tablette personnelle.  Dans ce cas, le téléphone de la société est inscrit à la gestion des périphériques et protégé par les stratégies MAM, et l’appareil personnel est protégé par les stratégies MAM uniquement.

- **La gestion des périphériques permet de s’assurer que l’appareil est protégé**.  Par exemple, vous pouvez demander un code confidentiel pour accéder à l’appareil, ou vous pouvez déployer des applications gérées à l’appareil. Vous pouvez également déployer des applications sur les appareils via votre solution périphériques mobiles, vous donner plus de contrôle sur la gestion de l’application.

- **Stratégies MAM permet de s’assurer que la protection de la couche d’application est en place**. Par exemple, vous pouvez demander un code confidentiel ouvrir une application dans un contexte de travail, ou si les données peuvent être partagé entre les applications, ou empêcher les données de l’application d’enregistrées dans un emplacement de stockage personnel de la société.


### Stratégies MAM sont actuellement prises en charge dans :
-   iOS 8.1 ou version ultérieure

-   Android 4 ou version ultérieure

Appareils Windows ne sont actuellement pas pris en charge.
##  Comment les stratégies MAM protéger vos données de l’application

####  Applications sans stratégie MAM :

![Image qui affiche des données vous pouvez déplacer librement entre applications lorsqu’il n’y a aucune stratégie MAM en place](../media/Apps_without_MAM_policies.png)

Lorsque des applications sont utilisées sans restriction, société et données personnelles pouvant obtenir le mélange de.  Données de la société peuvent finir dans emplacements, tels que stockage personnel ou transféré aux applications en dehors de votre limites, ce qui crée de perte de données. Les flèches dans le diagramme affichent déplacement de données sans restriction entre les applications (d’entreprise et personnelles) et à l’emplacement de stockage.

### Protection des données avec les stratégies MAM :

![Image montrant comment les données d’entreprise est protéger lorsque MAM stratégies sont appliquées ](../media/Apps_with_mobile_app_policies.png)

Vous pouvez utiliser des stratégies MAM pour empêcher les données de la société de l’enregistrement pour le stockage local du périphérique et limiter le déplacement des données vers d’autres applications qui ne sont pas protégés par les stratégies MAM. Paramètres de stratégie MAM suivants :
- Règles de déplacement des données telles que **Empêcher Enregistrer sous**, **restreindre couper, copier et coller**.
- Paramètres de stratégie d’accès comme **simple code confidentiel pour l’accès est nécessaire**, **bloc gérées applications de s’exécuter sur des appareils racine ou jailbroken**.

### Protection des données avec les stratégies MAM sur périphériques gérés par une solution périphériques mobiles :

![Image montrant comment fonctionnent les stratégies MAM sur les appareils BYOD](../media/MAM_BYOD_November.png)

**Pour les appareils inscrit dans une solution périphériques mobiles**-

L’illustration ci-dessus montre les couches de protection qui proposent des stratégies de la gestion des périphériques et MAM ensemble.

La solution périphériques mobiles :

-   Inscrit auprès de l’appareil

-   Déploie les applications sur l’appareil

-   Offre de gestion et de conformité de périphérique en cours

**Stratégies MAM Ajouter valeur par :**

-   Protéger les données d’entreprise à partir de perd aux services et applications consommateur

-   Appliquer des restrictions (Enregistrer-en tant que, Presse-papiers, code confidentiel, etc.) pour les applications mobiles

-   Effacer les données d’entreprise à partir des applications sans supprimer ces applications à partir de l’appareil


### Protection des données avec des stratégies de MAM pour appareils sans inscription

![Image montrant comment fonctionnent les stratégies MAM sur les appareils gérées](../media/MAM_ManagedDevices_November.png)

Le diagramme ci-dessus illustre comment fonctionnent les les stratégies de protection des données au niveau de l’application sans MDM.

Pour les appareils BYOD ne pas inscrits dans n’importe quelle solution périphériques mobiles, stratégies MAM peuvent contribuer à protéger les données d’entreprise au niveau de l’application.
Il existe cependant certaines limitations importants, tels que :

-   Vous ne pouvez pas déployer des applications à l’appareil.  L’utilisateur final a obtenir les applications à partir du magasin.

-   Vous ne pouvez pas mise en service des profils de certificats sur les appareils suivants.

-   Vous ne pouvez pas mise en service de société Wi-Fi et paramètres VPN sur les appareils suivants.


## Identité multiples

Applications qui prennent en charge plusieurs identité offre la fonctionnalité permettant d’utiliser des comptes différents - fonctionne et personnel, pour accéder à la même applications lors de stratégies MAM sont appliquée sur lorsque les applications sont utilisées dans le contexte de travail.  

Par exemple, lorsque l’utilisateur final lance l’application OneDrive à l’aide de leur compte professionnel, ils ne peuvent pas déplacer les fichiers vers un emplacement de stockage personnel. Toutefois, lorsque l’utilisateur final utilise OneDrive avec leur compte personnel, ils peuvent copier et déplacer des données à partir de leur OneDrive personnel sans restriction.  

Pour plus d’informations de l’expérience de l’utilisation des applications qui sont associées à des stratégies MAM et comment applications avec plusieurs identité prend en charge activer appliquer des stratégies MAM uniquement dans le contexte de travail, lus [à l’aide d’applications avec prise en charge plusieurs identité](end-user-experience-for-mam-enabled-apps-with-microsoft-intune.md#using-apps-with-multi-identity-support)

Toutes les applications Office mobile prennent en charge plusieurs identité.

##  Étapes suivantes
[Préparez-vous à configurer des stratégies de gestion de l’application mobile](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

[Créer et déployer des stratégies de gestion de l’application mobile avec Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)
