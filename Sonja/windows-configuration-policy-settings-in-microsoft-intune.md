---
title: "Paramètres de stratégie Windows | Microsoft Intune"
description: "Utilisez la stratégie de configuration générale de Intune Windows (Windows 8.1 et versions ultérieures) pour configurer les paramètres pour les appareils Windows 8.1 et Windows 8 inscrits."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: b02804f933f8c259ea12efefd0353a7d5ceda25c
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Paramètres de stratégie Windows Intune Microsoft
Utilisez la Microsoft Intune **stratégie de configuration général de Windows (Windows 8.1 et versions ultérieures)** pour configurer les paramètres suivants pour les appareils Windows 8 et Windows 8.1 inscrits :

## Paramètres d’application

|Nom du paramètre|Plus d’informations|
|----------------|----------------------------------|
|**Appliquer toutes les configurations vers Windows 10**|Active les paramètres dans cette stratégie à appliquer aux appareils Windows 10, en plus de périphériques Windows 8 et Windows 8.1.|

## Paramètres de sécurité

|Nom du paramètre|Plus d’informations|Windows 8.1 et Windows RT 8.1|Windows RT|
|----------------|------|----------------------------|--------------|
|**Obligatoires type de mot de passe**|Spécifie le type de mot de passe requis, par exemple alphanumérique ou numérique uniquement.|Oui|Oui|
|**Tapez votre mot de passe requis – nombre minimal de jeux de caractères**|Spécifie le nombre de caractères différents jeux doivent être inclus dans le mot de passe. Il existe quatre jeux de caractères : toutes les lettres minuscules, majuscules, nombres et symboles. Toutefois, pour les appareils iOS, ce paramètre spécifie le nombre de symboles qui doivent être inclus dans le mot de passe.|Oui|Oui|
|**Longueur minimale**<sup>1</sup>|Configure la longueur minimale requise (en caractères) pour le mot de passe.|Oui|Oui|
|**Nombre d’échecs de signe répétées autorisé avant que l’appareil est sélective**|Efface le périphérique si les tentatives de connexion échouent ce nombre de fois.|Oui|Oui|
|**Minutes d’inactivité avant la désactivation écran**|Spécifie le nombre de minutes qu'un périphérique doit être inactif avant un mot de passe est requis pour la déverrouiller.| Oui|Oui|
|**Expiration du mot de passe (jours)**|Spécifie le nombre de jours avant que le mot de passe doit être modifié.|Oui|Oui|
|**N’oubliez pas de l’historique de mot de passe**|Indique si l’utilisateur peut configurer des mots de passe utilisés précédemment.|Oui|Oui|
|**Historique de mot de passe mémoriser** : **éviter la réutilisation des mots de passe précédents**|Spécifie le nombre de mots de passe précédemment utilisés rappeler par le périphérique.|Oui|Oui|
|**Autoriser le mot de passe image et un code confidentiel**|Permet l’utilisation d’un mot de passe image et un code confidentiel. Un mot de passe image permet à l’utilisateur connectez-vous à l’aide de gestes sur une image. Un code confidentiel permet aux utilisateurs de se connecter rapidement avec un code à quatre chiffres.|Oui|Oui|
<sup>1</sup> lorsque vous déployez une stratégie de longueur de mot de passe aux périphériques qui exécutent Windows RT, les utilisateurs auront à réinitialiser les mots de passe, même si son mot de passe actuel est conforme aux critères de la stratégie.

## Paramètres de chiffrement

|Nom du paramètre|Plus d’informations|Windows 8.1 et Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Exiger le chiffrement sur appareil mobile**<sup>1</sup>|Nécessite que les fichiers sur l’appareil sont chiffrés.<br>Pour les appareils Windows Phone 8, vous devez définir sur **Oui**.|Oui|N°|
<sup>1</sup> des informations supplémentaires pour les appareils exécutant Windows 8.1

-   Pour appliquer le chiffrement sur les appareils exécutant Windows 8.1, vous devez installer le [décembre 2014 MDM mise à jour du client pour Windows](http://support.microsoft.com/kb/3013816) sur chaque appareil.

-   Si vous activez ce paramètre pour les appareils Windows 8.1, tous les utilisateurs de l’appareil doivent avoir un compte Microsoft.

-   Pour le chiffrement fonctionne, le périphérique doit respecter les exigences de certification Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) matériel.

-   Lorsque vous appliquez le chiffrement sur un appareil, la clé de récupération n’est accessible à partir de compte Microsoft de l’utilisateur, qui est accessible à partir de leur propre compte OneDrive. Vous ne pouvez pas récupérer cette touche au nom d’un utilisateur.

## Paramètres de programmes malveillants

