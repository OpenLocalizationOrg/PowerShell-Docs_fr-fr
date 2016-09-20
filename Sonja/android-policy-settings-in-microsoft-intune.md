---
title: "Android et les paramètres de stratégie Samsung KNOX | Microsoft Intune"
description: "Créer des stratégies qui contrôlent les paramètres et les fonctionnalités sur les appareils Android que vous gérez avec Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71cc39cf-e726-40fd-8d08-78776e099a4b
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 870d735644f08e3eca8c72bca2b156947d798cb5
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Android et les paramètres de stratégie Samsung KNOX dans Microsoft Intune

Intune fournit une plage de paramètres généraux prédéfinis que vous pouvez configurer sur les appareils Android. En outre, vous pouvez spécifier des valeurs d’ouvrir Mobile Alliance Uniform Resource Identifier (URI OMA) pour créer des paramètres personnalisés qui ne sont pas disponibles dans Intune.

## Stratégie de configuration général

Utilisez la Intune **stratégie de configuration général Android** pour configurer les paramètres pour :

-   **Paramètres de sécurité d’appareil mobile** - choisir parmi une liste de paramètres prédéfinis qui vous permettent de contrôler une plage de fonctionnalités sur l’appareil.

-   **Mode plein écran** (pour les appareils Samsung KNOX périphériques uniquement) - verrouiller un appareil pour autoriser uniquement certaines fonctionnalités de fonctionner. Par exemple, vous pouvez autoriser un appareil exécuter une application gérée que vous spécifiez, ou vous pouvez désactiver les boutons de volume sur un appareil. Ces paramètres peuvent être utilisés pour un modèle de démonstration d’un appareil ou un appareil dédié à l’exécution d’une seule fonction, par exemple un périphérique de vente.

-   **Conforme et applications non conformes** - spécifier une liste d’applications qui sont conformes dans votre entreprise. Sur les appareils Android et iOS, le **Rapport applications non conformes** peut servir à afficher la conformité des applications que vous avez spécifié dans la liste des applications que les utilisateurs ont installé. Le rapport ne peut pas réellement bloquer l’installation de l’application.

