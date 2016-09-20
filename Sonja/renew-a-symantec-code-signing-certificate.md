---
title: "Renouveler un certificat de signature de code Symantec d’entreprise à utiliser avec Intune | Microsoft Intune"
description: "Conseils pour renouveler les certificats Symantec permet de gérer certains appareils mobiles Windows et Windows Phone"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c4813044-a925-4273-b0ec-e992fd55850a
ms.reviewer: damionw
ms.suite: ems
ms.openlocfilehash: 09b5bf6501acfa7743555737d9e69a6141dda8ac
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Renouveler un certificat de signature de code Symantec d’entreprise pour appareils Windows

Le certificat de Symantec permet de gérer certains appareils mobiles Windows et Windows Phone doit être renouvelé périodiquement. Pour les appareils Windows Phone 8.0, une application portail d’entreprise signée et le certificat de signature de code sont nécessaires pour l’inscription de l’appareil. Une version ultérieure de Windows Phone périphériques peut utiliser l’application portail d’entreprise téléchargée à partir du magasin. Un certificat de signature de code est également être requis pour le déploiement des applications métier.

## Comment renouveler le certificat de signature de code Symantec enterprise

1.  Recherchez un message électronique de renouvellement envoyé à partir de Symantec environ 14 jours avant l’expiration du certificat. Ce courrier électronique contient des instructions de Symantec sur le renouvellement de votre certificat d’entreprise.

    Pour plus d’informations sur les certificats Symantec, visitez [www.symantec.com](http://www.symantec.com) ou appeler 1-877-438-8776 ou 1-650-426-3400.

2.  Accédez au site Web (exemple : [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)) et connectez-vous à l’aide de l’ID de l’éditeur Symantec et courrier électronique adressé associée au certificat. Pensez à utiliser le même ordinateur pour démarrer le renouvellement que vous utiliserez pour télécharger le certificat.

3.  Une fois que le renouvellement est approuvé et payé pour, téléchargez le certificat.

## Comment faire pour installer le certificat mis à jour pour Windows Phone 8.0

1.  Télécharger et se la dernière portail d’entreprise Windows Phone situé ici : [http://www.microsoft.com/en-us/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060).

2.  Ouvrez votre Console d’Administration Intune ([https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)) et accédez à **Admin**, **Gestion des appareils mobiles** &gt; **Windows Phone** et cliquez sur **Télécharger l’application signé**.

3.  Télécharger l’application portail d’entreprise nouvellement signé. Vous devez le SSP.xap nouvellement signé et la nouvelle. Fichier PFX que vous avez reçu de Symantec ou le jeton de l’inscription d’application qui a été créé avec ce nouveau. Fichier PFX.

4.  Lorsque le téléchargement est terminé, supprimez l’ancienne version de l’application portail d’entreprise dans l’espace de travail **logiciel** dans la Console de gestion Intune.

5.  Signer toutes les applications de secteur d’activité entreprise en utilisant le même certificat et téléchargez et remplacer des applications existantes.

Fournir un fichier SSP.xap signé est actuellement le seul moyen pour fournir le code mis à jour le certificat de signature. Pour prendre en charge des applications métier connectées, vous devez vous connecter et télécharger une application portail d’entreprise, même si vos utilisateurs installent l’application portail d’entreprise à partir du magasin.

## Comment installer le certificat mis à jour pour Windows Phone 8.1 et des générations ultérieures

1.  Télécharger et se le portail d’entreprise Windows Phone plus récente à partir du centre de téléchargement situé ici : [http://www.microsoft.com/en-us/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060).

2.  Ouvrez la [Console d’Administration Intune](https://admin.manage.microsoft.com) (https://admin.manage.microsoft.com) et accédez à **administrateur** &gt; **Gestion des appareils mobiles** &gt; **Windows Phone** et cliquez sur **Télécharger l’application signé**.

3.  Télécharger l’application portail d’entreprise nouvellement signé. Vous devez le SSP.xap nouvellement signé et la nouvelle. Fichier PFX que vous avez reçu de Symantec ou le jeton de l’inscription d’Application qui a été créé avec ce nouveau. Fichier PFX.

4.  Lorsque le téléchargement est terminé, supprimez l’ancienne version de l’application portail d’entreprise dans l’espace de travail **logiciel** .

5.  Connectez-vous à toutes les nouvelles et mises à jour les applications professionnelles d’entreprise à l’aide du nouveau certificat. Applications existantes est inutile d’être démissionné et redéployé.


### Voir aussi
[Configurer la gestion de Windows Phone 8.0](set-up-windows-phone-8.0-management-with-microsoft-intune.md)
[configurer la gestion de Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)
