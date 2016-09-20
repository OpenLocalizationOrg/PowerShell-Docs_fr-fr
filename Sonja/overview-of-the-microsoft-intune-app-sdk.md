---
title: "Vue d’ensemble du Kit application Intune | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ef1751bb-3a2f-4662-a922-38c076869eb3
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: 4d5e10ecc50387350eb7f1746603b7b7602190a4
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Vue d’ensemble du Kit application Intune
Le SDK application Intune est disponible pour iOS et Android plateforme et Active les fonctionnalités de gestion de l’application mobile avec Microsoft Intune. En outre, nous nous efforçons de réduire la quantité de modifications de code requises du développeur. Vous constaterez que vous pouvez activer la plupart des fonctionnalités SDK sans modifier le comportement de votre application. Pour l’utilisateur final améliorée et expérience de l’administrateur informatique, vous pouvez utiliser notre API pour personnaliser le comportement de votre application des fonctionnalités qui nécessitent votre participation d’application. 

Une fois que vous avez activé votre application, les administrateurs informatiques peuvent déployer des stratégies aux applications Intune gérée et tirez parti de ces fonctionnalités protège les données d’entreprise.

# Fonctionnalités
## Contrôler la capacité des utilisateurs à déplacer des documents d’entreprise
Les administrateurs informatiques peuvent contrôler déplacement des fichiers de documents d’entreprise dans les applications Intune gérée. Par exemple, ils peuvent déployer une stratégie qui désactive les applications de sauvegarde de fichier de sauvegarde des données d’entreprise dans le cloud.  

## Configurer les restrictions du Presse-papiers
Les administrateurs informatiques peuvent configurer le comportement de Presse-papiers dans les applications Intune gérée. Par exemple, ils peuvent déployer une stratégie afin que les utilisateurs finaux ne peuvent pas utiliser le Presse-papiers pour couper/copier à partir d’une application gérées Intune et la coller dans une application non géré.

## Configurer les restrictions de capture d’écran
Les administrateurs informatiques peuvent empêcher les utilisateurs de capture de l’écran si une application gérées Intune s’affiche. L’application cette restriction empêche la capture et la version finale du contenu d’entreprise confidentiel. Cette fonctionnalité est disponible uniquement pour les appareils android. 

## Appliquer le chiffrement de données enregistrées
Les administrateurs informatiques peuvent appliquer une stratégie qui garantit que les données enregistrées par l’application à l’appareil sont chiffrées.

## Effacer à distance des données d’entreprise
Les administrateurs informatiques peuvent effacer à distance des données d’entreprise à partir d’une application gérées Intune lorsque l’appareil est unenrolled à partir de Microsoft Intune. Cette fonctionnalité est basé sur l’identité et supprime uniquement les fichiers associés à l’identité d’entreprise de l’utilisateur final. Pour ce faire, la fonctionnalité requiert la participation de l’application. L’application peut spécifier l’identité pour laquelle la réinitialisation doit avoir lieu en fonction des paramètres utilisateur. En l’absence de ces paramètres utilisateur spécifié à partir de l’application, le comportement par défaut consiste à réinitialiser le répertoire de l’application et avertir l’utilisateur final que l’accès aux ressources société a été supprimé. 

## Appliquer l’utilisation d’un navigateur gérée
Les administrateurs informatiques pouvant imposer l’utilisation d’un navigateur gérée lors de l’ouverture des liens dans les applications gérées Intune. À l’aide du navigateur gérée permet de garantir que les liens qui s’affichent dans des messages électroniques (qui se trouvent dans un client de messagerie gérées Intune) sont conservés dans le domaine de Intune Microsoft Intune gèrent les applications.

## Appliquer une stratégie de code confidentiel
Les administrateurs informatiques appliquer une stratégie de code confidentiel quand une application gérées Intune est démarrée. Cette stratégie permet de garantir que les utilisateurs finaux qui inscrit leurs appareils avec Microsoft Intune sont les personnes mêmes qui débutent les applications. Lorsque les utilisateurs finaux configurez son code confidentiel, Intune application SDK utilise Azure Active Directory pour vérifier les informations d’identification d’utilisateurs finaux contre les informations d’identification de périphérique d’inscription. 

## Les utilisateurs doivent entrer des informations d’identification avant qu’ils puissent commencer des applications
Les administrateurs informatiques peuvent que les utilisateurs entrent leurs informations d’identification avant que les utilisateurs peuvent démarrer une application Intune géré. Intune application SDK utilise Azure Active Directory pour fournir une expérience authentification unique, où les informations d’identification, entrées une seule fois, sont réutilisées pour les connexions suivantes. Nous prennent également en charge l’authentification de l’identité des solutions de gestion des [fédérées avec Azure Active Directory](/active-directory/active-directory-aadconnect-federation-compatibility). 

## Vérifier l’intégrité du dispositif et conformité
Les administrateurs informatiques peuvent une vérification du fonctionnement de l’appareil et sa mise en conformité avec les stratégies d’entreprise avant les utilisateurs finaux accéder aux applications gérées Intune. Sur la plateforme iOS, cette stratégie vérifie si le périphérique a été jailbroken. Sur la plateforme Android, cette stratégie vérifie si le périphérique a été racine.  


