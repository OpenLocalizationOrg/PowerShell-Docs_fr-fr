---
title: Quelle est la nouvelle archive | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
ms.openlocfilehash: 3e5ca7345aef574446d437bac25bffc0c3414c68
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
## Le mois de décembre 2015
### Modifications et mises à jour de Microsoft application portail d’entreprise
Les modifications suivantes ont été apportées à l’application portail d’entreprise dans cette version.

**Application du portail d’entreprise Android**

Les modifications suivantes ont été apportées à nouveau aux exigences Google. Sur Android 6.0 et versions ultérieures appareils, deux nouveaux messages sont affichés aux utilisateurs :
* Autoriser le portail d’entreprise à émettre et gérer des appels téléphoniques ?
* Autoriser le portail d’entreprise pour accédez à des photos, multimédias et les fichiers sur votre appareil ?

Voir les tableaux suivants pour plus d’informations sur les deux messages.



Texte du message  |Autoriser le portail d’entreprise à émettre et gérer des appels téléphoniques ?  
---------|---------
Sens de message     |  Permet de numéro de téléphone de l’utilisateur appareil et IMEI à envoyer au service Intune et apparaissent dans la console d’administration dans la page matériel.   </br></br>**Remarque : L’application portail d’entreprise jamais rend ou gère les appels téléphoniques !** Le texte du message est contrôlé par Google et ne peuvent pas être modifié. </br></br>Pour afficher la page **matériel** , accédez à des **groupes** > **tous les appareils mobiles** > **appareil**s. Sélectionnez le périphérique de l’utilisateur, puis accédez à **Afficher les propriétés** > **matériel**.    
Quand et où message s’affiche  | Le message s’affiche lorsque les utilisateurs de se connecter à l’application portail d’entreprise pour la première fois démarrer s’inscrire leur appareil.|         
Que se passe-t-il si les utilisateurs autoriser l’accès  |  Numéro de téléphone et IMEI l’appareil seront affichent dans la page matériel dans la console d’administration. |         
Que se passe-t-il si les utilisateurs refusent l’accès     | Ils peuvent continuer à utiliser l’application portail d’entreprise et inscrire leur appareil, mais les utilisateurs numéro de téléphone appareil et IMEI sera vide dans la page matériel dans la console d’administration.       </br></br> La deuxième fois que les utilisateurs se connecter à l’application portail d’entreprise après refuser l’accès, le message affiche une case à cocher **ne jamais demander à nouveau** les utilisateurs peuvent sélectionner afin que le message affiche jamais à nouveau.</br></br>Si les utilisateurs autorisent mais puis ultérieurement refuser l’accès, le message s’affiche les prochaine fois qu’ils se connecter à l’application portail d’entreprise après l’inscription.</br></br>Si vous décidez plus tard autoriser l’accès aux utilisateurs, ils peuvent accédez à **paramètres** > **applications** > **Portail d’entreprise** > **autorisations** > **téléphone**, puis activer l’autorisation.
Plus d’informations     |  Pour vos utilisateurs : [se connecter à l’application portail d’entreprise](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_signin_cp)  </br></br>Pour les informaticiens : Les informations contenues dans ce tableau sont également aider [vos utilisateurs comprendre les messages de l’application portail d’entreprise](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)   

Texte du message  |Autoriser le portail d’entreprise pour accédez à des photos, multimédias et les fichiers sur votre appareil ?  
---------|---------
Sens de message     |  Active le périphérique écrire des journaux de données dans la carte SD du périphérique, qui permet des fichiers journaux à être déplacés à l’aide d’un câble USB.   </br></br>**Remarque : L’application portail d’entreprise accède à jamais photos, des médias et des fichiers utilisateurs !** Le texte du message est contrôlé par Google et ne peuvent pas être modifié.     
Quand et où message s’affiche  | Ce message s’affiche lorsque les utilisateurs appuyez sur **Envoyer des données** à envoyer les journaux de données à leur administrateur informatique.|         
Que se passe-t-il si les utilisateurs autoriser l’accès  |  Les journaux seront copiées vers la carte SD. |         
Que se passe-t-il si les utilisateurs refusent l’accès     | Vous pouvez toujours envoyer les journaux de données, mais les journaux ne soit copiés vers carte SD de l’appareil.       </br></br> La deuxième fois que les utilisateurs se connecter à l’application portail d’entreprise après refuser l’accès, le message affiche une case à cocher **ne jamais demander à nouveau** les utilisateurs peuvent sélectionner afin que le message affiche jamais à nouveau.</br></br>Si les utilisateurs autorisent mais puis ultérieurement refuser l’accès, le message s’affiche que les prochaine fois qu’ils tentent d’envoyer les journaux.</br></br>Si vous décidez plus tard autoriser l’accès aux utilisateurs, ils peuvent accédez à **paramètres** > **applications** > **Portail d’entreprise** > **autorisations** > **stockage**, puis activer l’autorisation.
Plus d’informations     |  Pour vos utilisateurs : [envoi des journaux de données de diagnostic à votre administrateur informatique par courrier électronique](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_send_diag_logs)  </br></br>Pour les informaticiens : Les informations contenues dans ce tableau sont également aider [vos utilisateurs comprendre les messages de l’application portail d’entreprise](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)   


