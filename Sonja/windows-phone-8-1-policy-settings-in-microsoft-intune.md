---
title: "Paramètres de stratégie de Windows Phone 8.1 | Microsoft Intune"
description: "Intune fournit une plage de paramètres généraux prédéfinis que vous pouvez configurer sur les appareils Windows Phone 8.1. En outre, vous pouvez spécifier des valeurs de OMA URI pour créer des paramètres personnalisés qui ne sont pas disponibles dans Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 83f7469c-272e-43f2-8139-b0d7bc34f43f
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 315e492b301387c2030440e7188dfdb35a99ddd9
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Paramètres de stratégie de Windows Phone 8.1 dans Microsoft Intune

Intune fournit une plage de paramètres généraux prédéfinis que vous pouvez configurer sur les appareils Windows Phone 8.1. En outre, vous pouvez spécifier des valeurs d’ouvrir Mobile Alliance Uniform Resource Identifier (URI OMA) pour créer des paramètres personnalisés qui ne sont pas disponibles dans Intune.

## Paramètres de configuration générale

Utiliser la **stratégie de configuration général de Windows Phone (Windows Phone 8.1 et versions ultérieur)** de Microsoft Intune pour configurer les paramètres suivants pour les appareils Windows Phone 8.1 :

-   **Paramètres de sécurité des périphériques mobiles** – choisir dans la liste des paramètres prédéfinis qui vous permettent de contrôler une plage de fonctionnalités sur l’appareil.

-   **Conforme et applications non conformes** - spécifier une liste d’applications qui sont conformes ou n’est pas compatible dans votre entreprise. Appareils Windows Phone peuvent bloquer ou autoriser l’installation de ces applications.

### Paramètres d’application

|Nom du paramètre|Plus d’informations|
|----------------|----------------------------------|
|**Appliquer toutes les configurations vers Windows 10**|Active les paramètres dans cette stratégie à appliquer aux appareils Windows 10 Mobile outre les appareils Windows Phone 8.1.|

### Paramètres de mot de passe

|Nom du paramètre|Plus d’informations|Windows Phone 8|Windows Phone 8.1|
|----------------|------|-----|------------------------------|
|**Demander un mot de passe pour la déverrouiller les appareils mobiles**|Indique si les utilisateurs doivent entrer un mot de passe pour accéder à leurs appareils.|Oui|Oui|
|**Obligatoires type de mot de passe**|Spécifie le type de mot de passe qui sera requis, tels qu’alphanumérique ou numérique uniquement.|Oui|Oui|
|**Tapez votre mot de passe requis – nombre minimal de jeux de caractères**|Spécifie le nombre de caractères différents jeux doivent être inclus dans le mot de passe. Il existe quatre jeux de caractères : toutes les lettres minuscules, majuscules, nombres et symboles. Toutefois, pour les appareils iOS, cela spécifie le nombre de symboles qui doivent être inclus dans le mot de passe.|Oui|Oui|
|**Longueur minimale**|Spécifie le nombre minimal de caractères qui sont requis dans le mot de passe.|Oui|Oui|
|**Autoriser les mots de passe simples**|Spécifie que les mots de passe simples tels que « 0000 » et « 1234 » peuvent être utilisées.|Oui|Oui|
|**Nombre d’échecs de signe répétées autorisé avant que l’appareil est sélective**|Spécifie le nombre d’heures que peut être entré un mot de passe avant de l’appareil est sélective.|Oui|Oui|
|**Minutes d’inactivité avant la désactivation de l’écran**|Spécifie la durée pendant laquelle qu'un appareil doit rester inactif avant que l’écran est verrouillé automatiquement.|Oui|Oui|
|**Expiration du mot de passe (jours)**|Spécifie le nombre de jours avant que le mot de passe doit être modifié.|Oui|Oui|
|**N’oubliez pas de l’historique de mot de passe**|Indique si les mots de passe précédemment utilisés sont à retenir pour empêcher l’utilisateur de les utiliser à nouveau.|Oui|Oui|
|**Historique de mot de passe mémoriser** : **éviter la réutilisation des mots de passe précédents**|Spécifie le nombre de mots de passe précédemment utilisés sont à retenir.|Oui|Oui|

### Paramètres de chiffrement

