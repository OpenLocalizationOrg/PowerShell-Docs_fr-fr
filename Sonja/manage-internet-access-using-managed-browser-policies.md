---
title: "Gérer l’accès web avec le navigateur géré | Microsoft Intune"
description: "Déploiement de l’application de navigateur gérées pour limiter la navigation sur le web et les transferts de données web aux autres applications."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54
ms.reviewer: maxles
ms.suite: ems
ms.openlocfilehash: a8cf580a7df1d9c5240fc702107563bc965ce6ad
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Gérer l’accès à Internet à l’aide de stratégies de navigateur gérées avec Microsoft Intune
Le navigateur géré est une application que vous pouvez déployer dans votre organisation à l’aide de Microsoft Intune de navigation web. Une stratégie de navigateur gérées configure une liste verte ou une liste de blocs qui limite les sites Web que les utilisateurs du navigateur géré peuvent visiter.

Étant donné que cette application est une application gérée, vous pouvez également appliquer des stratégies de gestion des applications mobiles à l’application. Ces politiques peuvent inclure le contrôle de l’utilisation de couper, copier et coller, empêchant écran capture, et s’assurer que des liens vers du contenu que les utilisateurs, sélectionnez Ouvrir uniquement dans d’autres gérées applications. Pour plus d’informations, voir [configurer et déployer des stratégies de gestion des applications mobiles dans la console Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> [!IMPORTANT]
>Si les utilisateurs installer le navigateur géré dans l’app store et Intune ne le gère pas, le problème suivant s’applique :<br /><br />
iOS – l’application gérée navigateur peut être utilisé comme un navigateur web de base, mais certaines fonctionnalités ne sera pas disponibles et qu’il ne sera pas en mesure d’accéder aux données provenant d’autres applications gérées Intune.<br />
Android – l’application gérée navigateur ne peuvent pas être utilisée.<br /><br />
Si les utilisateurs du navigateur géré s’installer sur un appareil iOS avec une version antérieure à iOS 9, aucune stratégie que vous créez ne gère le navigateur. Pour vous assurer que Intune gère le navigateur, les utilisateurs doivent désinstaller l’application avant de déployer leur comme une application gérée. Sur iOS 9 et versions ultérieures, si les utilisateurs installent le navigateur géré eux-mêmes, il devra pour lui permettre de devenir géré par la stratégie.

Vous pouvez créer des stratégies de navigateur gérées pour les types d’appareil suivants :

-   Appareils exécutant Android 4 et versions ultérieures

-   Périphériques exécutant iOS 8.0 et versions ultérieures

Le navigateur géré Intune prend en charge l’ouverture du site web du contenu [Microsoft Intune partenaires](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)d’application.

## Créer une stratégie de navigateur gérées

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **stratégie** &gt; **Ajouter une stratégie**.

2.  Configurer l’un des types de stratégie **logiciels** suivants :

    -   **Navigateur gérée (Android 4 et versions ultérieur)**

    -   **Navigateur gérée (iOS 8.0 et versions ultérieures)**

    Pour plus d’informations sur la façon de créer et déployer des stratégies, consultez la rubrique [fonctionnalités sur vos appareils avec Microsoft Intune stratégies et gérer les paramètres](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) .

3.  Utilisez les éléments suivants pour vous aider à configurer les paramètres de stratégie de navigateur gérées :

    - **Nom**. Entrez un nom unique pour la stratégie de navigateur gérées pour vous aider à identifier dans la console Intune.
    - **Description**. Fournir une description qui offre une vue d’ensemble de la stratégie de navigateur gérées et autres informations pertinentes qui vous aide à rechercher.
    - **Activer une liste Autoriser ou bloquer limiter les URL le navigateur gérées peuvent ouvrir**. Sélectionnez une des options suivantes :
        - **Autoriser le navigateur géré pour ouvrir uniquement les URL présentées ci-après**. Spécifiez une liste d’URL que le navigateur géré peut ouvrir.
        - **Bloquer le navigateur géré d’ouvrir les URL présentées ci-après**. Spécifiez une liste d’URL que le navigateur géré est bloqué ouverture.
**Remarque :** Vous ne pouvez pas inclure URL autorisés et bloqués dans la même stratégie navigateur gérées.
Pour plus d’informations sur les formats d’URL que vous pouvez spécifier, voir **format de l’URL pour autorisés et bloqués URL** dans cette rubrique.

4.  Lorsque vous avez terminé, cliquez sur **Enregistrer la stratégie**.

La nouvelle stratégie apparaît dans le nœud de **Stratégies de Configuration** de l’espace de travail de **stratégie** .

## Création d’un déploiement pour l’application de navigateur gérées
Après avoir créé la stratégie de navigateur géré, vous pouvez créer un déploiement du logiciel pour l’application de navigateur gérées et associer à la stratégie de navigateur gérée que vous avez créé.

> [!IMPORTANT]
> Gèrent les stratégies ne sont pas déployées de la même façon que d’autres Intune stratégies de navigateur. Ce type de stratégie doit être associé à l’ensemble de logiciels navigateur gérées.

Déploiement de l’application, en sélectionnant la stratégie de navigateur gérées sur la page **Gestion des applications mobiles** pour associer la stratégie à l’application.

Pour plus d’informations sur le déploiement des applications, voir [déployer des applications dans Microsoft Intune](deploy-apps-in-microsoft-intune.md).

## Sécurité et confidentialité pour le navigateur gérée

-   Sur les appareils iOS, des sites Web que les visiteurs ayant un certificat qui a expiré ou non fiable ne peuvent pas être ouverts.

-   Le navigateur géré n’utilise pas les paramètres par les utilisateurs du navigateur intégrée sur leurs appareils. C’est parce que le navigateur géré n’a pas accès à ces paramètres.

-   Si vous configurez l’option **Exiger simple code confidentiel pour l’accès** ou **nécessitent des informations d’identification d’entreprise pour access** dans une stratégie de gestion des applications mobiles associée au navigateur géré, et un utilisateur sélectionne le lien aide dans la page authentification, ils peuvent ensuite rechercher tous les sites Internet indépendamment qu’ils ont été ajoutés à une liste de blocage de la stratégie de navigateur gérées.

-   Le navigateur géré peut bloquer l’accès aux sites uniquement lorsqu’ils sont accessibles directement. Il ne peut pas bloquer l’accès lorsque les services intermédiaires (par exemple, un service de traduction) sont utilisées pour accéder au site.

-   Pour autoriser l’authentification et pour vous assurer que la documentation Intune peut être accessible,**& #42 ;. Microsoft.com** est exempt des paramètres de la liste Autoriser ou bloquer. Il est toujours autorisée.

### Désactiver l’utilisation des données
Microsoft recueille automatiquement des données anonymes sur les performances et l’utilisation du navigateur gérée pour améliorer les produits et services Microsoft. Les utilisateurs peuvent désactiver la collecte des données en utilisant le paramètre de **Données d’utilisation** sur leurs appareils. Vous avez aucun contrôle sur la collection de ces données.

## Informations de référence

### Format de l’URL pour autorisés et bloqués URL
Utilisez les informations suivantes pour en savoir plus sur les formats autorisés et les caractères génériques que vous pouvez utiliser lorsque vous spécifiez l’URL dans les listes autorisés et bloqués :

-   Vous pouvez utiliser le symbole de caractère générique (**& #42 ;**) conforme aux règles dans la liste autorisée des motifs suivants.

-   Placez le préfixe toutes les URL par **http** ou **https** lorsque vous les entrez dans la liste.

-   Vous pouvez spécifier les numéros de port dans l’adresse. Si vous ne spécifiez pas un numéro de port, les valeurs utilisées seront :

    -   Port 80 pour http

    -   Port 443 pour https

    Utilisation de caractères génériques pour le numéro de port n’est pas pris en charge. Par exemple, * *http&colon;//www&period;contoso&period;com :*;* *et* *http&colon;//www&period;contoso&period;com : /*; ** ne sont pas pris en charge.

-   Utilisez le tableau suivant pour en savoir plus sur les modèles autorisés que vous pouvez utiliser lorsque vous spécifiez l’URL :

|URL|Plus d’informations|Correspondances|Ne correspond pas à|
    |-------|---------------|-----------|------------------|
    |http://www.contoso.com|Correspond à une seule page|www.contoso.com|Host.contoso.com<br /><br />www.contoso.com/images<br /><br />Contoso.com/|
    |http://contoso.com|Correspond à une seule page|Contoso.com/|Host.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com|
    |http://www.contoso.com/&#42;|Correspond à toutes les URL commençant par www.contoso.com|www.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com/videos/tvshows|Host.contoso.com<br /><br />Host.contoso.com/images|
    |http://&#42;.contoso.com/&#42 ;|Correspond à tous les sous-domaines sous contoso.com|Developer.contoso.com/resources<br /><br />News.contoso.com/images<br /><br />News.contoso.com/videos|Contoso.Host.com|
    |http://www.contoso.com/images|Correspond à un seul dossier|www.contoso.com/images|www.contoso.com/images/Dogs|
    |http://www.contoso.com:80|Correspond à une seule page, en utilisant un numéro de port|http://www.contoso.com:80||
    |https://www.contoso.com|Correspond à une page unique et sécurisée|https://www.contoso.com|http://www.contoso.com|
    |http://www.contoso.com/images/&#42;|Correspond à un seul dossier et tous ses sous-dossiers|www.contoso.com/images/Dogs<br /><br />www.contoso.com/images/Cats|www.contoso.com/videos|

-   Voici quelques exemples de certaines des entrées que vous ne pouvez pas spécifier :

    -   & #42 ;. com

    -   & #42 ;. Contoso / & #42 ;

    -   www.contoso.com/&#42;images

    -   www.contoso.com/&#42;images&#42;pigs

    -   www.contoso.com/page&#42;

    -   Adresses IP

    -   https://&#42 ;

    -   http://&#42 ;

    -   http://www.contoso.com : & #42 ;

    -   http://www.contoso.com : / & #42 ;

### Comment les conflits entre les listes verte et doivent être résolus
Si plusieurs géré stratégies de navigateur sont déployés sur un appareil et le paramètres sont en conflit, les deux le mode (autoriser ou empêcher) et les listes d’URL sont évaluées pour les conflits. En cas de conflit, le problème suivant s’applique :

-   Si les modes dans chaque stratégie sont identiques, mais les listes d’URL sont différents, les URL ne seront pas appliquées sur l’appareil.

-   Si les modes dans chaque stratégie sont différents, mais les listes d’URL sont identiques, les URL ne seront pas appliquées sur l’appareil.

-   Si un appareil reçoit des stratégies de navigateur gérées pour la première fois et un conflit de deux stratégies, les URL ne seront pas appliquées sur l’appareil. Utilisez le nœud de **Conflits de stratégies** de l’espace de travail de **stratégie** pour afficher les conflits.

-   Si un appareil a déjà reçu une stratégie de navigateur gérées et une seconde stratégie est déployée avec les paramètres en conflit, les paramètres d’origine restent sur l’appareil. Utilisez le nœud de **Conflits de stratégies** de l’espace de travail de **stratégie** pour afficher les conflits.
