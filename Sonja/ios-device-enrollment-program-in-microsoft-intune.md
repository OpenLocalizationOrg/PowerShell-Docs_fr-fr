---
title: "Gestion de la fonctionnalité Apple pour les appareils iOS | Microsoft Intune"
description: "Déployer un profil d’inscription qui s’inscrit les appareils iOS achetés via le programme d’inscription d’un appareil (PED) iOS « sur l’air » pour gérer les périphériques d’Apple."
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: fa02292c2cd6a8b627428752d97cf8a04dcc19b0
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# S’inscrire appartenant à l’entreprise les appareils iOS appareil inscription d’un programme
Microsoft Intune pouvez déployer un profil d’inscription qui s’inscrit les appareils iOS achetés via le programme d’inscription appareil (PED) « via l’air. » Le package d’inscription peut inclure les options de l’assistant configuration pour l’appareil. Appareils inscrits via la fonctionnalité ne peut pas être inscrits par les utilisateurs.

## Gestion de Apple DEP pour les appareils iOS avec Microsoft Intune
Pour gérer les appareils iOS appartenant à l’entreprise avec Apple appareil inscription d’un programme (PED), votre organisation doit rejoindre Apple DEP et acquérir des équipements à l’aide de ce programme. Détails de ce processus sont disponibles dans la page : [https://deploy.apple.com](https://deploy.apple.com). Avantages du programme comprennent ensemble mains libres haut des appareils sans connexion USB chaque appareil à un ordinateur.

Vous pouvez vous inscrire appareils iOS appartenant à l’entreprise avec la fonctionnalité, vous devez DEP jeton d’Apple. Ce jeton permet Intune de synchronisation d’informations sur les périphériques participant DEP appartenant à votre entreprise. Il permet également de Intune pour effectuer des chargements de profil d’inscription à pomme et affecter des appareils à ces profils.

1.  **Démarrer la gestion des appareils iOS avec Microsoft Intune** Avant d’inscrire iOS appareils appareil inscription d’un programme (PED), vous devez effectuer activer la gestion d’iOS pour Intune.

2.  **Obtenir une clé de chiffrement** En tant qu’administrateur, ouvrez la [console d’administration Microsoft Intune](http://manage.microsoft.com), accédez à **administrateur** &gt; **Gestion des appareils mobiles** &gt; **iOS** &gt; **Appareil inscription d’un programme**, puis cliquez sur **Télécharger la clé de chiffrement**. Enregistrez le fichier de clé (.pem) de chiffrement localement. Le fichier .pem est utilisé pour demander un certificat de relation d’approbation à partir du portail Apple appareil inscription d’un programme.

      ![Mettre à jour un jeton de programme d’inscription d’un appareil](../media/dev-sa-ios-dep.png)

3.  **Obtenir un programme d’inscription d’un appareil jeton** Accédez au [Portail du programme d’inscription appareil](https://deploy.apple.com) (https://deploy.apple.com) et connectez-vous avec votre société ID Apple. Cet identifiant Apple doit être utilisé à l’avenir pour renouveler votre jeton DEP.

    1.  Dans le portail [Portail du programme d’inscription appareil](https://deploy.apple.com) , accédez **Appareil inscription d’un programme** &gt; **Gérer les serveurs**, puis cliquez sur **Ajouter un serveur périphériques mobiles**.

    2.  Entrez le **Nom de serveur de la gestion des périphériques** , puis sur **suivant**. Le nom du serveur est de référence identifier le serveur de la gestion des périphériques. Il n’est pas nom ou l’URL du serveur Microsoft Intune.

    3.  La **Ajouter &lt;nom du serveur&gt; ** boîte de dialogue s’ouvre. Cliquez sur **Choisir le fichier...** Pour télécharger le fichier .pem, puis sur **suivant**.

    4.  La **Ajouter &lt;nom du serveur&gt; ** boîte de dialogue affiche un lien **Jeton de votre serveur** . Téléchargez le fichier du jeton (.p7m) serveur sur votre ordinateur, puis cliquez sur **terminé**.

    Ce fichier de certificat (.p7m) est utilisé pour établir une relation d’approbation entre Intune et d’Apple serveurs appareil inscription d’un programme.

4.  **Ajouter le jeton DEP Intune** Dans la [console d’administration Microsoft Intune](http://manage.microsoft.com), accédez à **administrateur** &gt; **Gestion des appareils mobiles** &gt; **iOS** &gt; **Appareil inscription d’un programme**, puis cliquez sur **Télécharger le jeton DEP**. **Recherchez** le fichier de certificat (.p7m), entrez votre **Identifiant Apple**, puis cliquez sur **Télécharger**.

5.  **Ajouter la stratégie d’inscription appareil d’entreprise** Dans la [console d’administration Microsoft Intune](http://manage.microsoft.com), accédez à la **stratégie de** &gt; **Inscription d’un appareil d’entreprise** , puis sur **Ajouter**.

    Fournir des informations **générales** , y compris le **nom** et une **Description**, spécifiez si les périphériques affectés au profil ont affinité utilisateur ou appartenir à un groupe.
      - **Choisir l’affinité utilisateur**: le périphérique doit être affilié à un utilisateur lors de l’installation initiale et pourrait puis être autorisé à accéder aux données de la société et la messagerie électronique en tant que cet utilisateur.  **Affinité utilisateur** doit être configuré pour les périphériques gérés DEP qui appartiennent aux utilisateurs et que vous devez utiliser le portail d’entreprise (c'est-à-dire pour installer des applications). **Remarque :** Appareils DEP avec affinité utilisateur ne peut pas en charge l’authentification multifacteur.
      - **Aucune affinité utilisateur**: l’appareil n’est pas affilié à un utilisateur. Utilisez cette affiliation pour appareils mobiles qui effectuent des tâches sans accès aux données utilisateur local. Applications nécessitant une affiliation utilisateur, y compris l’application portail d’entreprise utilisée pour les applications professionnelles de l’installation, ne fonctionnent pas.

    Vous pouvez également **attribuer les appareils pour le groupe suivant**. Cliquez sur **Select...** pour choisir un groupe.

    [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

    Ensuite, activez **paramètres configurer appareil inscription d’un programme de cette stratégie** à la prise en charge logicielle.

      ![Volet assistant de configuration](../media/pol-sa-corp-enroll.png)

     Les paramètres suivants sont disponibles pour les périphériques gérés par cette fonctionnalité :

     - **Département** - s’affiche lorsque les utilisateurs appuyez sur « À propos de la Configuration » lors de l’activation
     - **Numéro de téléphone de support technique** - affiché lorsque l’utilisateur clique sur le bouton **Besoin d’aide** lors de l’activation
     - **Mode de préparation** - cet état est définie lors de l’activation et ne peut pas être modifié sans usine la réinitialisation de l’appareil :
        - **Unsupervised** - fonctionnalités de gestion des limitée
        - **Supervised** - permet à plusieurs options de gestion et désactive l’Activation verrouillage par défaut
     - **Profil de l’inscription verrouillage sur appareil** - cet état est défini lors de l’activation et ne peut pas être modifié sans une réinitialisation d’usine
        - **Désactiver** - permet le profil de gestion à supprimer dans le menu **paramètres**
        - **Activer** - (nécessite le **Mode de préparation** = **Supervised**) désactive les paramètres d’iOS qui pourraient autoriser la suppression du profil de gestion
     - **Options de l’Assistant Configuration** - ces paramètres sont facultatives et peut être configurés plus loin dans le menu **paramètres** iOS
        - **Code secret** - choisir le code secret lors de l’activation. Toujours demander un code secret, sauf si le périphérique sera sécurisé ou ont accès contrôlé d’une autre manière (par exemple, le mode plein écran qui limite l’appareil à une application).
        - **Services de localisation** - si activé, l’Assistant de configuration vous invite au service lors de l’activation
        - **Restaurer** - si activé, l’Assistant de configuration vous invite à iCloud sauvegarde lors de l’activation
        - **ID Apple** - un ID Apple nécessaire au téléchargement iOS applications App Store, y compris ceux qui sont installés par Intune. Si activé, iOS inviter les utilisateurs d’un ID Apple lorsque Intune essaie d’installer une application sans un identifiant.
        - **Termes et Conditions** - si activé, l’Assistant de configuration invite les utilisateurs à accepter les termes et conditions de Apple lors de l’activation
        - **Touchez ID** - si activé, l’Assistant de configuration vous invite à ce service lors de l’activation
        - **Apple payer** - si activé, l’Assistant de configuration vous invite à ce service lors de l’activation
        - **Effectuer un zoom avant** - si activé, l’Assistant de configuration vous invite à ce service lors de l’activation
        - **Siri** - si activé, l’Assistant de configuration vous invite à ce service lors de l’activation
        - **Envoyer des données de diagnostic pour Apple** - si activé, l’Assistant de configuration vous invite à ce service lors de l’activation
     -  **Activer la gestion de configuration du Apple supplémentaire** - défini sur **ne pas autoriser** pour éviter la synchronisation des fichiers avec iTunes ou gestion via le programme de configuration Apple. Microsoft recommande vous définissez sur **ne pas autoriser**, exportez aucune configuration supplémentaire à partir d’Apple outil de configuration et puis déployez comme un profil de configuration personnalisé iOS via Intune, plutôt que ce paramètre permet d’autoriser déploiement manuel avec ou sans un certificat.
        - **Ne pas autoriser** - empêche le périphérique de communiquer via USB (désactive le jumelage)
        - Permet d' **Autoriser** - appareil communiquer via une connexion USB pour n’importe quel PC ou Mac
        - **Nécessitent le certificat** - permet le jumelage avec un Mac avec un certificat importé dans le profil d’inscription

6.  **Affecter des appareils DEP pour la gestion** Accédez au [Portail du programme d’inscription appareil](https://deploy.apple.com) (https://deploy.apple.com) et connectez-vous avec votre société ID Apple. Accédez **déploiement programme** &gt; **appareil inscription d’un programme** &gt; **Gestion des appareils**. Spécifiez comment vous allez **Choisir les périphériques**, fournissent des informations sur les périphériques et spécifiez détails en appareil de **numéro de série**, **Numéro de la commande**ou **Télécharger un fichier CSV**. Ensuite, sélectionnez **affecter au serveur** et sélectionnez le &lt;nom du serveur&gt; spécifiée pour Intune Microsoft, puis cliquez sur **OK**.

7.  **Synchroniser des équipements DEP** En tant qu’administrateur, ouvrez la [console d’administration Microsoft Intune](http://manage.microsoft.com), accédez à **administrateur** &gt; **Gestion des appareils mobiles** &gt; **iOS** &gt; **Appareil inscription d’un programme**, puis cliquez sur **Synchroniser maintenant**. Une demande de synchronisation est envoyée au Apple. Pour afficher des équipements DEP après la synchronisation, dans la [console d’administration Microsoft Intune](http://manage.microsoft.com) accédez **groupes** &gt; **Tous les périphériques** &gt; **d’entreprise appareils pré-inscrit** &gt; **par iOS numéro de série**. Dans l’espace de travail **par iOS numéro de série** , l' **état** pour des périphériques gérés lit « N’a pas contacté » jusqu'à ce que l’appareil est sous tension et exécuté l’Assistant de configuration pour l’inscription de l’appareil.

    Pour respecter les termes d’Apple pour le trafic DEP acceptable, Intune impose les restrictions suivantes :
     -  Une synchronisation DEP complet peut exécuter pas plus de 7 jours. Au cours d’une synchronisation complète, Intune actualise chaque numéro de série Qu'apple a affecté à Intune si le numéro de série a déjà été synchronisé ou non. Si une synchronisation complète est tentée dans les 7 jours de la synchronisation complète précédente, Intune actualise uniquement des numéros de série pas encore répertoriés dans Intune.
     -  Toute demande de synchronisation est compris entre 10 minutes pour terminer. Pendant ce temps ou jusqu'à ce que la demande a réussi, le bouton Synchroniser est désactivé.

8.  **Répartir appareils aux utilisateurs** Vos périphériques appartenant à l’entreprise peuvent être distribuées aux utilisateurs. Lorsqu’un appareil iOS est activé en il doit s’inscrire à gestion par Intune.

## Modifications apportées aux affectations de groupe Intune

À partir de novembre, gestion des appareils groupe permet de déplacer vers Azure Active Directory. Après la transition aux groupes Azure Active Directory, affectation de groupe n’apparaîtront pas dans les options de **Profil d’inscription d’entreprise** . Étant donné que cette modification mettra en place sur une série de mois, vous ne verrez pas la modification immédiatement. Après avoir déplacé vers le nouveau portail, affectations de groupe dispositif dynamique peuvent être définies en fonction du nom du profil de l’inscription de l’entreprise. Ce processus garantit que les périphériques préalable affectés à un groupe de périphériques inscriront automatiquement dans le groupe avec la stratégie et applications déployées. [Pour plus d’informations sur les groupes Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/)

### Voir aussi
[Préparer d’inscription des appareils mobiles](get-ready-to-enroll-devices-in-microsoft-intune.md)