|Nom du paramètre|Plus d’informations|Windows Phone 8|Windows Phone 8.1|
|----------------|------|------|-----------------------------|
|**Exiger le chiffrement sur appareil mobile**|Nécessite que les données sur les appareils mobiles pris en charge chiffrées.<br>Pour les appareils Windows Phone 8, vous devez définir sur **Oui**.|Oui|Oui|

### Paramètres système

|Nom du paramètre|Plus d’informations|Windows Phone 8|Windows Phone 8.1|
|----------------|-----|------|------------------------------|
|**Permettre la capture d’écran**|Permet à l’utilisateur de capturer le contenu de l’écran en tant que fichier image.|N°|Oui|
|**Autorise l’envoi de données de diagnostic**|Active le périphérique envoyer les informations de diagnostic à Microsoft.|N°|Oui|

### Comptes et la synchronisation des paramètres de cloud

|Nom du paramètre|Plus d’informations|Windows Phone 8|Windows Phone 8.1|
|----------------|------|-----|------------------------------|
|**Autoriser le compte Microsoft**|Permet à un compte Microsoft pour être lié à l’appareil.|N°|Oui|

### Paramètres de messagerie

|Nom du paramètre|Plus d’informations|Windows Phone 8|Windows Phone 8.1|
|----------------|-----|-----|-------------------------------|
|**Autoriser les comptes de messagerie personnalisé**|Active le périphérique pour vous connecter à des comptes de messagerie non Microsoft.|N°|Oui|

### Paramètres de l’application - navigateur

|Nom du paramètre|Plus d’informations|Windows Phone 8|Windows Phone 8.1|
|----------------|-----|-----|-------------------------------|
|**Autoriser le navigateur web**|Active ou bloque le navigateur web intégré sur les appareils.|N°|Oui|

### Paramètres de l’application - applications

|Nom du paramètre|Plus d’informations|Windows Phone 8|Windows Phone 8.1|
|----------------|-----|------|------------------------------|
|**Autoriser le magasin d’applications**|Permet aux utilisateurs de se connecter au magasin des applications à partir de l’appareil.|N°|Oui|

### Paramètres du périphérique fonctionnalités - matériel

|Nom du paramètre|Plus d’informations|Windows Phone 8|Windows Phone 8.1|
|----------------|-----|----|--------------------------------|
|**Autoriser l’appareil photo**|Permet d’activer ou de blocs de photo l’appareil.|N°|Oui|
|**Autoriser le stockage amovible**|Permet au périphérique utiliser amovibles tels que des cartes SD.|Oui|Oui|
|**Autoriser le Wi-Fi**|Active ou désactive la fonctionnalité Wi-Fi du périphérique.|N°|Oui|
|**Autoriser le Wi-Fi attache**|Permet d’utiliser le Wi-Fi attache sur l’appareil.|N°|Oui
|**Autoriser la connexion automatique libérer des points d’accès Wi-Fi**|Active le périphérique pour vous connecter automatiquement pour libérer des points d’accès Wi-Fi et accepter automatiquement les conditions d’utilisation.|N°|Oui|
|**Autoriser les rapports de zone réactive Wi-Fi**|Envoie les informations à propos des connexions réseau Wi-Fi pour aider l’utilisateur à découvrir à proximité des connexions.|N°|Oui|
|**Autoriser géolocalisation**|Active le périphérique à utiliser les informations d’emplacement.|N°|Oui|
|**Autoriser NFC**|Permet aux opérations qui utilisent communication de champ proche.|N°|Oui|
|**Autoriser Bluetooth**|Active ou désactive les fonctionnalités Bluetooth de l’appareil.|N°|Oui|

### Paramètres du périphérique fonctionnalités - fonctionnalités

|Nom du paramètre|Plus d’informations|Windows Phone 8|Windows Phone 8.1|
|----------------|----|------|-------------------------------|
|**Autoriser les copier et coller**|Permet de copie et coller des fonctionnalités sur les appareils.|N°|Oui|

### Paramètres pour les applications autorisées et bloquées
Dans la liste **autorisés et bloquées applications** , spécifiez une liste des applications que vous souhaitez autoriser ou bloquer en utilisant les informations suivantes :

> [!NOTE]
> Une seule stratégie peut contenir une liste des applications bloquées ou autorisées. Vous ne pouvez pas spécifier à la fois dans la même stratégie.

