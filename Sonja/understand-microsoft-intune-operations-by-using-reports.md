---
title: "Comprendre les opérations à l’aide de rapports | Microsoft Intune"
description: "Créer et gérer des rapports sur les logiciels, matériel et licences de votre organisation."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 06/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 857309c2-61c9-4c22-becf-4839fedeaece
ms.reviewer: pbala
ms.suite: ems
ms.openlocfilehash: c9df7eddbae77e64cc3b0fdf9ddc158ed2ed2860
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Comprendre les opérations Microsoft Intune à l’aide de rapports
Utilisez les informations dans cette rubrique pour vous aider à créer et gérer des rapports Microsoft Intune qui fournissent des informations sur le logiciel, le matériel et licences de votre organisation.

## Utilisation de rapports
Rapports Intune fournissent des informations sur les logiciels, matériel et licences de votre organisation. Rapports peuvent vous aider à confirmer les besoins actuels et d’anticiper les dépenses futures. L’espace de travail **rapports** vous offre les outils pour créer et gérer les rapports. 

### Types de rapports

|Type de rapport|Description|
|---------------|---------------|
|**Rapports de mise à jour**|Afficher les mises à jour a réussi sur les ordinateurs de votre organisation. Ils affichent également les mises à jour qui a échoué, qui sont en attente ou sont nécessaires. Pour plus d’informations sur les mises à jour logicielles, voir [Conserver PC Windows à jour avec les mises à jour logicielles dans Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).|
|**Rapports de logiciels détectés**|Afficher les logiciels installés sur les ordinateurs de votre organisation. Versions de logiciel sont incluses. Vous pouvez filtrer les informations qui s’affiche en fonction de l’éditeur de logiciels et la catégorie de logiciel. Vous pouvez développer les mises à jour dans la liste pour afficher plus en détail (par exemple, les ordinateurs sur lesquels est installé une mise à jour) en choisissant la flèche en regard de l’élément de liste.<br /><br />Lorsque vous retirer ordinateurs ou modifiez leur appartenance aux groupes dans Intune, il peut prendre plusieurs minutes pour que ces modifications reflétées dans le rapport de logiciels détectés. Pour les données d’inventaire logiciel plus précises, patientez quelques minutes après la suppression des ordinateurs ou en modifiant leurs appartenances avant d’exécuter un rapport de logiciels détectés qui inclut ces ordinateurs.|
|**Rapports des stocks ordinateur**|Afficher des informations sur les ordinateurs gérés dans votre organisation. Utilisez ce rapport pour planifier des achats de matériel et pour en savoir plus sur les besoins de matériel d’utilisateurs de votre organisation. Pour plus d’informations sur l’utilisation des ordinateurs gérés, voir [Gérer les PC Windows avec Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md).|
|**Rapports des stocks appareil mobile**|Afficher des informations sur les appareils mobiles dans votre organisation. Vous pouvez filtrer les informations qui s’affiche en fonction des groupes, si le périphérique est un jailbroken ou un périphérique racine et par système d’exploitation.|
|**Rapports d’acheter des licences**|Afficher les titres pour tous les logiciels sous licence dans des groupes de licences sélectionné, en fonction de leurs contrats de licence. Si les informations de licence logiciel n’a pas actualisé dans plus de 24 heures, elle actualisera lorsque vous générez un rapport de licence. Un rapport de licence n’est pas un calcul exact de logiciels en cours d’utilisation ou preuve de conformité avec les contrats. Le rapport est un outil pour vous aider à prendre des décisions de gestion des licences pour votre organisation. Intune peut ne pas détecte certains produits qui sont en mesure de disposer d’une licence en volume Microsoft. Les filtres disponibles sont :<br /><br />**Tous les accords** affiche tous les produits sous licence logicielle qui sont gérés par Intune.<br /><br />**Contrats de licence en volume** affiche uniquement les produits logiciels en Volume Service centre de gestion des licences.<br /><br />**Autres contrats de licence logiciel** affiche logiciels gérés en dehors de la gestion des.|
|**Rapports d’Installation des licences**|Comparer les logiciels installés sur les ordinateurs de votre organisation avec votre couverture du contrat de licence en cours, en fonction de la gestion des. Les filtres incluent :<br /><br />**Tous les accords** affiche tous les produits sous licence logicielle qui sont gérés par Intune.<br /><br />**Contrats de licence en volume** affiche uniquement les produits de gestion des logiciels.<br /><br />**Autres contrats de licence logiciel** affiche logiciels gérés en dehors de la gestion des.|
|**Termes et Conditions des rapports**|Afficher si les utilisateurs accepté les termes et conditions que vous avez déployée et la version ils acceptées. Vous pouvez afficher l’acceptation de des conditions qui ont été déployées pour jusqu'à 10 utilisateurs, ou afficher l’état d’acceptation pour un terme particulier qui a été déployé leur.|
|**Rapports d’applications non conformes**|Afficher des informations sur les utilisateurs qui possèdent des applications installées sur vos listes des applications conformes et non conformes. Utilisez ce rapport pour trouver des utilisateurs et dispositifs qui ne sont pas dans le respect des stratégies de votre application d’entreprise.|
|**Rapports de conformité certificat**|Afficher les certificats ont été émis à des utilisateurs et des appareils via SCEP ou PKCS #12 (. PFX). Utilisez ce rapport pour rechercher des certificats qui sont émis, expirés ou révoqués.|
|**Rapports sur l’historique des périphériques**|Afficher un journal historique de déclassement, réinitialisation et les actions de suppression. Utilisez ce rapport pour voir qui a initié actions sur les appareils par le passé.|
|**Rapports d’intégrité Attestation**|Afficher l’état des périphériques mobiles.|
|**Mac OS X matériel rapport**|Affiche les détails du matériel pour tous les périphériques de Mac OS X inscrits dans les groupes que vous sélectionnez. Pour plus d’informations sur l’inventaire matériel qui est collectée à partir de ces appareils, voir [comprendre vos périphériques en stock dans Microsoft Intune](understand-your-devices-with-inventory-in-microsoft-intune.md).|
|**Mac OS X logiciel rapport**|Affiche le logiciel est installé sur tous les périphériques de Mac OS X dans les groupes que vous avez sélectionné. Le rapport répertorie le nom du logiciel (comme un ID de groupe), la version courte (ou convivial) nom, la version et le nombre d’appareils avec le logiciel est installé.|

