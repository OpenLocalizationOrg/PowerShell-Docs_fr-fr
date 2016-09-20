---
title: "Conditions préalables pour l’inscription d’un appareil mobile | Microsoft Intune"
description: "Paramétrer les conditions préalables mobile device management (MDM) et se préparer à s’inscrire différents systèmes d’exploitation."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40
ms.reviewer: damionw
ms.suite: ems
ms.openlocfilehash: aca401a5bc7274d6d20980bc27d2d8fe23d8e548
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Conditions préalables pour la gestion des appareils mobiles dans Intune
Pour permettre aux employés de s’inscrire les appareils mobiles (y compris [Android](set-up-android-management-with-microsoft-intune.md), [iOS et Mac](set-up-ios-and-mac-management-with-microsoft-intune.md), [Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)et [Windows PC](set-up-windows-device-management-with-microsoft-intune.md)) avec Intune ou pour gérer les périphériques appartenant à l’entreprise, vous devez activer inscription d’un appareil. Pour permettre l’inscription, vous devez définir une autorité de gestion des (périphériques mobiles) appareil mobile, configurez le portail d’entreprise Intune, attribuer des licences et activer l’inscription pour la plateforme de l’appareil.

## Définir l’autorité de gestion des appareils mobiles
L’autorité MDM définit le service de gestion qui dispose des autorisations nécessaires pour gérer un ensemble d’appareils. Les options pour l’administration de la gestion des périphériques incluent Intune par lui-même et Gestionnaire de Configuration avec Intune. Si vous définissez le Gestionnaire de Configuration de l’autorité de gestion, aucun autre service ne peut servir pour la gestion des appareils mobiles.

>[!IMPORTANT]
> Prenez en compte si vous souhaitez gérer les appareils mobiles à l’aide de Intune (service en ligne) ou System Center Configuration Manager avec Intune (en local solution logicielle conjointement avec le service en ligne). Après avoir défini l’autorité de gestion des périphériques mobiles, cela ne peut pas être modifié.



1.  Dans la [console d’administration Microsoft Intune](http://manage.microsoft.com), choisissez **administrateur** &gt; **Gestion des appareils mobiles**.

2.  Dans la liste des **tâches** , cliquez sur **Définir Mobile Device Management autorité**. La boîte de dialogue **Définir la gestion des périphériques autorité** s’ouvre.

    ![Boîte de dialogue Configurer la gestion des périphériques autorité](../media/intune-mdm-authority.png)

3.  Intune demande confirmation que vous souhaitez Intune comme autorité périphériques mobiles. Activez la case à cocher et puis cliquez sur **Oui** pour utiliser Microsoft Intune pour gérer les appareils mobiles.

## Configurer le portail d’entreprise Intune

Le portail d’entreprise Intune est où les utilisateurs accéder aux données de la société et peut effectuer les tâches courantes telles que l’inscription des appareils, de l’installation d’applications et de localisation des informations pour obtenir une assistance à partir de votre service informatique.

> [!TIP]
> Lorsque vous personnalisez le portail d’entreprise, les configurations s’appliquent à la fois le site Web de portail d’entreprise et les applications du portail d’entreprise.

Personnalisation de l’application portail d’entreprise permet de fournir une expérience utilisateur familière et utile pour vos utilisateurs finaux. Pour ce faire, simplement se connecter à la [console d’administration Microsoft Intune](https://manage.microsoft.com) en tant qu’un administrateur client ou service, choisissez **administrateur** &gt; **Portail d’entreprise**et configurer les paramètres du portail d’entreprise.

![Admin-console-Admin-Workspace-comp-Portal-Settings](../media/cp_sa_cpsetup.PNG)

### Déclaration de confidentialité et les informations contact société

Nom de la société s’affiche comme titre du portail d’entreprise. Les informations de contact et les détails sont affichés pour les utilisateurs dans l’écran de l’informatique contacter le portail d’entreprise. La déclaration de confidentialité s’affiche lorsqu’un utilisateur clique sur le lien de la confidentialité.

|Nom de champ|Longueur maximale|Plus d’informations|
    |----------|------------------------|----------------|
    |Nom de la société|40|Ce nom s’affiche en tant que le titre de l’application portail d’entreprise. **Remarque**: les caractères Alpha-numériques uniquement. Ce champ ne prend pas en charge les caractères spéciaux.|
    |Nom du contact département informatique|40|Ce nom s’affiche dans la page **Contact informatique** .|
    |Numéro de téléphone du service informatique|20|Ce numéro de contact s’affiche dans la page **Contact informatique** .|
    |Adresse de messagerie du service informatique|40|Cette adresse contact s’affiche dans la page **Contact informatique** . Vous devez entrer une adresse de messagerie valide dans format **alias@domainname.com**.|
    |Informations supplémentaires|120|Ces informations sont affiche dans la page **Contact informatique** .|
    |URL de déclaration de confidentialité de société|79|Vous pouvez spécifier vos propres déclaration de confidentialité de société qui s’affiche lorsque les utilisateurs cliquent sur les liens de confidentialité à partir du portail d’entreprise. Vous devez entrer une URL valide dans le format https://www.contoso.com.|

### Prise en charge des contacts
Le site Web est présenté aux utilisateurs du portail d’entreprise afin de leur permettre d’accéder au support en ligne.

|Nom de champ|Longueur maximale|Plus d’informations|
    |----------|------------------------|----------------|
    |L’URL du site Web de support|150|Si vous avez un site Web de prise en charge que vous voulez que vos utilisateurs à utiliser, spécifiez l’URL ici. L’URL doit être placé dans le format https://www.contoso.com. Si vous ne spécifiez pas une URL, rien ne s’affiche pour le site Web de prise en charge dans la page **Contact informatique** dans le portail d’entreprise.|
    |Nom du site Web|40|Ce nom est le nom convivial qui s’affiche pour l’URL pour le site Web de prise en charge. Si vous spécifiez une URL de site Web de support et aucun nom convivial, **accédez au site Web informatique** puis s’affiche dans la page **Contact informatique** dans le portail d’entreprise.|


### Personnalisation de personnalisation de société

Vous pouvez personnaliser votre portail d’entreprise avec votre logo de société, nom de la société, couleur de thème et l’arrière-plan.

|Nom de champ|Plus d’informations|
    |----------|----------------|
    |Couleur de thème|Sélectionnez une couleur de thème à appliquer à l’application portail d’entreprise.|
    |Inclure le logo de société|Lorsque vous activez cette option, vous pouvez télécharger le logo de votre société à afficher dans votre portail d’entreprise. Vous pouvez télécharger deux logos : un logo qui s’affiche lorsque l’arrière-plan de l’application portail d’entreprise est blanc et un logo qui s’affiche lorsque l’arrière-plan de l’application portail d’entreprise utilise votre couleur de thème sélectionné. Chaque logo doit être un fichier .png ou .jpg, ont une résolution maximale de 400 x 100 pixels et être 750 Ko taille inférieure ou égale.|
    |Choisissez un arrière-plan pour [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)] application portail d’entreprise|Ce paramètre affecte l’arrière-plan de la [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)] uniquement l’application portail d’entreprise.|


