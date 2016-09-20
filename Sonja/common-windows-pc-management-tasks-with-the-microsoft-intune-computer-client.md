---
title: "Tâches de gestion courantes PC Windows | Microsoft Intune"
description: "Passez en revue les tâches dans cette rubrique pour apprendre à gérer des PC Windows qui s’exécutent le logiciel client Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb912c73-54d2-4d78-ac34-3cbe825804c7
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: 9ef18ee054928fcfb12a36fe8ac3ad3c2909f6c1
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Tâches de gestion courantes PC Windows avec le logiciel client Intune
Passez en revue les tâches dans cette rubrique pour apprendre à gérer vos ordinateurs qui exécutent le logiciel client Intune. Si vous n’avez pas encore installé le client sur vos ordinateurs, consultez [installer le logiciel client Intune](install-the-windows-pc-client-with-microsoft-intune.md).


## Utiliser des stratégies pour simplifier la gestion des PC

PC Windows la Intune logiciel client peut être géré à l’aide de stratégies de **Gestion de l’ordinateur** de Intune en cours d’exécution.

![Modèle de stratégies pour les PC Windows](../media/pc_policy_template.png)

### Gérer le centre de Intune Microsoft
Utilisateurs de voir le client logiciel Intune comme **Microsoft Intune Center**. Le Microsoft Intune Center permet aux utilisateurs :

-   Obtenir des applications à partir du portail d’entreprise.

-   Vérifier les mises à jour.

-   Gérer Microsoft Intune Endpoint Protection.

-  Demander assistance à distance.

Le Microsoft Intune Center est installé sur tous les ordinateurs gérés. Vous pouvez configurer les paramètres suivants dans une stratégie Intune et ceux-ci sont affichés pour les utilisateurs dans le Microsoft Intune Center :

|Paramètre de stratégie|Plus d’informations|
|------------------|--------------------|
|**Nom**|Le nom de l’administrateur qui gère l’ordinateur.<br /><br />Longueur maximale : 40 caractères|
|**Numéro de téléphone**|Le numéro de téléphone de l’administrateur qui gère l’ordinateur.<br /><br />Longueur maximale : 20 caractères|
|**Adresse de messagerie**|L’adresse de messagerie de l’administrateur qui gère l’ordinateur.<br /><br />Longueur maximale : 40 caractères|
|**Nom du site Web**|Le nom de votre site Web de support pour les utilisateurs.<br /><br />Longueur maximale : 40 caractères|
|**URL du site Web**|L’URL de votre site Web de support.<br /><br />Longueur maximale : 150 caractères|
|**Notes**|Une note qui s’affiche pour les utilisateurs.<br /><br />Longueur maximale : 120 caractères|

## Paramètres de mise à jour logicielles
Utiliser des stratégies pour configurer les paramètres que les ordinateurs sous gestion pour vérifier et télécharger les mises à jour logicielles à partir de Microsoft et de fournisseurs tiers. Ces mises à jour n’incluent pas (c'est-à-dire les mises à niveau du système d’exploitation la mise à niveau de Windows 7 vers Windows 10 ou mises à niveau à partir d’une version de Windows 10 vers une version ultérieure). Pour plus d’informations, voir [Conserver PC Windows à jour avec les mises à jour logicielles dans Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).

### Paramètres de Protection du point de terminaison
Utiliser des stratégies pour configurer les paramètres de Protection de point de terminaison que vous déployez puis sur les ordinateurs gérés. Cela inclut les analyses et actions à effectuer lors de la détection de programmes malveillants. Pour plus d’informations, consultez [l’aide de sécuriser les PC Windows avec Endpoint Protection pour Intune Microsoft](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).

## Paramètres du pare-feu Windows
Les stratégies simplifient la gestion des paramètres du pare-feu Windows sur les ordinateurs gérés. Pour plus d’informations, voir [protéger Windows PC à l’aide de stratégies de pare-feu Windows dans Microsoft Intune](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md).

## Afficher le stock matérielle et logicielle
Intune recueille des informations détaillées sur la configuration matérielle et logicielle d’ordinateurs gérés. Utilisez les informations dans les procédures suivantes pour découvrir comment créer :

-   Un état qui répertorie les informations sur les capacités matérielles de vos ordinateurs.

-   Un état qui répertorie les logiciels installés sur chaque ordinateur.

-   Comment actualiser un inventaire ordinateurs pour vous assurer que les données dans le rapport soient en cours.

### Pour afficher des informations sur vos ordinateurs

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), cliquez sur **rapports** &gt; **Ordinateur inventaire rapports**.

