---
title: "Paramètres de stratégie de conformité pour les appareils iOS | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a59d24f-ed58-49b1-b874-b2d4aea3ec76
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: a2f98bbd34cf8b0c86531ae6ff40b1044c15d8bd
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Paramètres de stratégie de conformité pour les appareils iOS dans Microsoft Intune

Les paramètres de stratégie décrites dans cette rubrique s’appliquent aux appareils exécutant iOS 8.0 et versions ultérieures.

Si vous recherchez des informations sur d’autres plateformes, sélectionnez une des opérations suivantes :
> [!div class="op_single_selector"]
- [Paramètres de stratégie de conformité pour les appareils Android](android-compliance-policy-settings-in-microsoft-intune.md)
- [Paramètres de stratégie de conformité pour les appareils Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## Paramètres de sécurité système
### Mot de passe
- **Exiger un mot de passe pour la déverrouiller les appareils mobiles :**    Définir sur **Oui** pour obliger les utilisateurs à entrer un mot de passe avant de pouvoir accéder à leur appareil. les appareils iOS qui utilisent le mot de passe sont chiffrés.

- **Autoriser les mots de passe simples :**    Définir sur **Oui** pour permettre aux utilisateurs de créer des mots de passe simples tels que «**1234**» ou «**1111**».

-  **Longueur minimale du mot de passe :** Spécifier le nombre minimal de chiffres ou de caractères que le mot de passe doit contenir.
- **Obligatoires type de mot de passe :** Spécifier si les utilisateurs doivent créer un **alphanumérique**ou un mot de passe **numérique** .

- **Nombre minimal de jeux de caractères :** Si vous affectez **obligatoires type de mot de passe** **alphanumérique**, utilisez ce paramètre pour spécifier le nombre minimal de jeux de caractères que le mot de passe doit contenir. Quatre jeux de caractères sont :
  -   Lettres minuscules
  -   Lettres majuscules
  -   Symboles
  -   Numéros

  Configuration d’un nombre plus élevé pour ce paramètre signifie que les utilisateurs à créer des mots de passe qui sont plus complexes.

  Pour les appareils iOS, ce paramètre fait référence au nombre de caractères spéciaux (par exemple, **!**, **#**, **&amp;**) qui doivent être inclus dans le mot de passe.
- **Minutes d’inactivité avant de mot de passe est nécessaire :**  Spécifier la durée d’inactivité avant que l’utilisateur doit retaper son mot de passe.

- **Expiration du mot de passe (jours) :** Sélectionnez le nombre de jours avant l’expiration du mot de passe de l’utilisateur et ils doivent créer un nouvel identifiant.

- **N’oubliez pas de l’historique de mot de passe :** Utilisez ce paramètre conjointement avec **éviter la réutilisation d’anciens mots de passe** pour empêcher l’utilisateur de créer des mots de passe utilisés précédemment.

- **Éviter la réutilisation des mots de passe précédents :** Si **l’historique de mémoriser mot de passe** est sélectionnée, indiquez le nombre de mots de passe précédemment utilisés ne peut pas être réutilisée.

- **Exiger un mot de passe lorsque l’appareil est retournée à partir d’un état d’inactivité :** Ce paramètre doit être utilisé avec la dans le paramètre de **Minutes d’inactivité avant de mot de passe est requis** . Les utilisateurs finaux êtes invités à entrer un mot de passe pour accéder à un périphérique qui a été inactif pendant la durée spécifiée dans le paramètre de **Minutes d’inactivité avant de mot de passe est requis** .

### Profil de messagerie
- **Compte de messagerie doit être géré par Intune :** Lorsque cette option est définie sur **Oui**, le périphérique doit utiliser la messagerie non conforme déployé sur le périphérique. Le périphérique est considéré comme non conforme dans les situations suivantes :
  - Le profil de messagerie doit également être déployé sur le même groupe d’utilisateurs en tant que groupe d’utilisateurs ciblé par la stratégie de conformité, dans le cas contraire appareils utilisateurs sont considérés non conformes.
  - L’appareil est signalé comme non conforme si l’utilisateur a déjà configuré un compte de messagerie de l’appareil qui correspond au profil de messagerie Intune déployé sur le périphérique. Intune ne peut pas remplacer le profil utilisateur configuré et par conséquent ne peuvent pas gérer celui-ci. Pour garantir la conformité, l’utilisateur doit supprimer les paramètres de messagerie existants, puis Intune peut installer le profil de messagerie gérées.


- **Sélectionnez le profil de messagerie qui doit être géré par Intune :** 
   si le paramètre de **compte de messagerie doit être géré par Intune** est sélectionné, choisissez **Sélectionner** pour indiquer le profil de messagerie Intune. Le profil de messagerie doit être présent sur le périphérique.

     Pour plus d’informations sur les profils de messagerie, voir [configurer l’accès à la messagerie d’entreprise en utilisant les profils de courrier électronique avec Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).

## Paramètres d’intégrité du périphérique

- **Périphérique ne doit pas être jailbroken ou associés à une racine :** Si vous activez ce paramètre, appareils jailbroken ne sera pas conformes.

##  Propriétés de l’appareil
- **Système d’exploitation minimum requis :** Lorsqu’un appareil ne répond pas à la configuration minimale requise de version minimale du système d’exploitation, il est signalé comme non conformes.
Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final pouvez choisir de mettre à niveau leur appareil après laquelle ils doivent être en mesure d’accéder aux ressources de société.

- **Version du système d’exploitation maximale autorisée :** Lorsqu’un appareil utilise une version du système d’exploitation ultérieure à celle indiquée dans la règle, accès aux ressources de l’entreprise est bloqué et l’utilisateur est invité à contacter son administrateur informatique. Jusqu'à ce qu’une modification dans une règle pour autoriser la version du système d’exploitation, cet appareil ne peuvent pas être utilisé pour accéder aux ressources de l’entreprise.
