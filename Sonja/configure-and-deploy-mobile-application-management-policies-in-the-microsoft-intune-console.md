---
title: "Configurer des stratégies MAM dans la console Intune | Microsoft Intune"
description: "Stratégies de gestion des applications mobiles dans Microsoft Intune vous permettent de modifier les fonctionnalités des applications que vous déployez pour aider à les aligner sur la conformité et les stratégies de sécurité de votre entreprise."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b4fb33a8-a2fa-4353-bd89-5bda48b68e83
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: 1584022db4b312919f88ef39dd3912c47b859099
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Configurer et déployer des stratégies de gestion des applications mobiles dans la console Microsoft Intune
Stratégies de gestion (MAM) des applications mobiles dans Microsoft Intune vous permettent de modifier les fonctionnalités des applications que vous déployez pour aider à les aligner avec les stratégies de sécurité et conformité de votre entreprise. Par exemple, vous pouvez limiter les couper, copier et coller dans une application gérée, ou configurer une application pour ouvrir tous les liens web à l’intérieur d’un navigateur géré.

Prise en charge d’application mobile gestion des stratégies :

-   Appareils exécutant Android 4 et versions ultérieures.

-   Appareils exécutant iOS 8.0 et versions ultérieures.

> [!TIP]
> Stratégies de gestion des applications mobiles prennent en charge les périphériques qui sont inscrits avec Intune.
>
> Si vous recherchez pour plus d’informations sur la création des stratégies de gestion des périphériques Intune ne gérer l’application, voir [Protégez vos données d’application à l’aide de stratégies de gestion de l’application mobile avec Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

Contrairement aux autres stratégies Intune, vous ne pas déployez une stratégie de gestion des applications mobiles directement. À la place, vous associez la stratégie à l’application que vous voulez limiter. Lorsque l’application est déployée et installée sur les périphériques, les paramètres que vous spécifiez prendront effet.

Pour appliquer des restrictions à une application, l’application doit comporter le SDK application Intune. Il existe trois méthodes permettant d’obtenir ce type d’application :

-   **Utiliser une application de stratégie gérée**. Une application gérée stratégie a l’application SDK intégrée. Pour ajouter ce type d’application, vous spécifiez un lien à l’application à partir d’un magasin d’application tel qu’iTunes store ou Google Play. Aucun traitement supplémentaire n’est requis pour ce type d’application. Pour plus d’informations, consultez la [liste des applications que vous pouvez utiliser avec les stratégies de gestion des applications mobiles Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).

-   **Utiliser une application renvoyé à la ligne**. Une application renvoyé à la ligne est une application qui vous réorganiser afin d’inclure le Kit de développement de l’application à l’aide de l’outil d’habillage Microsoft Intune application. Cet outil est généralement utilisé pour traiter les applications de société qui ont été créées en interne. Vous ne pouvez pas l’utiliser pour traiter les applications qui ont été téléchargées à partir de l’app store. Pour plus d’informations, voir [préparer iOS applications pour la gestion des applications mobiles avec l’outil d’habillage de Microsoft Intune application](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) et [applications Android préparer pour la gestion des applications mobiles avec l’outil d’habillage de Microsoft Intune application](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

- **Écrivez votre propre application qui comprend le Kit de développement de l’application Intune**. Le SDK application Intune vous permet d’incorporer des fonctionnalités de gestion de l’application dans une application pendant que vous le tapez. Pour plus d’informations, voir [Vue d’ensemble du Kit de développement logiciel Intune application](/intune/develop/intune-app-sdk).

Pour choisir entre l’outil d’habillage application et Intune application SDK plus facilement, voir [déterminer comment préparer des applications pour la gestion des applications mobiles avec Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).

Certaines applications gérées, comme l’application Outlook pour iOS et Android, prend en charge *plusieurs identité*. Cela signifie que Intune s’applique des paramètres de gestion uniquement aux comptes d’entreprise ou des données dans l’application.

Par exemple, à l’aide de l’application Outlook :

-   Si l’utilisateur a configuré un compte de messagerie d’entreprise et un compte de messagerie personnel, Intune applique les paramètres de gestion des uniquement sur le compte d’entreprise et ne pas gère votre compte personnel.

-   Si l’appareil est déclassé ou unenrolled, seules les données Outlook d’entreprise sont supprimées de l’appareil.

-   Le compte d’entreprise doit être le même compte qui a été utilisé pour inscrire l’appareil avec Intune.

> [!TIP]
> Si vous utilisez Intune avec le Gestionnaire de Configuration, voir [comment des applications à l’aide de Mobile Application de gestion des stratégies de contrôle dans le Gestionnaire de Configuration](https://technet.microsoft.com/library/mt131414.aspx).

## Créer et déployer une application avec une stratégie de gestion des applications mobiles

-   **Étape 1 :** Obtenir le lien vers une application gérée stratégie, créer une application renvoyé à la ligne ou utiliser le SDK application Intune pour écrire une application compatibles avec MAM.

-   **Étape 2 :** Publier l’application sur votre espace de stockage cloud.

-   **Étape 3 :** Créer une stratégie de gestion des applications mobiles.

-   **Étape 4 :** Associer l’application à une stratégie de gestion des applications mobiles, puis déployez l’application.

-   **Étape 5 :** Surveillez le déploiement de l’application.

## Étape 1 : Obtenir le lien vers une application gérée stratégie, créer une application renvoyé à la ligne, ou utilisez le SDK application Intune pour écrire une application MAM activés

À partir de l’app store, recherchez et notez l’URL de l’application gérée stratégie que vous voulez déployer. Par exemple, l’URL de Microsoft Word pour iPad application est **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.


## Étape 2 : Publier l’application sur votre espace de stockage cloud
Lorsque vous publiez une application gérée, les procédures diffèrent selon que vous publiez une application de stratégie gérée ou une application qui a été traitée par à l’aide de la l’outil d’habillage de Microsoft Intune application pour iOS.

#### Pour publier une stratégie gérées application

1.  Lorsque vous êtes prêt à télécharger l’application dans votre espace de stockage cloud, suivez les instructions dans les [applications Ajouter pour les appareils mobiles dans Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).

2.  Pour les applications iOS, sélectionnez **Managed l’application à partir de l’App Store pour iOS** sous **Sélectionnez comment ce logiciel est accessibles aux appareils**.

    Pour les applications Android, sélectionnez **lien externe**.

3.  Sous **spécifier l’URL**, entrez l’URL à l’application gérée stratégie que vous avez noté précédemment.

Une fois le téléchargement terminé, vous verrez **Oui** pour **Les stratégies de gestion de l’application** dans la page **Propriétés du logiciel** de l’application de télécharger.

Après avoir vérifié que l’application est téléchargée avec succès, passez à l’étape 3.

#### Publier une application qui a été traitée via l’outil d’habillage Microsoft Intune application

1.  Lorsque vous êtes prêt à télécharger l’application dans votre espace de stockage cloud, suivez les instructions dans les [applications Ajouter pour les appareils mobiles dans Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).

2.  Sélectionnez **Programme d’installation logicielle** sous **Sélectionnez comment ce logiciel est accessibles aux appareils**.

3.  Sélectionnez le package d’application **pour iOS (& #42 ;. fichier de loi)** sous **type de fichier d’installation de logiciel**.

Une fois le téléchargement terminé, vous verrez **Oui** pour **Les stratégies de gestion de l’application** dans la page **Propriétés du logiciel** de l’application de télécharger.

Après avoir vérifié que l’application est téléchargée avec succès, passez à l’étape 3.

## Étape 3 : Créer une stratégie de gestion des applications mobiles

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **stratégie** &gt; **vue d’ensemble** &gt; **Ajouter une stratégie**.

2.  Configurer et déployer une des stratégies de **logiciel** suivantes, selon le type d’appareil que vous voulez configurer les applications pour :

    -   **Stratégie de gestion des applications mobiles (Android 4 et versions ultérieur)**

    -   **Stratégie de gestion des applications mobiles (iOS 8.0 et versions ultérieures)**

    Vous pouvez utiliser les paramètres recommandés ou personnaliser les paramètres. Pour plus d’informations, voir [Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Configurer les paramètres suivants selon les besoins. Les options peuvent différer en fonction du type d’appareil pour lequel vous configurez la stratégie.

|Nom du paramètre|Plus d’informations|
    |---------|--------------------|
    |**Nom**|Attribuez un nom à cette stratégie.|
    |**Description**|Si vous le souhaitez, entrez une description pour cette stratégie.|
    |**Restreindre le contenu web à afficher dans un navigateur géré d’entreprise**|Lorsque ce paramètre est activé, tous les liens dans l’application seront ouvre dans le navigateur géré. Pour utiliser cette option, vous devez avoir déployé cette application aux périphériques.|
    |**Empêcher Android sauvegardes** ou **empêcher les sauvegardes iTunes et iCloud**|Ce paramètre désactive la sauvegarde de toute information de l’application.|
    |**Autoriser l’application pour transférer des données vers d’autres applications**|Ce paramètre spécifie les applications cette application peut envoyer des données à. Vous pouvez choisir de ne pas autoriser le transfert de données à n’importe quelle application autorise transfert uniquement aux autres applications gérées, ou transféré vers n’importe quelle application. <br /><br />Par exemple, lorsque vous n’autorisez pas le transfert de données, limiter le transfert de données aux services tels que SMS de messagerie, en attribuant des images aux contacts et publier des billets dans Facebook ou Twitter.<br /><br />Pour les appareils iOS, pour empêcher le transfert de document entre les applications gérées et non gérées, vous devez également configurer et déployer une stratégie de sécurité d’appareil mobile qui désactive le paramètre **Autoriser gérées des documents dans d’autres applications non gérées**. Si vous choisissez Autoriser le transfert uniquement aux autres applications gérées, les visionneuses Intune PDF et image (si déployé) servira à ouvrir le contenu des modes respectifs.<br /><br />En outre, si vous définissez cette option **Stratégie gérées applications** ou **Aucun**, la fonction iOS 9 qui permet la recherche Spotlight pour rechercher des données dans les applications est bloquée.<br><br>Ce paramètre ne contrôle pas l’utilisation de la fonctionnalité Ouvrir dans sur les appareils mobiles. Pour gérer ouvert dans, voir [gérer le transfert de données entre les applications iOS avec Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).|
    |**Autoriser l’application pour recevoir des données provenant d’autres applications**|Ce paramètre spécifie les applications cette application peut recevoir des données à partir de. Vous pouvez choisir de ne pas autoriser le transfert de données à partir de n’importe quelle application, autoriser le transfert uniquement à partir d’autres applications gérées ou autoriser le transfert à partir de n’importe quelle application.<br /><br />Lorsqu’un utilisateur accède à des données à partir d’une application qui n’est pas gérée par une stratégie de gestion des applications mobiles, les données sont traitées comme les données d’entreprise et protégées par la stratégie. Cela s’applique aux applications iOS cette prise en charge plusieurs identité (où Intune s’applique des paramètres de gestion uniquement aux comptes d’entreprise ou des données dans l’application). Ou bien, cela s’applique à un périphérique inscrit avec une stratégie de gestion des applications mobiles.|
    |**Empêcher les « Enregistrer sous »**|Ce paramètre désactive l’utilisation de l’option **Enregistrer sous** pour enregistrer les données dans des emplacements de stockage cloud personnel (tel que OneDrive ou Dropbox) dans une application qui utilise cette stratégie.|
    |**Limiter les commandes Couper, copier et coller avec d’autres applications**|Ce paramètre spécifie comment couper, copier et coller une peut être utilisée avec l’application. Choisir :<br /><br />**Bloqués**. N’autorisez pas couper, copier et coller une entre cette application et d’autres applications.<br /><br />**Applications géré une stratégie**. Autoriser couper, copier et coller uniquement entre cette application et d’autres applications gérées.<br /><br />**Stratégie gérée applications avec coller dans**. Autoriser les données coupé ou copié à partir de cette application pour être collé dans d’autres applications gérées. Autoriser les données coupé ou copié à partir de n’importe quelle application pour être collé dans cette application.<br /><br />**N’importe quelle application**. Ne placez aucune restriction sur Couper, copier et coller des opérations vers ou à partir de cette application.<br /><br />Pour copier et coller des données entre les applications gérées, les deux applications doivent avoir la **Stratégie gérées applications** ou une **Stratégie gérées applications avec coller dans** paramétrage configuré.|
    |**Simple code confidentiel est nécessaire pour l’accès**|Ce paramètre, l’utilisateur à entrer un code confidentiel qu’ils ont spécifiés pour utiliser cette application. L’utilisateur est invité à configuré ces paramètres pour la première fois qu’ils exécuter l’application.|
    |**Nombre de tentatives avant réinitialisation du code confidentiel**|Spécifier le nombre de tentatives de saisie du code confidentiel pouvant être effectuées avant que l’utilisateur doit réinitialiser le code confidentiel.|
    |**Exiger des informations d’identification d’entreprise pour l’accès**|Ce paramètre nécessite l’utilisateur à entrer ses informations d’ouverture de session d’entreprise avant de pouvoir accéder à l’application.|
    |**Exiger la conformité appareil avec la stratégie d’entreprise pour l’accès**|Ce paramètre permet à l’application à utiliser uniquement lorsque l’appareil n’est pas jailbroken ou associés à une racine.|
    |**Revérifier les conditions d’accès (minutes)**|Dans le champ **délai d’expiration** , spécifiez la période de temps avant que les conditions d’accès pour l’application sont revérifiées une fois que l’application est ouverte.|
    |**Période de grâce en mode hors connexion**|Si l’appareil est en mode hors connexion, spécifiez la période de temps avant que les conditions d’accès pour l’application sont revérifiées.|
    |**Chiffrer les données d’application**|Ce paramètre spécifie que toutes les données associées à cette application seront chiffrées. Cela inclut les données stockées en externe, par exemple cartes SD.<br /><br />**Chiffrement pour iOS**<br /><br />Pour les applications qui sont associées à une stratégie de gestion des applications mobiles Intune, les données sont chiffrées inactives via le chiffrement au niveau du périphérique qui fournit le système d’exploitation. Cette option est activée via une stratégie de code confidentiel que l’administrateur informatique définit périphérique. Lorsqu’un code confidentiel est nécessaire, les données sont chiffrées selon les paramètres de la stratégie de gestion des applications mobiles. Comme indiqué dans la documentation Apple, [les modules qu’iOS utilisations sont certifié FIPS140 - 2](http://support.apple.com/en-us/HT202739).<br /><br />**Chiffrement pour Android**<br /><br />Pour les applications qui sont associées à une stratégie de gestion des applications mobiles Intune, Microsoft fournit le chiffrement. Données sont chiffrées synchrone au cours des opérations d’e/s de fichier.  Le contenu sur le stockage de l’appareil est toujours chiffré. La méthode de chiffrement n’est pas certifié FIPS140-2.|
    |**Capture d’écran de bloc** (Pour les appareils android uniquement)|Ce paramètre indique que les fonctionnalités de capture d’écran de l’appareil sont bloquées lorsque quelqu'un utilise cette application.|
    
4. Lorsque vous avez terminé, cliquez sur **Enregistrer la stratégie**.

La nouvelle stratégie apparaît dans le nœud de **Stratégies de Configuration** de l’espace de travail de **stratégie** .

## Étape 4 : Associer l’application à une stratégie de gestion des applications mobiles et déployez ensuite l’application
Veillez à sélectionner la stratégie de gestion des applications mobiles sur la page de **Gestion de l’application Mobile** de la boîte de dialogue **Gérer le déploiement** à associer la stratégie de l’application.

Pour plus d’informations, voir [déployer des applications dans Microsoft Intune](deploy-apps.md).

> [!IMPORTANT]
> Si l’appareil est unenrolled à partir de Intune, stratégies ne sont pas supprimés à partir des applications. Toutes les applications incluant des stratégies appliquées conserve les paramètres de stratégie après que l’application est désinstallez et réinstallez.

### Que faire lorsqu’une application est déjà déployée sur appareils mobiles
Situations dans lesquelles vous déployez une application et l’un des utilisateurs ciblées ou appareils contient déjà une version non managée de l’application installée est peut-être. Par exemple, l’utilisateur a peut-être installé Microsoft Word à partir de l’app store.

Dans ce cas, vous devez demander à l’utilisateur de désinstaller manuellement la version non gérée afin que la version managée que vous avez configuré peut être installée.

Toutefois, pour appareils mobiles qui s’exécutent iOS 9 et versions ultérieures, Intune demandera automatiquement l’utilisateur pour l’autorisation de prendre en charge la gestion de l’application existante. Si elles s’accordent, puis l’application est gérée localement via Intune et les stratégies de gestion des applications mobiles que vous avez associé à l’application seront appliquent également.

> [!TIP]
> Si l’appareil est en mode contrôlé, Intune prendra sur la gestion de l’application existante sans demander l’autorisation de l’utilisateur.

## Étape 5 : Surveillez le déploiement d’application
Une fois que vous avez créé et déployé une application associée à une stratégie de gestion des applications mobiles, procédez comme suit pour surveiller l’application et résoudre les conflits de stratégie.

#### Pour afficher l’état du déploiement

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **groupes** &gt; **vue d’ensemble**.

2.  Effectuez l’une des opérations suivantes :

    -   Sélectionnez **Tous les utilisateurs**, puis double-cliquez sur l’utilisateur dont vous souhaitez examiner le dispositif. Une la page **Propriétés de l’utilisateur** , sélectionnez des **périphériques**et puis double-cliquez sur le périphérique que vous souhaitez examiner.

    -   Cliquez sur **tous les périphériques** &gt; **tous les appareils mobiles**. Dans la page **Propriétés du groupe de périphérique** , sélectionnez des **périphériques**et puis double-cliquez sur le périphérique que vous souhaitez examiner.

3.  Dans la page **Propriétés de l’appareil Mobile** , choisissez **stratégie** pour afficher la liste des stratégies de gestion des applications mobiles qui ont été déployés à l’appareil.

4.  Sélectionnez la stratégie de gestion des applications mobiles dont vous souhaitez afficher le statut. Vous pouvez afficher les détails de la stratégie dans le volet inférieur et développer son nœud pour afficher ses paramètres.

5.  Colonne de chacune des stratégies de gestion des applications mobiles, **Conforms**, **sont conformes (en attente)**ou **erreur** s’affichent sous l' **état** . Si la stratégie sélectionnée a un ou plusieurs paramètres en conflit, **erreur** s’affichent dans ce champ.

6.  Une fois que vous avez identifié un conflit, vous pouvez modifier les paramètres de stratégie en conflit pour utiliser le même paramètre, ou vous pouvez déployer une seule stratégie à l’application et utilisateur.

### Résolution des conflits de stratégie
Lorsqu’il y a un conflit de stratégie de gestion des applications mobiles sur le premier déploiement à l’utilisateur ou l’appareil, la valeur de paramètre spécifique en conflit a être supprimée de la stratégie déployée dans l’application. L’application utilise une valeur de conflit intégrée.

Lorsqu’il y a un conflit de stratégies de gestion de l’application mobile sur les déploiements ultérieurs à l’application ou l’utilisateur, la valeur de paramètre spécifique en conflit ne sera pas actualisée sur la stratégie de gestion de l’application mobile déployée à l’application. L’application utilise la valeur existante pour ce paramètre.

Dans les cas où l’appareil ou l’utilisateur reçoit les deux stratégies contradictoires, le problème suivant s’applique :

-   Si une stratégie a déjà été déployée à l’appareil, les paramètres de stratégie ne sont pas remplacées.

-   Si aucune stratégie n’a déjà été déployé à l’appareil et déployés des deux paramètres en conflit, le paramètre par défaut intégré à l’appareil est utilisé.