2.  Dans la page **Créer un nouveau rapport** , acceptez les valeurs par défaut ou les personnaliser pour filtrer les résultats qui seront renvoyés par le rapport. Par exemple, vous pouvez sélectionner que seuls les ordinateurs qui exécutent Windows 8.1 seront affichera dans le rapport.

3.  Cliquez sur **Afficher le rapport** pour ouvrir le **Rapport d’inventaire ordinateur** dans une nouvelle fenêtre.

    Vous pouvez trier le rapport par une des colonnes, par exemple, **nom**, **Type de boîtier** ou **fabricant** en sélectionnant chaque en-tête de colonne.

### Pour afficher les logiciels installés sur vos ordinateurs

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), cliquez sur **rapports** &gt; **Détecté logiciel rapports**.

2.  Dans la page **Créer un nouveau rapport** , acceptez les valeurs par défaut ou les personnaliser pour filtrer les résultats qui seront renvoyés par le rapport. Par exemple, vous pouvez sélectionner qu’uniquement les logiciels publiés par Microsoft seront affichera dans le rapport.

3.  Cliquez sur **Afficher le rapport** pour ouvrir le **Rapport de logiciels détectés** dans une nouvelle fenêtre.

    Vous pouvez trier le rapport par une des colonnes, par exemple, **nom**, **Publisher** ou **catégorie** en sélectionnant chaque en-tête de colonne. Vous pouvez développer les mises à jour dans la liste pour afficher plus en détail (par exemple, les ordinateurs sur lesquels il est installé) en choisissant la flèche en regard de l’élément de liste.

### Pour actualiser les ressources de l’ordinateur pour vérifier qu’il est en cours

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **groupes** &gt; **Tous les périphériques** (ou un autre groupe qui contient l’ordinateur pour lequel vous souhaitez actualiser stock).

2.  Sélectionnez un ordinateur, ou appuyez sur et maintenez la touche **Ctrl** pour sélectionner plusieurs ordinateurs.

3.  Dans la barre des tâches, sélectionnez **Tâches à distance** &gt; **Stock actualiser**.

4.  Pour afficher l’état des tâches, cliquez sur **Tâches à distance** dans le coin inférieur droit de la page.

    La boîte de dialogue **État des tâches** affiche les tâches à distance en cours, état des tâches, nom de l’appareil et toutes les erreurs signalées et fournit un lien vers des informations de dépannage.


## Redémarrer à distance un PC Windows

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **groupes** &gt; **Tous les périphériques** (ou un autre groupe qui contient l’ordinateur que vous souhaitez redémarrer).

2.  Sélectionnez un ou plusieurs ordinateurs, puis **Tâches à distance** &gt; **Redémarrer l’ordinateur**.

3.  Pour afficher l’état des tâches, cliquez sur **Tâches à distance** dans le coin inférieur droit de la page.

4.  Dans la boîte de dialogue **État de la tâche** , passez en revue les tâches à distance en cours, état des tâches, nom de l’appareil et toutes les erreurs signalées.

## Retirer un ordinateur

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **groupes** &gt; **Tous les périphériques** (ou un autre groupe qui contient l’ordinateur que vous voulez retirer).

2.  Sélectionnez les appareils que vous voulez retirer, puis **Déclassement/réinitialisation**.

