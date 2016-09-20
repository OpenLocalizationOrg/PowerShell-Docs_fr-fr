---
title: "Paramètres de stratégie de Mac OS X | Microsoft Intune"
description: "Intune fournit une plage de paramètres généraux prédéfinis que vous pouvez configurer sur les périphériques de Mac OS X. En outre, vous pouvez utiliser l’outil de configuration du Apple pour créer des paramètres personnalisés qui ne sont pas disponibles dans Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 98b2f19b-bee8-42d7-a215-a716d56a25a3
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: c6b010e49b4e581dad056aa6e8bb17123030f7b0
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Paramètres de stratégie de configuration de Mac OS X dans Microsoft Intune

Intune fournit une plage de paramètres généraux prédéfinis que vous pouvez configurer sur les périphériques de Mac OS X. En outre, vous pouvez utiliser l’outil de configuration du Apple pour créer des paramètres personnalisés qui ne sont pas disponibles dans Intune.

## Paramètres de stratégie de configuration générale

Utilisez la Microsoft Intune **stratégie de configuration générale de Mac OS X** pour configurer les paramètres pour :

-   **Les paramètres de sécurité**. Choisir parmi une liste de paramètres prédéfinis qui vous permettent de contrôler une plage de fonctionnalités sur l’appareil.

-   **Conforme et applications non conformes**. Spécifiez une liste des applications qui sont conformes ou n’est pas compatible dans votre entreprise. L’état d’applications non conformes peut être utilisé pour afficher la conformité des applications que vous avez spécifié dans la liste contre les applications que vous ont installé (mais les utilisateurs ne peuvent pas réellement bloquer l’installation de l’application).

Si le paramètre que vous recherchez n’apparaît pas dans cette liste, vous pourrez peut-être créer votre document à l’aide d’une stratégie personnalisée Mac OS X qui vous permet d’importer les paramètres que vous avez créé à l’aide de l’outil de configuration du Apple. Pour plus d’informations, voir « Paramètres de stratégie personnalisée » plus loin dans cette rubrique.

### Paramètres de mot de passe

|Nom du paramètre|Plus d’informations|
|----------------|---------------|
|**Exiger un mot de passe pour la déverrouiller appareils**|Spécifiez si l’utilisateur doit utiliser un mot de passe pour accéder à leur ordinateur Mac. **Importantes :** Contrairement aux appareils iOS, sur les périphériques de Mac OS X, l’utilisateur n’est pas averti immédiatement mettre à jour son mot de passe pour respecter ce paramètre.|
|**Obligatoires type de mot de passe**|Spécifier si le mot de passe peut être **numérique** uniquement, ou si elle doit être **alphanumérique** (contenir des lettres et des nombres). **Importantes :** Ce paramètre est pris en charge uniquement sur Mac OS X version 10.10.3 et versions ultérieures.|
|**Nombre de caractères complexes requis dans mot de passe**|Spécifier le nombre de caractères complexes requis dans le mot de passe (**0** à **4**).<br /><br />Un caractère complexe est un symbole, tel que **?**.|
|**Longueur minimale**|Spécifiez la longueur minimale pour le mot de passe (**4** à **14** caractères).|
|**Autoriser les mots de passe simples**|Permettre l’utilisation de mots de passe simples tels que **0000** ou **1234**.|
|**Minutes d’inactivité avant de mot de passe est nécessaire**|Spécifier la durée pendant laquelle l’ordinateur doit être inactif avant un mot de passe est requis pour la déverrouiller.|
|**Expiration du mot de passe (jours)**|Spécifier le nombre de jours s’écouler avant que l’utilisateur doit changer le mot de passe (**1** à **255** jours).|
|**N’oubliez pas de l’historique de mot de passe**|Empêcher l’utilisateur d’utiliser un mot de passe précédemment utilisé. Lorsque cette option est définie, vous pouvez également définir **éviter la réutilisation des mots de passe précédents** pour spécifier le nombre de mots de passe utilisés précédemment qui ne peuvent pas être réutilisées (**1** à **24**).|
|**Minutes d’inactivité avant de l’écran de veille Active**|Spécifier la durée pendant laquelle l’ordinateur doit être inactif avant que l’économiseur d’écran est activé.|

### Paramètres pour les applications conformes et non conformes
Dans la **compatible &amp; liste d’applications non conformes pour Mac OS X**, activer **les paramètres gérés pour appareils mobiles**et spécifiez une liste des applications conformes en utilisant les informations suivantes.

> [!NOTE]
> Une seule stratégie peut contenir uniquement une liste des applications conformes ou une liste des applications non conformes. Vous ne pouvez pas spécifier à la fois dans la même stratégie.
>
> Intune vous permet de vous signaler les appareils mobiles avec les applications non conformes. Il ne bloquent installation ni supprimer des applications non conformes.

