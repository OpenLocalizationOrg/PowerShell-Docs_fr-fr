---
title: Retirer appareils | Microsoft Intune
description: "Intune prend en charge une réinitialisation sélective et une réinitialisation complète afin de supprimer le périphérique de la gestion des Intune en supprimant sa stratégie et le portail d’entreprise."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 93c8c07632c067fdb2eef221bc149fa7f6e9d495
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Retirer les périphériques de gestion Intune

Si les périphériques sont appartenant à l’entreprise ou personnel, il arrive un moment lorsqu’un périphérique géré doit être supprimé de la gestion des Intune. Un périphérique devrez peut-être déclassé pour diverses raisons :

-   Utilisateur quitte une entreprise de façon planifiée (« gérées » au départ)
-   Utilisateur quitte brusquement (se déclenche, se ferme, etc..).
-   Perte de l’appareil
-   Réutilisation d’un périphérique (déplacer vers un autre utilisateur, réutilisation pour un objectif différent, etc.).

Vous pouvez effectuer une réinitialisation sélective et ou complet à distance sur les appareils gérées comme les appareils mobiles ou verrouiller un appareil et son mot de passe. Par effacement de l’appareil vous libérez de l’abonnement de l’utilisateur pour ajouter un autre appareil. Vous pouvez également annulez PC gérés avec le logiciel client Intune.

## Effacer les données et applications à partir d’appareils
Une réinitialisation sélective et une réinitialisation complète supprimez le périphérique de la gestion des Intune en supprimant sa stratégie et le portail d’entreprise, ce qui signifie que l’appareil n’a plus les informations d’identification nécessaires pour vous connecter à des ressources de l’entreprise tels que Microsoft SharePoint, messagerie ou Office 365.

[Réinitialisation sélective](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) est l’action par défaut pour les employés qui ont inscrits leurs propres périphériques dans Intune car il n’affecte pas les informations personnelles sur l’appareil. Uniquement les données d’entreprise sont supprimées.

Pour les périphériques qui doivent pouvoir le réutiliser, que vous pouvez également utiliser une [réinitialisation complète](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe), qui réinitialise le périphérique paramètres par défaut.

## Pour supprimer des appareils dans le portail Azure Active Directory

1.  Informations d’identification de connexion avec votre organisation pour [http://aka.ms/accessaad](http://aka.ms/accessaad) ou [https://portal.office.com](https://portal.office.com) , puis sélectionnez **administrateur centres** &gt; **Azure AD**.

2.  Créer un abonnement Azure si vous n’en avez pas. Cela ne doit pas prendre une carte de crédit ou un paiement si vous possédez un compte payant (cliquez sur le lien d’abonnement **inscrire votre gratuit Azure Active Directory** ).

4.  Sélectionnez **Active Directory** , puis sélectionnez votre organisation.

5.  Sélectionnez l’onglet **utilisateurs** .

6.  Sélectionnez l’utilisateur dont vous voulez supprimer les périphériques.

7.  Sélectionnez des **périphériques**.

8.  Sélectionnez les périphériques le cas échéant, puis cliquez sur **Supprimer appareil**. Le périphérique est supprimé la prochaine fois qu’il est synchronisé avec Active Directory. Cela se produit généralement dans les 4 heures. Après la synchronisation, le périphérique est supprimé de la gestion. Cela supprime un périphérique de la limite du périphérique pour cet utilisateur.

## Supprimer des ordinateurs gérés
Ordinateurs gérés avec Intune logiciel client peut être supprimé de la gestion de la console d’administration Intune. Cette également désinstallation du logiciel client et supprime Intune stratégie de l’ordinateur. Plus d’informations sur la [suppression des ordinateurs gérés par le logiciel client Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#retire-a-computer.md).

## Bloquer l’accès un périphérique
Dans le cas d’un périphérique perdu ou lorsque vous devez la supprimer un appareil, car un employé quitte votre entreprise sans retour un matériel appartenant à l’entreprise, vous pouvez également [code secret réinitialiser et à distance verrouiller](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) l’appareil. Cela conserve informations société est incorrecte, bien que vous devrez peut-être écrire sur l’unité comme une perte.

Vous souhaitez également retirer la licence de compte d’utilisateur de l’employé Intune. Cela permet de libérer la licence et vous pouvez l’affecter à un nouveau compte d’utilisateur.

## Supprimer le matériel
Parfois, il est le périphérique lui-même qui a atteint sa fin de vie. Dans ce cas, [Rétablir paramètres par défaut](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) avec une réinitialisation complète supprime toutes les données et supprime le périphérique de Intune. Vous pouvez ensuite supprimer du matériel en fonction de la stratégie de votre entreprise.

### Voir aussi
[Protéger vos données avec réinitialisation sélective ou complète](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)
