---
title: "Paramètres de stratégie de sécurité appareil mobile | Microsoft Intune"
description: "Intune utiliser pour configurer un large éventail de paramètres que vous pouvez déployer sur gèrent les périphériques de votre organisation."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 04dec6046a54550070b4fec4622d134ec9ff94b3
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Paramètres de stratégie de sécurité appareil mobile dans Microsoft Intune
> [!IMPORTANT]
> Microsoft Intune comporte désormais des stratégies de configuration distincts pour chaque plateforme de l’appareil. Ces règles contiennent les paramètres plus à jour que vous pouvez utiliser. Vous pouvez continuer à utiliser la stratégie de sécurité d’appareil mobile, et les déploiements existantes fonctionnent toujours. Toutefois, vous devez planifier migrer vers les nouvelles stratégies de configuration dès que possible, car la stratégie de sécurité d’appareil mobile sont supprimée à l’avenir.

Vous pouvez utiliser les stratégies de sécurité Intune appareil mobile pour configurer un large éventail de paramètres que vous pouvez déployer sur périphériques gérés dans votre organisation. Ces paramètres sont utilisés pour contrôler la fonctionnalité et la sécurité de vos appareils.

Vous pouvez créer et déployer des stratégies de sécurité d’appareil mobile pour les types d’appareil suivants :

-   Inscrits périphériques de Windows 8.1 et Windows RT 8.1

-   Windows RT

-   Windows Phone 8 et Windows Phone 8.1

-   iOS

-   Android et Samsung KNOX

> [!NOTE]
> Certains paramètres ne sont pas applicables à certains appareils. Consultez les tableaux ci-dessous pour une liste complète des paramètres que vous pouvez configurer.

## Paramètres de sécurité

|Nom du paramètre|Windows 8.1 et Windows RT 8.1|Windows RT|Windows Phone 8 et Windows Phone 8.1|iOS|Android et Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Demander un mot de passe pour la déverrouiller les appareils mobiles**|N°|N°|Oui|Oui|Oui|
|**Obligatoires type de mot de passe**<br /><br />Ce paramètre spécifie le type de mot de passe qui sera requis, par exemple numérique uniquement ou alphanumérique.|Oui|Oui|Oui|Oui|N°|
|**Tapez votre mot de passe requis – nombre minimal de jeux de caractères**<br /><br />Il existe quatre jeux de caractères : toutes les lettres minuscules, majuscules, nombres et symboles. Ce paramètre spécifie le nombre de caractères différents jeux doivent être inclus dans le mot de passe. Toutefois, pour les appareils iOS, cela spécifie le nombre de caractères spéciaux qui doivent être inclus dans le mot de passe.|Oui|Oui|Oui|Oui|N°|
|**Longueur minimale**|Oui|Oui|Oui|Oui|Oui|
|**Autoriser les mots de passe simples**<br /><br />Les mots de passe simples incluent « 0000 » et « 1234 ».|N°|N°|Oui|Oui|N°|
|**Nombre d’échecs de signe répétées autorisé avant que l’appareil est sélective**|Oui|Oui|Oui|Oui|Oui|
|**Minutes d’inactivité avant de l’écran désactive les**<sup>1</sup>|Oui|Oui|Oui|Oui|Oui|
|**Expiration du mot de passe (jours)**|Oui|Oui|Oui|Oui|Oui|
|**N’oubliez pas de l’historique de mot de passe**|Oui|Oui|Oui|Oui|Oui|
|**Historique de mot de passe mémoriser** : **éviter la réutilisation des mots de passe précédents**|Oui|Oui|Oui|Oui|Oui|
|**Qualité de mot de passe**|N°|N°|N°|N°|Oui|
|**Autoriser le mot de passe image et un code confidentiel**|Oui|Oui|N°|N°|N°|
|**Minutes d’inactivité avant de mot de passe est nécessaire**|N°|N°|N°|Oui|N°|
|**Autoriser l’empreinte déverrouiller**|N°|N°|N°|iOS 7 et versions ultérieures|N°|
<sup>1</sup>pour les appareils iOS, lorsque vous configurez les paramètres de **Minutes d’inactivité avant de l’écran désactive les** **Minutes d’inactivité avant de mot de passe est requis**, ils sont appliqués dans l’ordre. Par exemple, si vous définissez la valeur pour les deux paramètres à **5** minutes, l’écran de désactiver automatiquement après 5 minutes, et l’appareil est verrouillé après une supplémentaire 5 minutes. Toutefois, si l’utilisateur désactive manuellement l’écran, le deuxième paramètre est appliqué immédiatement. Dans cet exemple, une fois que l’utilisateur a désactivé l’écran, le périphérique verrouille 5 minutes plus tard.

