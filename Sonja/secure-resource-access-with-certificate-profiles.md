---
title: "Profils pour accéder aux ressources du certificat | Microsoft Intune"
description: "Sécuriser les VPN, Wi-Fi et accès à la messagerie avec un certificat est installé sur chaque appareil utilisateur."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0
ms.reviewer: kmyrup
ms.suite: ems
ms.openlocfilehash: b807ecdbd132692dc022bfa5f7a9418d3a614dfb
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Ressource accès sécurisé avec les profils de certificat dans Microsoft Intune
Lorsque vous autoriser l’accès aux ressources d’entreprise via VPN, Wi-Fi ou les profils de messagerie, vous pouvez protéger le niveau d’accès à l’aide d’un certificat est installé sur chaque appareil utilisateur. Voici comment procéder :

1. Vérifiez que vous disposez de l’infrastructure de certificats droite en place, comme décrit dans [l’infrastructure de certificat configurer pour SCEP](configure-certificate-infrastructure-for-scep.md) et [infrastructure de certificats configurer pour PFX](configure-certificate-infrastructure-for-pfx.md).

2. Installer un certificat racine ou une autorité de Certification (CA) intermédiaires sur chaque appareil afin que le périphérique reconnaît légitime votre autorité de certification. Pour ce faire, créez et déployez un **Profil de certificat approuvés**. Lorsque vous déployez ce profil, les appareils que vous gérez avec Intune demandent et reçoivent le certificat racine. Vous devez créer un profil distinct pour chaque plate-forme. Le **Profil de certificat approuvés** est disponible pour ces plateformes :
 -  iOS 8.0 et versions ultérieures
 -  Mac OS X 10.9 et version ultérieure
 -  Android 4.0 ou version ultérieure
 -  Windows 8.1 et versions ultérieures
 -  Windows Phone 8.1 et versions ultérieur

3. Créer des profils de certificat afin que les périphériques demander un certificat à utiliser pour l’authentification de VPN, Wi-Fi et accès à la messagerie, comme décrit dans [les profils de certificat Intune Configurer](configure-intune-certificate-profiles.md). Vous pouvez créer et déployer un **PKCS #12 (. Profil de certificat PFX)** *ou* un **Profil de certificat SCEP** pour appareils exécutant ces plateformes :

  -  iOS 8.0 et versions ultérieures
  -  Android 4.0 ou version ultérieure
  -  Windows 10 (ordinateur de bureau et mobiles) et version ultérieure

  Utiliser un **Profil de certificat SCEP** pour appareils exécutant ces plateformes :
    -   Mac OS X 10.9 et version ultérieure
    -   Windows Phone 8.1 et versions ultérieur

Vous devez créer un profil distinct pour chaque plate-forme. Lorsque vous créez le profil, l’associer avec le **Profil de certificat racine de confiance** que vous avez déjà créé.

> [!NOTE]           
> - Si vous n’avez pas une autorité de Certification d’entreprise, vous devez créer un.
>- Si vous décidez, selon votre plateformes d’appareil, pour utiliser le profil simplifié certificat d’inscription Protocol (SCEP), vous devez également configurer un serveur réseau périphérique d’inscription Service NDES.
>-  Si vous envisagez d’utiliser SCEP ou. Profils PFX, vous devez télécharger et configurer le connecteur Microsoft Intune certificat.
>-  Apprenez à configurer tous les services requis dans [infrastructure de certificats configurer pour SCEP](configure-certificate-infrastructure-for-scep.md) ou [infrastructure de certificats configurer pour PFX](configure-certificate-infrastructure-for-pfx.md).

### Étapes suivantes
- [Configurer l’infrastructure de certificats pour SCEP](configure-certificate-infrastructure-for-scep.md)
- [Configurer l’infrastructure de certificats pour PFX](configure-certificate-infrastructure-for-pfx.md)
- [Configurer les profils de certificat Intune](configure-intune-certificate-profiles.md)