|Nom du paramètre|Plus d’informations|
|----------------|---------------|
|**Signaler non-conformité lorsque les utilisateurs installer les applications répertoriées**|Affiche les applications Mac OS X utilisateurs n’êtes pas autorisés à installer. Si les utilisateurs installent une de ces applications, ils sont signalés lors du **Rapports applications non conformes**.|
|**Signaler non-conformité lorsque les utilisateurs installer des applications qui ne sont pas répertoriées**|Affiche les applications Mac OS X utilisateurs sont autorisés à installer. Si les utilisateurs installent toutes les autres applications, ils sont signalés lors du **Rapports applications non conformes**.|
|**Ajouter**|Ajouter une application à la liste sélectionnée. Spécifiez un nom de votre choix, vous pouvez également l’éditeur de l’application et l’ID de l’ensemble de guides de l’application. **Conseil :** Pour rechercher l’ID de l’ensemble d’une application, procédez comme suit sur un ordinateur Mac qui est installée l’application :<ol><li>Ouvrez le dossier dans lequel l’application est installée (par exemple, **/ applications**).</li><li>Sélectionnez le * &lt;nom de l’application&gt;***.app** regrouper, puis cliquez sur **Afficher le contenu du Package**.</li><li>Ouvrez le fichier **Info.plist** .</li><li>Vérifiez la valeur associée à la clé **CFBundleIdentifier**.</li></ol>Le format de l’ID de l’ensemble de guides est **com.contoso.appname**.|
|**Importer des applications**|Importer une liste des applications que vous avez spécifié dans un fichier de valeurs séparées par des virgules. Dans le fichier, utilisez ce format : nom de l’application, publisher, application offre groupée identifiant.|
|**Modifier**|Modifier le nom, publisher et application offre groupée ID de l’application sélectionnée.|
|**Supprimer**|Supprimer l’application sélectionnée de la liste.|
> [!TIP]
> Pour plus d’informations à propos des rapports Intune, voir [comprendre Microsoft Intune opérations à l’aide de rapports](understand-microsoft-intune-operations-by-using-reports.md).

> [!IMPORTANT]
> Lorsqu’un appareil Mac OS X est en mode mise en veille, stratégies et des profils ne peut pas remis ou stocks. Par conséquent, la console Intune susceptibles de s’afficher temporairement l’état **des paramètres de stratégie erreur** jusqu'à la prochaine fois que l’appareil sort du mode veille.

### Surveiller des applications conformes et non conformes
**Rapports d’applications non conformes** permet d’afficher la conformité des applications que vous avez spécifié.

#### Pour exécuter un rapport

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), cliquez sur **rapports** &gt; **Non conformes rapports d’applications**.

2.  Sélectionnez les groupes de l’appareil que vous voulez rechercher, indiquez si vous voulez rechercher les applications conformes, applications non conformes ou les deux, puis cliquez sur **Afficher le rapport**.

## Paramètres de stratégie personnalisés de Mac OS X dans Microsoft Intune
Utilisez la **stratégie de configuration personnalisée de Mac OS X** de Microsoft Intune pour déployer les paramètres que vous avez créé à l’aide de l' [outil de configuration du Apple](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) aux périphériques de Mac OS X. Cet outil vous permet de créer de nombreux paramètres qui contrôlent le fonctionnement de ces périphériques et les exporter vers un profil de configuration. Vous pouvez importer ce profil de configuration dans une stratégie personnalisée Intune Mac OS X et déployer les paramètres pour les utilisateurs et périphériques de votre organisation.

Cette fonctionnalité permet de déployer des paramètres de Mac OS X qui ne peuvent pas être configurés avec la stratégie de configuration générale Intune Mac OS X.

### Conditions préalables
Avant de commencer, vous devez avoir installé l’outil de configuration Apple et créé un fichier de configuration qui contient les paramètres que vous voulez déployer à des utilisateurs ou des appareils mobiles. Vous pouvez télécharger et en savoir plus sur la configuration du Apple à partir [Du Mac App Store](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

> [!NOTE]
> Intune ne signale pas la conformité des paramètres individuels dans une stratégie personnalisée Mac OS X. Toutefois, la conformité globale de la stratégie est signalée.

### Paramètres généraux

|Nom du paramètre|Plus d’informations|
    |----------------|--------------------|
    |**Nom**|Entrez un nom unique pour la stratégie personnalisée Mac OS X pour vous aider à identifier dans la console Intune.|
    |**Description**|Fournir une description qui donne un aperçu de la stratégie personnalisée Mac OS X et d’autres informations pertinentes qui vous aide à rechercher.|


### Paramètres personnalisés

|Nom du paramètre|Plus d’informations|
    |----------------|--------------------|
    |**Nom du profil configuration personnalisée (présenté aux utilisateurs)**|Indiquez un nom pour la stratégie tel qu’il s’affichera sur l’appareil et dans les rapports de stratégie Intune.|
    |**Fichier de configuration de profil**|Cliquez sur **Importer**, puis puis naviguez vers le profil de configuration que vous avez créé à l’aide de l’outil de configuration d’Apple. **Conseil :** Dans cette rubrique d’aide pour créer le profil de configuration, voir « Comment créer un fichier de configuration de profil ».|
    |**Détails de profil de configuration**|Affichez le code XML pour le profil de configuration que vous avez importés.|



### Comment créer un fichier de configuration de profil
Vous pouvez créer le fichier de profil de configuration utilisé par la stratégie personnalisée de deux façons :

-   Exporter le fichier (avec l' extension **.mobileconfig**) à partir de l’outil de configuration du Apple.

-   Créez le fichier en utilisant le schéma approprié à partir de la [Référence de clé Apple Configuration profil](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html).


### Voir aussi
[Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