Une fois que vous enregistrez vos modifications, vous pouvez utiliser les liens qui sont fournies au bas de la page du **Portail d’entreprise** de la console d’administration pour afficher le site Web portail d’entreprise. Ces liens ne peuvent pas être modifiés. Lorsqu’un utilisateur se connecte, ces liens affichent vos abonnements dans le portail d’entreprise.

## Attribuer une licence utilisateur Intune

Le **portail de gestion d’Office 365** vous permet d’ajouter des utilisateurs sur le nuage et attribuer des licences pour les comptes d’utilisateur sur le nuage et les comptes qui sont synchronisés depuis votre locale d’Active Directory à Azure Active Directory (AD Azure) manuellement.

1.  Connectez-vous au [portail de gestion d’Office 365](https://portal.office.com/Admin/Default.aspx) à l’aide de vos informations d’identification d’administrateur client.

2.  Sélectionnez le compte d’utilisateur que vous voulez attribuer une licence utilisateur Intune, puis la case à cocher **Microsoft Intune** sur les propriétés du compte utilisateur.

3.  Le compte d’utilisateur est maintenant ajouté au groupe d’utilisateurs Microsoft Intune, qui accorde les autorisations utilisateur à utiliser le service et inscrire leur appareil en gestion.

## Configurer la gestion des appareils
Après avoir configuré l’autorité périphériques mobiles, vous devez configurer la gestion des périphériques pour les systèmes d’exploitation que votre organisation souhaite prend en charge. Les étapes nécessaires pour configurer la gestion des appareils varient selon le système d’exploitation. Par exemple, le système d’exploitation Android ne nécessite pas rien dans la console d’administration Intune à faire. En revanche, Windows et iOS nécessitent une relation d’approbation entre les périphériques et Intune pour permettre la gestion.

Configurer la gestion pour les plates-formes suivantes :
- [Android](set-up-android-management-with-microsoft-intune.md)
- [iOS et Mac](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Windows PC et ordinateurs portables](set-up-windows-device-management-with-microsoft-intune.md)
- [Mobile Windows 10 et Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)

Vous pouvez également :
 - Utiliser le [compte du Gestionnaire de périphériques d’inscription](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) pour vous inscrire grand nombre d’appareils.
 - [Spécifier les périphériques appartenant à l’entreprise à l’aide de numéros IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) pour inscrire appareils et cibler stratégie.
