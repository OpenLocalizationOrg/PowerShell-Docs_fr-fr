---
title: "Planifier vos groupes d’utilisateurs et des périphériques | Microsoft Intune"
description: "Planifier les groupes pour répondre aux besoins de votre organisation."
keywords: 
author: sanchusa
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356
ms.reviewer: lpatha
ms.suite: ems
ms.openlocfilehash: dc76ed0c368f616f8533c42b298f40bd18b22fce
ms.sourcegitcommit: b7f116805520a34e657d15ad324d50e60218e658
translationtype: MT
---
# Planifier vos groupes d’utilisateurs et des périphériques
Groupes dans Intune vous offrent une grande flexibilité lorsque vous gérez vos périphériques et des utilisateurs. Vous pouvez définir des groupes en fonction des besoins de votre organisation en fonction de :

- emplacement géographique
- département
- caractéristiques matérielles
- Système d'exploitation
- Si le périphérique est appartenant à l’utilisateur ou appartenant à la société


## Comment fonctionnent les groupes Intune


Il s’agit de l’affichage par défaut du nœud **groupes** dans la console d’administration Intune :

![Capture d’écran de l’affichage par défaut du nœud groupes dans la console Intune](../media/Intune_Planning_Groups_Default_small.png)

Stratégies sont déployés à des groupes, afin de la hiérarchie de groupe est un des vos éléments de conception clés. Il est important de savoir que vous ne pouvez pas modifier groupe parent d’un groupe une fois que vous avez créé le groupe. La création de vos groupes est essentiel dès que vous commencez à utiliser le service Intune. Certains recommandé recommandées pour concevoir une hiérarchie de groupe en fonction des besoins de votre organisation sont décrites ici.

## Règles de l’appartenance aux groupes

- Un groupe peut contenir des utilisateurs ou appareils, mais pas les deux.

    * **Groupes de périphériques**. Cela inclut les ordinateurs et appareils mobiles. Avant de pouvoir ajouter un ordinateur à un groupe, il doit être inscrit. Avant de pouvoir ajouter un appareil mobile à un groupe, votre environnement doit être configuré pour prendre en charge des appareils mobiles et le périphérique doit être inscrits ou découvertes dans Exchange ActiveSync.

    * **Les groupes d’utilisateurs**. Un groupe peut avoir des utilisateurs à partir de groupes de sécurité. Synchronisation de groupes de sécurité avec votre instance d’Active Directory. Si vous ne pas synchroniser avec Active Directory, vous pouvez créer manuellement ces groupes.

- Un périphérique ou un utilisateur peut appartenir à plusieurs groupes.

- Un groupe d’inclure et exclure les membres en fonction des règles d’appartenance suivants :

    * **L’appartenance aux critères**. Il s’agit de règles dynamiques Intune s’exécute pour inclure ou exclure les membres. Ces critères utilisent des groupes de sécurité et autres informations synchronisées avec votre instance locale d’Active Directory. Lorsque le groupe de sécurité ou les données change, l’appartenance aux groupes change lors de la synchronisation avec Active Directory.

    * **L’appartenance directes**. Il s’agit de règles statiques qui explicitement ajouter ou exclure les membres. La liste d’appartenance est statique.

-   Services de domaine Active Directory (AD DS) n’est pas nécessaire lors de la création de groupes d’utilisateurs ou groupes de périphériques qui incluent des utilisateurs ou des ordinateurs. Mais, pour les groupes de périphériques inclure les appareils mobiles, votre environnement doit être configuré pour prendre en charge des appareils mobiles.

    En outre, les appareils doivent être découvert et ajoutés au Intune.

## Règles de relation de groupe

- Chaque groupe que vous créez peut comporter qu’un groupe parent. Vous ne pouvez pas modifier le groupe parent d’un groupe une fois que vous avez créé le groupe.

