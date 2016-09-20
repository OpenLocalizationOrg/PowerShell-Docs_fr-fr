---
title: "Mises à jour logicielles pour les PC Windows | Microsoft Intune"
description: "Intune vous permet de maintenir vos ordinateurs gérés à jour en garantissant les derniers correctifs et mises à jour logicielles sont installés rapidement."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 48e9c41a-d2de-424e-9610-cfd1ad514210
ms.reviewer: owenyen
ms.suite: ems
ms.openlocfilehash: e26786066b98adf187a6cf3ccbf172e919871f50
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Maintenir PC Windows à jour avec les mises à jour logicielles dans Microsoft Intune
Microsoft Intune peut vous aider à sécuriser vos ordinateurs gérés dans de différentes manières, y compris la gestion des mises à jour logicielles maintenir vos ordinateurs à jour en veillant à ce logiciel les derniers correctifs mises à jour sont installées rapidement.

Si vous n’avez pas encore installé le client Intune sur vos ordinateurs, voir [installer le client PC Windows avec Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Lorsque les nouvelles mises à jour sont disponibles à partir de Microsoft Update, ou vous avez créé une mise à jour de tiers, et elles sont appliquent à vos ordinateurs gérés, une notification s’affiche dans la page **vue d’ensemble** de l’espace de travail **mises à jour** . Après avoir choisi ce lien de notification, vous pouvez ensuite effectuer diverses opérations comme afficher plus d’informations sur la mise à jour, l’approbation ou refus de la mise à jour et afficher les ordinateurs qui va installer la mise à jour si elle est approuvée.

> [!IMPORTANT]
> L’espace de travail **mises à jour** n’est pas affiché dans la console administrateur jusqu'à ce que vous avez installé le client sur et gérez correctement au moins un ordinateur client.

Mises à jour sont approuvés et installés, vous pouvez examiner la réussite ou l’échec de l’installation de l’espace de travail **mises à jour** de la console Intune.

Les sections suivantes vous aidera à tenir à jour les logiciels sur vos ordinateurs gérés.

## Avant de commencer
Avant de commencer à créer et approuver des mises à jour logicielles, configurer et déployer des stratégies sur vos ordinateurs qui contrôlent quand et comment les mises à jour sont installés.

### Pour configurer les paramètres de stratégie de mise à jour

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **stratégie** &gt; **vue d’ensemble** &gt; **Ajouter une stratégie**.

2.  Configurer et déployer une stratégie de **Paramètres de l’Agent Intune Microsoft** pour les paramètres de mise à jour. Vous pouvez utiliser les paramètres recommandés ou personnaliser les paramètres. Si vous avez besoin de plus d’informations sur la façon de créer et déployer des stratégies, voir [tâches de gestion courantes PC Windows avec le client ordinateur Intune Microsoft](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

Le tableau suivant montre les valeurs que vous pouvez configurer la stratégie, ainsi que les valeurs recommandées qui seront utilisés si vous ne personnalisez la stratégie. Vous trouverez ces paramètres dans la section **mises à jour** .

  |Paramètre de stratégie|Plus d’informations|
    |------------------|--------------------|
    |**Fréquence de détection de mise à jour et d’application (heures)** |Spécifie la fréquence (de 8-22 heures) Intune recherchent les nouvelles mises à jour et les applications.<br /><br />Valeur recommandée : **8** heures.|
    |**Automatisé ou invité à l’installation des mises à jour et des applications** |Indique si les mises à jour sont installées automatiquement ou si l’utilisateur est invité avant l’installation. En outre, ce paramètre vous permet de planifier l’installation des mises à jour et les applications.<br /><br />**Installer les mises à jour et applications automatiquement comme prévu** installe mises à jour et les applications à l’aide de la planification spécifiée.<br /><br />Comme un paramètre de stratégie dépendante, **ordinateurs utilisation automatique Maintenance pour Windows** indique que les mises à jour et applications sont installées au cours de la fenêtre de gestion automatique de Windows.<br /><br />**Demander à l’utilisateur pour l’installation** , l’utilisateur à installer les mises à jour lorsqu’elles sont prêtes.<br /><br />Valeurs recommandées :<br /><br />**Installer les mises à jour et applications automatiquement comme prévu** sélectionné<br /><br />**Jour planifiée : tous les jours**<br /><br />**Durée prévue : 3:00 AM**<br /><br />**Utilisation automatique pour les fenêtres de Maintenance ordinateurs** sélectionnés|
    |**Autoriser l’installation immédiate des mises à jour qui ne pas interrompre Windows** |**Autoriser** installe des mises à jour immédiatement après leur téléchargement, à l’exception des mises à jour qui seraient interrompre ou redémarrez Windows. Ces mises à jour sont installées en fonction de la configuration du paramètre **automatique ou invité à l’installation des mises à jour** .<br /><br />**Ne pas autoriser** installe mises à jour en fonction de la configuration du paramètre **automatique ou invité à l’installation des mises à jour** .<br /><br />Valeur recommandée : **Autoriser** |
    |**Retard de redémarrer Windows après l’installation des mises à jour planifiées et des applications (en minutes)** |Spécifie (à partir de 1 à 30 minutes), le délai d’attente de redémarrer Windows après l’installation des mises à jour planifiées et des applications.<br /><br />Valeur recommandée : **15 minutes** |
    |**Retard suivant redémarrer Windows pour commencer l’installation manqués mises à jour planifiées et les applications (en minutes)** |Spécifie (à partir de 1-60 minutes), la durée d’attendre avant de démarrer l’installation des mises à jour et des applications après le redémarrage de Windows lorsqu’une mise à jour planifiée a été omis.<br /><br />Valeur recommandée : **5 minutes**|
    |**Autoriser l’utilisateur connecté contrôler le redémarrage de Windows après l’installation des mises à jour planifiées et des applications** |Indique si l’utilisateur connecté peut retarder le redémarrage de Windows (si la valeur **Oui**), ou être averti du redémarrage Windows automatique (si définie sur **non**). Si aucun utilisateur n’est connecté lors de l’installation des mises à jour et des applications planifiée est terminée, Windows est redémarré automatiquement lorsque cela est nécessaire. Lorsque la valeur **non**, par défaut, le délai avant le redémarrage de Windows est défini sur 5 minutes.<br /><br />Valeur recommandée : **Oui**|
    |**Inviter l’utilisateur à redémarrer Windows au cours de mises à jour obligatoires Intune client agent** |Indique si les utilisateurs connectés est invité à redémarrer Windows lorsqu’une mise à jour obligatoire Intune client nécessite le redémarrage de Windows.<br /><br />Valeur recommandée : **Oui**|
    |**Agent du client Microsoft Intune obligatoire met à jour la planification de l’installation** |Plannings lors de l’installation des mises à jour du client.<br /><br />Valeur recommandée : non configuré|
    |**Délai entre les invites pour redémarrer Windows après l’installation des mises à jour planifiées et les applications (en minutes)** |Spécifie la fréquence (entre 1 et 1440 minutes) l’utilisateur est invité à redémarrer Windows lorsqu’une mise à jour planifiée ou une application qui nécessite le redémarrage de Windows est installé, et l’utilisateur retarde le redémarrage.<br /><br />Valeur recommandée : **30 minutes** |

## Logiciel de mise à jour apportée par Microsoft
Mise à jour de logiciels Microsoft nécessite très peu de travail de votre part. Toutefois, avant de commencer, il existe deux choses que vous devez configurer :

-   **Catégories de produits et les classifications de mise à jour** – définit les catégories et les classifications les mises à jour que vous souhaitez rendre disponibles pour les ordinateurs. Par exemple, vous pouvez décider que vous voulez uniquement les mises à jour critiques pour Microsoft Office doit être installé.

-   **Règles d’approbation automatique** – ces règles approuver types spécifiés de mise à jour automatiquement et réduire vos frais administratifs. Par exemple, vous souhaiterez peut-être approuver automatiquement toutes les mises à jour critiques.

Utilisez les deux procédures suivantes vous aideront à utiliser les mises à jour logicielles :

### Configurer les catégories de produits et les classifications de mise à jour que vous souhaitez rendre disponibles pour les ordinateurs gérés

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **administrateur** &gt; **mises à jour**.

2.  Sur le **paramètres du Service : mises à jour** page, dans la liste **Catégorie de produit** , sélectionnez les catégories de mise à jour que vous souhaitez rendre disponibles pour les ordinateurs. Notez que les mises à jour plus courants sont activées par défaut.

    > [!IMPORTANT]
    > Pour vous assurer que les ordinateurs reçoivent les mises à jour qui ont été approuvés par l’administrateur, le paramètre de stratégie de groupe Windows Server mettre à jour les Services (WSUS), **emplacement de service de mise à jour spécifier Intranet Microsoft** ne doit pas être appliqué à des ordinateurs qui ont été inscrits avec Intune.

3.  Dans la liste de **Classification de mettre à jour** , sélectionnez les classes de mise à jour que vous souhaitez rendre disponibles pour les ordinateurs gérés. Là encore, les options les plus courantes sont sélectionnées par défaut.

4.  Cliquez sur **Enregistrer** pour enregistrer vos sélections.

### Pour configurer les règles d’approbation automatique pour les mises à jour logicielles

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **administrateur** &gt; **mises à jour**.

2.  Dans la section **Règles d’approbation automatique** de le **paramètres du serveur : mises à jour** page, cliquez sur **Nouveau**.

3.  Dans la page **Général** de l’Assistant créer une règle d’approbation automatique, spécifiez un nom et une description facultative de la règle.

4.  Dans la page **Catégories de produits** , sélectionnez tous les produits dont vous souhaitez que les mises à jour approuvées automatiquement.

5.  Dans la page **Mettre à jour les Classifications** , spécifiez les classifications de mise à jour que vous souhaitez ont approuvés automatiquement.

6.  Dans la page de **déploiement** , procédez comme suit :

    -   Sélectionnez les groupes d’ordinateurs à laquelle vous souhaitez déployer la nouvelle règle, puis **Ajouter**.

    -   Pour spécifier une date d’installation pour les mises à jour, activez la case à cocher **appliquer l’échéance d’installation pour ces mises à jour** , puis dans la liste de la **date d’Installation** , la date d’échéance d’installation.

        > [!NOTE]
        > Si vous spécifiez une date d’installation, l’ordinateur géré peut nécessiter une ou plusieurs redémarre une fois l’intervalle de délai dépassé.

    -   Lorsque vous avez terminé, sélectionnez **suivant**.

7.  Dans la page de **Résumé** , passez en revue les paramètres pour la nouvelle règle et puis cliquez sur **Terminer**.

La nouvelle règle est affichée dans la section **Règles d’approbation automatique** de le **paramètres du Service : mises à jour** page.

> [!NOTE]
> Lorsque vous créez une règle d’approbation automatique, il uniquement approuve mises à jour ultérieures et n’approuve pas automatiquement mises à jour précédemment existantes qui existent déjà dans Intune. Pour approuver ces mises à jour, vous devez exécuter la règle d’approbation automatique.


### Pour modifier, exécuter ou supprimer une règle de mise à jour automatiquement approuvée

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **administrateur** &gt; **mises à jour**.

2.  Dans la section **Règles d’approbation automatique** , sélectionnez une règle et effectuez l’une des opérations suivantes :

    -   Pour modifier la règle, choisissez **Modifier**, puis modifiez les paramètres de la règle dans l' **Assistant règle de mise à jour automatique approbation**.

    -   Pour exécuter la règle, cliquez sur **Exécuter sélectionnée**.

    -   Pour supprimer la règle, cliquez sur **Supprimer**.

        > [!NOTE]
        > Suppression d’une règle n’affecte pas les mises à jour précédentes qui ont été approuvés par la règle supprimée.

## Mise à jour logicielle non développée par Microsoft
Vous pouvez déployer les mises à jour de logiciel n’est pas apportées par Microsoft. Pour cela, à l’aide de l’Assistant **Télécharger mettre à jour** pour obtenir la mise à jour dans votre espace de stockage Cloud, après laquelle vous pouvez approuver ou refuser tout comme la mise à jour avec les logiciels Microsoft.

### Pour télécharger et configurer une mise à jour de tiers

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), sélectionnez **mises à jour** &gt; **vue d’ensemble** &gt; **Télécharger**.

2.  Dans la page **mettre à jour des fichiers** , cliquez sur **Parcourir** pour sélectionner les fichiers d’installation qui sont requises pour installer le package de mise à jour. Le fichier peut être un fichier Windows Installer (.msi), un fichier de correctif (.msp) de Windows Installer ou un fichier de programme .exe. Vous pouvez également inclure les fichiers ou dossiers supplémentaires qui se trouvent dans le même dossier que le fichier d’installation.

    La taille totale des fichiers sélectionnés pour la télécharger s’affiche. Notez que cette taille n’inclut pas les tailles compressées ou développés des fichiers d’installation.

3.  Une fois que vous spécifiez les fichiers d’installation, la page **mettre à jour description** affiche le nom, description et classification plus d’informations sur qui Intune extrait les fichiers d’installation du logiciel. Vous pouvez sélectionner une classification pour le type d’étiquette de mise à jour vous déployez (mises à jour, mises à jour critiques, mises à jour, mettre à jour les sélections multiples ou Service Packs). Cliquez sur **suivant** lorsque vous avez terminé.

4.  Dans la page **Configuration requise** de l’Assistant, sélectionnez l’architecture (32 bits, 64 bits ou les deux) et les systèmes d’exploitation des ordinateurs gérés à laquelle cette mise à jour seront applicable.

5.  Dans la page **règles de détection** , spécifiez comment Intune détermine si la mise à jour existe déjà sur les ordinateurs gérés. Si vous utilisez l’option par défaut, **Utilisez les règles de détection par défaut**, Intune toujours installe le package de mise à jour sur chaque ordinateur cible une seule fois.

    > [!NOTE]
    > Si le fichier que vous avez spécifié d’installation de la mise à jour est un programme d’installation de Windows ou un fichier .msp la page **règles de détection** de l’Assistant n’apparaît pas. C’est parce que les fichiers Windows Installer et .msp contiennent leurs propre instructions pour détecter les installations précédentes mise à jour.

    Sélectionnez une ou plusieurs des règles suivantes pour déterminer si la mise à jour est déjà installée sur les ordinateurs gérés :

    -   **Fichier existe**

    -   **Code de produit MSI existe**

    -   **Clé de Registre existe**

6.  Fournir des informations qui sont nécessaire pour configurer la règle de détection comme un chemin d’accès et nom, code de produit Windows Installer ou une clé de Registre tout supplémentaires, puis choisissez **suivant**.

7.  Dans la page **Configuration requise** de l’Assistant, vous spécifiez un logiciel doit déjà être installé pour pouvoir installer cette mise à jour. Vous pouvez spécifier **Aucun**, sélectionnez un logiciel qui a déjà été ajouté au et est géré par Intune, ou vous pouvez spécifier l’une des règles suivantes pour décrire le logiciel :

    -   **Fichier existe**

    -   **Code de produit MSI existe**

    -   **Clé de Registre existe**

8.  Fournir des informations qui sont nécessaire pour configurer la règle de détection comme un chemin d’accès et nom, code de produit Windows Installer ou une clé de Registre tout supplémentaires, puis choisissez **suivant**.

9. Dans la page **des arguments de ligne de commande** de l’Assistant, vous pouvez ajouter toutes les propriétés d’installation nécessaires à la ligne de commande d’installation pour modifier le comportement du fichier de configuration. Par exemple, certains logiciels prend en charge la **propriété/q** pour activer l’installation en mode silencieux. Consultez la documentation de votre logiciel pour en savoir plus sur les arguments de ligne de commande pris en charge. Spécifier des arguments de ligne de commande vous avez besoin, puis sélectionnez **suivant**.

    > [!NOTE]
    > Si la mise à jour ne prend pas en charge installation en mode silencieux, vous ne pouvez pas installer la mise à jour à l’aide Intune

10. Dans la page de **codes de retour** de l’Assistant, vous pouvez spécifier comment codes retour à partir de la mise à jour installation sont interprétés. Par défaut, Intune utilise des codes retour normalisé pour signaler une installation réussie ou non d’un package de mise à jour. Les codes de retour fournis sont :

|Code de retour|Plus d’informations|
|---------------|------------------|
|**0**|Opération réussie|
|**3010**|Redémarrer le succès|

11. Tout code retour qui n’est pas répertorié est considéré comme un échec.
Certaines mises à jour utilisent interprétation non standard pour les codes de retour. Dans ce cas, vous pouvez spécifier vos propres interprétation du code de retour.

12. Spécifier ou modifier les codes de retour nécessaires, puis choisissez **suivant**.

13. Dans la page de **Résumé** de l’Assistant, passez en revue les actions qui s’affichera, puis cliquez sur **Télécharger** pour terminer l’Assistant.

La mise à jour téléchargée est stockée dans votre espace de stockage cloud Intune. Si vous avez manque d’espace libre pour télécharger le package de mise à jour, vous êtes averti de ce au cours du processus de téléchargement. Intune ne peut pas déterminer suffisamment d’espace libre jusqu'à une fois que le téléchargement de la mise à jour a déjà commencé, car compressé le programme d’installation et de fichiers d’installation nécessitent davantage d’espace lorsqu’elles sont compressées.

Après son téléchargement en Intune, une mise à jour de tiers s’affiche dans l’espace de travail **met à jour** dans le volet **Toutes les mises à jour** . Vous pouvez ensuite approuver et déployer la mise à jour. Pour plus d’informations, consultez la section « approuver et refuser mises à jour » ci-dessous.

## Approuver et refuser des mises à jour
Lorsque les mises à jour sont prêtes à être installées, un message s’affiche dans la page **Vue d’ensemble des mises à jour** de l’espace de travail **mises à jour** , sous **État de la mise à jour**. Cliquez sur ce message pour ouvrir la page de **Toutes les mises à jour** pour afficher les mises à jour sont prêts pour approbation.

Vous pouvez utiliser la liste de **filtres** pour faciliter leur rechercher des mises à jour. Par exemple, vous pouvez afficher uniquement les mises à jour qui a échoué ou mises à jour qui ont été remplacés.

Lorsque vous sélectionnez une mise à jour dans la liste, d’autres commandes sont disponibles qui vous permettent de gérer les mises à jour comme indiqué dans le tableau suivant :

|Tâche|Plus d’informations|
|--------|--------------------|
|**Afficher les propriétés**|Affiche des informations détaillées sur la mise à jour, y compris le nombre d’ordinateurs auxquels elle s’applique.|
|**Modifier**|Pour Microsoft non mises à jour uniquement. Vous permet de modifier les propriétés de la mise à jour.|
|**Approuver**|Approuve la mise à jour sélectionné et permet de vous permettent de configurer les groupes est sera déployée sur. Pour plus d’informations, consultez la procédure **d’approuver des mises à jour** dans cette rubrique.|
|**Refuser**|Supprime les approbations précédente pour la mise à jour et masque la mise à jour des vues par défaut. En outre, les données du rapport pour la mise à jour sont été supprimées.<br /><br />Si vous souhaitez ultérieurement localiser une mise à jour refusée, définissez le filtre dans la page de **Toutes les mises à jour** comme **refusé**. Vous pouvez ensuite approuver cette mise à jour si nécessaire.<br /><br />Si une mise à jour a été refusée parce que la mise à jour a expiré dans Microsoft Update, cette mise à jour ne peut pas être approuvé dans la console d’administration Intune.<br /><br />Si vous supprimez une stratégie de mises à jour qui est déployée sur les ordinateurs, les valeurs de ces mises à jour des paramètres de stratégie sont réinitialisés à l’état par défaut pour le système d’exploitation est installé sur les ordinateurs.|
|**Supprimer**|Pour Microsoft non mises à jour uniquement. Supprime la mise à jour sélectionné.|
|**Télécharger**|Démarre l’Assistant de **Télécharger une mise à jour** qui vous permet de télécharger des mises à jour non Microsoft que vous voulez déployer.|

### Approuver des mises à jour

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), sélectionnez **mises à jour** &gt; **vue d’ensemble** &gt; **nouvelles mises à jour à approuver**.

    Dans l’espace de travail **mises à jour** , choisissez **Aperçu** &gt; **nouvelles mises à jour à approuver**.

    > [!NOTE]
    > Le lien de **nouvelles mises à jour pour approuver** apparaît dans la zone **d’État de mises à jour** uniquement lorsqu’il y a au moins un ordinateur géré qui nécessite une mise à jour doit être approuvé.

