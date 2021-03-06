---
title: Configurer la gestion des appareils Windows avec Microsoft Intune | Microsoft Intune
description: Activer la gestion des appareils mobiles (MDM) pour les PC Windows, y compris les appareils Windows 10 avec Microsoft Intune.
keywords: 
author: NathBarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
ms.openlocfilehash: 6b6249c2429af6c9dd85d5044dd8e0cc1f4d9a67
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Configurer la gestion des appareils Windows

En tant qu’un administrateur Intune, vous pouvez activer l’inscription et la gestion pour les PC Windows de deux façons :

- L' **[inscription automatique avec Azure AD](#azure-active-directory-enrollment)** - Windows 10 et les utilisateurs de Windows 10 Mobile inscrire leur appareil en ajoutant un compte professionnel ou scolaire à l’appareil
- **[Inscription de l’application portail d’entreprise](#company-portal-app-enrollment)** - Windows 8.1 et des générations ultérieures inscrite en téléchargement et installation de l’application portail d’entreprise, puis en saisissant leur travail ou scolaire des informations d’identification de compte dans l’application.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## Inscription de l’application portail configurer société
Vous pouvez laisser les utilisateurs à inscrire leur appareil en installant et inscrire leur appareil avec l’application portail d’entreprise Intune. Création d’un DNS CNAME permet aux utilisateurs de se connecter et inscrire au programme d’Intune sans entrer de nom de serveur.

1. **Configurer la Intune**<br>
Si vous n’avez pas déjà, préparer pour la gestion des appareils mobiles en [définissant l’autorité de gestion des périphériques mobiles](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) comme **Microsoft Intune** et la configuration MDM.

2. **Créer des enregistrements CNAME** (facultatif)<br>Créer des enregistrements de ressource **CNAME** DNS pour le domaine de votre entreprise simplifier l’inscription. Création d’entrées CNAME DNS est facultative, création d’enregistrements CNAME facilite l’inscription des utilisateurs. Si aucune inscription d’un enregistrement CNAME n’est trouvée, les utilisateurs sont invités à entrer manuellement le nom du serveur MDM `https://manage.microsoft.com`.  Les enregistrements de ressource CNAME doivent contenir les informations suivantes :

  |TYPE|Nom d’hôte|Pointe vers|DURÉE DE VIE|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment s.manage.microsoft.com |1 heure|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 heure|

  `EnterpriseEnrollment-s.manage.microsoft.com` – Prend en charge une redirection au service Intune avec la reconnaissance domaine de nom de domaine de messagerie

  `EnterpriseRegistration.windows.net` – Prend en charge les appareils Windows 8.1 et Windows 10 Mobile qui seront enregistré avec Azure Active Directory à l’aide de leur compte professionnel ou scolaire

  Si votre société utilise plusieurs domaines pour les informations d’identification utilisateur, créer des enregistrements CNAME pour chaque domaine.

  Par exemple, si le site Web de votre entreprise est contoso.com, vous voulez créer un enregistrement CNAME dans le système DNS qui redirige EnterpriseEnrollment.contoso.com vers EnterpriseEnrollment s.manage.microsoft.com. Modifications des enregistrements DNS peuvent prendre jusqu'à 72 heures de se propager. Vous ne pouvez pas vérifier le changement DNS Intune jusqu'à ce que l’enregistrement DNS transmet.

3.  **Vérifier CNAME**<br>Dans la [console d’administration Intune](http://manage.microsoft.com), cliquez sur **administrateur** &gt; **Gestion des appareils mobiles** &gt; **Windows**. Tapez l’URL du domaine vérifié du site Web de société dans la zone **Spécifiez un nom de domaine vérifié** , puis sur **La détection automatique de Test**.

  ![Boîte de dialogue de gestion de périphérique Windows](../media/enroll-intune-winenr.png)

4.  **Étapes facultatives**<br>L’étape de **chargement de version test ajouter clés** n’est pas nécessaire pour Windows 10. L’étape du **Certificat de signature de télécharger le Code** est nécessaire uniquement si vous envisagez de distribuer-métier (métier) applications aux périphériques n’est pas disponibles à partir du Windows Store. [Pour en savoir plus](set-up-windows-phone-8.0-management-with-microsoft-intune.md)

6.  **Informer les utilisateurs**<br>Vous devez indiquer à vos utilisateurs comment inscrire leur appareil et à quoi s’attendre une fois qu’il est enregistré dans la gestion des :
      - [Ce qu’indiquer à vos utilisateurs finaux sur l’utilisation de Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
      - [Guide de l’utilisateur final pour les appareils Windows](../enduser/using-your-windows-device-with-intune.md)

### Voir aussi
[Préparer d’inscription des appareils dans Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)
