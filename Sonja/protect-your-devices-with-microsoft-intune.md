---
title: "Protéger les périphériques | Microsoft Intune"
description: "Découvrez quelques-unes des méthodes permettant de Intune que vous protégez vos appareils contre l’accès non autorisé et autres menaces."
keywords: 
author: Robstackmsft
manager: angrobe
ms.date: 09/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: af47644a4d9808ee43a80e8e211ae82b738080aa
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Protéger les périphériques avec Microsoft Intune

Microsoft Intune propose un ensemble complet de fonctionnalités pour vous aider à protéger les appareils que vous gérez et les données stockées sur ces appareils. Lisez cette rubrique pour découvrir les notions de base de ces fonctionnalités et pour savoir comment procéder pour en savoir plus.

## Approches générales pour protéger tous les périphériques

### Configuration de l’appareil
De Intune [stratégies de configuration](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md), vous aident à Protégez et configurez les périphériques en contrôlant une multitude de paramètres et fonctionnalités. Par exemple :
- Vous pouvez limiter l’utilisation des fonctionnalités de matériel sur le périphérique tels que la caméra ou Bluetooth.
- Vous pouvez configurer les applications conformes et non conformes. Vous serez averti si une application non conforme est installée (et certaines plateformes réellement peuvent se bloquer l’installation).

### Réinitialiser les codes secrets lorsque les utilisateurs sont verrouillés déconnecter leurs appareils
Étant donné que la première étape de protection des données d’entreprise sur les appareils mobiles est afin d’exiger un code secret pour utiliser le périphérique, parfois vous avez réinitialiser [un code secret](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) et aider un employé à faire, soit en supprimant le code secret ou définir un mot de passe temporaire à distance. Vous pouvez également [Verrouiller un appareil à distance](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) si elle est perte ou de vol.

### Éliminer les appareils et supprimer des données
Lorsqu’un appareil doit être [supprimé de la gestion Intune](retire-devices-from-microsoft-intune-management) (par exemple, un utilisateur quitte ou perte ou de vol de l’appareil), il est probable que vous voulez supprimer des données à partir de cet appareil. Intune fournit une plage de méthodes afin de que garantir la sécurité de vos données d’entreprise.

### Besoin de périphériques pour respecter les exigences en
Fonctionnalités de Intune [des stratégies de conformité appareil](introduction-to-device-compliance-policies-in-microsoft-intune) qui vous permettent d’évaluer (et dans certains cas, mettre à jour) périphériques qui ne sont pas compatibles avec les règles que vous spécifiez. Par exemple, vous pouvez signaler sur les appareils iOS qui sont jailbroken, si les périphériques sont chiffrés, ou si les appareils Windows 10 sont signalées comme exact par le Service Attestation santé.

### Protéger les applications et les données qu’ils utilisent
Intune vous offre une variété de fonctionnalités pour vous aider à protéger les applications et leurs données. Par exemple, stratégies de gestion des (MAM) application mobile peuvent empêcher que les données sauvegardées à partir d’une application protégée, restreindre copier et coller dans d’autres applications, exiger un code confidentiel accéder à une application et bien plus encore. Pour plus d’informations sur la protection des applications, voir [protéger applications et des données avec Microsoft Intune](protect-apps-and-data-with-microsoft-intune)

## Fonctionnalités supplémentaires pour les appareils Windows

### Ajouter un niveau de protection supplémentaire pour appareils Windows
[L’authentification multifacteur (MFA)](protect-windows-devices-with-multi-factor-authentication.md) est une pratique plus sécurisée de l’authentification des utilisateurs d’appareils Windows et Windows Phone sur le réseau.  Avec l’authentification Multifacteur, les utilisateurs ont besoin confirmer son identité au-delà de nom d’utilisateur et mot de passe, via un appel téléphonique ou message texte.

### Contrôle Windows Hello pour les paramètres sur les appareils Windows
Intune vous permet d’intégrer avec [Windows Hello entreprise](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) (anciennement Microsoft Passport) qui est une connexion méthode alternative pour Windows 10 et versions ultérieures qui utilise Active Directory, ou un compte Azure Active Directory pour remplacer un mot de passe, une carte à puce ou une carte à puce virtuelle.

## Fonctions supplémentaires pour les appareils iOS

### Ignorer l’Activation de verrou sur les appareils iOS
Verrouiller l’activation est une fonctionnalité qui vous permettent de protéger les périphériques des utilisateurs en demandant leur ID Apple et le mot de passe doivent être renseignées avant tout le monde peut effacer ou réactiver le périphérique. Toutefois, cela peut entraîner des problèmes, par exemple, si l’utilisateur quitte l’entreprise sans supprimer le verrou. [éviter de verrouiller l’Activation iOS](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md) peut vous aider en supprimant le verrou à partir d’appareils iOS contrôlés qui vous permet de réaffecter ou les supprimer.



## Protéger les PC Windows gérés par le client Intune
Intune continue à prendre en charge les stratégies de sécurité pour les PC Windows ne s’inscrire, mais gérer avec le logiciel Intune ordinateur client. Pour savoir comment ces stratégies peuvent vous aider que vous sécurisez votre PC Windows, consultez [utiliser des stratégies pour protéger Windows PC qui exécutent le logiciel client Intune](policies-to-protect-windows-pcs-in-microsoft-intune.md).