> [!TIP]
> Vous pouvez configurer des termes et conditions pour les utilisateurs afin qu’ils reconnaissent que toutes les applications sur leur appareil, y compris les applications personnelles, seront évaluées et que les applications non conformes ne doit être bloquées ou signalées comme non conformes. Les utilisateurs doivent accepter les conditions d’utilisation avant de pouvoir inscrire leur appareil et utiliser le portail d’entreprise pour obtenir des applications. Pour plus d’informations sur l’utilisation des termes et conditions, voir [conditions et paramètres de stratégie de condition dans Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Si le paramètre que vous recherchez n’apparaît pas dans cette rubrique, vous pourrez peut-être créer votre document à l’aide d’une stratégie personnalisée Android qui vous permet d’utiliser des paramètres d’OMA URI pour contrôler l’appareil. Pour plus d’informations, accédez aux [paramètres de stratégie personnalisée](#custom-policy-settings) plus loin dans cette rubrique.

### Paramètres de mot de passe

|Nom du paramètre|Plus d’informations|Android 4.0 +|Samsung KNOX|
|----------------|-|----------------|----------------|
|**Demander un mot de passe pour la déverrouiller les appareils mobiles**|Spécifie s’il faut exiger un mot de passe sur les appareils pris en charge.|Oui|Oui|
|**Longueur minimale**|Spécifie la longueur minimale du mot de passe.|Oui|Oui|
|**Nombre d’échecs de signe répétées autorisé avant que l’appareil est sélective**|Spécifie le nombre d’échecs de connexion autorisé avant que l’appareil est sélective.|Oui|Oui|
|**Minutes d’inactivité avant la désactivation écran**|Spécifie le nombre de minutes d’inactivité avant de l’appareil verrouille automatiquement.|Oui|Oui|
|**Expiration du mot de passe (jours)**|Spécifie le nombre de jours avant d’un mot de passe doit être modifié.|Oui|Oui|
|**N’oubliez pas de l’historique de mot de passe**|Spécifie le nombre de mots de passe précédemment utilisés à l’esprit.|Oui|Oui|
|**N’oubliez pas de l’historique de mot de passe** - **empêcher la réutilisation des mots de passe précédents**|Empêche la réutilisation des mots de passe précédents.|Oui|Oui|
|**Qualité de mot de passe**|Spécifie le niveau de la complexité de mot de passe requis et si les périphériques biométriques peuvent être utilisées.|Oui|Oui|
|**Autoriser l’empreinte déverrouiller**|Permet l’utilisation d’une empreinte pour déverrouiller le périphérique.|N°|Oui|
|**Autoriser verrouillage Smart et autres agents de gestion de la confidentialité**<br>(Android 5 et versions ultérieur)|Vous permet de contrôler la fonctionnalité de verrouillage actives sur les appareils Android compatibles. Cette fonctionnalité de téléphone, un agent de gestion de la confidentialité, signalisation routière vous permet de désactiver ou ignorer le mot de passe écran de verrouillage périphérique si le périphérique est dans un emplacement approuvé (par exemple, lorsqu’il est connecté à un appareil Bluetooth spécifique, ou lorsqu’il est près une balise NFC.) Vous pouvez utiliser ce paramètre pour empêcher les utilisateurs de configurer verrouiller actives.|Oui|N°|

### Paramètres de chiffrement

|Nom du paramètre|Plus d’informations|Android 4.0 +|Samsung KNOX|
|----------------|---|-------------|----------------|
|**Exiger le chiffrement sur appareil mobile**|Nécessite que les fichiers sur le périphérique mobile sont chiffrés.|Oui|Oui|
|**Exiger le chiffrement sur les cartes de stockage**|Indique si la carte de stockage appareil doit être chiffrée.|N°|Oui|

### Paramètres système

|Nom du paramètre|Plus d’informations|Android 4.0 +|Samsung KNOX|
|----------------|---|-------------|----------------|
|**Permettre la capture d’écran**|Permet à l’utilisateur de capturer du contenu de l’écran en tant qu’image.|N°|Oui|
|**Autorise l’envoi de données de diagnostic**|Permet de présenter les informations de diagnostic pour Google.|N°|Oui|
|**Autoriser usine par défaut**|Permet à l’utilisateur effectuer une usine réinitialisée sur l’appareil.|N°|Oui|

### Paramètres - documents et des données en nuage

|Nom du paramètre|Plus d’informations|Android 4.0 +|Samsung KNOX|
|----------------|----|------------------------|----------------|
|**Autoriser la sauvegarde Google**|Permet l’utilisation de la sauvegarde de Google.|N°|Oui|

### Paramètres de cloud - comptes et la synchronisation

|Nom du paramètre|Plus d’informations|Android 4.0 +|Samsung KNOX|
|----------------|-----|-----------|----------------|
|**Autoriser la synchronisation automatique de compte Google**|Permet aux paramètres du compte Google à synchroniser automatiquement.|N°|Oui|

### Paramètres de l’application - navigateur

|Nom du paramètre|Plus d’informations|Android 4.0 +|Samsung KNOX|
|----------------|-----|-----------|----------------|
|**Autoriser le navigateur web**|Indique si le navigateur par défaut de l’appareil peut être utilisé.|N°|Oui|
|**Autoriser la recopie incrémentée**|Permet à la fonction de la recopie incrémentée du navigateur web à utiliser.|N°|Oui|
|**Autoriser le bloqueur de fenêtres**|Permet l’utilisation de la bloqueur de fenêtres dans un navigateur web.|N°|Oui|
|**Activer les cookies**|Permet de navigateur web périphérique à utiliser les cookies.|N°|Oui|
|**Autoriser les scripts actifs**|Permet de navigateur web périphérique à utiliser active scripting.|N°|Oui|

### Paramètres de l’application - applications

|Nom du paramètre|Plus d’informations|Android 4.0 +|Samsung KNOX|
|----------------|----|------------|----------------|
|**Autoriser Google Play store**|Permet à l’utilisateur à accéder à Google Play store sur l’appareil.|N°|Oui|

### Paramètres du périphérique fonctionnalités - matériel

|Nom du paramètre|Plus d’informations|Android 4.0 +|Samsung KNOX|
|----------------|-----|-----------|----------------|
|**Autoriser l’appareil photo**|Permet l’utilisation de la caméra de l’appareil.|Oui|Oui|
|**Autoriser le stockage amovible**|Permet du périphérique à utiliser le stockage amovible, comme une carte SD.|N°|Oui|
|**Autoriser le Wi-Fi**|Permet d’utiliser des capacités Wi-Fi du périphérique.|N°|Oui|
|**Autoriser le Wi-Fi attache**|Permet l’utilisation du Wi-Fi attache sur l’appareil.|N°|Oui|
|**Autoriser géolocalisation**|Permet au périphérique d’utiliser les informations d’emplacement.|N°|Oui|
|**Autoriser NFC**|Permet aux opérations qui utilisent communication de champ proche si le périphérique prend en charge.|N°|Oui|
|**Autoriser Bluetooth**|Permet l’utilisation de Bluetooth sur l’appareil.|N°|Oui|
|**Autoriser power désactiver**|Permet à l’utilisateur d’éteindre l’appareil.<br /><br />Si ce paramètre est désactivé, le paramètre **nombre d’échecs autorisé avant que l’appareil est sélective de connexion répétées** pour les appareils Samsung KNOX ne fonctionne pas.|N°|Oui|

### Paramètres du périphérique fonctionnalités - cellulaires

|Nom du paramètre|Plus d’informations|Android 4.0 +|Samsung KNOX|
|----------------|---|-------------|----------------|
|**Autoriser l’itinérance vocale**|Permet de voix d’itinérance lorsque l’appareil est dans un réseau cellulaire.|N°|Oui|
|**Autoriser l’itinérance de données**|Permet aux données d’itinérance lorsque l’appareil est dans un réseau cellulaire.|N°|Oui|
|**Autoriser la messagerie SMS/MMS**|Permet l’utilisation de SMS et MMS la messagerie sur l’appareil.|N°|Oui|

### Paramètres du périphérique fonctionnalités - fonctionnalités

|Nom du paramètre|Plus d’informations|Android 4.0 +|Samsung KNOX|
|----------------|----|------------|----------------|
|**Autoriser l’assistant de voix**|Permet l’utilisation du logiciel assistant voice sur l’appareil.|N°|Oui|
|**Autoriser la numérotation vocale**|Active ou désactive la fonctionnalité de numérotation vocale sur l’appareil.|N°|Oui|
|**Autoriser les copier et coller**|Permet de copier et coller des fonctions sur l’appareil.|N°|Oui|
|**Autoriser Presse-papiers partager entre les applications**|Permet l’utilisation du Presse-papiers pour copier et coller entre les applications.|N°|Oui|
|**Autoriser YouTube**|Permet l’utilisation de YouTube sur l’appareil.|N°|Oui|

### Paramètres pour les applications conformes et non conformes
Dans la **compatible &amp; applications non conformes** liste, spécifiez une liste des applications conformes qui utilisent les informations suivantes :

> [!NOTE]
> Une seule stratégie peut contenir uniquement une liste des applications conformes ou une liste des applications non conformes. Vous ne pouvez pas spécifier à la fois dans la même stratégie.

|Nom du paramètre|Plus d’informations|
|----------------|--------------------|
|**Signaler non-conformité lorsque les utilisateurs installer les applications répertoriées**|Répertorie les applications qui ne sont pas gérés par Intune et qui vous ne souhaitez pas que les utilisateurs à installer et exécuter. Si les utilisateurs installent une de ces applications, il apparaît dans le rapport applications non conformes.|
|**Ne pas signaler non-conformité lorsque les utilisateurs installer les applications répertoriées**|Répertorie les applications que vous souhaitez autoriser. Pour rester compatible, les utilisateurs doivent installer pas toutes les applications qui ne sont pas répertoriées. Applications qui sont gérées par Intune sont automatiquement autorisées.|
|**Ajouter**|Ajoute une application à la liste sélectionnée. Spécifiez le nom de l’application, l’éditeur de l’application (facultatif) et l’URL de l’application dans l’app store.<br /><br />Pour plus d’informations, voir [spécifier les URL à application stocke](#specify-urls-to-app-stores) plus loin dans cette rubrique.|
|**Importer des applications**|Importer une liste des applications que vous avez spécifié dans un fichier de valeurs séparées par des virgules. Utiliser le format de nom de l’application, publisher et URL de l’application dans le fichier.|
|**Modifier**|Vous permet de modifier le nom, publisher et l’URL de l’application sélectionnée.|
|**Supprimer**|Supprime l’application sélectionnée dans la liste.|

### Paramètres du mode plein écran
Spécifier les paramètres suivants pour **les appareils Samsung KNOX**:

|Nom du paramètre|Plus d’informations|
|----------------|--------------------|
|**Sélectionnez une application gérée qui peut s’exécuter lorsque l’appareil est en mode plein écran**|Cliquez sur **Parcourir**et sélectionnez l’application gérée peut s’exécuter lorsque l’appareil est en mode plein écran (applications spécifiés comme un lien vers le magasin ne sont pas actuellement pris en charge). Aucun autres applications ne pourront s’exécuter sur l’appareil.|
|**Autoriser les boutons de volume**|Active ou désactive l’utilisation des boutons volume sur l’appareil.|
|**Autoriser le bouton de veille écran veille**|Active ou désactive le bouton écran veille veille sur l’appareil.|

### Informations de référence pour les applications conformes et non conformes

#### Surveiller des applications conformes et non conformes
Utilisez le **Rapport applications non conformes** pour afficher la conformité des autorisés et bloqués applications.

###### Pour exécuter le rapport applications non conformes

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), cliquez sur **rapports** &gt; **Rapport applications non conformes**.

2.  Sélectionnez les groupes de l’appareil que vous souhaitez vérifier. Puis choisissez si vous souhaitez vérifier les applications conformes, applications non conformes ou les deux. Pour finir, cliquez sur **Afficher le rapport**.

#### Spécifient des URL vers banques d’application
Pour spécifier une URL de l’application dans la liste d’applications conformes et non conformes, procédez comme suit :

Dans la [section applications de Google Play](https://play.google.com/store/apps), recherchez l’application que vous voulez utiliser.

Ouvrez la page d’installation pour l’application et puis copiez l’URL dans le Presse-papiers. Vous pouvez désormais utiliser ce que l’URL dans des options la liste d’applications conformes.

Exemple : Recherche Google Play pour Microsoft Office Mobile. L’URL que vous utilisez seront **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

## Paramètres de stratégie personnalisés
Utilisez la Microsoft Intune **stratégie Android configuration personnalisée** pour déployer les paramètres OMA URI pouvant être utilisées pour contrôler les fonctionnalités sur les appareils Android. Il s’agit des paramètres standard de nombreux fabricants d’appareil mobile permettent de contrôler les fonctionnalités de l’appareil.

Cette fonctionnalité est destinée à vous permettent de déployer des paramètres Android ne peuvent pas être configurés avec stratégies Intune.

> [!NOTE]
> Pour l’instant, Android stratégies personnalisées ne prennent en charge configuration des paramètres Wi-Fi pour les appareils Android incluant une clé communiquée.

### Paramètres généraux

|Nom du paramètre|Plus d’informations|
    |----------------|--------------------|
    |**Nom**|Entrez un nom unique pour la stratégie personnalisée Android pour vous aider à identifier dans la console Intune.|
    |**Description**|Fournir une description qui offre une vue d’ensemble de la stratégie personnalisée Android et autres informations pertinentes qui vous aide à rechercher.|

### Paramètres d’OMA URI

   |Nom du paramètre|Plus d’informations|
    |--------|--------------------|
    |**Nom du paramètre**|Entrez un nom unique pour le paramètre OMA URI pour vous aider à identifier dans la liste des paramètres.|
    |**Description du paramètre**|Fournir une description qui offre une vue d’ensemble du paramètre et d’autres informations pertinentes pour vous aider à rechercher.|
    |**Type de données**|Sélectionnez le type de données dans laquelle vous spécifierez ce paramètre OMA URI. Sélectionnez à partir de **chaîne, chaîne (XML), Date et heure, entier, virgule flottante**, ou **booléenne**.|
    |**OMA-URI (respecter la casse)**|Spécifiez l’OMA-URI que vous souhaitez fournir un paramètre pour.|
    |**Valeur**|Spécifier la valeur à associer à l’URI OMA que vous avez spécifiée précédemment.|

### Exemples

- [Créer un profil Wi-Fi avec une clé communiquée](pre-shared-key-wi-fi-profile.md)
- [Utiliser une stratégie personnalisée pour créer un profil VPN par application pour les appareils Android](per-app-vpn-for-android-pulse-secure.md)
- [Utiliser des stratégies personnalisées pour autoriser et bloquer des applications pour les appareils Samsung KNOX](custom-policy-to-allow-and-block-samsung-knox-apps.md)

### Voir aussi
[Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
