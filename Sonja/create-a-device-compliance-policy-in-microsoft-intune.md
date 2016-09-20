---
title: "Créer une stratégie de conformité appareil | Microsoft Intune"
description: "Créer une stratégie de conformité pour aider les appareils mobiles sécurisés et PC permettant d’accéder aux données de votre société."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5336dac0-a2cc-4cd4-8511-67e4f95bd700
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 2ff0b24d0a6991c22b23da5da5c63a9bb26ccdd2
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Créer une stratégie de conformité appareil dans Microsoft Intune
Cette rubrique décrit les étapes que vous pouvez utiliser pour créer une stratégie de conformité un appareil doit suivre afin d’être considéré comme compatible.

##  Étape 1 : Ajouter une nouvelle stratégie
  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **stratégie** &gt; **Des stratégies de conformité** &gt; **Ajouter**.

  ![Capture d’écran de la page de stratégie de conformité dans la console d’administration Intune, montrant l’option Ajouter dans le menu en haut de la page](./media/intune-sa-3a-add-compliance-policy.png)

##  Étape 2 : Configurer les paramètres
Dans la page **Créer une stratégie** , activez les paramètres que vous avez besoin :
  -   Les paramètres de sécurité système tels que le mot de passe et de chiffrement
  -   Paramètres d’intégrité du périphérique, tels qu’ou non un appareil est jailbroken ou est signalé par le service Windows appareil santé attestation correct.
  -   Paramètres de propriété de périphérique, tels que la version du système d’exploitation minimale requise ou une version du système d’exploitation maximale autorisée.
![Onglet Général de la page Créer une stratégie ](./media/intune-sa-3b-create-policy.png)


##  Étape 3 : Enregistrer la stratégie
Lorsque vous avez terminé, cliquez sur **Enregistrer la stratégie**.

Vous aurez la possibilité de déployer la stratégie juste après l’enregistrement de la stratégie, ou vous pouvez choisir de déployer ultérieurement. La nouvelle stratégie s’affiche dans le nœud de **Stratégies de conformité** de l’espace de travail de **stratégie** .

##  Étape 4 : Définir la période de validité de l’état de conformité
Pour spécifier l’heure de que l’appareil a à archiver avant un appareil est considéré comme non compatible, accédez aux paramètres de stratégie de conformité et mettre à jour l’heure.  La valeur par défaut est défini sur 30 jours.

![option de paramètres de stratégie de conformité dans la barre de menus de stratégie](../media/mdm-compliance-policy-settings.png)

![boîte de dialogue de stratégie de conformité](../media/mdm-ca-compliance-status-validity-period.png)

## Paramètres de stratégie pris en charge
Le tableau suivant répertorie les paramètres de stratégie de conformité et les plateformes sur lequel ils sont pris en charge.

-------------
|Paramètre|iOS|Android|Windows|
|-----|----|-----|-----|
|Demander un mot de passe pour la déverrouiller les appareils mobiles|iOS 6 et versions ultérieures|Android 4.0 ou version ultérieure <br>Samsung KNOX Standard 4.0 et versions ultérieur|Windows Phone 8 et versions ultérieur|
|Autoriser les mots de passe simples|iOS 6 et versions ultérieures|Non pris en charge|Windows Phone 8 et versions ultérieur|
|Longueur minimale|iOS 6 et versions ultérieures| Android 4.0 ou version ultérieure<br>Samsung KNOX Standard 4.0 et versions ultérieur| Windows Phone 8 et versions ultérieur<br>Windows 8.1|
|Obligatoires type de mot de passe|iOS 6 et versions ultérieures|Non disponible|Windows Phone 8 et versions ultérieur <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|Nombre minimal de jeux de caractères|iOS 6 et versions ultérieures|Non disponible|Windows Phone 8 et versions ultérieur <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|Qualité de mot de passe|Non disponible|Android 4.0 ou version ultérieure <br>Samsung KNOX Standard 4.0 et versions ultérieur|Non disponible|
|Minutes d’inactivité avant de mot de passe est nécessaire|iOS 6 et versions ultérieures|Android 4.0 ou version ultérieure<br>Samsung KNOX Standard 4.0 et versions ultérieur|Windows Phone 8 et versions ultérieur<br>Windows RT et Windows RT 8.1<br>Windows 8.1|
|Expiration du mot de passe (jours)|iOS 6 et versions ultérieures|Android 4.0 ou version ultérieure<br>Samsung KNOX Standard 4.0 et versions ultérieur|Windows Phone 8 et versions ultérieur<br>Windows RT et Windows RT 8.1<br>Windows 8.1|
|N’oubliez pas de l’historique de mot de passe|iOS 6 et versions ultérieures|Android 4.0 ou version ultérieure<br>Samsung KNOX Standard 4.0 et versions ultérieur|Windows Phone 8 et versions ultérieur<br>Windows RT et Windows RT 8.1<br>Windows 8.1|
|Éviter la réutilisation des mots de passe précédents|iOS 6 et versions ultérieures|Android 4.0 ou version ultérieure<br>Samsung KNOX Standard 4.0 et versions ultérieur|Windows Phone 8 et versions ultérieur<br>Windows RT et Windows RT 8.1<br>Windows 8.1|
|Demander un mot de passe lorsque l’appareil est retournée à partir d’un état d’inactivité| Non disponible| Non disponible|Windows 10 Mobile|
|Exiger le chiffrement sur appareil mobile|Non applicable|Android 4.0 ou version ultérieure<br>Samsung KNOX Standard 4.0 et versions ultérieur|Windows Phone 8 et versions ultérieur<br> Windows 8.1|
|Besoin de périphériques pour être signalé comme exact| Non disponible| Non disponible|Windows <br>Windows 10 Mobile|
|Appareil ne doit pas être jailbroken ou associés à une racine|iOS 6 et versions ultérieures|Android 4.0 ou version ultérieure<br>Samsung KNOX Standard 4.0 et versions ultérieur|Non disponible|
|Compte de messagerie doit être géré par Intune|iOS 6 et versions ultérieures|Non disponible| Non disponible|
|Sélectionnez le profil de messagerie qui doit être géré par Intune|iOS 6 et versions ultérieures|Non disponible| Non disponible|
|Système d’exploitation au minimum|iOS 6 et versions ultérieures|Android 4.0 ou version ultérieure<br>Samsung KNOX Standard 4.0 et versions ultérieur| Windows Phone 8 et versions ultérieur<br>Windows 8.1|
|Version du système d’exploitation maximale autorisée|iOS 6 et versions ultérieures|Android 4.0 ou version ultérieure<br>Samsung KNOX Standard 4.0 et versions ultérieur|Windows Phone 8 et versions ultérieur<br>Windows 8.1|

Sélectionnez une des opérations suivantes pour en savoir plus sur les paramètres de conformité prises en charge sur chaque plate-forme :
> [!div class="op_single_selector"]
- [Paramètres de stratégie de conformité pour les appareils iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Paramètres de stratégie de conformité pour les appareils Android](android-compliance-policy-settings-in-microsoft-intune.md)
- [Paramètres de stratégie de conformité pour Windows et les téléphones Windows ](windows-compliance-policy-settings-in-microsoft-intune.md)


## Étapes suivantes
[Déployer et surveiller une stratégie de conformité](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### Voir aussi
[Introduction aux stratégies de conformité appareil](introduction-to-device-compliance-policies-in-microsoft-intune.md)
