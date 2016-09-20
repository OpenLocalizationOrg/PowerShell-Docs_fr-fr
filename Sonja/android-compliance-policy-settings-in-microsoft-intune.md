---
title: "Paramètres de stratégie de conformité pour les appareils Android | Microsoft Intune"
description: "Cette rubrique décrit les paramètres de stratégie de conformité appareil pour les appareils Android."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: cf1fde5b5ed55552e573c724b6165203033683da
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Paramètres de stratégie de conformité pour les appareils Android dans Microsoft Intune

Les paramètres de stratégie décrites dans cette rubrique s’applique aux appareils exécutant Android 4.0 ou version ultérieure, Samsung KNOX 4.0 ou version ultérieure.

Si vous recherchez des informations sur d’autres plateformes, sélectionnez une des opérations suivantes :
> [!div class="op_single_selector"]
- [Paramètres de stratégie de conformité pour les appareils iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Paramètres de stratégie de conformité pour les appareils Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## Paramètres de sécurité système
### Mot de passe
- **Exiger un mot de passe pour la déverrouiller les appareils mobiles :** Définir sur **Oui** pour obliger les utilisateurs à entrer un mot de passe avant de pouvoir accéder à leur appareil.

-  **Longueur minimale du mot de passe :** Spécifier le nombre minimal de chiffres ou de caractères que le mot de passe doit contenir.

- **Qualité de mot de passe :** Activez ce paramètre pour configurer le mot de passe pour les appareils Android. Choisir :
  -   **Sécurité faible biométrique**
  - **Obligatoire**
  -   **Au moins numérique**
  -   **Au moins alphabétique**
  -   **Au moins alphanumérique**
  -   **Alphanumérique par des symboles**

- **Minutes d’inactivité avant de mot de passe est nécessaire :**  Spécifie la durée d’inactivité avant que l’utilisateur doit retaper son mot de passe.

- **Expiration du mot de passe (jours) :** Sélectionnez le nombre de jours avant l’expiration du mot de passe de l’utilisateur et ils doivent créer un nouvel identifiant.

- **N’oubliez pas de l’historique de mot de passe :** Utilisez ce paramètre conjointement avec **éviter la réutilisation d’anciens mots de passe** pour empêcher l’utilisateur de créer des mots de passe utilisés précédemment.

- **Éviter la réutilisation des mots de passe précédents :** Si **l’historique de mémoriser mot de passe** est sélectionnée, indiquez le nombre de mots de passe précédemment utilisés ne peut pas être réutilisée.

- **Exiger un mot de passe lorsque l’appareil est retournée à partir d’un état d’inactivité :** Ce paramètre doit être utilisé avec la dans le paramètre de **Minutes d’inactivité avant de mot de passe est requis** . Les utilisateurs finaux êtes invités à entrer un mot de passe pour accéder à un périphérique qui a été inactif pendant la durée spécifiée dans le paramètre de **Minutes d’inactivité avant de mot de passe est requis** .

### Chiffrement
- **Exiger le chiffrement sur appareil mobile :** Définir sur **Oui** pour exiger des appareils à chiffrer afin de vous connecter à des ressources. Périphériques sont chiffrés lorsque vous configurez le paramètre **Exiger un mot de passe pour la déverrouiller les appareils mobiles**.

## Paramètres du périphérique santé et de sécurité

- **Périphérique ne doit pas être jailbroken ou associés à une racine :** Si vous activez ce paramètre, appareils jailbroken seront évaluées comme non conformes.
- **Exiger que les périphériques empêchent l’installation des applications d’origine inconnue (Android 4.0 ou version ultérieure)** Bloc qu’aux appareils dotés du **sécurité > inconnue** activé sur le périphérique, ce paramètre est activé et définissez-la sur **Oui**.  
>[!IMPORTANT]
>Applications à chargement latéral nécessite que le paramètre **inconnue** est activé.  Vous ne devez appliquer cette stratégie de conformité que si vous n’êtes pas à chargement latéral Android applications sur les appareils.

- **Exiger que débogage USB est désactivé (Android 4.2 ou version ultérieure)**: ce paramètre spécifie s’il faut détecter la USB option sur le périphérique de débogage est activée.
- **Les appareils aient activés appareil d’analyse des menaces (4.2 4.4 Android)**: ce paramètre spécifie que la fonctionnalité de **vérification applications** est activée sur le périphérique.
- **Correctif de sécurité pour Android minimale niveau (Android 6.0 ou version ultérieure)**: utilisez ce paramètre pour spécifier le niveau de correctif Android minimale.  Appareils mobiles qui ne sont pas au moins à ce niveau correctif sera non conformes. La date doit être spécifiée au format : AAAA-MM-JJ.
- **Exiger protection contre les menaces appareil doit être activé**: utilisez ce paramètre pour prendre l’évaluation des risques à partir de la solution de plan de référence affût comme condition de conformité. Sélectionnez le niveau de menace autorisés maximale qui est une des opérations suivantes :

  - **Aucun (sécurisée)** Il s’agit de la plus sûre. Cela signifie que le périphérique ne peut pas contenir toutes les menaces. Si l’appareil est détecté comme ayant n’importe quel niveau de menaces, il sera évaluée comme non conformes.
  - **Faible :** Appareil est évalué comme conforme si une seule menaces niveau faibles sont présents. Toute valeur au-dessus place le périphérique dans un état irrégulière.
  - **Support :** Appareil est évalué comme conforme si les menaces qui sont présents sur l’appareil sont niveau faible ou moyen. Si le périphérique est détecté d’avoir menaces niveau élevés, il est déterminé comme irrégulière.
  - **Haute :** Il s’agit de la moins sûre. Pour l’essentiel, ainsi, tous les menaces niveaux et éventuellement uniquement utile si vous utilisez cette solution uniquement pour les rapports.

  Pour plus d’informations, voir [Activer la règle de protection de menace périphérique dans la stratégie de conformité](enable-device-threat-protection-rule-in-compliance-policy.md).

## Paramètres de la propriété appareil
- **Système d’exploitation minimum requis :** Lorsqu’un appareil ne répond pas à la configuration minimale requise de version minimale du système d’exploitation, il est signalé comme non conformes.
  Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final la possibilité de mettre à niveau leur appareil après laquelle ils peuvent accéder aux ressources de société.

- **Version du système d’exploitation maximale autorisée :** Lorsqu’un appareil utilise une version du système d’exploitation ultérieure à celle indiquée dans la règle, accès aux ressources de l’entreprise est bloqué et l’utilisateur est invité à contacter son administrateur informatique. Jusqu'à ce qu’une modification dans une règle pour autoriser la version du système d’exploitation, cet appareil ne peuvent pas être utilisé pour accéder aux ressources de l’entreprise.
