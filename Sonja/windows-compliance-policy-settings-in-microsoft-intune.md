---
title: "Paramètres de stratégie de conformité pour les appareils Windows | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f996842c-e9a4-4819-acb4-ee66e8fb35b8
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 12239464012029e3ffff3a9bed4f4ccb2cebe633
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Paramètres de stratégie de conformité pour appareils Windows dans Microsoft Intune

Les paramètres de stratégie décrites dans cette rubrique s’applique aux appareils exécutant le système d’exploitation Windows. La version de Windows spécifique pris en charge est entourée dans les sections ci-dessous.

Si vous recherchez des informations sur d’autres plateformes, sélectionnez une des opérations suivantes :
> [!div class="op_single_selector"]
- [Paramètres de stratégie de conformité pour les appareils iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Paramètres de stratégie de conformité pour les appareils Android](android-compliance-policy-settings-in-microsoft-intune.md)

## Paramètres de stratégie de conformité pour les appareils Windows Phone
Les paramètres répertoriés dans cette section sont pris en charge sur Windows Phone 8.1 et versions ultérieures.

## Paramètres de sécurité système
### Mot de passe
- **Exiger un mot de passe pour la déverrouiller les appareils mobiles :**    Définir sur **Oui** pour obliger les utilisateurs à entrer un mot de passe avant de pouvoir accéder à leur appareil.

- **Autoriser les mots de passe simples :**    Définir sur **Oui** pour permettre aux utilisateurs de créer des mots de passe simples tels que «**1234**» ou «**1111**».

-  **Longueur minimale du mot de passe :** Spécifier le nombre minimal de chiffres ou de caractères que le mot de passe doit contenir.
- **Obligatoires type de mot de passe :** Spécifier si les utilisateurs doivent créer un **alphanumérique**ou un mot de passe **numérique** .

  Pour appareils mobiles qui exécutent Windows et accessible avec un compte Microsoft, la stratégie de conformité ne pourra pas être évaluée correctement si longueur minimale est supérieure à huit caractères ou si le nombre minimal de jeux de caractères est plus de deux.

- **Nombre minimal de jeux de caractères :** Si **nécessaire type mot de passe** est défini sur **alphanumérique**, ce paramètre spécifie le nombre minimal de jeux de caractères que le mot de passe doit contenir. Quatre jeux de caractères sont :
  -   Lettres minuscules
  -   Lettres majuscules
  -   Symboles
  -   Numéros

  Configuration d’un nombre plus élevé pour ce paramètre signifie que les utilisateurs à créer des mots de passe qui sont plus complexes. Pour appareils mobiles qui exécutent Windows et accessible avec un compte Microsoft, la stratégie de conformité ne pourra pas être évaluée correctement si longueur minimale est supérieure à huit caractères ou si le nombre minimal de jeux de caractères est plus de deux.
- **Minutes d’inactivité avant de mot de passe est nécessaire :**  Spécifie la durée d’inactivité avant que l’utilisateur doit retaper son mot de passe.

- **Expiration du mot de passe (jours) :** Sélectionnez le nombre de jours avant l’expiration du mot de passe de l’utilisateur et ils doivent créer un nouvel identifiant.

- **N’oubliez pas de l’historique de mot de passe :** Utilisez ce paramètre conjointement avec **éviter la réutilisation d’anciens mots de passe** pour empêcher l’utilisateur de créer des mots de passe utilisés précédemment.

- **Éviter la réutilisation des mots de passe précédents :** Si **l’historique de mémoriser mot de passe** est sélectionnée, indiquez le nombre de mots de passe précédemment utilisés ne peut pas être réutilisée.
- **Exiger un mot de passe lorsque l’appareil est retournée à partir d’un état d’inactivité :** Ce paramètre doit être utilisé avec le paramètre de **Minutes d’inactivité avant de mot de passe est requis** . Les utilisateurs finaux êtes invités à entrer un mot de passe pour accéder à un périphérique qui a été inactif pendant la durée spécifiée dans le paramètre de **Minutes d’inactivité avant de mot de passe est requis** .

  **Ce paramètre s’applique uniquement aux appareils Windows 10 Mobile.**
### Chiffrement
- **Exiger le chiffrement sur appareil mobile :** Définir sur **Oui** pour exiger l’appareil à chiffrer afin de vous connecter à des ressources.

