---
title: Notes de publication pour Microsoft Intune | Microsoft Intune
description: Notes de publication Intune
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: 98b838c3bcb5401dc070da9bb37780c1365109c1
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Notes de publication pour Microsoft Intune
Microsoft Intune est une solution de gestion de client intégrée, sur le nuage qui fournit des outils, des rapports et des licences mise à niveau vers la dernière version de Windows, et vous aide à conserver vos ordinateurs à jour et sécurisé. En outre, Intune vous permet de gérer les appareils mobiles sur le réseau via Exchange ActiveSync ou directement via Intune. Les notes suivantes décrivent les informations importantes et les problèmes connus dans Microsoft Intune.


## Utilisateurs Android ne peut pas envoyer des messages électroniques en cas d’implémentation d’accès conditionnel pour Exchange Online

Les utilisateurs exécutant Samsung Android 5.1.1 et ci-dessus sur leurs appareils ne parvenez pas à envoyer des messages électroniques lorsque accès conditionnel pour Exchange Online a été configurée. Samsung reconnaît que le problème se trouve dans un client de messagerie intégrée dans 5.1.1 Android et versions ultérieures et cherche actuellement un correctif.

**Solution de contournement 1 :** Informez les utilisateurs finaux pour utiliser l’application Outlook pour Android.

**Solution de contournement 2 :** Pour activer les utilisateurs affectés à envoyer des messages électroniques, vous pouvez suivre ces étapes :

1. Placer l’utilisateur concerné dans un groupe de sécurité dans la section « exemptés groupes » de la stratégie d’accès conditionnel pour Exchange Online.
2. Autoriser l’utilisateur à synchroniser temporairement messagerie électronique sur le client de messagerie intégrée.
3. Supprimer l’utilisateur concerné du groupe exempté et confirmez que cet utilisateur peut désormais envoyer des messages.

Microsoft va continuer à travailler en étroite collaboration avec Samsung sur un correctif ou des solutions de contournement.



## Modification d’un profil d’accès aux ressources entre les groupes pour iOS et Android peut échouer
**Problème :** Lorsque vous modifiez le message électronique ou profils d’accès ressource protocole SCEP (Simple Certificate d’inscription Protocol) entre les groupes, les profils peuvent entrer en conflit et échouer. Par exemple, supposons que vous avez un existant profil en pointant sur le serveur Exchange locales, destiné à un groupe, de messagerie et puis vous créez un nouveau profil de messagerie qui pointe vers Exchange online, destinée au groupe B. Lorsque vous déplacez les utilisateurs d’un groupe vers le groupe B, appareils conserve le profil de messagerie Exchange sur site et essayez d’installer le profil de messagerie en ligne Exchange qui est destiné au groupe B.

À ce stade, une des opérations suivantes se produit : 
* Si les profils de messagerie A et B sont identiques, le périphérique refuse profil de messagerie B, car le profil de messagerie B contient déjà messagerie profil A.
* Si le profil de messagerie A est différent de profil de messagerie B, comme indiqué dans l’exemple ci-dessus, le périphérique finit avec deux profils de messagerie.

**Remarque :** Le nom d’hôte et l’attribut utilisé pour le nom d’utilisateur sont vérifiées pour distinguer un profil de messagerie d’un autre.

Dans les deux cas, le profil d’accès ressource (profil de messagerie) n'a pas été supprimé de l’appareil afin d’empêcher la suppression accidentelle d’accès d’un utilisateur vers un e-mail ou SCEP du certificat client.

**Solution de contournement :** Aucun.

## Lorsque vous inscrivez un appareil Windows 8.1 qui doit s’authentifier à un serveur proxy, le processus d’inscription échoue et aucune indication visible sur la cause du problème
**Problème :** Lorsque vous inscrivez un appareil Windows 8.1 et le périphérique doit s’authentifier à un serveur proxy au cours du processus d’inscription, l’inscription échoue si l’appareil n’a pas mis en cache les informations d’identification du serveur proxy. Lorsque les informations d’identification pour le serveur proxy ne sont pas mises en cache sur le périphérique, le processus d’inscription doit attendre pour l’utilisateur à entrer les informations d’identification. Toutefois, l’invite à fournir des informations d’identification server le proxy n’affiche pas pendant le processus d’inscription. Le résultat est que le processus d’inscription ne peut pas s’authentifier sur le serveur proxy et il n’existe aucune indication visible de l’erreur présentée à l’utilisateur.

**Solution de contournement :** Pour les appareils Windows 8.1 qui doit s’inscrire à un réseau qui nécessite l’utilisation d’un serveur proxy authentifié, configurer et enregistrer les informations d’identification pour le serveur proxy avant d’inscription de l’appareil. Pour configurer et enregistrer les informations d’identification sur un appareil Windows 8.1 :

1.  Sur l’appareil Windows 8.1, ouvrez **Internet Explorer**.

2.  Lorsque vous y êtes invité pour les informations d’identification du serveur proxy, entrez les informations d’identification, puis sélectionnez l’option **Mémoriser mes informations d’identification**.

3.  Inscrire l’appareil.

## Appareils Windows Phone 8.1 échouent s’inscrire à Microsoft Intune lorsque l’authentification appareil est activée dans AD FS
**Problème :** Lorsque vous inscrivez un appareil Windows Phone 8.1, l’inscription échoue si le paramètre facultatif pour l’authentification de l’appareil est activé dans le cadre de la stratégie d’authentification global dans les Services fédérés Active Directory (AD FS).

**Solution de contournement :** Désactiver l’authentification appareil sur le serveur AD FS en désactivant **Activer l’authentification appareil** dans **Modifier la stratégie d’authentification Global**. Pour plus d’informations, voir [Configuration des stratégies d’authentification](http://technet.microsoft.com/library/dn486781.aspx)


## Microsoft Intune application habillage outil pour Android intègre aucune capacité de désinstallation
**Problème :** L' **Outil d’habillage application Microsoft pour Android** n’a pas de fonctionnalité intégrée pour la désinstallation de l’outil.

**Solution de contournement :** Accédez à l’emplacement où vous avez installé l’outil, puis supprimez le répertoire. L’emplacement d’installation par défaut est : **C:\Program Files (x86) \Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**. Pour plus d’informations sur l’outil de retour à la ligne de l’application, voir [applications Android préparer pour la gestion avec application habillage outil](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool).

## Assistance à distance n’est pas disponible sur les ordinateurs qui exécutent Windows 8 ou Windows 8.1
**Problème :** Dans cette version, la fonctionnalité de l’assistance à distance n’est pas disponible sur les ordinateurs qui exécutent Windows 8 ou Windows 8.1.

**Solution de contournement :** Aucun.

## Notifications d’alerte pour les destinataires qui sont automatiquement ajoutés peuvent ne pas fonctionnent
**Problème :** Si un destinataire est ajouté automatiquement à un message d’alerte, ils peuvent recevoir pas toujours une notification.

**Solution de contournement :** Pour vous assurer que les destinataires recevront la notification de message, vous devez ajouter manuellement des destinataires au notifications d’alerte.

## Langue prise en charge dans le portail preview Azure
Le portail preview Azure repose sur une nouvelle plateforme et prend en charge les langues suivantes : chinois (simplifié), chinois (traditionnel), tchèque, néerlandais, anglais, allemand, hongrois, italien, japonais, portugais (Brésil), portugais (Portugal), russe, espagnol, anglais, Français, coréen, polonais, suédois, turc.

La Console d’administration Intune et l’utilisateur final facing expériences mobiles prennent en charge danois, grec, fin, norvégien et roumain, en plus de toutes les langues prises en charge par le portail Azure preview.