#### Pour créer un rapport

1.  Dans la console d’administration Intune, choisissez **rapports**. Puis sélectionnez le type de rapport que vous souhaitez générer, comme décrit dans le tableau précédent.

2.  Dans la page **Créer un nouveau rapport** , acceptez les valeurs par défaut ou les personnaliser pour filtrer les résultats qui seront renvoyés par le rapport. Par exemple, vous pouvez sélectionner qu’uniquement les logiciels publiés par Microsoft seront affichera dans le rapport de logiciels détectés.

3.  Cliquez sur **Afficher le rapport** pour l’ouvrir dans une nouvelle fenêtre.

Pour trier le rapport par une des colonnes affichées, cliquez sur l’en-tête de colonne. En outre, certains rapports vous permettent développer des éléments dans la liste pour afficher plus de détails.

## Plusieurs actions associées au rapport
En outre, rapports prennent en charge les actions suivantes :

|Action|Plus d’informations|
|----------|--------------------|
|**Imprimer**|Dans un rapport ouvert, cliquez sur l’icône d’impression et suivez les instructions.|
|**Exporter**|Dans un rapport ouvert, cliquez sur l’icône Exporter et suivez les instructions. Vous pouvez exporter un rapport vers valeurs séparées par des virgules (.csv) ou au format HTML.|
|**Enregistrer**|Dans la page **Créer un nouveau rapport** , chaque utilisateur peut enregistrer jusqu'à 100 rapports. Configurer les paramètres du rapport à vos besoins, puis sur **Enregistrer** ou **Enregistrer sous** (si vous voulez utiliser un autre nom).|
|**Chargement**|Dans la page **Créer un nouveau rapport** , choisissez **charger** pour extraire tous les jeux de paramètres de rapport enregistrés précédemment.|
|**Supprimer**|Dans l’espace de travail **rapports** , sélectionnez le type de rapport de votre choix et choisissez **charger**. Puis, dans la liste des rapports, cliquez sur l’icône Supprimer (x) en regard du rapport.|

### Voir aussi
[Surveillance et des rapports avec Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