Lorsque vous déployez une stratégie de longueur de mot de passe aux périphériques qui exécutent Windows RT, les utilisateurs auront à leur mot de passe, même si son mot de passe actuel est conforme aux critères de la stratégie.

## Paramètres de chiffrement

|Nom du paramètre|Windows 8.1 et Windows RT 8.1|Windows RT|Windows Phone 8 et Windows Phone 8.1|iOS|Android et Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Exiger le chiffrement sur appareil mobile**<sup>1</sup><br /><br />Pour les appareils Windows Phone 8, vous devez définir sur **Oui**.<br /><br />Pour activer le chiffrement sur les appareils iOS, activez le paramètre **Exiger un mot de passe pour la déverrouiller les appareils mobiles**.|Oui|N°|Oui|N°|Oui|
|**Exiger le chiffrement sur les cartes de stockage**<br /><br />Ce paramètre s’applique aux périphériques sont également gérés par Exchange ActiveSync.|n/a|n/a|n/a <br />Applications et données associées sont chiffrées automatiquement.|n/a|Oui|
<sup>1</sup>Voici des informations supplémentaires pour les appareils exécutant Windows 8.1 :

-   Pour appliquer le chiffrement sur les appareils exécutant Windows 8.1, vous devez installer le [décembre 2014 MDM mise à jour du client pour Windows](http://support.microsoft.com/kb/3013816) sur chaque appareil.

-   Si vous activez ce paramètre pour les appareils Windows 8.1, tous les utilisateurs de l’appareil doivent avoir un compte Microsoft.

-   Pour le chiffrement fonctionne, le périphérique doit respecter les exigences de certification Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) matériel.

-   Lorsque vous appliquez le chiffrement sur un appareil, la clé de récupération n’est accessible à partir de compte Microsoft de l’utilisateur, qui est accessible à partir de leur propre compte OneDrive. Vous ne pouvez pas récupérer cette touche au nom d’un utilisateur.

## Paramètres de programmes malveillants

|Nom du paramètre|Windows 8.1 et Windows RT 8.1|Windows RT|Windows Phone 8 et Windows Phone 8.1|iOS|Android et Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Exiger pare-feu réseau**|Oui|N°|N°|N°|N°|
|**Activer SmartScreen**|Oui|N°|N°|N°|N°|

## Paramètres système

|Nom du paramètre|Windows 8.1 et Windows RT 8.1|Windows RT|Windows Phone 8 et Windows Phone 8.1|iOS|Android et Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Exiger des mises à jour automatiques**|Oui|N°|N°|N°|N°|
|**Exiger des mises à jour automatiques – classification Minimum d’installation automatiquement mises à jour**<br /><br />Choisissez la classification des mises à jour qui sera automatiquement installé :<br /><br />- **Important**. Installe toutes les mises à jour qui sont classés comme étant important.<br /><br />- **Recommandé**. Installe toutes les mises à jour qui sont considérés comme important ou recommandés.|Oui|N°|N°|N°|N°|
|**Permettre la capture d’écran**|N°|N°|Windows Phone 8.1 uniquement|Oui|Oui (Samsung KNOX uniquement)|
|**Autoriser le centre de contrôle dans l’écran de verrouillage**|N°|N°|N°|iOS 7 et versions ultérieures|N°|
|**Autoriser l’affichage de la notification dans l’écran de verrouillage**|N°|N°|N°|iOS 7 et versions ultérieures|N°|
|**Autoriser l’affichage aujourd'hui dans l’écran de verrouillage**|N°|N°|N°|iOS 7 et versions ultérieures|N°|
|**Contrôle de compte d’utilisateur**|Oui|N°|N°|N°|N°|
|**Autorise l’envoi de données de diagnostic**|Oui|N°|Windows Phone 8.1 uniquement|Oui|Oui (Samsung KNOX uniquement)|
|**Autoriser les certificats TLS non approuvés**|N°|N°|N°|Oui|N°|
|**Autoriser les logiciels de portefeuille personnel lorsqu’elles sont verrouillées**|N°|N°|N°|Oui|N°|
|**Autoriser usine par défaut**|N°|N°|N°|N°|Oui (Samsung KNOX uniquement)|


## Paramètres de documents et des données en nuage

