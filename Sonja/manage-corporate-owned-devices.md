---
title: "Gestion des appareils appartenant à l’entreprise | Microsoft Intune"
description: "Importer des périphériques appartenant à l’entreprise (CR) dans la gestion de différentes manières en fonction de l’appareil, comment il a été acheté et besoins de l’organisation."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 6c8a658532ba9e7367c12c62581486399ff77840
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# S’inscrire périphériques appartenant à l’entreprise avec Microsoft Intune
Organisation ou périphériques appartenant à l’entreprise (CR) peuvent être mis en gestion par Intune dans de différentes manières en fonction de l’appareil, comment il a été acheté et les besoins de l’organisation. Périphériques appartenant à l’entreprise peuvent également être inscrit et gérés par l’installation de l’application portail d’entreprise comme dans « mettre votre propre périphérique » scénarios (BYOD).

## Appareils iOS appartenant à l’entreprise
Ces méthodes d’inscription sont utiles pour « Choisir votre propre appareil » scénarios (CYOD) où l’organisation des achats les appareils pour les utilisateurs, mais souhaite conserver la gestion de l’appareil. Si votre organisation a acheté les appareils iOS, vous pouvez configurer avant d’inscription afin que l’appareil est géré à partir de la première fois que son utilisateur l’active. Intune prend en charge l’inscription par le biais [Appareil inscription d’un programme (PED) d’Apple](ios-device-enrollment-program-in-microsoft-intune.md) ou à l’aide de l’outil de configuration du Apple s’exécutant sur un ordinateur Mac pour [direct](ios-direct-enrollment-in-microsoft-intune.md) ou [L’Assistant de configuration](ios-setup-assistant-enrollment-in-microsoft-intune.md) d’inscription.

[Inscription des appareils iOS appartenant à l’entreprise](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## Gestionnaire de périphériques d’inscription
Organisations peuvent utiliser Intune pour gérer un grand nombre d’appareils mobiles avec un seul compte d’utilisateur appelé un compte du Gestionnaire d’inscription appareil. Après avoir créé un compte du Gestionnaire d’inscription appareil, ce compte peut être utilisé par un responsable d’inscription plus que les périphériques de cinq standards autorisés par défaut pour les utilisateurs normales. Inscription des appareils avec un responsable d’inscription appareil fonctionne uniquement pour les périphériques qui ne sont pas utilisés par un utilisateur spécifique. Ces périphériques sont bon pour les applications du point de vente ou de l’utilitaire, par exemple, mais incorrect pour les utilisateurs qui doivent y accéder à des ressources de messagerie ou de la société.

[S’inscrire périphériques appartenant à l’entreprise avec le Gestionnaire d’inscription device](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## S’inscrire appartenant à l’entreprise de bureau de Windows 10

Si votre organisation possède Azure Active Directory Premium (AADP) ou Suite de gestion de Enterprise (EM), vous pouvez [inscrire Windows 10 pour les entreprises](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview) et ils seront automatiquement marqués comme « entreprise appartenant » lorsque les utilisateurs d’ajouter leur travail compte professionnel ou scolaire.

## Identifiez les périphériques en tant que propriétaire d’entreprise

Périphériques appartenant à l’entreprise sont répertoriés sous forme **d’entreprise** sous **la propriété** dans les listes d’appareils. Équipements peuvent être identifiés en tant que propriétaire d’entreprise des façons suivantes :

 - [Inscrit avec le Gestionnaire d’inscription de périphériques (DEM)](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)
 - Inscrit auprès du [programme d’inscription (PED)](ios-device-enrollment-program-in-microsoft-intune.md) ou [Configuration du Apple](ios-setup-assistant-enrollment-in-microsoft-intune.md) d’Apple
 - [Predeclare appareils avec numéros IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)
 - [Azure inscription Active Directory/Enterprise Management Suite des appareils Windows 10](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview)

### Identité équipement mobile international (IMEI)

Les numéros d’identité (IMEI) uniques équipement mobile internationaux sont une propriété appareil courantes pour de nombreux fabricants d’appareil mobile. Les administrateurs Intune peuvent importer numéros IMEI pour appareils que propriétaire de la société. Lorsque l’appareil est géré par Intune, il est marqué comme un périphérique appartenant à l’entreprise.

[Spécifier les périphériques appartenant à l’entreprise avec les numéros d’identité (IMEI) international appareils mobiles](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)