- Lorsque vous ajoutez des utilisateurs ou les périphériques à un groupe enfant :

    * Le groupe enfant est toujours un sous-ensemble du groupe parent.

    * Nouveaux membres que vous ajoutez à un groupe enfant sont automatiquement ajoutés au groupe parent de ce groupe.

    * Vous ne pouvez pas ajouter un membre à un groupe enfant lorsque ce membre est exclu du groupe parent.

- L’appartenance d’un groupe parent définit l’appartenance disponible pour le groupe enfant.

- Lorsque vous supprimez un groupe parent, tous les groupes enfants sont supprimés.

- Vous pouvez déployer du contenu et les stratégies d’un groupe parent, mais exclure le déploiement aux groupes enfants.

- Vous pouvez ajouter un utilisateur spécifique ou un périphérique à un groupe enfant si l’utilisateur ou l’appareil n’est pas déjà un membre du groupe parent. Si vous procédez ainsi, le nouveau membre du groupe enfant est ajouté au groupe parent.

    Toutefois, vous ne pouvez pas ajouter un membre à un groupe enfant si le membre est exclu du groupe parent.

- L’appartenance aux groupes est récurrent. Par exemple :

    * **Patrick** est membre du groupe qu’une seule, le groupe de sécurité des **Utilisateurs d’ordinateurs portables** .

    * Le groupe **d’Utilisateurs d’ordinateurs portables** est membre du groupe de sécurité **Utilisateurs approuvé** .

    * Vous créez un groupe dans Intune qui utilise une requête appartenance dynamique qui inclut les membres du groupe **d’Utilisateurs approuvé** . Le résultat est que votre groupe d’utilisateurs Intune inclut **Patrick**.

> [!TIP]
> Lorsque vous créez des groupes, pensez à la façon dont vous voulez appliquer la stratégie. Par exemple, vous devrez stratégies qui sont spécifiques aux systèmes d’exploitation de périphérique, ou stratégies qui sont spécifiques aux différents rôles ou les unités organisationnelles que vous avez déjà définis dans votre service d’annuaire Active Directory. Certains administrateurs s’avérer utile pour créer des groupes de périphériques spécifiques pour iOS, Android et Windows. Il s’agit en plus de la création de groupes d’utilisateurs pour chaque rôle d’organisation.

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your organization. Then, you create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful when you name your policies, so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy, you'll want to communicate it to your users. After you create the more general groups and policies, pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## Groupes prédéfinis
Intune comporte neuf groupes prédéfinis que vous ne pouvez pas modifier ou supprimer : <!--maybe a screen shot would be best?-->

-   **Tous les utilisateurs**
    -   Utilisateurs dissociées
-   **Tous les périphériques**
    -   Tous les ordinateurs
    -   Tous les appareils mobiles
        -   Tous les périphériques gérées directes
        -   Tous les Exchange ActiveSync périphériques gérés
    -   Tous les périphériques appartenant à l’entreprise
    -   Appareils dissociées

> [!NOTE]
> Laissez à votre slogan : *Restez simple*. Si votre organisation n’a pas de besoins spécifiques, tels que ceux décrits dans les sections suivantes, conserver simples et accédez à la structure de groupe par défaut et les stratégies. Cette option permettra que le service plus facile à gérer à long terme. Maintenance sera plus facile si vous pouvez considérer uniformément vos utilisateurs. Avec peu de différencier par groupe, vous aurez moins stratégies pour mettre à jour.


### Tous les utilisateurs et périphériques de votre organisation
Définir un groupe parent pour tous les utilisateurs et périphériques de votre organisation. Vous êtes susceptible d’avoir des stratégies qui seront appliquent à tous. Vous pouvez utiliser les groupes Intune par défaut **Tous les utilisateurs** et **tous les périphériques** à cet effet. Sous-groupes qui organiser les appareils par caractéristiques de l’objet, comme un groupe pour mettre votre propre périphérique (BYOD) et une pour périphériques (co-création) appartenant à l’entreprise, peuvent être des groupes enfants des groupes parent **Tous les utilisateurs** et **tous les périphériques** .