|Nom du paramètre|Windows 8.1 et Windows RT 8.1|Windows RT|Windows Phone 8 et Windows Phone 8.1|iOS|Android et Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Autoriser de sauvegarde sur iCloud**|N°|N°|N°|Oui|N°|
|**Autoriser la synchronisation de document à iCloud**|N°|N°|N°|Oui|N°|
|**Autoriser la synchronisation des flux de Photo pour iCloud**|N°|N°|N°|Oui|N°|
|**Exiger la sauvegarde chiffrée**|N°|N°|N°|Oui|N°|
|**URL de dossiers de travail**<br /><br />Ce paramètre définit l’URL du dossier de travail pour autoriser les documents à synchroniser tous les périphériques.|Oui|N°|N°|N°|N°|
|**Autoriser la sauvegarde Google**|N°|N°|N°|N°|Oui (Samsung KNOX uniquement)|

## Comptes et la synchronisation des paramètres de cloud

|Nom du paramètre|Windows 8.1 et Windows RT 8.1|Windows RT|Windows Phone 8 et Windows Phone 8.1|iOS|Android et Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Autoriser le compte Microsoft**|N°|N°|Windows Phone 8.1 uniquement|N°|N°|
|**Autoriser la synchronisation automatique de compte Google**|N°|N°|N°|N°|Oui (Samsung KNOX uniquement)|

## Paramètres de messagerie

|Nom du paramètre|Windows 8.1 et Windows RT 8.1|Windows RT|Windows Phone 8 et Windows Phone 8.1|iOS|Android et Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permettre aux utilisateurs de télécharger des pièces jointes**<sup>1</sup>|n/a|n/a|n/a|n/a|n/a|
|**Période de synchronisation de messagerie** <br /><br />Ce paramètre s’applique aux périphériques sont également gérés par Exchange ActiveSync.|n/a|n/a|n/a|n/a|n/a|
|**Autoriser les périphériques mobiles qui ne prennent entièrement en charge ces paramètres pour la synchronisation avec Exchange (Exchange ActiveSync)** <br /><br />Ce paramètre s’applique aux périphériques sont également gérés par Exchange ActiveSync.|n/a|n/a|n/a|n/a|n/a|
|**Faites Microsoft compte facultatives dans l’application Windows Mail**|Oui|N°|N°|N°|N°|
|**Autoriser les comptes de messagerie personnalisé**|N°|N°|Windows Phone 8.1 uniquement|N°|N°|

## Paramètres de l’application - navigateur

|Nom du paramètre|Windows 8.1 et Windows RT 8.1|Windows RT|Windows Phone 8 et Windows Phone 8.1|iOS|Android et Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Autoriser le navigateur web**|N°|N°|Windows Phone 8.1 uniquement|Oui|Oui (Samsung KNOX uniquement)|
|**Autoriser la recopie incrémentée**|Oui|N°|N°|Oui|Oui (Samsung KNOX uniquement)|
|**Autoriser le bloqueur de fenêtres**|Oui|N°|N°|Oui|Oui (Samsung KNOX uniquement)|
|**Activer les cookies**|N°|N°|N°|Oui|Oui (Samsung KNOX uniquement)|
|**Autoriser le plug-in**|Oui|N°|N°|N°|N°|
|**Autoriser les scripts actifs**|Oui|N°|N°|Oui|Oui (Samsung KNOX uniquement)|
|**Autoriser l’avertissement de fraude**|Oui|N°|N°|Oui|N°|
|**Autoriser site intranet pour la saisie de mot unique**<br /><br />(Ce paramètre permet d’utiliser un seul mot pour diriger Internet Explorer vers un site Web — par exemple, sur Bing.)|Oui|N°|N°|N°|N°|
|**Autoriser la détection automatique du réseau intranet**|Oui|N°|N°|N°|N°|
|**Niveau de sécurité pour Internet**|Oui|N°|N°|N°|N°|
|**Niveau de sécurité pour un intranet.**|Oui|N°|N°|N°|N°|
|**Niveau de sécurité pour les sites de confiance**|Oui|N°|N°|N°|N°|
|**Niveau de sécurité pour les sites sensibles**|Oui|N°|N°|N°|N°|
|**Envoyer l’en-tête de suivi de faire pas**|Oui|N°|N°|N°|N°|
|**Autoriser l’accès au menu Mode entreprise**|Oui|N°|N°|N°|N°|
|**Emplacement du Mode entreprise site liste**|Oui|N°|N°|N°|N°|

## Paramètres de l’application - applications

|Nom du paramètre|Windows 8.1 et Windows RT 8.1|Windows RT|Windows Phone 8 et Windows Phone 8.1|iOS|Android et Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Autoriser le magasin d’applications**|N°|N°|Windows Phone 8.1 uniquement|Oui|Oui (Samsung KNOX uniquement)|
|**Demander un mot de passe pour accéder aux magasin d’applications**|N°|N°|N°|Oui|N°|
|**Autoriser les achats dans l’application**|N°|N°|N°|Oui|N°|
|**Autoriser les documents gérées dans les autres applications non gérées**|N°|N°|N°|iOS 7 et versions ultérieures|N°|
|**Autoriser les documents non gérés dans d’autres applications gérées**|N°|N°|N°|iOS 7 et versions ultérieures|N°|
|**Autoriser les visioconférences**|N°|N°|N°|Oui|N°|
|**Autoriser le gros contenu multimédia Store**|N°|N°|N°|Oui|N°|
|**Autoriser l’installation de l’application**|N°|N°|N°|iOS 6 et versions ultérieures|N°|