## Paramètres d’intégrité du périphérique
- **Besoin de périphériques pour être signalé comme exact :** Vous pouvez définir une règle pour exiger que les appareils **Windows 10 Mobile** doivent être signalés comme exact dans des stratégies de conformité nouvelle ou existante.  Si ce paramètre est activé, appareils Windows 10 sont évaluées via le Service de Attestation santé (HAS) pour les points de données suivants :
  -  **BitLocker est activé :** Lorsque BitLocker est activé, l’appareil est en mesure de protéger les données qui sont stockées sur le disque des accès non autorisés, lorsque le système est désactivé ou accède à la mise en veille prolongée. Chiffrement de lecteur BitLocker chiffre toutes les données stockées sur le volume de système d’exploitation Windows. BitLocker utilise le module pour protéger le système d’exploitation Windows et des données utilisateur et permet de se pour assurer qu’un ordinateur n'est pas falsifié, même si elle n’est pas automatisé, perdu ou vol. Si l’ordinateur est équipé d’un module de plateforme sécurisée compatible, BitLocker utilise le module pour verrouiller les clés de chiffrement qui protègent les données. Par conséquent, les touches ne sont pas accessibles du jusqu'à ce que le module a vérifié l’état de l’ordinateur
  -  **L’intégrité du code est activée :** L’intégrité du code est une fonctionnalité qui valide l’intégrité d’un fichier pilote ou système chaque fois qu’il est chargé en mémoire. L’intégrité du code détecte si un fichier système ou pilote non signé est chargé dans le noyau, ou un fichier système a été modifié par les logiciels malveillants qui sont exécuté par un compte d’utilisateur avec des privilèges d’administrateur.
  - **Démarrage sécurisé est activé :** Lorsque le démarrage sécurisé est activé, le système obligé de démarrer en un état usine approuvé. En outre, lorsque initialisation banque d’informations sécurisé est activée, les composants de base utilisées pour démarrer l’ordinateur doivent avoir des signatures de chiffrement corrects approuvés par l’organisation fabricant de l’appareil. Le microprogramme UEFI vérifie que c’est avant qu’il permet l’ordinateur de démarrer. Si tous les fichiers ont été falsifiés, annulation de sa signature, le système ne démarre pas.

  Pour plus d’informations sur le fonctionnement du service HAS, voir [Santé Attestation fournisseur](https://msdn.microsoft.com/library/dn934876.aspx).
##  Paramètres de la propriété appareil
- **Système d’exploitation minimum requis :** Lorsqu’un appareil ne répond pas à la configuration minimale requise de version minimale du système d’exploitation, il est signalé comme non conformes.
    Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final pouvez choisir de mettre à niveau leur appareil après laquelle ils peuvent accéder aux ressources de société.

- **Version du système d’exploitation maximale autorisée :** Lorsqu’un appareil utilise une version du système d’exploitation ultérieure à celle indiquée dans la règle, accès aux ressources de l’entreprise est bloqué et l’utilisateur est invité à contacter son administrateur informatique. Jusqu'à ce qu’une modification dans une règle pour autoriser la version du système d’exploitation, cet appareil ne peuvent pas être utilisé pour accéder aux ressources de l’entreprise.


## Paramètres de stratégie de conformité pour les PC Windows
Les paramètres répertoriés dans cette section sont pris en charge sur les PC Windows.
## Paramètres de sécurité système
### Mot de passe
- **Longueur minimale du mot de passe :** - pris en charge sur Windows 8.1.

  Spécifier le nombre minimal de chiffres ou de caractères que le mot de passe doit contenir.

  Pour les périphériques sont accessibles à un Account Microsoft, la stratégie de conformité ne pourra pas être évaluée correctement si **longueur minimale du mot de passe** est supérieure à 8 caractères ou si **nombre minimal de caractères définit** est plus de deux caractères.

- **Obligatoires type de mot de passe :** - pris en charge sur Windows RT, Windows RT 8.1 et Windows 8.1

  Spécifier si les utilisateurs doivent créer un **alphanumérique**ou un mot de passe **numérique** .

- **Nombre minimal de jeux de caractères :** - pris en charge sur Windows RT, Windows RT 8.1 et Windows 8.1. Si **nécessaire type mot de passe** est défini sur **alphanumérique**, ce paramètre spécifie le nombre minimal de jeux de caractères que le mot de passe doit contenir. Quatre jeux de caractères sont :
  -   Lettres minuscules
  -   Lettres majuscules
  -   Symboles
  -   Nombres : Configuration d’un nombre plus élevé pour ce paramètre signifie que les utilisateurs à créer des mots de passe qui sont plus complexes.

  Pour les périphériques sont accessibles à un Account Microsoft, la stratégie de conformité ne pourront pas évaluer correctement si **longueur minimale du mot de passe** est supérieure à 8 caractères ou si **nombre minimal de caractères définit** est plus de 2 caractères.
- **Minutes d’inactivité avant de mot de passe est nécessaire :** - pris en charge sur Windows RT, Windows RT 8.1 et Windows 8.1

  Spécifier la durée d’inactivité avant que l’utilisateur doit retaper son mot de passe.

- **Expiration du mot de passe (jours) :** -pris en charge sur Windows RT, Windows RT 8.1 et Windows 8.1.

  Sélectionnez le nombre de jours avant l’expiration du mot de passe de l’utilisateur et ils doivent créer un nouvel identifiant.

- **N’oubliez pas de l’historique de mot de passe :** - pris en charge sur Windows RT, Windows RT et Windows 8.1.

  Utilisez ce paramètre conjointement avec **éviter la réutilisation d’anciens mots de passe** pour empêcher l’utilisateur de créer des mots de passe utilisés précédemment.
- **Éviter la réutilisation des mots de passe précédents :** - pris en charge sur Windows RT, Windows RT 8.1 et Windows 8.1

  Si **n’oubliez pas de l’historique de mot de passe :** est sélectionnée, indiquez le nombre de mots de passe précédemment utilisés ne peut pas être réutilisée.

## Paramètres d’intégrité du périphérique
- **Besoin de périphériques pour être signalé comme exact :** - pris en charge sur les appareils Windows 10.
Vous pouvez définir une règle pour exiger que les appareils Windows 10 doivent être signalés comme exact dans des stratégies de conformité nouvelle ou existante.  Si ce paramètre est activé, appareils Windows 10 sont évaluées via le Service de Attestation santé (HAS) pour les points de données suivants :
  -  **BitLocker est activé :** Lorsque BitLocker est activé, l’appareil est en mesure de protéger les données qui sont stockées sur le disque des accès non autorisés, lorsque le système est désactivé ou accède à la mise en veille prolongée. Chiffrement de lecteur BitLocker chiffre toutes les données stockées sur le volume de système d’exploitation Windows. BitLocker utilise le module pour protéger le système d’exploitation Windows et des données utilisateur et permet de se pour assurer qu’un ordinateur n'est pas falsifié, même si elle n’est pas automatisé, perdu ou vol. Si l’ordinateur est équipé d’un module de plateforme sécurisée compatible, BitLocker utilise le module pour verrouiller les clés de chiffrement qui protègent les données. Par conséquent, les touches ne sont pas accessibles du jusqu'à ce que le module a vérifié l’état de l’ordinateur
  -  **L’intégrité du code est activée :** L’intégrité du code est une fonctionnalité qui valide l’intégrité d’un fichier pilote ou système chaque fois qu’il est chargé en mémoire. L’intégrité du code détecte si un fichier système ou pilote non signé est chargé dans le noyau, ou un fichier système a été modifié par les logiciels malveillants qui sont exécuté par un compte d’utilisateur avec des privilèges d’administrateur.
  - **Démarrage sécurisé est activé :** Lorsque le démarrage sécurisé est activé, le système obligé de démarrer en un état usine approuvé. En outre, lorsque initialisation banque d’informations sécurisé est activée, les composants de base utilisées pour démarrer l’ordinateur doivent avoir des signatures de chiffrement corrects approuvés par l’organisation fabricant de l’appareil. Le microprogramme UEFI vérifie que c’est avant qu’il permet l’ordinateur de démarrer. Si tous les fichiers ont été falsifiés, annulation de sa signature, le système ne démarre pas.
  - **Contre les logiciels malveillants barre de lancement rapide sont activé :** Au plus tôt lancement malveillants (ELAM) offre une protection pour les ordinateurs de votre réseau lorsqu’ils démarrent et avant de l’initialisation des pilotes tiers.

  Pour plus d’informations sur le fonctionnement du service HAS, voir [Santé Attestation fournisseur](https://msdn.microsoft.com/library/dn934876.aspx).

## Paramètres de la propriété appareil
- **Système d’exploitation minimum requis :** - pris en charge sur Windows 8.1 et Windows 10.

  Spécifier le nombre de version.inter.Build ici. Le numéro de version doit correspondre à la version renvoyée par la commande winver.

  Lorsqu’un appareil doté d’une version antérieure que la version du système d’exploitation spécifiée, elle est signalée comme non conformes. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final pouvez choisir de mettre à niveau leur appareil après laquelle ils peuvent accéder aux ressources de société.

- **Version du système d’exploitation maximale autorisée :** - pris en charge sur Windows 8.1 et Windows 10.

  Lorsqu’un appareil utilise une version du système d’exploitation ultérieure à celle indiquée dans la règle, accès aux ressources de l’entreprise est bloqué et l’utilisateur est invité à contacter son administrateur informatique. Jusqu'à ce qu’une modification dans une règle pour autoriser la version du système d’exploitation, cet appareil ne peuvent pas être utilisé pour accéder aux ressources de l’entreprise.

Pour trouver la version du système d’exploitation à utiliser pour le **système d’exploitation Minimum requis**et les paramètres de **version du système d’exploitation maximale autorisée** , exécutez la commande **winver** à partir de l’invite de commandes. La commande winver renvoie la version du système d’exploitation signalée.
- Windows 8.1 PC retournent une version du **6.3**.    Si la règle de la version du système d’exploitation est définie sur Windows 8.1 pour Windows, l’appareil est signalé comme non conformes même si le périphérique a Windows 8.1.
- PC qui exécutent Windows 10, la version doit être définie comme « 10.0 » + le numéro de version du système d’exploitation renvoyées par la commande winver. Par exemple, cela peut s’intitule 10.0.10586.
> ![CA_Win10OSVersion](./media/ca_win10-os-version.png)
