---
title: "Gérer les contrats de licence logiciel sur les PC exécutant le logiciel client Intune | Microsoft Intune"
description: "Intune vous permet de gérer les contrats de licence logiciel acheté via des contrats de licence en Volume Microsoft et pour les logiciels qui a été acheté par d’autres moyens."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59d8635-3f66-40f5-824a-a71c738e0341
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: 4af08b38716e04766175e2ab55db1a0dba788c20
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Gérer les contrats de licence de logiciel PC Windows Intune Microsoft
Microsoft Intune permet d’ajouter et gérer les informations de contrat de licence logiciel a été acheté via des contrats de licence en Volume Microsoft. Vous pouvez également faire ceci pour Microsoft ou logiciel non-Microsoft qui a été acheté par d’autres moyens. Vous pouvez organiser ces informations en groupes logiques.

> [!IMPORTANT]
> Cette fonctionnalité est fournie par commodité uniquement, et précision n’est pas garantie. Vous ne devez pas compter sur pour vérifier la conformité avec les contrats de licence en Volume Microsoft. Microsoft n’utilisera les données collectées pour déterminer l’origine des violations potentielles d’ou la conformité avec les contrats de licence que vous deviez avec nous.
>
> Licences que vous ajoutez au Intune ne concernent pas votre contrat de licence ou les droits d’accès à utiliser votre logiciel. Par exemple, si vous supprimez une paire/contrat de licence de Intune, vous ne pas supprimer ou annulent le contrats de licence qui existent entre vous et Microsoft.

Dans l’espace de travail **des licences** de la console d’administration Intune, vous pouvez :

-   Ajouter et modifier des contrats de licence en Volume Microsoft.

-   Ajouter et modifier les autres logiciels contrat de licence.

-   Gérer les licences et groupes.

-   Comparer les informations de droit Intune récupère à partir de la Volume Service centre de gestion des licences à l’inventaire des logiciels Microsoft Intune détecte sur votre PC Windows gérés.

En outre, vous pouvez générer des rapports qui indiquent l’installation et nombre de licences pour les titres de logiciel. Rapports de licence peuvent vous aider à évaluer votre position licence complet pour les titres de logiciels Microsoft software et non Microsoft.

> [!TIP]
> L’espace de travail **licences** n’est pas affiché dans la console administrateur jusqu'à ce que vous gérez au moins un PC Windows avec le client PC Windows Intune.