## Paramètres de l’application - jeux

|Nom du paramètre|Windows 8.1 et Windows RT 8.1|Windows RT|Windows Phone 8 et Windows Phone 8.1|iOS|Android et Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Autoriser vos amis centre des jeux**|N°|N°|N°|Oui|N°|
|**Autoriser les jeux multijoueurs**|N°|N°|N°|Oui|N°|

## Paramètres du périphérique fonctionnalités - matériel

|Nom du paramètre|Windows 8.1 et Windows RT 8.1|Windows RT|Windows Phone 8 et Windows Phone 8.1|iOS|Android et Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Autoriser l’appareil photo**|N°|N°|Windows Phone 8.1 uniquement|Oui|Oui|
|**Autoriser le stockage amovible**|N°|N°|Oui|N°|Oui (Samsung KNOX uniquement)|
|**Autoriser le Wi-Fi**|N°|N°|Windows Phone 8.1 uniquement|N°|Oui (Samsung KNOX uniquement)|
|**Autoriser le Wi-Fi attache**|N°|N°|Windows Phone 8.1 uniquement|N°|Oui (Samsung KNOX uniquement)|
|**Autoriser la connexion automatique libérer des points d’accès Wi-Fi**|N°|N°|Windows Phone 8.1 uniquement|N°|N°|
|**Autoriser les rapports de zone réactive Wi-Fi**<br /><br />Ce paramètre envoie les informations à propos des connexions réseau Wi-Fi pour aider à découvrir à proximité des connexions.|N°|N°|Windows Phone 8.1 uniquement|N°|N°|
|**Autoriser géolocalisation**<br /><br />Ce paramètre permet le périphérique à utiliser les informations d’emplacement.|N°|N°|Windows Phone 8.1 uniquement|N°|Oui (Samsung KNOX uniquement)|
|**Autoriser NFC**<br /><br />Ce paramètre permet les opérations qui utilisent la communication de champ proche.|N°|N°|Windows Phone 8.1 uniquement|N°|Oui (Samsung KNOX uniquement)|
|**Autoriser Bluetooth**|N°|N°|Windows Phone 8.1 uniquement|N°|Oui (Samsung KNOX uniquement)|
|**Autoriser power désactiver**<br>Si ce paramètre est désactivé, le paramètre **nombre d’échecs autorisé avant que l’appareil est sélective de connexion répétées** pour les appareils Samsung KNOX ne fonctionne pas.|N°|N°|N°|N°|Oui (Samsung KNOX uniquement)|

## Paramètres du périphérique fonctionnalités - cellulaires

|Nom du paramètre|Windows 8.1 et Windows RT 8.1|Windows RT|Windows Phone 8 et Windows Phone 8.1|iOS|Android et Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Autoriser l’itinérance vocale**|N°|N°|N°|Oui|Oui (Samsung KNOX uniquement)|
|**Autoriser l’itinérance de données**|Oui|N°|N°|Oui|Oui (Samsung KNOX uniquement)|
|**Autoriser la synchronisation automatique en cas d’itinérance**|N°|N°|N°|Oui|N°|
|**Autoriser la messagerie SMS/MMS**|N°|N°|N°|N°|Oui (Samsung KNOX uniquement)|

## Paramètres du périphérique fonctionnalités - fonctionnalités

|Nom du paramètre|Windows 8.1 et Windows RT 8.1|Windows RT|Windows Phone 8 et Windows Phone 8.1|iOS|Android et Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Autoriser l’assistant de voix**|N°|N°|N°|Oui|Oui (Samsung KNOX uniquement)|
|**Autoriser assistant vocale lors de l’appareil est verrouillé**|N°|N°|N°|Oui|N°|
|**Autoriser la numérotation vocale**|N°|N°|N°|Oui|Oui (Samsung KNOX uniquement)|
|**Autoriser les copier et coller**|N°|N°|Windows Phone 8.1 uniquement|N°|Oui (Samsung KNOX uniquement)|
|**Autoriser Presse-papiers partager entre les applications**|N°|N°|N°|N°|Oui (Samsung KNOX uniquement)|
|**Autoriser YouTube**|N°|N°|N°|N°|Oui (Samsung KNOX uniquement)|

### Voir aussi
[Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