## Personnaliser des groupes pour votre organisation

### BYOD et périphériques appartenant à l’entreprise
Si votre organisation permet aux employés d’utiliser leurs propres périphériques, fournit aux périphériques de société propriétaire ou dispose d’une combinaison des deux, nous vous recommandons d’appliquer des stratégies distinctes pour ces catégories d’appareils.

Dans le cas de BYOD ou un mélange, en veillant à ne planifier les stratégies ne pas enfreint sur réglementations locales sur la confidentialité. Créer un groupe parent pour tous les utilisateurs qui recevra leurs propres périphériques. Vous pouvez utiliser ce groupe pour appliquer des stratégies qui s’appliquent à tous les utilisateurs de cette catégorie.

![Création d’un groupe parent BYOD](../media/Intune_Planning_Groups_BYOD_small.png)

De même, vous pouvez créer un groupe pour la co-création les utilisateurs d’appareils de votre organisation :

![Groupes d’utilisateurs frères pour les périphériques de co-création et BYOD](../media/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### Groupes de régions géographiques
Si votre organisation a besoin de stratégies pour des régions spécifiques, vous pouvez créer des groupes en fonction de région géographique. Vous pouvez baser sur groupes régionaux que vous avez peut-être déjà créé dans l’instance d’Active Directory, et les synchroniser avec votre service d’Azure Active Directory. Vous pouvez également créer des groupes régionaux directement dans Azure Active Directory.

Les captures d’écran suivantes vous montrent comment créer des groupes Intune basées sur les groupes synchronisées avec votre instance Active Directory local. Ces exemples part du principe que vous disposez d’un groupe de sécurité Active Directory appelé **Groupe utilisateurs US**.

Tout d’abord, fournissent des informations générales.

![Capture d’écran de la zone de groupe Édition](../media/Intune_Planning_Groups_AD_General_small.png)

Sous **critères d’appartenance**, sélectionnez le **Groupe d’utilisateurs US**, synchronisées avec Active Directory, comme le groupe de sécurité à utiliser sous règles d’adhésion.

![Capture d’écran de la boîte de dialogue Modifier le groupe](../media/Intune_Planning_Groups_AD_Criteria_small.png)

Passez en revue vos entrées et puis cliquez sur **Terminer** pour créer le groupe.

![Capture d’écran de la boîte de dialogue Modifier le groupe](../media/Intune_Planning_Groups_AD_Summary_small.png)

Dans notre exemple, nous avons également créé un groupe appelé **MEA**, pour le Moyen Orient et l’Asie.

> [!NOTE]
> Si l’appartenance au groupe n’est pas remplie en fonction de l’appartenance au groupe de sécurité, vérifiez que vous avez attribué les licences de Intune aux membres du groupe.

### Groupes pour le matériel spécifique
Si votre organisation exige stratégies qui s’appliquent aux types de matériel spécifiques, vous pouvez créer des groupes en fonction de cette exigence. Vous pouvez baser les stratégies sur des groupes spécifiques que vous avez déjà créé dans votre instance locale d’Active Directory et puis les synchroniser avec Azure Active Directory. Vous pouvez également créer des groupes directement dans Azure Active Directory. Dans cet exemple, nous utilisons **US utilisateurs groupe** en tant que groupe parent pour le groupe **d’Utilisateurs d’ordinateurs portables** .

![Boîte de dialogue Sélectionner un groupe de sécurité](../media/Intune_Planning_Groups_Laptop_small.png)

À ce stade, hiérarchie de votre groupe doit ressembler à la capture d’écran suivante. Vous pouvez voir qu’il existe désormais membres dans le groupe Intune **Utilisateurs d’ordinateurs portables**. Les stratégies appliquées à ce groupe seront appliquées aux utilisateurs d’ordinateurs portables BYOD provenant de la région US.

![Affichage du groupe d’utilisateurs d’ordinateurs portables](../media/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### Groupes pour les systèmes d’exploitation spécifiques
Si votre organisation exige stratégies qui s’appliquent aux systèmes d’exploitation spécifiques, comme Windows, iOS ou Android, vous pouvez créer des groupes en fonction de cette exigence. Comme dans les exemples précédents, vous pouvez baser sur des groupes spécifiques du système d’exploitation que vous avez déjà créé dans votre instance locale d’Active Directory et les synchroniser avec Azure Active Directory. Vous pouvez également créer les directement dans votre instance d’Azure Active Directory.

En utilisant la méthode même à partir des exemples précédents, vous pouvez créer des groupes basées sur les utilisateurs <!--devices?--> qui utilisent les plateformes de système d’exploitation spécifique.

> [!NOTE]
> Si vous avez des utilisateurs qui utilisent plusieurs plateformes mobiles ou systèmes d’exploitation et vous n’avez pas d’une façon automatisée pour classer les utilisateurs en tant que les utilisateurs Android, les utilisateurs iOS ou Windows, vous pouvez appliquer des stratégies au niveau du périphérique. Cela vous offre davantage de flexibilité pour appliquer des stratégies spécifiques à un système d’exploitation.
>
> Vous ne pouvez pas mise en service de groupes de façon dynamique en fonction du système d’exploitation du périphérique. Au lieu de cela, procédez comme suit à l’aide de groupes de sécurité Active Directory ou Azure Active Directory.

![Groupe d’utilisateurs de portable](../media/Intune_Planning_Groups_OS_Hierachy_small.png)

Une fois tous les de vos utilisateurs groupes sont remplis selon vos besoins d’organisation, votre hiérarchie de groupe doit ressembler à ceci :

![Affichage de hiérarchie de groupe](../media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

Vous pouvez utiliser cette hiérarchie pour appliquer des stratégies de l’organisation.

### Groupes de périphériques
Vous pouvez également créer des groupes similaires pour les appareils comme illustré ici, en commençant par un groupe large qui inclut tous les périphériques appartenant à l’employé, pour le scénario BYOD.

![Boîte de dialogue Créer un groupe](../media/Intune_Planning_Groups_Device_General_small.png)

Assurez-vous de sélectionner **tous les périphériques (ordinateurs et mobile)** afin que le groupe doit inclure tous les périphériques BYO :

![Définir l’appartenance aux critères page](../media/Intune_Planning_Groups_Device_Criteria_small.png)

Passez en revue vos entrées et puis cliquez sur **Terminer** pour créer le groupe BYOD.

![Boîte de dialogue Créer un groupe](../media/Intune_Planning_Groups_Device_Summary_small.png)

Continuez à créer des groupes de périphériques jusqu'à ce que vous possédez une hiérarchie de groupe appareil qui est similaire à la hiérarchie du groupe utilisateur. Le nœud de votre groupe dans la console Intune doit se présenter comme suit :

![Affichage de hiérarchie de groupes Intune](../media/Intune_Groups_Hierarchy_Final_Small.png)

## Hiérarchies de groupes et des conventions
Pour faciliter la gestion de la stratégie, nous vous recommandons de que vous nommez chaque stratégie en fonction de l’objectif, la plateforme et l’étendue à laquelle vous appliquez. Utiliser une norme d’appellation qui suit la structure du groupe que vous avez créé lors de la préparation appliquer vos stratégies.

Par exemple, pour une stratégie Android qui s’applique à tous les périphériques d’entreprise, Android, mobiles au niveau régional américain, vous pouvez nommer la stratégie **CO_US_Mob_Android_General**.

![Créer des stratégies pour Android](../media/Intune_planning_policy_android_small.png)

Lorsque vous nommez vos stratégies de cette façon, vous pouvez rapidement identifier les stratégies et leur utilisation prévue et étendue dans le nœud de **stratégies** , comme suit :

![Liste des stratégies Intune](../media/Intune_planning_policy_view_small.png)

## Étapes suivantes
[Créer des groupes](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)