**application portail d’entreprise iOS**
* Les utilisateurs peuvent désormais utiliser Microsoft Outlook ou autres applications de messagerie pour envoyer les journaux de diagnostic à l’administrateur informatique. Précédemment, uniquement l’application native peut être utilisée.
* Prise en charge a été améliorée pour appareil d’inscription programme (PED) et des générations d’entreprise inscrite d’Apple. Pour plus d’informations, voir [vous êtes invité à identifier votre appareil lorsque vous essayez d’inscription](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_id_your_device).
* Dans la liste des appareils inscrits, une coche verte apparaît maintenant en regard de l’appareil que l’utilisateur utilise actuellement. Avant que cette case à cocher a été ajoutée, les utilisateurs n’a pas pu savoir choisir un périphérique inscrit qu’ils utilisaient.

**Application du portail d’entreprise Windows**

Microsoft recueille automatiquement des données anonymes sur les performances et l’utilisation de l’application portail d’entreprise pour améliorer les produits et services Microsoft. Les utilisateurs finaux peut désactiver la collecte de données en utilisant le paramètre de données d’utilisation sur leur appareil, mais les administrateurs ont aucun contrôle sur la collecte de données et ne pouvez pas modifier la sélection de l’utilisateur final pour ce paramètre.



## Novembre 2015
### Gestion de l’application
Intune prend en charge les stratégies de gestion des (MAM) application mobile permettant d’empêcher les données d’entreprise divulgation des informations à des applications de consommateur ou services. Traditionnellement, ces politiques uniquement appliquera dans des applications mobiles en cours d’exécution sur les périphériques qui ont été inscrite également pour la gestion des appareils mobiles (MDM) en Intune.

Mise à jour de ce mois, Intune se développe ses capacités MAM aux nouvelles catégories de périphériques. En plus des périphériques inscrits dans Intune, vous pouvez maintenant appliquer des stratégies MAM sur :
* périphériques gérés par n’importe quel autre solution de gestion (MDM) appareil
* appareil qui ne sont pas inscrit dans n’importe quel système de gestion de périphérique, généralement mettre vos propres des appareils (BYO)

Vous trouverez plus d’informations sur ces nouvelles fonctionnalités MAM dans les billets de blog suivant :
* [Amélioration de la productivité mobile gérée](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)
* [Annonce des nouvelles fonctions Microsoft entreprise mobilité](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)

