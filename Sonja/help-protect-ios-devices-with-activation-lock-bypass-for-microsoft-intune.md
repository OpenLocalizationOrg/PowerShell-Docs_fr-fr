---
title: "Gérer les iOS verrouiller l’Activation sur les appareils | Microsoft Intune"
description: "Microsoft Intune peut vous aider à gérer iOS verrouiller l’Activation, une fonctionnalité de la recherche mon application iPhone pour iOS 7.1 et des générations ultérieures."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984
ms.reviewer: joglocke
ms.suite: ems
ms.openlocfilehash: 5cc03b724f8b9b00feb6bf693bd9b420c02e4ed3
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Protéger iOS appareils avec verrouiller l’Activation par téléphone évitent pour Intune Microsoft
Microsoft Intune peut vous aider à gérer iOS verrouiller l’Activation, une fonctionnalité de la recherche mon application iPhone pour iOS 8.0 et des générations ultérieures. Verrouiller l’activation est activée automatiquement lorsqu’un utilisateur ouvre la rechercher mon application iPhone sur un appareil. Une fois qu’il est activé, ID Apple et le mot de passe de l’utilisateur doivent être saisies avant tout le monde peut : 

-   Désactiver rechercher mon iPhone.

-   Effacer l’appareil

-   Réactiver le périphérique

## Verrouiller l’Activation incidence vous
Verrouiller l’Activation permet des appareils iOS sécurisé et améliore les chances de récupération d’un appareil de perte ou de vol, cette fonctionnalité peut présenter vous, en tant qu’administrateur informatique, avec un certain nombre de défis. Par exemple :

-   Un utilisateur définit l’Activation verrou sur un appareil. L’utilisateur quitte l’entreprise, puis renvoie le périphérique. Sans ID Apple et mot de passe de l’utilisateur, il n’existe aucun moyen pour réactiver le périphérique.

-   Vous avez besoin d’un rapport de tous les périphériques dotées de verrouiller l’Activation activé.

-   Vous voulez réaffecter certains appareils vers un autre département au cours d’une actualisation du périphérique de votre organisation. Vous ne pouvez réaffecter appareils qui n’ont pas de verrouiller l’Activation activé.

Pour aider à résoudre ces problèmes, Apple introduite dérivation verrouiller l’Activation dans iOS 7.1. Cela vous permet de supprimer le verrou Activation à partir d’appareils contrôlés sans ID Apple et le mot de passe de l’utilisateur. Appareils contrôlés peuvent générer un code de contournement de verrouiller l’Activation spécifiques à l’appareil, qui est stocké sur le serveur d’activation d’Apple.

> [!TIP]
> Mode contrôlé pour les appareils iOS vous permet d’utiliser le programme de configuration Apple pour verrouiller une fonctionnalité de limite et l’appareil à des fins spécifiques de l’entreprise. Le mode contrôlé est généralement uniquement pour les périphériques appartenant à l’entreprise.

## Comment Intune vous permet de gérer l’Activation de verrouillage
Intune pouvez demander le statut de verrouillage de l’Activation des périphériques contrôlés et qui fonctionne sans surveillance qui s’exécutent iOS 8.0 et versions ultérieures. Pour les périphériques contrôlés uniquement, Intune peut récupérer le code de contournement verrouiller l’Activation et le soumettre directement à l’appareil. Si l’appareil a été sélective, vous pouvez accéder directement à l’appareil en utilisant le code en tant que le nom d’utilisateur et un mot de passe vide.

**Les avantages de ce sont**:

-   L’utilisateur reçoit les avantages de sécurité de la recherche mon application iPhone.

-   Vous pouvez activer aux utilisateurs de faire leur travail et sauront pas que lorsqu’un appareil doit pouvoir le réutiliser, vous pouvez supprimer ou déverrouiller.

## Comment utiliser dérivation verrouiller l’Activation de la console d’administration Intune
> [!IMPORTANT]
> Une fois que vous ignorez le verrou Activation sur un appareil, un nouveau verrou Activation est appliqué automatiquement si la rechercher mon application iPhone est ouvert. En raison de cette option, **que vous devez être en possession du périphérique avant de suivre cette procédure**.

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **groupes** &gt; **Tous les périphériques** &gt; **périphériques appartenant à tous les d’entreprise**.

2.  Sélectionnez le périphérique dont verrouillage Activation que vous souhaitez ignorer. Choisissez **l’Activation verrouillage dérivation**.

3.  Lisez le message d’avertissement. Cliquez sur **Oui** pour continuer.

Vous pouvez examiner l’état de la demande de déverrouillage dans la page Détails de l’appareil.

## Comment afficher les périphériques sont à l’aide de l’Activation de verrouillage
Vous pouvez voir quels sont les appareils sont à l’aide de verrouiller l’Activation de deux façons :

-   Exécutez les **rapports d’inventaire appareil Mobile**. Ce rapport affiche les colonnes **Statut de verrouillage d’Activation** et **Supervised** pour indiquer l’état d’appareils. Les valeurs de **Supervised** sont **Oui** ou **non**et les valeurs de **Statut de verrouillage d’Activation** sont :

    -   Activé avec un code de contournement

    -   Activé sans code dérivation (appareil n’est pas contrôlé)

    -   Activé sans code dérivation (appareil ne peuvent pas être atteintes)

    -   Non activé

    La zone de **Statut de verrouillage d’Activation** est vide pour les périphériques qui ne sont pas exécutées iOS 8.0 ou version ultérieure.

-   Sélectionner un périphérique dans un affichage des groupes pour afficher le statut de verrouillage de l’Activation dans le volet de détails appareil.

    Si vous sélectionnez un périphérique dans le nœud **appartenant à l’entreprise de tous les périphériques** et verrouiller l’Activation est activée pour l’appareil, vous pouvez également visualiser le code de contournement. Ce code peut être utilisé à problème manuellement un verrou Activation par téléphone évitent.

    > [!IMPORTANT]
    >Intune procède inventaire à partir d’appareils pour verrouiller l’Activation tous les sept jours. Pour cette raison, appareils peuvent immédiatement s’affiche pas avec leur statut de verrouillage de l’Activation de la console Intune.


### Voir aussi
[Retirer appareils](retire-devices-from-microsoft-intune-management.md)
[protéger vos appareils réinitialisation à distance verrouiller et le code secret](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)