|Nom du paramètre|Plus d’informations|
|----------------|--------------------|
|**Bloc appareils d’ouvrir la liste des applications**|Répertorie les applications qui ne sont pas gérés par Intune et les utilisateurs ne sont pas autorisé à installer et exécuter.|
|**Autoriser les périphériques à installer uniquement les applications répertoriées**|Répertorie les applications que les utilisateurs sont autorisés à installer. Les utilisateurs ne peuvent pas installer toutes les autres applications. Applications qui sont gérées par Intune sont automatiquement autorisées.|
|**Ajouter**|Ajoute une application à la liste sélectionnée. Spécifiez un nom de votre choix, l’URL à l’application dans l’app store et à l’éditeur de l’application (facultatif). Pour plus d’informations, voir comment spécifient des URL vers stores application plus loin dans cette rubrique.
|**Importer des applications**|Importer une liste des applications que vous avez spécifié dans un fichier de valeurs séparées par des virgules. Utiliser le format de nom de l’application, publisher et URL de l’application dans le fichier.|
|**Modifier**|Vous permet de modifier le nom, publisher et l’URL de l’application sélectionnée.|
|**Supprimer**|Supprime l’application sélectionnée dans la liste.|
> [!IMPORTANT]
> Si vous spécifiez une liste des applications autorisées pour les appareils Windows Phone 8.1, vous devez ajouter l’application portail d’entreprise à cette liste ou elle est bloquée.


### Informations de référence pour autorisés et bloqués applications

#### Comment spécifier un URL à application stocke
Pour spécifier une URL de l’application dans la liste d’applications autorisés et bloqués, utilisez le format suivant :

Dans la page [Applications Windows Phone + jeux](http://www.windowsphone.com/en-us/store/overview) , recherchez l’application que vous souhaitez utiliser.

Ouvrez la page de l’application et copiez l’URL dans le Presse-papiers. Vous pouvez désormais utiliser ce que l’URL dans des options la liste d’applications bloqués ou autorisés.

**Exemple :** Recherche dans le magasin pour l’application Skype. L’URL que vous utilisez sera **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.

## Paramètres de stratégie personnalisés
Utiliser la **stratégie de configuration personnalisée Windows Phone** de Microsoft Intune pour déployer des paramètres de OMA URI pouvant être utilisées pour contrôler les fonctionnalités sur les **appareils Windows Phone 8.1**. Il s’agit des paramètres standard de nombreux fabricants d’appareil mobile permettent de contrôler les fonctionnalités de l’appareil.

Cette fonctionnalité permet de déployer des paramètres de Windows Phone ne peuvent pas être configurés avec une stratégie de configuration générale Intune. Pour plus d’informations sur les paramètres que vous pouvez configurer ces stratégies, voir [Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

De l’aide de la création de paramètres OMA URI pour appareils Windows Phone, consultez la [documentation de protocole de Windows Phone 8.1 périphériques mobiles](http://technet.microsoft.com/library/dn499787.aspx).

### Paramètres généraux

|Nom du paramètre|Plus d’informations|
|----------------|--------------------|
|**Nom**|Entrez un nom unique pour la stratégie pour vous aider à identifier dans la console Intune.|
|**Description**|Fournir une description qui donne un aperçu de la stratégie et d’autres informations pertinentes qui vous aide à rechercher.|

### Paramètres d’OMA URI

Dans la section **Paramètres d’URI de OMA** , cliquez sur **Ajouter** pour ajouter un paramètre. Vous pouvez également modifier ou supprimer un paramètre existant.

Dans la boîte de dialogue **Ajouter ou modifier le paramètre OMA URI** , spécifiez les informations suivantes :

|Nom du paramètre|Plus d’informations|
    |--------|--------------------|
    |**Nom du paramètre**|Entrez un nom unique pour le paramètre OMA URI pour vous aider à identifier dans la liste des paramètres.|
    |**Description du paramètre**|Fournir une description qui offre une vue d’ensemble du paramètre et d’autres informations pertinentes pour vous aider à rechercher.|
    |**Type de données**|Sélectionnez le type de données dans laquelle vous spécifierez ce paramètre OMA URI. Choisir :<br /><br />-   **Chaîne**<br />-   **Chaîne (XML)**<br />-   **Date et heure**<br />-   **Nombre entier**<br />-   **Virgule flottante**<br />-   **Valeur booléenne**|
    |**OMA-URI (respecter la casse)**|Spécifiez l’URI OMA pour lequel vous souhaitez fournir un paramètre.|
    |**Valeur**|Spécifier la valeur à associer à l’URI OMA que vous avez spécifiée précédemment.|

### Voir aussi
[Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