|Nom du paramètre|Plus d’informations|Windows 8.1 et Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Exiger pare-feu réseau**|Nécessite que le pare-feu Windows est activé.|Oui|N°|
|**Activer SmartScreen**|Nécessite l’utilisation de Windows SmartScreen.|Oui|N°|

## Paramètres système

|Nom du paramètre|Plus d’informations|Windows 8.1 et Windows RT 8.1|Windows RT|
|----------------|-------|---------------------------|--------------|
|**Exiger des mises à jour automatiques**|Pour activer les mises à jour automatiques définition sur les appareils.|Oui|N°|
|**Exiger des mises à jour automatiques – classification Minimum d’installation automatiquement mises à jour**|Choisit le classement des mises à jour qui sera automatiquement installé :<br /><br />-   **Important** – installe toutes les mises à jour qui sont classés comme étant important.<br />-   **Recommandé** – installe toutes les mises à jour qui sont considérés comme important ou recommandés.|Oui|N°|
|**Contrôle de compte d’utilisateur**|Nécessite l’utilisation du contrôle (compte utilisateur) sur les appareils mobiles.|Oui|N°|
|**Autorise l’envoi de données de diagnostic**|Active le périphérique envoyer les informations de diagnostic à Microsoft.|Oui|N°|


## Paramètres de documents et des données en nuage

|Nom du paramètre|Plus d’informations|Windows 8.1 et Windows RT 8.1|Windows RT|
|----------------|------|----------------------------|--------------|
|**URL de dossiers de travail**|Définit l’URL du dossier de travail pour autoriser les documents à synchroniser tous les périphériques.|Oui|N°|

## Paramètres de messagerie

|Nom du paramètre|Plus d’informations|Windows 8.1 et Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Faites Microsoft compte facultatives dans l’application Windows Mail**|Permet d’accéder à l’application Windows Mail sans un compte Microsoft.|Oui|N°|

## Paramètres de l’application - navigateur

|Nom du paramètre|Plus d’informations|Windows 8.1 et Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Autoriser la recopie incrémentée**|Permet aux utilisateurs de modifier les paramètres de saisie semi-automatique dans le navigateur.|Oui|N°|
|**Autoriser le bloqueur de fenêtres**|Active ou désactive le bloqueur de navigateur.|Oui|N°|
|**Autoriser le plug-in**|Permet aux utilisateurs d’ajouter des plug-ins dans Internet Explorer.|Oui|N°|
|**Autoriser les scripts actifs**|Permet à l’Explorateur exécuter des scripts, tels que les scripts Active X.|Oui|N°|
|**Autoriser l’avertissement de fraude**|Active ou désactive les avertissements pour les sites Web frauduleux potentiels.|Oui|N°|
|**Autoriser site intranet pour la saisie de mot unique**|Permet d’utilise d’un seul mot pour diriger Internet Explorer vers un site web, tels que Bing.|Oui|N°|
|**Autoriser la détection automatique du réseau intranet**|Vous aide à configurer la sécurité pour les sites intranet dans Internet Explorer.|Oui|N°|
|**Niveau de sécurité pour Internet**|Définit le niveau de sécurité Internet Explorer pour les sites Internet.|Oui|N°|
|**Niveau de sécurité pour un intranet.**|Définit le niveau de sécurité Internet Explorer pour les sites intranet.|Oui|N°|
|**Niveau de sécurité pour les sites de confiance**|Configure le niveau de sécurité pour la zone sites de confiance.|Oui|N°|
|**Niveau de sécurité pour les sites sensibles**|Configure le niveau de sécurité pour la zone sites sensibles.|Oui|N°|
|**Envoyer l’en-tête de suivi de faire pas**|Envoie un en-tête de piste pas à des sites visités dans Internet Explorer.|Oui|N°|
|**Autoriser l’accès au menu Mode entreprise**|Permet aux utilisateurs d’accéder aux options de menu Mode entreprise à partir d’Internet Explorer.<br>Si vous sélectionnez ce paramètre, vous pouvez également spécifier un **emplacement de rapport des journaux**, qui contient une URL vers un état qui affiche les sites Web pour lequel les utilisateurs ont activé l’accès en Mode entreprise.|Oui|N°|
|**Emplacement du Mode entreprise site liste**|Spécifie l’emplacement de la liste des sites Web qui utiliseront le Mode entreprise lorsqu’elle est active.|Oui|N°|

## Paramètres du périphérique fonctionnalités - cellulaires

|Nom du paramètre|Plus d’informations|Windows 8.1 et Windows RT 8.1|Windows RT|
|----------------|----|------------------------------|--------------|
|**Autoriser l’itinérance de données**|Permet aux données d’itinérance lorsque l’appareil est dans un réseau cellulaire.|Oui|N°|



### Voir aussi
[Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
