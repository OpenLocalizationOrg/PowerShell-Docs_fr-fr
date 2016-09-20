---
title: "Protéger les données et applications | Microsoft Intune"
description: 
keywords: "Cette rubrique décrit les différents Intune les fonctionnalités qui sont disponibles pour vous aider à protéger vos données et applications d’entreprise."
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: cf2ef1510aa9dafeddf54855123c826c9ccc2fd0
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Protéger les applications et les données avec Microsoft Intune


Intune protège les données de société à travers plusieurs couches d’assistance.  Au niveau de la couche identité, accès conditionnel protège l’accès aux services en autorisant uniquement l’accès à partir d’appareils gérées et la conformité.  Au niveau des applications clientes, gestion de l’application mobile (MAM) protège les pertes de données en empêchant les données à déplacer vers des applications non protégées ou emplacements de stockage et par effacer les données lors de la perte ou de vol un appareil.  Ces deux niveaux de protection doit être utilisé ensemble afin de sécuriser les données tout en conservant vos collaborateurs mobiles productif.

Une première étape importante à la protection des données de la société consiste à mettre en œuvre access conditionnelle en vérifiant que périphériques utilisés pour accéder à ces données sont à l’aide de protection de sécurité tels que le mot de passe fort, du chiffrement et sont jailbroken pas. Microsoft Intune vous donne la possibilité de définir des conditions les appareils doivent être conformes, avant de pouvoir accéder à votre messagerie d’entreprise et les données.

[Accès conditionnel](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) est déterminé par deux types de stratégies que pouvant être définies dans Intune :
- [Stratégies de conformité](introduction-to-device-compliance-policies-in-microsoft-intune.md) déterminer la conformité d’un appareil. Ils évaluer les paramètres et conditions comme :
  - Code confidentiel et les mots de passe : vous pouvez créer des règles afin d’exiger des mots de passe avant de déverrouillage d’un appareil, la complexité de mot de passe et d’autres paramètres de mot de passe.
  - Chiffrement : Vous pouvez limiter l’accès aux appareils qui sont chiffrés.
  - Appareil n’est pas jailbroken ou associés à une racine : Intune détecte si un périphérique inscrit est jailbroken, et vous pouvez définir la stratégie pour bloquer l’accès sur des appareils.
- [Les stratégies d’accès conditionnelle](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) sont configurés pour un service particulier tels qu’Exchange Online ou SharePoint Online. Pour chaque service, vous pouvez définir les groupes d’utilisateurs, ces politiques doit être appliqué à. Par exemple, vous pouvez vous assurer que tout le monde Finances service peut uniquement accès envoyer par courrier électronique à partir d’appareils inscrits et la conformité.

Sécuriser l’accès aux ressources de l’entreprise est uniquement la première étape de protection des données de la société. Vous devez toujours la possibilité de protéger les données après avoir accédé sur l’appareil. Les données peuvent désormais être copiées, déplacées, enregistrées dans un autre emplacement ou partagées. Intune résout ce problème grâce à la possibilité pour restreindre le déplacement de données en créant un ensemble de règles, telles que :
- Bloc de copier-coller ou empêcher le transfert de données en dehors du contexte de travail.
- Empêcher le stockage cloud sauvegarde sur personnel, empêcher les enregistrer en tant que.
- Sécuriser l’accès de l’application en nécessitant les informations d’identification d’entreprise ou ÉPINGLER/code secret.
- Ouvrir tous les liens web dans le navigateur gérées Intune.

Cet ensemble de règles sont appelées [stratégies de gestion des (MAM) de l’application mobile](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).  Stratégies MAM peuvent être appliquées aux applications en cours d’exécution sur les périphériques qui ne peuvent pas être gérés par vous.  

Vous pouvez protéger vos données d’entreprise à l’aide de stratégies MAM pour appareils sont **inscrits à Intune**, périphériques **inscrit et gérés par un autre logiciel tiers MDM**ou un appareil est **pas inscrit dans n’importe quelle solution périphériques mobiles**, comme l’employé appartenant appareils.

Pour associer une application à une stratégie MAM, l’application doit intégrer le Kit de développement logiciel (SDK) Microsoft Intune application, ou utilisez l’outil de habillage application.

Applications telles que des applications Microsoft Office ont l’intégrées application SDK. Vous trouverez la liste complète des applications pris en charge dans la [Galerie des applications mobiles Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) dans la page partenaires d’application Intune Microsoft. Choisissez l’application pour afficher les scénarios pris en charge, plateformes et ou non l’application prend en charge plusieurs identité.

Vous pouvez également [activer votre ligne personnalisées des applications d’entreprise](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md) à utiliser avec les stratégies MAM.

En plus de restriction de déplacement de données, si un appareil obtient perte ou de vol, ou si l’utilisateur ne fonctionne plus avec votre société, vous pouvez [Réinitialiser sélectivement des données de la société](wipe-managed-company-app-data-with-microsoft-intune.md), laissant les données personnelles uniquement.
