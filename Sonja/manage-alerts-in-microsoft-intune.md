---
title: "Gérer les alertes | Microsoft Intune"
description: "L’espace de travail alertes Intune permet d’évaluer l’intégrité globale des périphériques de votre organisation."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 74dc4ce4-21da-4f40-a07f-3eea34561eee
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: pbala
ms.suite: ems
ms.openlocfilehash: 9578d58be2101a2013d5f687800245d5a8b53e01
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Gérer les alertes dans Microsoft Intune
Utilisez l’espace de travail **alertes** dans la console d’administration Intune à évaluer l’intégrité globale des périphériques de votre organisation et d’identifier les problèmes.

## Afficher les alertes actives

Consultez des informations générales et des données de synthèse à propos des alertes actives.

#### Pour afficher les alertes actives

Dans la console d’administration Intune, effectuez l’une de ces série d’étapes :

-  **Pour afficher des informations générales sur les alertes**, notamment les alertes de trois principaux et le nombre total d’alertes actives, cliquez sur **Vue d’ensemble du système**. Sélectionnez les liens dans ces alertes pour afficher des informations plus détaillées.

-  **Pour afficher les données récapitulatives pour les alertes**, sélectionnez **alertes** > **vue d’ensemble**. Dans la page **Vue d’ensemble des alertes** , vous pouvez consulter un résumé des alertes dans la zone **Type Alert résumé** . Alertes critiques apparaissent en premier. Sélectionnez les liens dans ces alertes pour afficher des informations plus détaillées.

        > [!NOTE]
        > In some cases, an alert type might appear more than once in the **Alerts Type Summary** list.
        >
        > For example, two instances of the Logical Free Disk Space alert type might be listed:
        >
        > -   3 Logical Free Disk Space
        > -   2 Logical Free Disk Space
        >
        > This occurs when the same alert type is generated for different devices that run different operating systems. In the example, the 3 Logical Free Disk Space alert type might have been generated by a computer that runs Windows 7. The 2 Logical Free Disk Space alert type might have been generated by a computer that runs Windows Vista.

-   **Pour afficher toutes les alertes actives**, choisissez **alertes** > **Toutes les alertes**. Dans la page **alertes** , vous pouvez afficher la liste de toutes les alertes actives. La page comporte ces colonnes :

    -   **Nom**. Il s’agit du nom du type alert ayant généré l’alerte.

    -   **Source**. Cette colonne comporte un lien vers la source de l’alerte. Si le seuil d’affichage du type d’alerte est défini sur **Afficher tout**, ce lien affiche un seul périphérique. Si le seuil d’affichage du type d’alerte est défini sur une valeur, le lien affiche une liste de chaque périphérique est affecté par cette alerte.

    -   **Dernière mise à jour**. Cela indique l’heure de dernière modification de l’alerte. Si une alerte est fermée, l’heure de fermeture de l’alerte s’affiche.

    -   **Gravité**. Cette colonne indique la gravité de l’alerte.

## Afficher les alertes de panneau d’affichage
Panneau d’affichage Alertes fournissent importantes annonces de service. Ils peuvent fournissent des informations sur une mise à niveau de service à venir ou planification de la maintenance ou l’état d’une coupure.

#### Pour afficher et gérer les alertes de panneau d’affichage

1.  Dans la console d’administration Intune, sélectionnez **Vue d’ensemble du système**.

2.  S’il existe importantes annonces de service, qu’ils apparaissent dans la zone de **notification de carte** .

3.  Si vous souhaitez exporter une alerte de panneau d’affichage à une valeur séparées par des virgules (CSV) ou un fichier HTML, dans la console d’administration Intune, sélectionnez **alertes** > **Toutes les alertes** >    **notifications**. Sélectionnez une notification, sélectionnez l’icône **Exporter la liste** , puis suivez les instructions affichées.

## Passez en revue l’état du système Intune
Dans l’espace de travail **Vue d’ensemble du système** , vous pouvez afficher **L’état du système** résumés des catégories de Endpoint Protection, mises à jour, l’intégrité des agents, stratégie et logiciels pour vous aider à identifier et hiérarchiser les problèmes nécessitant une attention immédiate. Messages d’erreur qui sont générés lorsque le système est interrompu lien vers le résumé de **l’État du Service** . **État du Service** résumé affiche des détails sur le problème à chaque emplacement et la dernière fois que l’état résumé a été mis à jour.

#### Pour afficher l’état de votre abonnement

1.  Dans la console d’administration Intune, sélectionnez **Vue d’ensemble du système**.

2.  Explorer la zone **d’État système** pour l’état des différents composants Microsoft Intune.

  La plupart des éléments sont liées afin que vous pouvez afficher des informations supplémentaires. Par exemple, sous **Endpoint Protection**, si vous choisissez le nombre d’instances, vous pouvez voir l’espace de travail **Endpoint Protection** , avec une liste des logiciels malveillants qui a été détecté. Si vous choisissez le nombre d’unités, vous pouvez voir l’espace de travail **groupes** , avec une liste des appareils sur lesquels les logiciels malveillants a été trouvée.

## Fermer et réactiver les alertes
Alertes Intune restent actifs jusqu'à ce qu’un des événements suivants se produit :

-   Le problème qui a provoqué l’alerte à générer est résolu.

-   L’alerte est fermé manuellement.

-   Cinq jours transmettre après que l’alerte a été généré. Après 45 jours, l’alerte arrive à expiration et se ferme automatiquement.

Alertes sont marqué comme fermé sont définitivement supprimés après 90 jours.

#### Pour fermer manuellement une alerte

Dans la console d’administration Intune, effectuez l’une de ces série d’étapes :

- **Pour fermer une alerte à partir de la liste des alertes**, sélectionnez **alertes** > **Toutes les alertes**. Sélectionnez une alerte, puis **Fermer alerte**.

- **Pour fermer une alerte pour un périphérique spécifique**, cliquez sur **groupes** > **Tous les périphériques**. Sélectionnez un appareil, puis **Afficher les propriétés**. Puis, sous l’onglet **alertes** , sélectionnez une alerte, puis **Fermer alerte**.

- **Pour fermer une alerte de panneau d’affichage**, cliquez sur **Vue d’ensemble du système**. Cliquez sur le **X** en regard de l’alerte de panneau d’affichage.

#### Pour afficher et réactiver alertes fermés

1.  Dans la console d’administration Intune, sélectionnez **alertes** > **Toutes les alertes**.

2.  Dans la liste de **filtres** , sélectionnez **fermé**.

    Vous pouvez voir les noms et les alertes dans le volet Liste de gestion des informations supplémentaires. Afficher des détails sur l’alerte sélectionnée dans le volet de visualisation.

3.  Pour réactiver l’alerte sélectionnée, choisissez **Réactiver une alerte**.

### Voir aussi
[Être informé par Microsoft Intune alertes](../deploy-use/get-notified-by-alerts.md)