En outre, voici quelques mises en lumières et des informations supplémentaires sur les fonctionnalités MAM de Intune :
* Les données d’entreprise sont isolées à partir des données consommateur dans les applications compatibles pour Intune, y compris les applications Office Mobile, des applications tierces qui ont adopté l’Intune SDK ou applications métier encapsulées par Intune.
* Données de la société peuvent être partagé (**Couper/copier/coller**) parmi les applications d’entreprise, tout en évitant le partage de données de l’entreprise dans les applications personnelles. Pour plus d’informations, lisez [stratégies MAM comment protéger vos données d’application](https://technet.microsoft.com/library/mt627825.aspx) . Cet exemple, l' [application à l’aide de Microsoft Word pour le travail et les tâches personnelles](https://technet.microsoft.com/library/mt627827.aspx), montre comment le partage de données de la société dans applications personnelles ne peut pas.
* Enregistrer des stratégies de prévention perte de données clés comme code confidentiel, d’application-contrôles et entre les applications de partage de données gérées. Lecture [créer et déployer des stratégies de gestion de l’application mobile avec Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx) pour afficher la liste de toutes les stratégies.
* Word, Excel, PowerPoint, Outlook, OneNote et OneDrive entreprise ont tous ces nouvelles fonctionnalités et peuvent être gérés avec et sans inscription d’un appareil. Les fonctionnalités de protection de perte de données en mode natif intégrées dans les applications Office standards dans l’Apple Store ou Google Play store et ne nécessitent pas habillage application ou le chargement de version test.
* Pour découvrir comment procéder, voir [prise en main stratégies de gestion de l’application mobile dans le portail Azure](https://technet.microsoft.com/library/mt627830.aspx). Pour découvrir comment configurer et déployer des stratégies de gestion de l’application mobile, voir [créer et déployer des stratégies de gestion de l’application mobile avec Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx).
* Lorsque les utilisateurs finaux s’authentifier à l’application avec leurs informations d’identification d’entreprise, les fonctionnalités de protection de perte de données sont configurées automatiquement. La rubrique [confronté à l’utilisateur final pour les applications associées aux stratégies de gestion de l’application mobile Microsoft Intune](https://technet.microsoft.com/library/mt627827.aspx) comporte des exemples de scénarios pour accéder à OneDrive sur les appareils iOS et Android.
* Fonctionne sur les appareils iOS et Android.

La liste des [applications Microsoft que vous pouvez utiliser avec les stratégies de gestion des applications mobiles Microsoft Intune](https://technet.microsoft.com/library/dn708489.aspx) a été mis à jour pour afficher les applications plus récentes.

### Gestion des appareils
 **Gestion des périphériques Mac OS X** Avec Intune, vous pouvez maintenant inscrire et gérer les périphériques de Mac OS X. Vous pouvez effectuer les opérations suivantes avec vos périphériques de Mac OS X :
* S’inscrire équipements gérés par Intune. Voir [configurer la gestion de Mac avec Microsoft Intune et iOS](https://technet.microsoft.com/library/dn408185.aspx).
* Contrôler les paramètres de l’appareil avec une stratégie de configuration général. Voir les [paramètres de stratégie de configuration de Mac OS X dans Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx).
* Déployer les paramètres de Mac OS X que vous avez créé avec l’outil de configuration d’Apple. Découvrez les [paramètres de stratégie personnalisée Mac OS X de Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx).
* Collecter l’inventaire matérielle et logicielle à partir d’appareils de Mac OS X. Voir [comprendre vos périphériques en stock dans Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx).
* Exécuter des rapports qui affichent les détails concernant les périphériques de Mac OS X que vous gérez. Voir [comprendre Microsoft Intune opérations à l’aide de rapports](https://technet.microsoft.com/library/dn646977.aspx).

**Paramètres du navigateur bord nouveau pour les appareils Windows 10** Paramètres ont été ajoutés à la stratégie de configuration générale Windows 10 qui vous permettent de gérer les paramètres et les fonctionnalités du navigateur Microsoft Edge. Découvrez les [paramètres de stratégie de configuration Windows 10 de Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx).

**Profils de messagerie** Une nouvelle stratégie de profils de messagerie a été ajoutée pour le bureau de Windows 10 et Windows 10 les appareils mobiles. Voir [Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](https://technet.microsoft.com/library/dn646984.aspx).

**Nouveaux paramètres de stratégie de conformité** Les paramètres de stratégie système et sécurité nouveau suivants ont été ajoutés à la liste des stratégies de conformité :
* Pour vous assurer que Windows 8.1 ou générations ultérieures qui accèdent aux ressources de votre entreprise ont les dernières mises à jour installés, utilisez le paramètre **exiger des mises à jour automatiques** . Vous pouvez également spécifier le type de mises à jour automatiquement--soit toutes les mises à jour marqué comme étant importants doit être installé, ou toutes les mises à jour marqué importante ou recommandée. Pour obtenir la liste complète des paramètres de stratégie de conformité, voir [gérer des stratégies de conformité appareil pour Intune Microsoft](https://technet.microsoft.com/library/dn705843.aspx).
* Le nouveau paramétrage **Exiger un mot de passe lorsque l’appareil est retournée à partir de l’état d’inactivité** associé à la valeur de **Minutes d’inactivité avant de mot de passe** existante vous permet de créer un paramètre de conformité qui exige l’utilisateur final pour entrer un mot de passe pour utiliser un appareil est inactif depuis un certain temps.

**Nouvelles options de stratégie d’accès conditionnel** Vous pouvez appliquer les stratégies d’accès conditionnelle à **tous les utilisateurs** dans des stratégies d’accès conditionnelle nouvelle ou existante. Tous les utilisateurs d’une licence pour Intune et Office 365 seront invités à inscrire leur appareil, et si la plateforme de l’appareil n’est pas pris en charge par Intune, accès est bloqué pour les applications clientes à l’aide de [l’authentification Active Directory en fonction de connexion (authentification moderne)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/).

Vous pouvez également spécifier que la stratégie d’accès conditionnelle s’applique à **toutes les plateformes**.  N’importe quelle application client à l’aide de la [connexion (authentification moderne) en fonction de l’authentification Active Directory](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/) est soumis à la stratégie d’accès conditionnel et si la plateforme n’est pas pris en charge par Intune, il sera bloqué.

### Modifications et mises à jour de Microsoft application portail d’entreprise
Les modifications suivantes ont été apportées aux applications de portail d’entreprise dans cette version :

* **Android**: un écran d’accueil a été ajouté à l’application portail d’entreprise Android pour aider les utilisateurs mieux comprendre l’utilité de l’application portail d’entreprise. Cet écran est conçu pour réduire les téléchargements de l’application par les utilisateurs dont entreprises ne sont pas Intune abonnés.

* **iOS**: Intune prend désormais en charge l’inscription des appareils de Mac OS X à l’aide du [site Web du portail d’entreprise](https://portal.manage.microsoft.com). Pour plus d’informations, voir [inscrire votre appareil Mac OS X dans Intune](https://technet.microsoft.com/library/mt598622.aspx).

* **Site Web du portail d’entreprise**: les utilisateurs qui ont inscrit leur appareil dans Intune peuvent à présent rétablir leur code secret à l’aide de l’option **Réinitialiser le code secret** sur le site Web portail d’entreprise. Précédemment, seuls les administrateurs informatiques peuvent réinitialiser codes secrets des utilisateurs. L’option Réinitialiser le mot de passe n’est pas pris en charge sur les appareils Windows 8.1 et Windows RT, et l’option s’affiche uniquement lorsque les périphériques sont inscrits dans la gestion des appareils mobiles (MDM) ou périphériques mobiles avec Exchange ActiveSync. Pour plus d’informations utilisateur, voir [Réinitialiser votre code secret](https://technet.microsoft.com/library/mt590895.aspx).

### Modifications apportées aux administrateurs globaux de licence
En octobre, nous partagé que les administrateurs généraux (également appelée administrateur de clients) peut continuer à effectuer les tâches d’administration quotidienne sans une licence distincte Intune ou Suite de mobilité d’entreprise (EM). Toutefois, si les administrateurs généraux souhaitez utiliser le service, par exemple pour inscrire leur appareil, un périphérique d’entreprise ou utiliser le portail d’entreprise Intune, elles devront une licence Intune ou em comme tout autre utilisateur. Voici quelques informations supplémentaires.
* Le portail d’entreprise Intune est l’endroit où les utilisateurs finaux peuvent :
    * inscrire leur appareil
    * afficher l’état de leur appareil
    * Télécharger le logiciel déployées par un administrateur général pour l’organisation
    * Vous trouverez des liens publiés par l’administrateur Global pour savoir comment contacter son service informatique

    [Obtenir des informations sur le portail d’entreprise](https://technet.microsoft.com/library/dn646966.aspx#BKMK_CompanyPortal) et savoir [comment personnaliser le portail d’entreprise](https://technet.microsoft.com/library/dn646983.aspx#BKMK_ConfigureCompanyPortal).
* La personne qui s’inscrit à acheter Intune ou em au nom d’une organisation automatiquement devient l’administrateur Global première dans leur client. Cet automne, Intune en main d’affecter automatiquement une licence Intune ou em pour que vous devez commencer par un administrateur Global dans le cadre du déplacement au [Portail Office 365](http://portal.office.com/) et déclassement du [Portail de compte Intune](http://account.manage.microsoft.com/). Les administrateurs globaux supplémentaires ajouté pouvez continuer à faire administration quotidienne sans une licence distincte Intune ou em. Agissant en tant qu’utilisateur final et inscrire leur appareil propre (ou d’entreprise) ou logiciel de téléchargement à partir du portail d’entreprise serait puis déclencher un besoin d’une licence, comme tout autre utilisateur.
* La modification est établie et maintenant démarre en janvier 2016.
* Pour Microsoft Partners, cette modification ne devrait pas affecter votre capacité à administrer le service au nom de clients. Pour les tâches de l’utilisateur final, un utilisateur devra disposer d’une licence Intune ou em afin de s’inscrire un appareil et un accès ou télécharger le logiciel à partir du portail d’entreprise.

Si vous avez des questions sur cette modification, n’hésitez pas à contacter le support technique Intune :
* [Microsoft Intune prise en charge de canaux](https://technet.microsoft.com/library/jj839713.aspx)
* [Prise en charge de la Communauté](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

Pour les commentaires Intune Microsoft généraux, y compris les classer les demandes de modification de conception (DCR) ou les bogues, visitez [voix utilisateur Intune](https://microsoftintune.uservoice.com/).


### Quelles sont les nouveautés dans la documentation Intune--novembre 2015
**Nouveau contenu**
* [Paramètres de stratégie de configuration de Mac OS X dans Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx): comment contrôler les paramètres de l’appareil et fonctionnalités pour les périphériques de Mac OS X.
* [Paramètres de stratégie personnalisés de Mac OS X dans Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx): comment déployer des paramètres du périphérique Mac OS X que vous avez créé à l’aide de l’outil de configuration du Apple.
* [Configurer les stratégies avec Microsoft Intune application de la prévention de le de perte de données](https://technet.microsoft.com/library/mt627825.aspx): contient des informations sur les scénarios que gestion de l’application mobile prise en charge des stratégies et le fonctionne de la stratégie pour protéger vos données.
* [Prise en main stratégies de gestion de l’application mobile dans le portail Azure](https://technet.microsoft.com/library/mt627830.aspx): ce que vous devez commencer à utiliser le portail Azure preview pour les stratégies de gestion de l’application mobile.
* [Créer et déployer des stratégies de gestion de l’application mobile avec Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx): contient une procédure pas à pas comment créer des stratégies de gestion des application mobile dans le portail Azure preview.
* [Stratégies de gestion de l’application mobile moniteur avec Microsoft Intune](https://technet.microsoft.com/library/mt627824.aspx): informations sur comment vous pouvez contrôler vos stratégies de gestion des application mobile à l’aide du portail Azure preview.
* [Stratégies de gestion de l’application mobile Microsoft Intune et iOS ouvrir dans](https://technet.microsoft.com/library/mt627821.aspx): informations sur le travail de stratégies de gestion des comment mobile application avec iOS fonctionnalité Ouvrir dans.
* [Expérience de l’utilisateur final pour applications associées aux stratégies de gestion de l’application mobile Microsoft Intune](https://technet.microsoft.com/library/mt627827.aspx): quelle est la satisfaction des utilisateurs lors de l’utilisation des applications associées de stratégie de gestion de l’application mobile.
* [Réinitialisation gérées des données de l’application d’entreprise avec Microsoft Intune](https://technet.microsoft.com/library/mt627826.aspx): comment vous pouvez supprimer les données de l’application d’entreprise.

**Contenu mis à jour**
* [Paramètres de stratégie de configuration de Windows 10 dans Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx): ajouté les nouveaux paramètres de navigateur de bord.
* [Configurer la gestion de Mac avec Microsoft Intune et iOS](http://technet.microsoft.com/library/dn408185.aspx): ajout d’informations sur la procédure d’inscription des appareils de Mac OS X.
* [Comprendre vos périphériques en stock dans Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx): ajout d’informations sur l’inventaire collectées à partir d’appareils de Mac OS X. En outre, mis à jour la rubrique avec les dernières informations sur toutes les plateformes d’appareil.
* [Opérations de comprendre Microsoft Intune à l’aide de rapports](https://technet.microsoft.com/library/dn646977.aspx): informations supplémentaires sur les nouveaux deux rapports utilisé pour afficher des informations sur vos périphériques de Mac OS X gérées.
* [Gérer des stratégies de conformité appareil pour Intune Microsoft](https://technet.microsoft.com/library/dn705843.aspx): ajout d’informations sur les nouvelles stratégies de conformité pour demander une mises à jour automatiques et des mots de passe lorsqu’un appareil renvoie à partir de l’état d’inactivité.
* [Gérer les accès de messagerie avec Intune Microsoft](https://technet.microsoft.com/library/dn705841.aspx): ajout d’informations sur la fonctionnalité permettant d’appliquer la stratégie d’accès conditionnel à toutes les plates-formes et tous les utilisateurs.
* [Access gérer SharePoint Online avec Intune Microsoft](https://technet.microsoft.com/library/dn705844.aspx): ajout d’informations sur la fonctionnalité permettant d’appliquer la stratégie d’accès conditionnel à toutes les plates-formes et tous les utilisateurs.

## Octobre 2015

### Mises à jour pour l’accès conditionnel pour Exchange en local
**Vous pouvez désormais autoriser l’accès à la messagerie Exchange Active Sync pour les appareils compatibles inscrit dans Intune lorsque la règle globale Exchange est définie sur Bloquer ou mettre en quarantaine** Jusqu'à présent, pour autoriser l’accès de messagerie sur les appareils inscrits et respecter les exigences, vous deviez la règle Exchange globale par défaut la valeur **Autoriser**.

Cette mise à jour de service, ce paramètre n’est plus une configuration minimale requise pour l’accès conditionnel. Si votre environnement Exchange requiert que votre règle globale par défaut à définir en **Bloc/mise en quarantaine**, vérifiez simplement la case à cocher **Règle de substitution par défaut** dans le Exchange local page de la stratégie d’accès conditionnel. La rubrique [Gérer les accès de messagerie avec Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx) comporte plus d’informations sur les règles et les notifications de l’utilisateur final qui en résulte.

**Nouvelle expérience de mise en quarantaine un seul clic** Nous avons simplifié l’expérience de messagerie de mise en quarantaine pour permettre l’inscription d’un seul clic. Cette mise à jour de service, les utilisateurs finaux et cliquez sur un seul lien dans le message de mise en quarantaine pour terminer le processus d’inscription au sein de l’application portail d’entreprise.
### Mises à jour de gestion des périphériques et application mobiles
**Android** Toutes les fonctionnalités de gestion des Intune prennent désormais en charge 6.0 Android (shamallow) comme décrit dans ce billet de blog : [Microsoft Intune fournit jour 0 prend en charge pour Android shamallow](http://blogs.technet.com/b/microsoftintune/archive/2015/10/09/microsoft-intune-to-provide-day-0-support-for-android-marshmallow.aspx)

**iOS** Vous ne pouvez plus créer nouveaux déploiements d’application pour les appareils iOS exécute une version antérieure à iOS 7.1. Les déploiements d’application existant pour appareils exécutant une version antérieure à iOS 7.1 continueront à fonctionner et être gérés par Intune.

**Windows 10** Intune prend désormais en charge le déploiement des applications Windows 10 universel en utilisant le type de programme d’installation de logiciels de **package d’application Windows** . Pour plus d’informations et configuration requise, voir [prise en main le déploiement des applications dans Microsoft Intune](http://technet.microsoft.com/en-US/library/dn646955.aspx).


### Modifications et mises à jour des applications Microsoft application portail d’entreprise
Les modifications suivantes ont été apportées aux applications de portail d’entreprise dans cette version : **iOS** nouveaux boutons ont été ajoutés à l’application portail d’entreprise pour simplifier aux utilisateurs d’envoyer les journaux de diagnostic pour les administrateurs informatiques :

|Nom du bouton|Où elle s’affiche|
|------------|---------------|
|Rapport|Messages d’erreur|
|Envoyer le rapport de Diagnostic|À propos de l’écran de l’application portail d’entreprise|



## Septembre 2015
### Mises à jour de gestion des périphériques et application mobiles
**Prise en charge désormais les fonctionnalités de gestion iOS Intune tous les iOS 9** Pour plus d’informations sur les fonctionnalités de gestion des 9 iOS, voir [ce billet de blog](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx).

**Nouvelle stratégie de configuration de l’application mobile pour iOS** Utilisez la nouvelle stratégie de configuration de l’application mobile pour fournir automatiquement les paramètres une application iOS devrez lorsqu’elle est exécutée. Par exemple, vous pouvez fournir un port réseau ou un nom d’utilisateur. Pour plus d’informations, voir [configurer les applications avec les stratégies de configuration de l’application mobile dans Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx).

**Simplification de la gestion des utilisateurs iOS 9 application** 
 dans cette version, vous pouvez transférer des applications vous avez déjà déployé sous gestion Intune pour iOS 9 utilisateurs. Pour les versions antérieures d’iOS, lorsque vous déployez une application et une version non managée de l’application est déjà installée sur un appareil, vous devez toujours demander à l’utilisateur de désinstaller l’application manuellement avant Intune peut installer l’application gérée.

 Mais commençant par cette version de Intune, vous pouvez désormais inviter les utilisateurs d’appareils iOS 9 à autoriser Intune reprendre la gestion de l’application et appliquer les stratégies de gestion des applications mobiles pertinents.

 **Gestion de Windows 10** Utilisez la nouvelle [stratégie de configuration générale Windows 10](https://technet.microsoft.com/library/mt404697.aspx) pour configurer votre mot de passe, appareil, navigateur et d’autres paramètres pour les appareils inscrits qui exécutent Windows 10 et Windows 10 Mobile.

 **Créer et déployer des applications sur les appareils Windows 10 inscrits** Tapez un nouveau programme d’installation du logiciel, Windows Installer via la gestion des périphériques (& #42 ;. MSI) vous permet de créer et déployer des applications Windows Installer aux périphériques inscrits qui exécutent Windows 10. Pour plus d’informations, voir [prise en main le déploiement des applications dans Microsoft Intune](https://technet.microsoft.com/library/dn646955.aspx).

### Modifications et mises à jour des applications Microsoft application portail d’entreprise
Les modifications suivantes ont été apportées aux applications de portail d’entreprise dans cette version :

**iOS**
* Microsoft recueille automatiquement des données anonymes sur les performances et l’utilisation de l’application portail d’entreprise pour améliorer les produits et services Microsoft. Les utilisateurs finaux peut désactiver la collecte de données en utilisant le paramètre de données d’utilisation sur leur appareil, mais les administrateurs ont aucun contrôle sur la collecte de données et ne pouvez pas modifier la sélection de l’utilisateur final pour ce paramètre.
* Support de résolution d’écran sur iPhone 6 et 6 complet Plus
* Correctifs pour améliorer la sécurité

### Quelles sont les nouveautés dans la documentation Intune--septembre 2015
**Présentation des nouvelles rubriques**

|Nom|Plus d’informations|
|----|--------|
|[Paramètres de stratégie de configuration de Windows 10 dans Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx)|Il s’agit d’une nouvelle stratégie de configuration qui vous permet de gérer des paramètres et fonctionnalités sur des appareils exécutant Windows 10 et Windows 10 Mobile.
| [Configurer les applications avec les stratégies de configuration de l’application mobile dans Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx)|Il s’agit d’un nouveau type de stratégie qui vous permet de fournir automatiquement les paramètres qui peuvent être nécessaires lorsque l’utilisateur exécute une application iOS. |

**Rubriques mises à jour**

|Nom|Plus d’informations|
|----|-------|
|[Utiliser des stratégies pour gérer les ordinateurs et appareils mobiles avec Microsoft Intune](https://technet.microsoft.com/library/dn743712.aspx)|Mise à jour pour inclure les dernières informations pour vous aider à comprendre et créer des stratégies.|

## Août 2015
### Mises à jour de gestion des périphériques et application mobiles
* **Termes et conditions** pour l’inscription de Intune et accès à la société sont [désormais gérés au moyen de stratégies](https://technet.microsoft.com/library/mt405893.aspx). Vous pouvez cibler différents ensembles de termes et conditions répondre aux exigences de groupe d’utilisateurs spécifiques. Par exemple, vous pouvez déployer des termes et conditions dans d’autres langues aux groupes d’utilisateurs géographiquement défini. Vous pouvez également [modifier vos termes et conditions](https://technet.microsoft.com/library/mt405893.aspx#BKMK_TCVers) et spécifiez si vous voulez incrémenter les numéros de version, obliger les utilisateurs à accepter les nouveaux termes et conditions avant de pouvoir utiliser le portail d’entreprise.
* **Un certain nombre de stratégies Intune ont été renommé** afin de les rendre plus cohérente sur le produit et vous permettent de trouver plus facilement. Pour obtenir la liste de toutes les stratégies Intune disponibles, voir [stratégies d’utilisation pour gérer les ordinateurs et appareils mobiles avec Microsoft Intune](https://technet.microsoft.com/library/dn743712.aspx).
* **PKCS #12 (. Profils de certificat PFX)** sont disponible pour Android 4.0 ou version ultérieure et Windows 10 (ordinateur de bureau et mobiles) et les versions ultérieures. À l’aide. PFX ne nécessite pas un serveur NDES. Apprenez à utiliser. Profils de certificat PFX dans [Activer l’accès aux ressources d’entreprise en utilisant les profils de certificat avec Microsoft Intune](http://technet.microsoft.com/library/dn818904.aspx)
* **Paramètres de limites d’entreprise pour Windows 10 Desktop et Mobile** activer granulaires paramètres VPN, comme décrit dans [aider les utilisateurs de se connecter à leur travail en utilisant les profils VPN avec Microsoft Intune](https://technet.microsoft.com/library/dn818905.aspx)
* **Application de l’OneDrive pour Android désormais prend en charge plusieurs identité**. Cette et autres mises à jour des stratégies de gestion de l’application mobile sont décrites dans la [liste des applications de Microsoft, vous pouvez gérer](https://technet.microsoft.com/library/dn708489.aspx).
* **iOS verrouiller l’Activation par téléphone évitent**. Si les appareils iOS appartenant à l’entreprise sont protégés par verrouiller l’Activation, vous devez entrer ID Apple et le mot de passe de l’utilisateur avant de pouvoir effacer ou réactiver le périphérique. Cela peut présenter un défi lorsqu’un utilisateur quitte la société et retourne un périphérique appartenant à l’entreprise sans la désactivation de l’Activation de verrouillage. Pour résoudre ce problème, vous pouvez utiliser [Intune Activation verrouiller dérivation](https://technet.microsoft.com/library/mt414176.aspx)

### Accès conditionnel pour PC
Vous pouvez maintenant configurer les stratégies d’accès conditionnelle pour PC. Cela permet aux applications de bureau Office pour accéder à Exchange Online et SharePoint online services.
Pour activer la stratégie d’accès conditionnel pour les PC, l’ordinateur doit être domaine rejoint ou être réclamation.
* Consultez la section **mise en route** de [gérer l’accès à la messagerie électronique et SharePoint avec Microsoft Intune](http://technet.microsoft.com/library/dn818907).aspx) pour la liste complète des conditions requises pour activer l’accès conditionnel pour PC.
* Pour les options que vous pouvez définir pour activer l’accès conditionnel pour l’accès de messagerie, consultez [Gérer les accès de messagerie avec Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx) .
* Consultez [accès gérer SharePoint Online avec Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx) pour les options que vous pouvez définir pour activer l’accès conditionnel pour SharePoint Online.

### Modifications et mises à jour des applications Microsoft application portail d’entreprise
Les modifications suivantes ont été apportées aux applications de portail d’entreprise dans cette version :

**Android**

Les utilisateurs verront maintenant savoir comment le périphérique d’inscription après la connexion si elles n’ont pas encore inscrit leur appareil pour la gestion.

### Quelles sont les nouveautés dans la documentation Intune--août 2015
**Présentation des nouvelles rubriques**

|Titre|Plus d’informations|
|-----|-------|
|[Protéger iOS appareils avec verrouiller l’Activation par téléphone évitent pour Intune Microsoft](https://technet.microsoft.com/library/mt414176.aspx)|Découvrez comment vous pouvez utiliser Intune pour ignorer iOS verrouillage Activation lorsqu’un utilisateur quitte l’entreprise et renvoie un appareil verrouillé.|

**Rubriques mises à jour**

|Titre|Plus d’informations|
|-----|-------|
|[Applications Microsoft que vous pouvez utiliser avec les stratégies de gestion des applications mobiles Microsoft Intune](https://technet.microsoft.com/library/dn708489.aspx)|Mise à jour avec les dernières informations sur les applications que vous pouvez gérer les stratégies de gestion des applications mobiles.
|[Utiliser des stratégies pour gérer les ordinateurs et appareils mobiles avec Microsoft Intune](http://technet.microsoft.com/library/dn743712.aspx)|Mises à jour avec les stratégies plus récent ajoutés à Intune.|
<!---
## July 2015
July updates for Intune are limited to behind-the-scenes enhancements that allow us to continue providing you with a high-quality service experience. New features are not included in this service update.

### Intune Onboarding benefit
Microsoft offers the Intune Onboarding benefit for eligible plans. The Onboarding benefit lets you work remotely with Microsoft specialists to get your Intune environment ready for use. For more information, see [Microsoft Intune Onboarding benefit description](https://technet.microsoft.com/library/mt228266.aspx)
### Changes and updates to Microsoft Company Portal apps
The following changes have been made to the company portal apps in this release.

**Android**

Microsoft automatically collects anonymous data about the performance and use of the company portal to improve Microsoft products and services. End users can turn off data collection by using the Usage Data setting on their device, but administrators have no control over the data collection and cannot change the end user’s selection for this setting.--->
