---
title: "Vue d’ensemble du cycle de vie MDM | Microsoft Intune"
description: "Découvrez comment Intune vous permet de gérer les périphériques dans son cycle de vie — à partir d’inscription, grâce à la configuration, déclassement éventuelle."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f6051fa7-133f-4712-86a5-e5f5bc5ab3c7
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: 8e769d5912de0a821add180053034ed14eb58537
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Vue d’ensemble de la politique de gestion des (périphériques mobiles) appareil mobile

Tous les appareils que vous gérez ont ce que nous appelons un *cycle de vie*. Intune peut vous aider à gérer ce cycle de vie — à partir d’inscription via la configuration et la protection, pour retirer le périphérique lorsque n’est plus nécessaire :

![Le cycle de vie appareil](./media/device-lifecycle.png "the Intune device lifecycle")

## S’inscrire
Gérer les stratégies de gestion (périphériques mobiles) celle du périphérique mobile avec une variété de téléphones et tablettes PC (iOS, Android, Windows et Mac OS X). Si vous devez être en mesure de gérer le périphérique, qui est généralement le cas pour les appareils appartenant à l’entreprise, la première étape consiste à [configurer l’inscription de l’appareil](enroll-devices-in-microsoft-intune.md). Vous pouvez également gérer PC Windows en vous abonnant les avec Intune (MDM) ou en [installant le logiciel client Intune](manage-windows-pcs-with-microsoft-intune.md).

## Configurer
Prise de vos périphériques inscrits est uniquement la première étape. Pour tirer parti de tous les Intune offres et pour vous assurer que vos périphériques sont sécurisés et conformes aux normes de l’entreprise, vous pouvez choisir parmi un large éventail de stratégies. Ils vous permettent de configurer presque tous les aspects d’équipements gérés comment fonctionner. Par exemple, les utilisateurs doivent avoir un mot de passe sur les appareils qui contiennent des données d’entreprise ? Vous pouvez demander une. Offrez-vous une entreprise Wi-Fi ? Vous pouvez le configurer automatiquement. Voici les types d’options de configuration disponibles :

- [**Stratégies de configuration**](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md). Ces stratégies vous permettent de configurer les fonctionnalités et les fonctionnalités des périphériques que vous gérez. Par exemple, vous pourriez nécessitent l’utilisation d’un mot de passe sur les téléphones Windows ou désactiver l’utilisation de la caméra sur iPhone.
- [**Stratégies d’accès de ressources de société**](enable-access-to-company-resources-with-microsoft-intune.md). Lorsque vous laissez vos utilisateurs à accéder à leur travail sur leur appareil personnel, ceci peut vous présenter d’aspects liés. Par exemple, comment vous assurer que tous les appareils que vous avez besoin d’accéder à messagerie d’entreprise sont correctement configurés ? Comment vous assurer que les utilisateurs peuvent accéder au réseau d’entreprise avec une connexion VPN sans connaître les paramètres complexes ? Intune peut vous aider à réduire cette charge en configurant automatiquement les appareils que vous gérez pour accéder aux ressources d’entreprise courants.
- [**Stratégies de gestion des PC Windows (avec le logiciel client Intune)**](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md). Lors de l’inscription PC Windows avec Intune vous donne les plupart des fonctionnalités de gestion des périphériques, Intune continue à prendre en charge la gestion des PC Windows avec le logiciel client Intune. Si vous avez besoin d’informations sur certains des tâches que vous pouvez effectuer avec PC, effectuez les étapes suivantes.

## Protéger
Dans le monde informatique moderne, protection des équipements des accès non autorisés est une des tâches plus importantes que vous devez effectuer. Outre les éléments dans l’étape **configurer** du cycle de vie appareil, Intune offre ces fonctionnalités qui protéger les périphériques que vous gérez tout accès non autorisé ou attaques :
- [**L’authentification multifacteur**](protect-windows-devices-with-multi-factor-authentication.md). Ajout d’un niveau supplémentaire d’authentification utilisateur se-ins permettent de sécuriser davantage d’appareils. Les appareils Windows, Windows Phone et Windows Mobile proposent une authentification multifacteur nécessite un deuxième niveau de l’authentification, tel qu’un appel téléphonique ou message texte, avant que les utilisateurs peuvent accéder.
- [**Paramètres de compte Microsoft Passport**](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md). Microsoft Passport est une méthode de connexion de remplacement qui permet aux utilisateurs d’utiliser un *mouvement*, tel qu’une empreinte ou Windows Hello : se connecter sans avoir besoin d’un mot de passe.
- [**Stratégies pour protéger des ordinateurs Windows (avec le logiciel client Intune)**](policies-to-protect-windows-pcs-in-microsoft-intune.md). Lorsque vous gérez un PC Windows à l’aide du logiciel client Intune, stratégies sont disponibles pour vous permettre de contrôler les paramètres pour le pare-feu Windows sur les PC que vous gérez Endpoint Protection et mises à jour logicielles.

## Retirer
Lorsqu’un appareil obtient perte ou de vol, quand il doit être remplacée, ou lorsque les utilisateurs placent à un autre endroit, il est généralement temps de [retrait ou réinitialiser](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) l’appareil. Il existe plusieurs façons, vous pouvez le faire, y compris la réinitialisation de l’appareil, suppression de la gestion des et supprimer les données d’entreprise dessus.
