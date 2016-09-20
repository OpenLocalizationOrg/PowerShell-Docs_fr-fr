---
title: "Utiliser des groupes pour gérer les utilisateurs et dispositifs | Microsoft Intune"
description: "Créer et gérer des groupes à l’aide de l’espace de travail de groupes."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb9b01ce-9b9b-4c2a-bf99-3879c0bdaba5
ms.reviewer: lpatha
ms.suite: ems
ms.openlocfilehash: 76b8ab90974dc258992ed8c660a04fc08872a4ec
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# Utiliser des groupes pour gérer les utilisateurs et dispositifs dans Microsoft Intune

Cette rubrique explique comment créer des groupes dans Intune. Il fournit également des informations sur la façon dont la gestion des groupes va agir en pour modifier le mois à venir. 

>[!IMPORTANT]
>
>Si vous ouvrez l’espace de travail groupes dans le portail Intune et un lien vers le portail Azure active directory (AD Azure), puis vous utilisez déjà la *nouvelle* Azure AD sécurité groupes approche gestion d’un groupe dans Intune, décrites dans la [communication des améliorations apportées à venir à l’expérience d’administration pour les groupes](#notice-of-upcoming-improvements-to-the-admin-experience-for-groups). Cliquez sur le lien vers le portail Azure AD pour créer et gérer vos groupes. Pour apprendre à utiliser des groupes de sécurité Azure AD, reportez-vous à [gestion de l’accès aux ressources des groupes de Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/).
>
>Si vous ne voyez pas le lien vers le portail Azure AD, vous utilisez toujours l’approche *actuelle* de gestion du groupe, décrite dans [créer des groupes pour gérer les utilisateurs et dispositifs avec Microsoft Intune](#Create-groups-to-manage-users-and-devices-with-Microsoft-Intune) dans cette rubrique.


## Notification des améliorations apportées à venir à l’expérience d’administration pour les groupes

Vous avez nous indiquer que vous souhaitez un regroupement et un ciblage expérience entre mobilité d’entreprise + sécurité. Nous vous entendre. En fonction de vos commentaires, plus tôt nous continuer à convertir groupes Intune aux groupes de sécurité basées sur Azure Active Directory. Cette modification unifiera gestion de groupe entre Intune et Azure Active Directory (AD Azure). La nouvelle expérience signifie que vous ne devez dupliquer des groupes entre les services. Il également fournira extensibilité via les options à utiliser Windows PowerShell et Microsoft Graph.

### Comment cela affecte-t-il m’intéresser ?
Cette modification n’affecte pas vous maintenant. Mais voici ce qui se passe :

-   Dans septembre 2016, nouveaux comptes qui sont mis en service après la publication de service mensuel utilisera les groupes de sécurité Azure AD au lieu de groupes d’utilisateurs Intune.   
-   Dans octobre 2016, nouveaux comptes qui sont mis en service après la publication de service mensuel gérer les groupes basés sur des utilisateurs et groupes basés sur un appareil dans le portail Azure AD. Il n’y a aucun effet sur les clients existants.
-   Dans novembre 2016, l’équipe du produit Intune commenceront à migrer les clients existants vers la nouvelle expérience de gestion des groupes Azure AD. Tous les groupes d’utilisateurs et des périphériques présents dans Intune aujourd'hui vont être migrées aux groupes de sécurité Azure AD. Nous effectuera la migration par lots démarrage dans novembre 2016. Nous ne démarre pas migrations jusqu'à ce que nous pouvons réduire aucun effet sur votre travail au quotidien, et quand nous prévoyons il n’y ait aucun effet sur vos utilisateurs. Nous avons également vous donne Notez avant que nous migrer votre compte.


### Quand et comment sera migrer vers la nouvelle expérience groupes ?
Nous allons migrer les clients Intune actuels sur une période donnée. Nous sommes Finalisation de la planification pour que la migration et met à jour cette rubrique dans quelques semaines pour obtenir des informations plus détaillées. Nous allons vous donner Notez avant de vous sont migrés. Si vous avez des problèmes de migration, veuillez contacter notre équipe de migration à <intunegrps@microsoft.com>.

### Que se passe-t-il à mon utilisateur existant et des groupes de l’appareil ?
 Groupes d’utilisateurs et groupes appareil que vous avez créés dans Intune migrent vers les groupes de sécurité Azure AD. Groupes Intune par défaut, tels que le groupe tous les utilisateurs, migrent uniquement si vous les utilisez dans les déploiements au moment de la migration. Migration peut être plus complexe pour des groupes. Vous serez averti si des étapes supplémentaires sont nécessaires pour la migration de votre organisation.

### Les nouvelles fonctionnalités seront disponibles pour moi ?
Voici les nouvelles fonctionnalités, que nous allons présenter avec cette migration de Intune vers Azure Active Directory :

-    Groupes de sécurité Azure AD seront pris en charge dans Intune pour tous les types de déploiements.
-    Groupes de sécurité Azure AD prend en charge le regroupement des périphériques et des utilisateurs.
-    Groupes de sécurité Azure AD prend en charge les groupes dynamiques qui ont des attributs de périphérique Intune. Par exemple, vous pourrez dynamiquement les périphériques de groupe par plateforme, comme iOS. Lorsqu’un nouvel appareil iOS inscrit dans votre organisation, il automatiquement est ajouté au groupe dynamique appareil iOS.
-    Avoir une expérience d’administration partagée pour la gestion de groupe entre Azure AD et Intune.
- Le rôle d’administrateur de Service Intune est ajouté à Azure AD afin que les administrateurs de service Intune peuvent effectuer des tâches de gestion de groupe dans Azure AD.

### Quelles sont les fonctionnalités Intune ne seront pas disponible ?
Bien que contribue à améliorer l’expérience de groupes, il y ait quelques fonctionnalités Intune qui ne sont pas disponibles une fois que votre organisation migre à partir de groupes Intune aux groupes de sécurité Azure AD.

#### Fonctionnalités de gestion de groupe

-   Après la migration, vous ne pourrez exclure des membres ou des groupes lorsque vous créez un nouveau groupe. Toutefois, avec les groupes dynamiques Azure AD, vous pouvez utiliser attributs pour créer des règles avancées que vous pouvez utiliser pour exclure les membres d’un groupe en fonction de critères que vous avez défini.
-   Groupes d’utilisateurs et dispositifs dissociée dissociées ne sont pas pris en charge. Nous n'allons pas migrer les groupes de Intune à Azure Active Directory.


#### Fonctionnalités dépendant du groupe

-   Le rôle d’administrateur de Service n’ont pas les autorisations de **Gérer les groupes** .
-   Vous ne pourrez pour regrouper les périphériques Exchange ActiveSync. Votre groupe de tous les périphériques gérés EAS est converti à partir d’un groupe à un affichage rapport.
-  Glissement des groupes dans les rapports ne sera pas disponible.
-  Groupe personnalisé ciblage de règles de notification ne sera pas disponible.

### Que dois-je faire pour préparer à cette modification ?
 Nous avons créé des recommandations qui vous faciliteront cette transition pour vous :

- Nettoyer les groupes Intune toute modification indésirables ou inutiles avant la migration.
- Évaluez votre utilisation d’exclusion dans les groupes et envisager de modifier vos groupes de sorte que vous n’avez pas besoin d’utiliser d’exclusion.
-  Si vous avez les administrateurs qui ne possèdent pas les autorisations nécessaires pour créer des groupes dans Azure AD, demandez à votre administrateur Azure AD pour les ajouter à l’administrateur de Service Intune rôle Azure AD.


## Créer des groupes pour gérer les utilisateurs et dispositifs avec Microsoft Intune

Cette section décrit comment créer des groupes Intune dans la console d’administration Intune.

Vous pouvez créer et gérer des groupes dans l’espace de travail **groupes** dans la console d’administration Microsoft Intune. La page **Vue d’ensemble de groupes** affiche synthèses d’état qui peuvent vous aider à identifient et hiérarchiser les problèmes qui nécessitent votre attention. Synthèses d’état couvrent ces domaines :

-   Alertes
-   Mises à jour logicielles
-   Endpoint Protection
-   Stratégie
-   Gestion des logiciels

Votre hiérarchie groupe présente également synthèses d’état pour vous aider à identifier et résoudre les problèmes pour les membres d’un groupe sélectionné.

## Créer des groupes

> [!TIP]
> Lorsque vous créez des groupes, envisagez comment appliquer les stratégies. Par exemple, vous devrez stratégies qui sont spécifiques à un système d’exploitation de périphérique et qui sont spécifiques aux différents rôles dans votre organisation, ou pour les unités organisationnelles que vous avez déjà défini dans Active Directory. Il peut être utile d’avoir des groupes de périphériques distincts pour iOS, Android et Windows, ainsi qu’un groupe d’utilisateurs pour chaque rôle d’organisation.
>
> Vous devrez probablement que vous voulez également créer une stratégie par défaut qui s’applique à tous les groupes et appareils, pour définir les exigences de conformité base de votre organisation. Ensuite, vous pouvez créer des stratégies plus spécifiques pour les catégories plus grand nombre d’utilisateurs et dispositifs. Par exemple, vous pouvez créer des stratégies de messagerie pour chacun des systèmes d’exploitation appareil.
>
> En veillant à ne lorsque vous nommez vos stratégies de sorte que vous pouvez facilement identifier ultérieurement. Par exemple, un nom de bonne stratégie descriptif est **Stratégie de messagerie WP pour toute entreprise**.
>
> Chaque fois que vous créez une stratégie restrictive, vous souhaiterez communiquer à vos utilisateurs. Après avoir créé les groupes et les stratégies plus générale, faites attention aux comment créer plus petits groupes, afin que vous pouvez encore réduire communication superflus.

### Pour créer un groupe de périphériques

1.  Dans la console d’administration Intune, choisissez **groupes** &gt; **vue d’ensemble** &gt; **Créer un groupe**.

2.  Entrez un nom et une description (facultative) pour le groupe et sélectionnez un groupe de périphériques en tant que groupe parent. Cliquez sur **suivant**.

3.  Dans la page **Définir l’appartenance aux critères** , sélectionnez le type d’unités à inclure dans le groupe. Vous disposez des options de configuration groupe supplémentaire basées sur les types d’appareils que vous choisissez d’inclure :

    -   **Ordinateur**. Indiquez si vous souhaitez inclure tous les membres du groupe parent ; les unités d’organisation que vous souhaitez inclure ou exclure ; et domaines que vous voulez inclure ou exclure. Vous pouvez obtenir des informations unité et le domaine d’organisation pour un ordinateur à partir de l’inventaire.

    -   **Mobile**. Sélectionnez s’il faut inclure les appareils mobiles qui sont gérés par Intune, les appareils mobiles qui sont gérés par Exchange ActiveSync, ou les deux.

    -   **Tous les périphériques**. Cette option inclut tous les périphériques, avec aucune exclusion basée sur n’importe quel critère.

4.  Dans la page **Définir l’appartenance directes** , cliquez sur **Parcourir** pour sélectionner des périphériques individuels pour inclure ou exclure. Si vous sélectionnez périphériques qui ne sont pas dans le groupe parent que vous avez spécifié, Intune ajoute automatiquement ces appareils au groupe parent.

5.  Dans la page de **Résumé** , passez en revue vos sélections et puis cliquez sur **Terminer**.

Le groupe nouvellement créé est présenté dans la liste **groupes** , dans l’espace de travail **groupes** , sous le groupe parent. C’est également l’endroit où vous pouvez modifier ou supprimer le groupe.

### Pour créer un groupe d’utilisateurs

1.  Dans la console d’administration Intune, choisissez **groupes** &gt; **vue d’ensemble** &gt; **Créer un groupe**.

2.  Entrez un nom et une description (facultative) pour le groupe et sélectionnez un groupe d’utilisateurs en tant que groupe parent. Cliquez sur **suivant**.

3.  Dans la page **Définir l’appartenance aux critères** , choisissez si vous souhaitez inclure tous les membres du groupe parent ou commencer avec un groupe vide. Ensuite, inclure ou exclure les membres basés sur les groupes de sécurité des utilisateurs que vous configurez dans le [Centre d’administration Office 365](http://go.microsoft.com/fwlink/?LinkId=698854), soit manuellement synchronisez depuis Active Directory. Si l’appartenance à un groupe de sécurité est modifiée, l’appartenance aux groupes d’utilisateurs en fonction de ce groupe de sécurité peut également changer.

    > [!IMPORTANT]
    > Pour l’instant, si votre groupe inclut les membres de groupes de sécurité spécifiques ou gestionnaire et vous permet d’exclure les membres à partir de certains groupes, les membres que vous avez inclus initiale sont été supprimés. Pour créer un groupe qui a inclus des membres et exclue membres, nous vous recommandons d’abord vous créez un groupe parent qui comporte les membres inclus. Ensuite, créez un groupe enfant pour le groupe parent. Dans le nouveau groupe enfant, répertorient les membres exclus. Ensuite, utilisez ce groupe enfant pour gérer les stratégies, les profils et la distribution de l’application Intune.

    > [!NOTE]
    > Dans le portail Azure, vous pouvez créer des groupes en fonction des responsables les utilisateurs signalent à. Ce type de groupe est dynamique, et elle ne change que les employés sont ajoutés ou supprimés à partir de l’équipe du responsable dans Azure Active Directory. Comment créer un groupe d’Azure basé sur le nom du responsable est décrite dans les [attributs à l’aide pour créer des règles avancées](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/), dans la section **pour configurer un groupe en groupe « Gestionnaire »**.

4.  Dans la page **Définir l’appartenance directes** , choisissez **Parcourir** pour sélectionner des utilisateurs individuels pour inclure ou exclure. Si vous sélectionnez les utilisateurs qui ne sont pas dans le groupe parent que vous avez spécifié, ceux-ci est automatiquement ajoutés au groupe parent. L’option Ajouter manuellement un utilisateur est en bas de la boîte de dialogue **Sélectionner les membres** . Cette opération est utile si vous voulez ajouter un utilisateur qui ne dispose pas encore d’un périphérique inscrit.

5.  Dans la page de **Résumé** , passez en revue vos sélections et puis cliquez sur **Terminer**.

Le groupe nouvellement créé est présenté dans la liste **groupes** , dans l’espace de travail **groupes** , sous le groupe parent. C’est également l’endroit où vous pouvez modifier ou supprimer le groupe.

> [!TIP]
> Groupes de sécurité sont une bonne ressource à utiliser lorsque vous remplissez les groupes d’utilisateurs. Étant donné que les groupes de sécurité définissent qui peut accéder à quelles ressources, groupes de sécurité peuvent traduire bien aux groupes d’utilisateurs Intune. Groupes de sécurité qui sont synchronisés à partir d’Active Directory à Azure Active Directory, ou que vous créez directement dans Azure Active Directory via le centre d’administration Office 365 ou le portail Azure sont disponibles pour pouvoir utiliser lorsque vous créez des groupes d’utilisateurs dans Intune.

## Filtrer les affichages d’administrateur par rôle
Dans les affichages de groupe filtré, vous pouvez personnaliser ce qu’un administrateur informatique peut afficher en fonction du rôle d’administrateur. Vous pouvez également limiter les groupes de chaque administrateur informatique peut gérer. Cela peut être utile lorsque :

-   Vous voulez que vos administrateurs informatiques puissent déployer des éléments uniquement sur les appareils mobiles et des utilisateurs spécifiques
-   Vous souhaitez que vos administrateurs informatiques pour afficher uniquement les groupes pertinents à cet administrateur

Vous pouvez configurer des affichages de groupe filtré pour les administrateurs de service dans la console d’administration Intune. Pour plus d’informations, voir [les éléments à connaître avant de commencer Intune Microsoft](/intune/get-started/what-to-know-before-you-start-microsoft-intune).

Après avoir configuré affichages pour un administrateur de service, le groupe filtré lors de l’administrateur déploie des logiciels ou des stratégies ou exécute des rapports, l’administrateur peut afficher et sélectionner uniquement les groupes que vous avez spécifié. L’administrateur n’également voit les informations d’état sur les pages suivantes de la console d’administration :

-   **Vue d’ensemble du système**
-   **Vue d’ensemble de groupes**
-   **Vue d’ensemble de la Protection de point de terminaison**
-   **Vue d’ensemble des alertes**
-   **Vue d’ensemble du logiciel**
-   **Présentation de la stratégie**

### Pour créer un affichage filtré groupe

1.  Dans la console d’administration Intune, choisissez **administrateur** &gt; **De l’administrateur gestion** &gt; **Les administrateurs de Service**.

2.  Sélectionnez l’administrateur de service que vous souhaitez créer un affichage de groupe filtré pour, puis **Gérer les groupes**.

3.  Dans la boîte de dialogue **Sélectionner les groupes qui sont visibles à cet administrateur de service** , ajoutez les groupes que l’administrateur de service seront en mesure d’accéder à, puis cliquez sur **OK**.

Une fois que vous avez configuré les vues groupe filtré, l’administrateur informatique sera en mesure d’afficher et sélectionner uniquement les groupes que vous avez indiquée.

## Gérer vos groupes
Après avoir créé vos groupes, vous pouvez continuer à gérer les besoins de votre organisation.

Vous pouvez modifier votre groupe pour modifier son nom ou la description, ou qui appartient au groupe.

Vous pouvez supprimer un groupe qui n’est plus gère les besoins de votre organisation. Suppression d’un groupe ne supprime pas les utilisateurs qui appartiennent à ce groupe.

## Étapes suivantes
Après avoir configuré vos groupes et des stratégies, passez en revue **Prévu une valeur** et **l’état** pour vérifier les implications pratiques de conception de votre.

### Pour vérifier votre conception

1. Sélectionnez n’importe quel appareil à partir d’un groupe de périphériques et parcourir les catégories d’informations en haut de la page.
2. Sélectionnez la **stratégie**. Vous verrez s’intitule cette capture d’écran de paramètres de stratégie d’un appareil Android.

![Exemple de stratégie paramètres Android](../media/Intune-Device-Policy-v.2.jpg)

Chaque stratégie a une **Valeur prévu** et un **état**. La valeur est ce que vous souhaitiez atteindre lorsque vous avez affecté la stratégie. L’état est ce que vous faire lorsque toutes les stratégies qui s’appliquent à l’appareil, ainsi que les restrictions et les conditions du matériel et du système d’exploitation sont considérés comme ensemble. Dans cette capture d’écran, vous pouvez voir deux exemples clairs :

-   **Autoriser les mots de passe simples** est défini sur **Oui**, comme indiqué dans la colonne **Valeur destiné** , mais son **statut** est **ne s’applique pas**. C’est parce que les mots de passe simples ne sont pas prises en charge pour les appareils Android.
-   De même, l’élément de stratégie étendue **des paramètres de messagerie pour les appareils iOS** n’est pas appliqué à cet appareil car il s’agit d’un appareil Android.

> [!NOTE]
> N’oubliez pas que lorsque deux stratégies que présentent différents niveaux de restriction s’appliquent à la même appareil utilisateur, la stratégie la plus restrictive s’applique dans la pratique.
