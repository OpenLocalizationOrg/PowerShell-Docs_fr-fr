---
title: "Utiliser des stratégies de configuration de l’application mobile iOS | Microsoft Intune"
description: "Utilisez les stratégies de configuration de l’application mobile dans Intune pour fournir des paramètres qui peuvent être nécessaires lorsque les utilisateurs exécutent une application iOS."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: mghadial
ms.suite: ems
ms.openlocfilehash: c7fe00828108ac3f84e91a0eeb3ed4c344228588
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Configurer des applications iOS avec les stratégies de configuration de l’application mobile dans Microsoft Intune
Utilisez les stratégies de configuration de l’application mobile dans Microsoft Intune pour fournir des paramètres qui peuvent être nécessaires lorsque les utilisateurs exécutent une application. Par exemple, une application peut nécessiter aux utilisateurs de spécifier :

-   Un numéro de port personnalisé.

-   Paramètres de langue.

-   Paramètres de sécurité.

-   Personnalisation des paramètres tels que le logo de votre entreprise.

Si les utilisateurs entrent ces paramètres de manière incorrecte, vous pouvez augmenter la charge sur votre support technique et ralentir l’adoption de nouvelles applications.

Stratégies de configuration de l’application mobile peuvent vous aider à éviter ces problèmes en vous permettant de déployer ces paramètres pour les utilisateurs dans une stratégie de pouvoir exécuter l’application. Les paramètres sont ensuite fournis automatiquement, et les utilisateurs doivent effectuer aucune action.

Vous ne déployez pas ces politiques directement à des utilisateurs et des appareils mobiles. À la place, vous associez une stratégie à une application, puis déployez l’application. Les paramètres de stratégie seront utilisés chaque fois que l’application vérifie les (en général, la première fois, est exécuté).

> [!TIP]
> Ce type de stratégie est actuellement disponible uniquement pour les appareils exécutant iOS 8.0 et versions ultérieures. Il prend en charge les types de l’installation d’application suivants :
>
> -   **Gèrent application iOS à partir de l’app store**
> -   **Package d’application pour iOS**
>
> Pour plus d’informations sur les types d’installation d’application, voir [déployer des applications avec Microsoft Intune](deploy-apps.md).

## Configurer une stratégie de configuration de l’application mobile

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **stratégie** &gt; **vue d’ensemble** &gt; **Ajouter une stratégie**.

2.  Dans la liste des stratégies, développer **iOS**, sélectionnez **Configuration de l’application Mobile**, puis **Créer une stratégie**.

    > [!TIP]
    > Vous pouvez configurer uniquement les paramètres personnalisés pour ce type de stratégie. Paramètres recommandés ne sont pas disponibles.

3.  Dans la section **Général** de la page **Créer une stratégie** , fournir un nom et une description facultative de la stratégie de configuration de l’application mobile.

4.  Dans la section de **Stratégie de Configuration de l’application Mobile** de la page, dans la zone, entrez ou collez une liste de propriété XML qui contient les paramètres de configuration de l’application souhaitée. Le format de la liste des propriétés XML varie selon l’application que vous configurez. Pour plus d’informations sur le format exact à utiliser, contactez le fournisseur de l’application.

    > [!TIP]
    > Pour en savoir plus sur les listes de propriété XML, voir [Description des listes de propriété XML](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) dans la bibliothèque de développeur iOS.

5.  Cliquez sur **Valider** pour vous assurer que le code XML que vous avez entrées se trouve dans un format de liste propriété valide.

    > [!IMPORTANT]
    > Lorsque vous cliquez sur **Valider**, Intune vérifie que le code XML que vous avez entré est dans un format valide. Il ne vérifie pas que la liste des propriétés XML fonctionnent avec l’application qui lui est associée.

6.  Lorsque vous avez terminé, cliquez sur **Enregistrer la stratégie**.

La nouvelle stratégie est affichée dans le nœud de **Stratégies de Configuration** .

## Informations sur le format de fichier XML

Intune prend en charge les types de données suivants dans une liste de propriétés :
    
- &lt;nombre entier&gt;
- &lt;réel&gt;
- &lt;chaîne&gt;
- &lt;tableau&gt;
- &lt;dictionnaire&gt;
- &lt;Vrai /&gt; ou &lt;false /&gt;
     
Pour plus d’informations sur les types de données, voir [à propos de propriété listes](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) dans la bibliothèque de développeur iOS.

En outre, Intune prend en charge les types de jetons suivants dans la liste des propriétés :
- \{\{userPrincipalName\}\} -(exemple : **John@contoso.com**)
- \{\{messagerie\}\} -(exemple : **John@contoso.com**)
- \{\{partialupn\}\} -(exemple : **John**)
- \{\{ID de compte\}\} -(exemple : **fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
- \{\{ID de périphérique\}\} -(exemple : **b9841cd9-9843-405f-be28-b2265c59ef97**)
- \{\{ID d’utilisateur\}\} -(exemple : **3ec2c00f-b125-4519-acf0-302ac3761822**)
- \{\{nom d’utilisateur\}\} -(exemple : **pré**)
- \{\{NuméroSérie\}\} -(exemple : **F4KN99ZUG5V2**) pour les appareils iOS
- \{\{serialnumberlast4digits\}\} -(exemple : **G5V2**) pour les appareils iOS
    
La \{\{ et \}\} caractères sont utilisés par les types de jetons uniquement et ne doit pas être utilisés à d’autres fins.

## Associer une stratégie de configuration de l’application mobile à une application
Après avoir créé une stratégie de configuration de l’application mobile, vous devez l’associer à l’application iOS vers laquelle vous souhaitez appliquer les paramètres de la stratégie de configuration.

Pour ce faire, suivez les étapes pour créer un déploiement de l’application dans [Ajouter des applications pour les appareils mobiles dans Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md) et [déployer les applications avec Microsoft Intune](deploy-apps-in-microsoft-intune.md). Lorsque vous atteignez la page **Configuration de l’application Mobile** de l’Assistant, sélectionnez la stratégie que vous souhaitez associer à l’application à partir de la liste déroulante de **Stratégie de Configuration d’application** .

Ensuite, continuez à déployer et surveiller le déploiement de l’application comme d’habitude.

Lorsque l’application déployée est exécutée sur un appareil, il est exécuté avec les paramètres que vous avez configuré dans la stratégie de configuration de l’application mobile.

> [!TIP]
> Si une ou plusieurs stratégies de configuration de l’application mobile sont en conflit, aucune stratégie est appliquée. Le conflit est signalé dans la console d’administration Intune **tableau de bord**.

## Exemple de format pour un fichier XML de configuration de l’application mobile

Lorsque vous créez un fichier de configuration de l’application mobile, vous pouvez spécifier une ou plusieurs des valeurs suivantes à l’aide de ce format :

```
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
</dict>

```