Pour ré-inscrire un ordinateur dans Intune, réinstaller le logiciel client sur le PC à l’aide de recommandations dans [installer le client PC Windows avec Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Si un ordinateur ne peut pas se connecter à Intune, un message s’affiche dans l’espace de travail de **tableau de bord** .

Lorsque vous annulez un ordinateur :

-   Il est supprimé de la gestion des Intune et de l’inventaire et la licence associée à l’ordinateur est mises à disposition des réutiliser. Retirer/réinitialisation supprime le logiciel client Intune mais ne supprime pas d’applications ou des données à partir de l’ordinateur. Ce déclassement n’effectue une réinitialisation complète sur l’ordinateur.

-   Son statut n’apparaît plus dans la console Intune.

-   Intune supprime le logiciel client de l’ordinateur. Si l’ordinateur n’est pas connecté au service Intune, le logiciel client a été supprimé de la prochaine fois qu’il se connecte.

-   Microsoft Intune Endpoint Protection est supprimée de l’ordinateur. Si l’ordinateur dispose d’une autre application de point de terminaison installée et qu’il est désactivé, application peut être réactivée après la suppression de Microsoft Intune Endpoint Protection pour vous assurer que vos ordinateurs sont protégés.

-   Toutes les stratégies sont supprimées de l’ordinateur et les valeurs qui ont été définies par la stratégie seront modifiés.

-   L’ordinateur ne reçoive plus mises à jour logicielles ou mises à jour des définitions de logiciels malveillants à partir du service Intune.

-   Selon la façon dont ils sont configurés, ordinateurs déclassés peuvent continuer à recevoir des mises à jour à l’aide de Windows Server Update Services, Windows Update ou Microsoft Update.

    > [!IMPORTANT]
    > Si le logiciel client a été installé à l’aide d’un objet (stratégie de groupe), vous devez supprimer l’objet (stratégie de groupe) avant de pouvoir supprimer le logiciel client pour éviter que le logiciel en cours de réinstallation.

    Si le client ne parvient pas à désinstaller, lisez [Résoudre les problèmes Endpoint Protection](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune) pour obtenir une aide supplémentaire.

## Gérer la liaison de périphérique utilisateur
Avant de déployer logiciel à un utilisateur, vous devez lier l’utilisateur à un ordinateur. Vous pouvez lier un utilisateur sur plusieurs ordinateurs, mais chaque ordinateur peut être lié à un seul utilisateur. Les utilisateurs sont liés automatiquement à tous les ordinateurs qu’ils inscrivent au programme d’Intune à l’aide du portail d’entreprise.

### Pour lier un utilisateur à un ordinateur

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **groupes** &gt; **Tous les périphériques** (ou un autre groupe qui contient l’ordinateur que vous souhaitez lier à un utilisateur).

2.  Sélectionnez l’ordinateur que vous souhaitez lier un utilisateur, puis **Lien utilisateur**.

    La boîte de dialogue **Lien** affiche une liste des utilisateurs disponibles avec leur nom complet, nom d’utilisateur, et le nombre d’ordinateurs à chaque utilisateur qui est lié. Si un utilisateur est déjà lié à l’ordinateur sélectionné, son nom et l’ID utilisateur sont affichent sous **utilisateur actuel**. Si l’ordinateur n’est pas lié à tous les utilisateurs, **Aucun utilisateur** s’affiche sous **Utilisateur actuel**.

3.  Effectuez l’une des opérations suivantes :

    -   Pour quitter l’ordinateur lié à son utilisateur actuel, le cas échéant, cliquez sur **Annuler**.

    -   Pour supprimer le lien à l’utilisateur actuel, le cas échéant, cliquez sur **Supprimer le lien** &gt; **OK**.

    -   Pour lier l’ordinateur à un nouvel utilisateur, dans la liste de **tous les utilisateurs** , sélectionnez un utilisateur. Vérifiez que les données utilisateur soient correctes, puis cliquez sur **OK**.

> [!TIP]
> Si vous souhaitez limiter la capacité des utilisateurs finaux à lier eux-mêmes à des ordinateurs, activez l’option **possibilité de restreindre les utilisateurs à lier eux-mêmes à des ordinateurs** dans la stratégie **Paramètres d’Agent Intune Microsoft** .

## Demander et fournir une assistance à distance pour les PC Windows

Microsoft Intune peuvent utiliser le logiciel [TeamViewer](https://www.teamviewer.com) , vendu séparément, pour permettre aux utilisateurs de PC qui exécutent le Intune logiciel client obtenir de l’aide de l’assistance à distance de votre part. Lorsqu’un utilisateur demande l’aide de la Microsoft Intune Center, vous êtes informé par une alerte, peut accepter la demande et puis fournir une assistance.
Cette fonctionnalité remplace la fonctionnalité Assistance à distance Windows Intune existante.


### Avant de commencer

Avant de commencer à établir et répondre à des demandes d’assistance à distance, vous devez vérifier que les composants requis suivants sont en place :

- Vous devez [inscrit à un compte TeamViewer](https://login.teamviewer.com/LogOn#register) pour vous connecter au site Web TeamViewer.
- PC Windows que vous souhaitez administrer doivent être [gérés par le client PC Windows](manage-windows-pcs-with-microsoft-intune.md)
- Tous les systèmes d’exploitation de PC Windows pris en charge par Intune gérables.

### Configurer le connecteur TeamViewer

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **administrateur**.
2. Dans l’espace de travail **administrateur** , choisissez **TeamViewer**.
3. Dans la page **TeamViewer** , sous **TeamViewer connecteur**, sélectionnez **Activer**.
4. Dans la boîte de dialogue **Activer TeamViewer** , affichage, puis **Accepter** le contrat de licence. Si vous ne possédez pas encore une licence TeamViewer, choisissez **acheter une licence TeamViewer**.
5. Une fois que la fenêtre du navigateur TeamViewer s’ouvre, vous connecter au site avec vos informations d’identification TeamViewer.
6. Sur le site TeamViewer, lisez, puis acceptez les options pour permettre Intune communiquer avec TeamViewer.
7. Dans la console Intune, vérifiez que l’élément de **Connecteur TeamViewer** affiche comme **activé**.


### Ouvrez une demande d’assistance à distance (utilisateur final)

1. Sur un PC Windows client, ouvrez le **Centre de Intune Microsoft**.
2. Titre **L’Assistance à distance**, choisissez **Demander assistance à distance**.
3. Une fois que vous approuvez la demande (voir ci-dessous), TeamViewer s’ouvre sur le client. L’utilisateur doit accepter les messages indiquant que le navigateur web tente d’ouvrir l’application TeamViewer.
4. L’utilisateur voit un message vous demandant si vous pouvez contrôler son PC. Ils doivent accepter ce message pour continuer.
5. Pendant la session d’assistance à distance, l’utilisateur voit une fenêtre indiquant les que vous êtes connecté. Si elles ferment cette fenêtre, la session distante se termine.

### Répondre à une demande d’assistance à distance

1. Lorsqu’un utilisateur envoie une demande d’assistance à distance, vous pouvez l’afficher dans l’espace de travail **alertes** , sous **surveillance** > **Assistance à distance**. Par exemple :
> ![Capture d’écran d’une demande d’assistance à distance](./media/team-viewer.png)

<br>Si une demande est sans réponse pendant plus de 4 heures, celui-ci est supprimé.
2. Pour accepter la demande, choisissez **Approuver la demande et lancer l’Assistance à distance**.
3. Dans la boîte de dialogue **A nouvelle demande d’Assistance à distance est en attente** , sélectionnez **accepter la demande d’assistance à distance**. S’il n’est pas déjà installé, TeamViewer va installer nécessaire de toutes les applications sur votre ordinateur.
4. TeamViewer avertit ensuite l’utilisateur final que vous voulez prendre le contrôle de leur ordinateur. Une fois que l’utilisateur a accepté la demande, les fenêtres TeamViewer s’ouvre et vous pouvez contrôler le PC.

Au cours d’une session assistance à distance, vous pouvez utiliser toutes les commandes TeamViewer disponibles pour contrôler l’ordinateur distant. Pour obtenir de l’aide ces commandes, téléchargez le [manuel d’utilisation de contrôle à distance](http://www.teamviewer.com/en/support/documents/) depuis le site Web TeamViewer.

### Fermer la session d’assistance à distance

Dans le menu **Actions** de la fenêtre **TeamViewer** , choisissez **Terminer la Session**.