## Ajouter des contrats de licence en Volume Microsoft
Contrats de licence en Volume Intune fournissent des informations de licence logiciel a été acheté via des contrats de licence en Volume Microsoft. Vous pouvez ajouter des contrats de licence en Volume Microsoft au Intune en fournissant des paires de nombres contrat. Les numéros de contrat ou de l’autorisation doivent correspondre à la licence correcte ou des numéros d’inscription. Paires de nombres accord sont obtenus lorsque vous achetez vos contrats de licence de [Volume Service centre de gestion des licences](http://go.microsoft.com/fwlink/?LinkID=223842).

1.  Dans la [console d’administration Microsoft Intune](https://account.manage.microsoft.com/admin/default.aspx), sélectionnez **licences**.

2.  Dans la page **Ajouter des contrats** , sous **Choisir un Type de contrat**, sélectionnez le **contrat de licence en Volume**.

3.  Dans la section **Ajouter des détails contrat** , choisissez si vous voulez télécharger un fichier, ou ajoutez manuellement les détails.

    -   **Télécharger un fichier CSV contenant les détails du contrat**. Cliquez sur **Parcourir** et sélectionnez le fichier CSV que vous voulez télécharger.

        -   Le fichier peut contenir deux ou trois colonnes ; deux pour paires contrat seuls ou trois si vous souhaitez ajouter un nom convivial pour chaque paire de contrat.

        -   Le nombre total de caractères dans un accord paire numéro ne peut pas dépasser 16 caractères ASCII.

        -   Seuls les caractères ASCII sont prises en charge.

        -   Les caractères suivants ne sont pas autorisés dans le nom du contrat : **~ ! @ # $ ^ &amp; & #42 ; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Les espaces sont autorisés dans le nom.

        -   Le nom de fichier doit être pas dépasser 128 caractères.

        -   Le fichier doit contenir paire au moins un accord et ne peut pas contenir plus de 5 000 paires contrat.

        **Format du fichier**

        Vous pouvez créer ce fichier en ajoutant des paires de votre contrat à un document au format texte brut dans un des formats suivants, selon le type d’organisation que vous avez enregistrés avec la gestion des. Spécifiez une paire nombre contrat par ligne.

        -   **Clients open Value :** *Numéro d’accord*, *Répétez numéro d’accord*, *nom de l’accord*

        -   **Clients open :** *Numéro d’autorisation*, *numéro de licence*, le *nom de contrat*

        -   **Les clients select et entreprise :** *Numéro d’accord*, *numéro d’inscription associées*, *nom de l’accord*

        L’écran **Ajouter des contrats** vous invite à rechercher ce fichier lorsque vous ajoutez un nouveau contrat.

        Voici un exemple de contenu du fichier .csv pour un client Open Value.

        `01-07001, 01-07001, Office agreements`

    -   **Ajouter manuellement des détails de l’accord**. Fournissez les informations suivantes, et tapez les paires de nombres contrat dans les zones **numéro d’autorisation/contrat** de **Licence / d’inscription/client** . Après avoir tapé les deux nombres, cliquez sur l’icône **Ajouter paire** pour enregistrer vos numéros, puis vous pouvez également ajouter une nouvelle paire.

        -   **Nom de l’accord** : spécifiez un nom unique pour le contrat.

            Le nom de contrat peut contenir un maximum de 256 caractères et ne peut pas contenir les caractères suivants : **~ ! @ # $ ^ &amp; & #42 ; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Les espaces sont autorisés dans le nom.

        -   **Numéro de l’autorisation/accord** - Entrez le nombre d’autorisations/accord de la paire de licence.

        -   **Numéro de licence / d’inscription/client** - Entrez le nombre de licences / d’inscription/client de la paire de licence.

        > [!NOTE]
        > Si vous ajoutez plusieurs paires de nombres contrat, Intune crée un contrat avec le nom que vous spécifiez et toutes les paires que vous avez ajouté une partie de ce contrat.

    Vous pouvez choisir **+** pour ajouter une autre paire de numéro de contrat, ou **-** pour supprimer une paire numéro contrat que vous avez déjà entré.

4.  Dans la zone **Sélectionnez un groupe de licences** , effectuez une des opérations suivantes :

    -   **Ajouter les accords au groupe accords non attribués**. Sélectionnez cette option si vous ne souhaitez pas ajouter les nouveaux accords à un groupe de licences.

    -   **Ajouter les accords à un nouveau groupe de licences**. Indiquez un nom pour le nouveau groupe de licences.

    -   **Ajouter les accords à un groupe existant de la licence**. Dans la liste **nom du groupe** , sélectionnez le groupe de licences à laquelle vous souhaitez ajouter le contrats.

5.  Cliquez sur **OK**.

L’affichage de **Tous les accords** et Intune se connecte au VLSC Microsoft pour valider les paires de nombres contrat que vous avez fourni.

Pour mettre à jour les informations de licence en volume après avoir ajouté des contrats de licence dans Intune, dans la page **Vue d’ensemble des licences** , cliquez sur **Actualiser maintenant**. Cette action extrait les informations de licence actuelles à partir de [Microsoft Volume Service centre de gestion des licences](http://go.microsoft.com/fwlink/?LinkId=223842).

> [!IMPORTANT]
> Jusqu'à ce que vous actualisez les informations de licence en volume, vous pouvez voir des informations différentes dans la liste des accords et les informations de droit sur la page **Vue d’ensemble des accords** .

Après avoir actualisé les informations de licence en volume, vous pouvez comparer les informations de licence du logiciel Microsoft détecté dans l’espace de travail **d’applications** . Vous pouvez également exécuter les rapports de licence suivants :

-   **Rapports d’acheter des licences** - vous permet d’afficher le logiciel sous licence en groupes de licences que vous choisissez pour vous aider à rechercher des écarts dans la couverture.

-   **Rapports d’Installation des licences** - vous permet de déterminer si vous avez suffisamment couverture du contrat de licence.

> [!NOTE]
> Le **Titre du produit** affiché pour tous les contrats de licence en Volume Microsoft n’est **pas disponible**.

## Ajouter et modifier les autres logiciels contrat de licence
Vous pouvez également ajouter d’autres types de contrats de licence pour Intune en plus de contrats de licence en Volume Microsoft. Ces accords peuvent inclure des logiciels non Microsoft ou logiciel Microsoft que vous avez acheté auprès d’un revendeur.

> [!IMPORTANT]
> Vous devez disposer au moins un PC Windows Intune inscrit avant de pouvoir ajouter un contrat.  En outre, au moins un ordinateur inscrit devez avoir téléchargé un logiciel sous licence que vous souhaitez utiliser pour ajouter un contrat de licence.

### Pour ajouter d’autres accords logiciel

1.  Dans la [console d’administration Microsoft Intune](https://account.manage.microsoft.com/admin/default.aspx), sélectionnez **licences**.

2.  Dans la section **Autres accords de licence logiciel** , sélectionnez **Ajouter des contrats** .

3.  Sélectionnez **autres contrat de licence logiciel** dans la section **Choisir le Type de contrat** de la page **Ajouter des contrats** .

4.  Dans la zone **Ajouter des détails contrat** , spécifiez les éléments suivants :

    -   **Nom de l’accord** (obligatoire). Le nom de contrat peut contenir un maximum de 256 caractères et ne peut pas contenir les caractères suivants : **~ ! @ # $ ^ &amp; & #42 ; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Les espaces sont autorisés dans le nom.

    -   **Publisher** (obligatoire). Lorsque vous commencez à taper un nom de l’éditeur, le service récupère tous les noms des éditeurs qui contiennent les lettres que vous tapez. Par exemple, si vous tapez « logiciel », le service renvoie tous les noms de publisher qui contiennent « logiciel » dans le cadre du nom, telles que « Microsoft » et « Microsoft Research ». Les noms de publisher sont récupérés à partir du catalogue de biens logiciel. Vous devez sélectionner l’éditeur avant d’entrer le nom du produit.

        > [!IMPORTANT]
        > La société que vous voulez ajouter peut-être ne pas apparaître dans cette liste. Vous pouvez uniquement ajouter accords logiciel pour les entreprises qui sont déjà présents dans le catalogue de biens logiciel. Toutefois, Microsoft fonctionne en permanence pour ajouter les titres les plus populaires. Si vous voulez envoyer une demande d’avoir une société ajoutée à cette liste, vous pouvez le faire sur le [site Intune Uservoice](https://microsoftintune.uservoice.com/).

    -   **Titre du produit** (obligatoire). Lorsque vous commencez à taper un titre de produit, le service récupère tous les titres de produit qui contiennent les lettres que vous tapez. Vous devez spécifier un **éditeur** avant de spécifier un **titre du produit**.

    -   **Nombre de licences** (obligatoire). Entrez le nombre de licences achetées.

    -   **Date de début de licence**. Entrez la date de début de la couverture de licence.

    -   **Date de fin de licence**. Entrez la date de fin de la couverture de licence.

    -   **Détails de l’accord**. Vous pouvez éventuellement spécifier des informations de contact et autres informations clés d’enregistrement.

5.  Dans la zone **Sélectionnez un groupe de licences** , effectuez une des opérations suivantes :

    -   Sélectionnez **Ajouter les accords au groupe accords non attribués** si vous ne souhaitez pas ajouter les nouveaux accords à un groupe existant ou nouveau licence. Vous pouvez ajouter les accords aux groupes de licence définies par l’utilisateur à tout moment.

    -   Sélectionnez **Ajouter les accords à un nouveau groupe de licences** pour ajouter les nouveaux accords à un nouveau groupe de licences. Vous êtes invité à fournir un nom pour le nouveau groupe de licences.

    -   Sélectionnez **Ajouter les accords à un groupe existant de la licence** à ajouter les nouveaux accords à un groupe existant de la licence. Dans la liste **nom du groupe** , sélectionnez le groupe de licences à laquelle vous souhaitez ajouter le contrats.

6.  Cliquez sur **OK**.

L’affichage de liste de **Tous les accords** s’affiche.

## Gérer les contrats de licence
Contrat de licence logiciel peut être ajoutés aux groupes de licences. Vous pouvez utiliser des groupes de licences pour organiser vos contrats de licence en unités qui sont adaptées à votre organisation. En outre, vous pouvez supprimer des contrats de licence que vous avez créé précédemment.

|||
|-|-|
|Tâche|Plus d’informations|
|Créer un groupe de licences|Dans la page **vue d’ensemble** de l’espace de travail **des licences** , sélectionnez **Créer un groupe de licence** dans le menu **tâches** . **Remarque :** Vous pouvez créer un total maximum de 500 groupes de licences.|
|Renommer un groupe de licences|Dans l’espace de travail **des licences** , sélectionnez un groupe de licences, puis **Modifier le groupe de licence** dans le Menu **tâches** .|
|Supprimer un groupe de licences|Dans l’espace de travail **des licences** , sélectionnez un groupe de licences, puis **Supprimer le groupe de licence** dans le Menu **tâches** . **Conseil :** Les licences qui ont été dans le groupe supprimé sont déplacés vers le groupe de licences **accords non attribués** .|
|Supprimer un contrat de licence|Dans l’espace de travail **des licences** , sélectionnez un contrat, puis **Supprimer**. **Conseil :** Après avoir supprimé accords de licence en Volume, pour mettre à jour les informations de licence, cliquez sur **Actualiser maintenant** dans la page **Vue d’ensemble des licences** ou sous l’onglet **Général** pour un groupe de licences spécifiques.|