2.  Sélectionnez une mise à jour, passez en revue les propriétés de mise à jour en bas de la page pour vous assurer que vous voulez approuver la mise à jour, puis cliquez sur **Approuver**. Vous pouvez sélectionner plusieurs mises à jour en maintenant la touche **CTRL** enfoncée lorsque vous sélectionnez chaque élément.

3.  Dans la page **Sélectionner des groupes** , sélectionnez un groupe que vous voulez déployer les mises à jour, puis **Ajouter**. Lorsque vous avez terminé de spécifier des groupes, cliquez sur **suivant**.

4.  Dans la page **Action de déploiement** , procédez comme suit pour chaque groupe dans la liste :

    -   Dans la liste **d’approbation** , sélectionnez une des opérations suivantes :

        -   **Installer obligatoire** - installe la mise à jour sur les ordinateurs dans le groupe spécifié.

        -   **N’installez pas** - application uniquement des rapports et n’installe pas la mise à jour.

        -   **Installer disponible** – l’utilisateur peut installer l’application à la demande à partir du portail d’entreprise.

        -   **Désinstaller** - supprime les mises à jour à partir d’ordinateurs dans le groupe ciblé.

            > [!IMPORTANT]
            > La mise à jour est supprimé même si elle n’a pas été installé par Intune.

    -   Dans la liste **échéance** , sélectionnez une des opérations suivantes :

        -   **Aucun** : indique qu’aucune échéance n’est appliquée pour l’installation de la mise à jour et les utilisateurs peuvent se dégrader la mise à jour en permanence.

        -   **Dès que possible** - installe la mise à jour à la prochaine occasion sur les ordinateurs cibles.

        -   **Personnalisé** - spécifie la date et l’heure auxquelles approuvé mises à jour sont installés.

        -   **Une semaine**, **deux semaines**, **un mois** – installe la mise à jour au sein de la période spécifiée.

5.  Cliquez sur **Terminer** pour enregistrer les paramètres ou sur **Annuler** pour annuler les paramètres et revenir à la liste des mises à jour.

    > [!IMPORTANT]
    > À moins que l’action **N’installez pas**, **Obligatoire installer**ou **désinstaller** a été explicitement configurée pour un groupe enfant, une action configurée pour un groupe parent est héritée par tous ses enfants.

6.  Vous pouvez vérifier le volet de détails en bas de la page de **Toutes les mises à jour** des messages de rappel relatifs à la mise à jour.


### Voir aussi
[Stratégies pour protéger des PC Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)
