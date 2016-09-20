---
title: Configurer la gestion de Mac et iOS | Microsoft Intune
description: "Activer la gestion des appareils mobiles (MDM) pour les appareils iOS, y compris iPad et iPhone ainsi que les périphériques de Mac OS X avec Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 566a1bbf353921257b4ab7c7c0b73aac987c2085
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Configurer l’iOS et gestion des périphériques Mac
Pour configurer votre iOS ou appareil Mac, vous pouvez trouver de l’aide [ici](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md).

Gestion des appareils mobiles Intune de l’iPad, iPhone et périphériques de Mac OS X et donner accès à la messagerie d’entreprise et les applications. Un certificat de service (APNs) de Notification Push Apple est requis pour Intune gérer les appareils iOS et Mac. Une fois que le certificat est ajouté au Intune, les utilisateurs peuvent installer l’application portail d’entreprise pour inscrire leur appareil ou l’administrateur peut configurer la [Gestion des appareils iOS appartenant à l’entreprise](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

1.  **Configurer la Intune**<br>
    Si vous n’avez pas déjà, préparer pour la gestion des appareils mobiles en [définissant l’autorité de gestion des périphériques mobiles](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) comme **Microsoft Intune** et la configuration MDM.

2.  **Obtenir un demande de signature de certificat**<br>
    En tant qu’administrateur, ouvrez la [console d’administration Microsoft Intune](http://manage.microsoft.com), accédez à **Administration** &gt; **Gestion des appareils mobiles** &gt; **iOS et Mac OS X** &gt; **télécharger un certificat APNs**, puis cliquez sur **Télécharger la demande de certificat APNs**. Enregistrez le certificat de signature d’un fichier de demande (.csr) localement. Le fichier .csr est utilisé pour demander un certificat de relation de gestion de la confidentialité à partir du portail Apple Push Certificates Portal.

    ![Télécharger la boîte de dialogue certificat APNs](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Obtenir un certificat de service de Notification Push Apple**<br>
    Accédez au [Portail Apple Push Certificates Portal](http://go.microsoft.com/fwlink/?LinkId=269844) et connectez-vous avec votre identifiant Apple société pour créer le certificat APNs en utilisant le fichier .csr. Après avoir cliqué sur **Télécharger** sur Portal de certificat d’Apple Push, vous recevez un fichier .json qui ne peuvent pas être utilisé pour APNs. Terminer le téléchargement et revenir à la portail Apple Push Certificates Portal certificats **pour les serveurs tiers** et cliquez sur **Télécharger**.

    Téléchargez le certificat APNs (.pem) et enregistrez le fichier en local. Cet identifiant Apple doit être utilisé à l’avenir pour renouveler votre certificat APNs.

4.  **Ajouter le certificat APNs Intune**<br>
    Dans la [console d’administration Microsoft Intune](http://manage.microsoft.com), accédez à **Administration** &gt; **Gestion des appareils mobiles** &gt; **iOS et Mac OS X** &gt; **télécharger un certificat APNs**, puis cliquez sur **Télécharger le certificat APNs**. **Accédez** au certificat (.pem) de fichier et cliquez sur **Ouvrir** , puis entrez votre **Identifiant Apple**. Avec le certificat APNs, Intune peut s’inscrire et gérer les appareils iOS en appuyant stratégie sur des appareils mobiles inscrits.

5.  **Indiquer aux utilisateurs comment accéder aux ressources d’entreprise avec le portail d’entreprise**<br>
    Vos utilisateurs devez savoir comment inscrire leur appareil et à quoi s’attendre une fois qu’il est enregistré dans la gestion.
    - [Ce qu’indiquer à vos utilisateurs finaux sur l’utilisation de Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Guide de l’utilisateur final pour appareils iOS et Mac](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md)

Si votre société ou organisation des achats appareils iOS pour les utilisateurs, ces appareils peuvent également être inscrits pour la gestion des [appareils iOS appartenant à l’entreprise](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

### Voir aussi
[Préparer d’inscription des appareils dans Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)
