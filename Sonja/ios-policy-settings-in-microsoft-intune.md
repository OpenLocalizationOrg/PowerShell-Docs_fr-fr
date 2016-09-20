---
title: "paramètres de stratégie iOS | Microsoft Intune"
description: "Créer des stratégies qui contrôlent les paramètres et les fonctionnalités sur les appareils iOS que vous gérez avec Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293
ms.reviewer: heenamac
ms.suite: ems
ms.openlocfilehash: 24540a74ce98adbf3f908cbea401328f027867ca
ms.sourcegitcommit: 28f2e8cf965a6baaa8cf317af8bc777cd28fac4c
translationtype: MT
---
# paramètres de stratégie iOS dans Microsoft Intune

Intune fournit une plage de paramètres généraux prédéfinis que vous pouvez configurer sur les appareils iOS. En outre, vous pouvez utiliser l’outil de configuration du Apple pour créer des paramètres personnalisés qui ne sont pas disponibles dans Intune.

## Paramètres de stratégie de configuration générale

Utilisez la Microsoft Intune **stratégie de configuration générale iOS** pour configurer les paramètres pour :

-   **Appareil général et les paramètres de sécurité**. Choisir parmi une liste de paramètres prédéfinis qui vous permettent de contrôler une plage de fonctionnalités sur l’appareil.

-   **Mode plein écran**. Verrouiller un appareil pour autoriser uniquement certaines fonctionnalités de fonctionner. Par exemple, vous pouvez autoriser un appareil exécuter une application gérée que vous spécifiez, ou vous pouvez désactiver les boutons de volume sur un appareil. Ces paramètres peuvent être utilisés pour un modèle de démonstration d’un appareil ou un périphérique dédié à l’exécution d’une seule fonction, par exemple un périphérique de vente.

-   **Conforme et applications non conformes**. Spécifiez une liste des applications qui sont conformes ou n’est pas compatible dans votre entreprise. Sur les appareils Android et iOS, le **Rapport applications non conformes** peut être utilisé pour afficher la conformité des applications que vous avez spécifié dans la liste contre les applications que vous ont installé (mais les utilisateurs ne peuvent pas réellement bloquer l’installation de l’application).

> [!TIP]
> Vous pouvez configurer les termes et conditions pour les utilisateurs afin qu’ils reconnaissent qu’applications sur leur appareil (y compris les applications personnelles) seront évaluées et applications non conformes doit être bloquées ou signalées comme non conformes. Les utilisateurs doivent accepter les conditions d’utilisation avant de pouvoir inscrire leur appareil et utiliser le portail d’entreprise pour obtenir des applications. Pour plus d’informations sur l’utilisation des termes et conditions, voir [paramètres de stratégie de termes et conditions dans Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Si le paramètre que vous recherchez n’apparaît pas dans cette rubrique, vous pourrez peut-être créer votre document en utilisant une stratégie personnalisée iOS qui vous permet d’importer les paramètres que vous avez créé à l’aide de l' [outil de configuration du Apple](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12). Pour plus d’informations, voir « Paramètres de stratégie personnalisée » plus loin dans cette rubrique.

### Paramètres de sécurité
Tous les paramètres s’appliquent à iOS 8.0 et versions ultérieures.

|Nom du paramètre|Plus d’informations|
|----------------|-------|
|**Demander un mot de passe pour la déverrouiller les appareils mobiles**|Spécifiez si l’utilisateur doit entrer un mot de passe pour accéder à leur appareil.|
|**Obligatoires type de mot de passe**|Spécifier le type de mot de passe qui sera requis, par exemple numérique uniquement ou alphanumérique.|
|**Nombre de caractères complexes requis dans mot de passe**|Spécifier le nombre de caractères spéciaux (tels que **#** ou **@**) qui doivent être inclus dans le mot de passe.|
|**Longueur minimale**|Spécifier le nombre minimal de caractères dans le mot de passe.|
|**Autoriser les mots de passe simples**|Autoriser les mots de passe simples tels que **0000** et **1234**.|
|**Nombre d’échecs de signe répétés autorisé avant que l’appareil est sélective**|Spécifier le nombre de tentatives de connexion infructueuses avant ce paramètre permet d’effacer l’appareil.|
|**Minutes d’inactivité avant de mot de passe**<sup>1</sup>|Spécifier la durée pendant laquelle l’appareil peut rester inactif avant que l’utilisateur doit retaper son mot de passe.|
|**Expiration du mot de passe (jours)**|Spécifier le nombre de jours avant que le mot de passe doit être modifié.|
|**N’oubliez pas de l’historique de mot de passe**|Spécifiez si l’utilisateur peut utiliser les mots de passe qu’ils ont utilisés précédemment.|
|**Historique de mot de passe mémoriser** : **éviter la réutilisation des mots de passe précédents**|Spécifier le nombre de mots de passe précédemment utilisés conserve l’appareil.|
|**Minutes d’inactivité avant de l’écran désactive les**<sup>1</sup>|Spécifier le nombre de minutes avant l’affichage du périphérique est désactivé.|
|**Autoriser l’empreinte déverrouiller**|Autoriser à l’aide d’une empreinte pour déverrouiller le périphérique.|
<sup>1</sup> pour les appareils iOS, lorsque vous configurez les paramètres de **Minutes d’inactivité avant de l’écran désactive les** **Minutes d’inactivité avant de mot de passe est requis**, ils sont appliqués dans l’ordre. Par exemple, si vous définissez la valeur pour les deux paramètres à **5** minutes, l’écran de désactiver automatiquement après 5 minutes, et l’appareil est verrouillé après une supplémentaire 5 minutes. Toutefois, si l’utilisateur désactive manuellement l’écran, le deuxième paramètre est appliqué immédiatement. Dans cet exemple, une fois que l’utilisateur a désactivé l’écran, le périphérique verrouille 5 minutes plus tard.

### Paramètres système
Tous les paramètres s’appliquent à iOS 8.0 et versions ultérieures.

|Nom du paramètre|Plus d’informations|
|----------------|-------|
|**Autoriser la capture d’écran**|Autoriser l’utilisateur capturer le contenu de l’écran en tant qu’image.|
|**Autoriser le centre de contrôle dans l’écran de verrouillage**|Autoriser l’utilisateur à accéder à l’application de centre de contrôle lorsque l’appareil est verrouillé.|
|**Autoriser l’affichage de la notification dans l’écran de verrouillage**|Autoriser l’utilisateur à accéder à l’affichage des notifications sans déverrouillage de l’appareil.|
|**Autoriser l’affichage aujourd'hui dans l’écran de verrouillage**|Autoriser l’utilisateur à afficher les notifications lorsque l’appareil est verrouillé.|
|**Autoriser les certificats TLS non approuvés**|Autoriser les certificats de Transport Layer Security approuvés sur l’appareil.|
|**Autorise l’envoi de données de diagnostic**|Autoriser ou bloquer l’appareil à partir de l’envoi de données de diagnostic pour Apple.|
|**Autoriser passbook lorsqu’elles sont verrouillées**|Autoriser l’utilisateur à accéder à l’application Passbook alors que l’appareil est verrouillé.|

### Paramètres de cloud pour les documents et données
Tous les paramètres s’appliquent à iOS 8.0 et versions ultérieures.

|Nom du paramètre|Plus d’informations|
|----------------|-------|
|**Autoriser de sauvegarde sur iCloud**|Autoriser l’utilisateur à sauvegarder le périphérique à iCloud.|
|**Autoriser la synchronisation de document à iCloud**|Autoriser la synchronisation de document et clé-valeur dans votre espace de stockage iCloud.|
|**Autoriser la synchronisation des flux de Photo pour iCloud**|Autoriser les photos sur le périphérique à synchroniser avec iCloud.|
|**Exiger sauvegarde chiffrée**|Exiger des sauvegardes appareil à chiffrer.|
|**Autoriser les applications gérées synchroniser des données à iCloud**|Autoriser les applications que vous gérez avec Intune à synchroniser des données pour le compte d’utilisateur iCloud.|
|**Autoriser Handoff continuer activités sur un autre appareil**|Autoriser l’utilisateur continuer le travail qu’ils démarrés sur un appareil iOS sur un autre iOS ou un appareil Mac OS X.|
|**Autoriser iCloud partage de photos**|Autoriser l’utilisation de la fonctionnalité de flux de données partagée photo iOS.|
|**Autoriser iCloud bibliothèque de photos**|Autoriser l’utilisateur à stocker des photos sur iCloud. Si désactivée, les photos déjà stockés sur iCloud sont été supprimés.|

### Paramètres de l’application pour le navigateur
Tous les paramètres s’appliquent à iOS 8.0 et versions ultérieures.

|Nom du paramètre|Plus d’informations|
|----------------|-------|
|**Autoriser Safari**|Indiquez si le navigateur Safari peut être utilisé sur l’appareil.|
|**Autoriser la recopie incrémentée**|Autoriser l’utilisateur à modifier les paramètres de saisie semi-automatique dans le navigateur.|
|**Autoriser le bloqueur de fenêtres**|Activer ou désactiver le bloqueur de navigateur.|
|**Activer les cookies**|Autoriser le navigateur à utiliser les cookies.|
|**Autoriser l’écriture de script Java**|Autoriser les scripts Java à exécuter dans le navigateur.|
|**Autoriser l’avertissement de fraude**|Autoriser les avertissements de fraude dans le navigateur.|

### Paramètres de l’application pour les applications
Tous les paramètres s’appliquent à iOS 8.0 et versions ultérieures.

|Nom du paramètre|Plus d’informations|
|----------------|-------|
|**Permettre l’installation des applications**|Laissez le périphérique pour accéder à l’app store et installer des applications.|
|**Demander un mot de passe pour accéder aux magasin d’applications**|Obliger l’utilisateur à entrer un mot de passe avant qu’ils peuvent visiter l’app store.|
|**Autoriser les achats dans l’application**|Autoriser les achats store à être effectué à partir d’une application en cours d’exécution.|
|**Autoriser les documents gérées dans les autres applications non gérées**|Autoriser les documents d’entreprise pour être affichés dans une application.<br>**Exemple :** Vous souhaitez empêcher les utilisateurs d’enregistrer des fichiers à partir de l’application OneDrive dans Dropbox. Configurez ce paramètre comme non. Une fois que le périphérique reçoit la stratégie (par exemple, après un redémarrage), il ne permettra plus l’enregistrement.|
|**Autoriser les documents non gérés dans d’autres applications gérées**|Autoriser n’importe quel document à afficher dans les applications gérées d’entreprise.|
|**Autoriser les visioconférences**|Autoriser les applications de conférence vidéo tels que FaceTime sur l’appareil.|
|**Autoriser l’utilisateur d’approuver nouveaux auteurs de l’application d’entreprise**|Permet à l’utilisateur Sélectionnez cette option pour approuver les applications qui n’ont pas été téléchargées à partir de l’app store.|


### Paramètres de l’application pour les jeux
Tous les paramètres s’appliquent à iOS 8.0 et versions ultérieures.

|Nom du paramètre|Plus d’informations|
|----------------|-------|
|**Autoriser l’ajout de contacts centre des jeux**|Autoriser l’utilisateur à ajouter des amis dans le centre de jeu.|
|**Autoriser les jeux multijoueurs**|Autoriser l’utilisateur à jouer sur l’appareil.|

### Paramètres de l’application pour le contenu multimédia
Tous les paramètres s’appliquent à iOS 8.0 et versions ultérieures.

|Nom du paramètre|Plus d’informations|
|----------------|-------|
|**Région évaluations**|Sélectionnez une région, puis sélectionnez la valeur maximale que les utilisateurs peuvent télécharger pour les **films**, **Télévisées** et **applications**.|
|**Autoriser le gros contenu multimédia Store**|Autoriser l’appareil d’accéder au contenu classé comme adulte à partir du magasin.|
|**Autoriser l’utilisateur à télécharger le contenu à partir du magasin iBook signalé comme « Érotisme »**|Autoriser l’utilisateur à télécharger la documentation de la catégorie « Érotisme ».|


### Paramètres de fonctionnalités appareil de matériel
Tous les paramètres s’appliquent à iOS 8.0 et versions ultérieures.

|Nom du paramètre|Plus d’informations|
|----------------|-------|
|**Autoriser l’appareil photo**|Spécifiez si l’appareil photo sur l’appareil peut être utilisé.|
|**Forcer appariés observations Apple pour utiliser la détection de poignet**|Lorsque activé, l’Apple Watch n’affichage des notifications lorsqu’elle n’est pas en cours porté.|
|**Demander un mot de passe jumelage pour les demandes d’AirPlay sortantes**|Demander un mot de passe jumelage lorsque l’utilisateur sert d’AirPlay pour transmettre du contenu avec d’autres appareils Apple.|

### Paramètres du périphérique fonctionnalités cellulaire
Tous les paramètres s’appliquent à iOS 8.0 et versions ultérieures.

|Nom du paramètre|Plus d’informations|
|----------------|-------|
|**Autoriser l’itinérance vocale**|Autoriser la voix d’itinérance lorsque l’appareil est dans un réseau cellulaire.|
|**Autoriser l’itinérance de données**|Autoriser les données d’itinérance lorsque l’appareil est dans un réseau cellulaire.|
|**Autoriser les récupérer en arrière-plan global en cas d’itinérance**|Laissez le périphérique extraire les données telles que courrier électronique lorsque celui-ci est d’itinérance sur un réseau cellulaire.|

### Paramètres du périphérique fonctionnalités pour les fonctionnalités
Tous les paramètres s’appliquent à iOS 8.0 et versions ultérieures.

|Nom du paramètre|Plus d’informations|
|----------------|-------|
|**Autoriser Siri**|Autoriser l’utilisation de l’assistant de voix Siri sur l’appareil.|
|**Autoriser Siri lors de l’appareil est verrouillé**|Autoriser l’utilisation de l’assistant de voix Siri sur le périphérique lorsqu’il est verrouillé.|
|**Autoriser la numérotation vocale**|Autoriser l’utilisation de la fonctionnalité composition vocale sur l’appareil.|
|**Ne pas autoriser largage à partir des applications gérées**|Taquets gèrent applications à partir de la possibilité d’envoyer des données via. Largage.|


### Paramètres pour les applications conformes et non conformes
Dans la **compatible &amp; applications non conformes** liste, spécifiez une liste des applications conformes en utilisant les informations suivantes.

> [!NOTE]
> Une seule stratégie peut contenir uniquement une liste des applications conformes ou une liste des applications non conformes. Vous ne pouvez pas spécifier à la fois dans la même stratégie.

|Nom du paramètre|Plus d’informations|
|----------------|--------------------|
|**Signaler non-conformité lorsque les utilisateurs installer les applications répertoriées**|Répertorier les applications (ne pas gérées par Intune) que les utilisateurs n’êtes pas autorisés à installer et exécuter.|
|**Signaler non-conformité lorsque les utilisateurs installer des applications qui ne sont pas répertoriées**|Liste des utilisateurs sont autorisés à installer les applications. Pour rester compatible, les utilisateurs doivent installer pas les applications qui ne sont pas répertoriées. Applications qui sont gérées par Intune sont automatiquement autorisées.|
|**Ajouter**|Ajouter une application à la liste sélectionnée. Spécifiez un nom de votre choix, vous pouvez également l’éditeur de l’application et l’URL à l’application dans l’app store. Consultez « spécifient des URL vers application stores » plus loin dans cette rubrique pour obtenir une aide supplémentaire.|
|**Importer des applications**|Importer une liste des applications que vous avez spécifié dans un fichier de valeurs séparées par des virgules. Dans le fichier, utilisez ce format : nom de l’application, publisher, URL de l’application.|
|**Modifier**|Modifier le nom, publisher et l’URL de l’application sélectionnée.|
|**Supprimer**|Supprimer l’application sélectionnée de la liste.|

### Paramètres du mode plein écran

|Nom du paramètre|Plus d’informations|
|----------------|--------------------|
|**Sélectionnez une application gérée qui est autorisée à exécuter lorsque l’appareil est en mode plein écran**|Cliquez sur **Parcourir**, puis spécifiez l’application gérée ou l’application à partir d’un magasin qui sera autorisé à exécuter lorsque l’appareil est en mode plein écran. Aucune autres applications ne pourront s’exécuter sur l’appareil. Pour obtenir de l’aide, voir « Comment spécifient des URL vers application stores » plus loin dans cette rubrique.|
|**Autoriser tactile**|Activer ou désactiver l’écran tactile sur l’appareil.|
|**Autoriser la rotation de l’écran**|Activer ou désactiver la modification de l’orientation de l’écran lorsque l’utilisateur fait pivoter l’appareil.|
|**Autoriser les boutons de volume**|Activer ou désactiver l’utilisation des boutons volume sur l’appareil.|
|**Autoriser le changement de sonnerie**|Activer ou désactiver le commutateur sonnerie (muet) sur l’appareil.|
|**Autoriser le bouton de veille écran veille**|Activer ou désactiver le bouton écran veille veille sur l’appareil.|
|**Autoriser verrouillage automatique**|Activer ou désactiver le verrouillage automatique de l’appareil.|
|**Activer la lecture audio mono**|Activer ou désactiver le paramètre **audio Mono**d’accessibilité.|
|**Activer le voice over**|Activer ou désactiver le paramètre **VoiceOver**qui lit à haute voix du texte sur l’affichage du périphérique d’accessibilité.|
|**Activer le voice over ajustements**|Activer ou désactiver les ajustements de voiceover, qui permettent à l’utilisateur d’ajuster la fonction VoiceOver (par exemple, la vitesse à l’écran le texte est lu à haute voix).|
|**Activer le zoom**|Activer ou désactiver le paramètre d’accessibilité **effectuer un zoom avant** , qui permet à l’utilisateur tactile permet d’effectuer un zoom pour l’affichage du périphérique.|
|**Activer l’ajustement de zoom**|Activer ou désactiver les ajustements de zoom, qui permettent à l’utilisateur d’ajuster la fonction de zoom.|
|**Activez inverser les couleurs**|Activer ou désactiver le paramètre **Inverser les couleurs** d’accessibilité, qui ajuste l’affichage pour aider les utilisateurs atteintes de troubles visuels.|
|**Activer l’ajustement des inverser les couleurs**|Activer ou désactiver les ajustements inverser les couleurs, qui permettent à l’utilisateur d’ajuster la fonction de couleurs inverser les.|
|**Activer les fonctions tactiles d’assistance**|Activer ou désactiver le paramètre d’accessibilité **D’assistance tactile** , qui permet à l’utilisateur d’effectuer à l’écran gestes qui peuvent s’avérer difficiles pour eux d’effectuer.|
|**Activer l’ajustement des fonctions tactiles d’assistance**|Activer ou désactiver des ajustements d’assistance tactile, qui permettent à l’utilisateur d’ajuster la fonction tactile d’assistance.|
|**Permettre des sélections de reconnaissance vocale**|Activer ou désactiver les paramètres d’accessibilité de **Sélection de la fonctionnalité vocale** , qui peuvent lu à haute voix le texte sélectionné par l’utilisateur.|
> [!NOTE]
> Les notes suivantes s’appliquent aux paramètres du mode plein écran pour les appareils iOS :
>
> -   Avant de configurer un appareil iOS en mode plein écran, vous devez utiliser l' [outil de configuration du Apple](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) ou le [Programme d’inscription des périphériques Apple](ios-device-enrollment-program-in-microsoft-intune) pour placer le périphérique en mode contrôlé. Pour plus d’informations sur l’outil de configuration du Apple, consultez la documentation d’Apple.
> -   Si l’application iOS que vous spécifiez est installée après le déploiement de la stratégie de configuration, le périphérique ne peut pas accéder mode plein écran jusqu’au redémarrage de celle-ci.

### Informations de référence pour les applications conformes et non conformes

Utilisez le **Rapport applications non conformes** pour afficher la conformité des autorisés et bloqués applications.

##### Pour exécuter le rapport applications non conformes

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), cliquez sur **rapports** &gt; **Rapport applications non conformes**.

2.  Sélectionnez les groupes de l’appareil que vous voulez rechercher, indiquez si vous voulez rechercher les applications conformes, applications non conformes ou les deux, puis cliquez sur **Afficher le rapport**.

#### Comment spécifier un URL à application stocke
Pour spécifier une URL de l’application dans la liste d’applications conformes et non conformes, ou l’option **Sélectionner une application gérée qui est autorisée à exécuter lorsque l’appareil est en mode plein écran** (iOS uniquement), utilisez le format suivant :

1. Utilisez un moteur de recherche, recherchez l’application que vous souhaitez utiliser dans l’App Store d’iTunes et ouvrez la page de l’application.

2. Copiez l’URL de la page et utilisez cette option en tant que l’URL pour configurer la liste d’applications conformes ou l’application que vous voulez exécuter en mode plein écran.

**Exemple :** Recherchez **Microsoft Word pour iPad**. L’URL que vous utilisez sera **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE]
> Vous pouvez également utiliser le logiciel iTunes pour rechercher l’application, puis utilisez la commande **Copier le lien** pour obtenir l’URL de l’application.

### Paramètres d’inscription
Tous les paramètres s’appliquent à iOS 8.0 et versions ultérieures.

|Nom du paramètre|Plus d’informations|
|----------------|--------------------|
|**Autoriser l’Activation verrouiller lorsque l’appareil est en mode contrôlé**|Activer l’option Verrouiller l’Activation sur les appareils iOS contrôlés.|

### Paramètres du mode contrôlés
Vous pouvez configurer les paramètres suivants sur les appareils exécutant iOS 8.0 et versions ultérieures qui sont en mode contrôlé.

### Paramètres du mode contrôlés pour les restrictions de l’appareil

|Nom du paramètre|Plus d’informations|
|----------------|--------------------|
|**Autoriser la modification du compte**|Autoriser l’utilisateur à modifier les paramètres de compte telles que les configurations de messagerie.|
|**Autoriser les modifications apportées à l’application paramètres de l’utilisation de données cellulaires**|Autoriser l’utilisateur de contrôler quelles applications sont autorisées à utiliser des données cellulaires.|
|**Permettre l’utilisation de l’effacement tout le contenu et option paramètres sur l’appareil**|Autoriser l’utilisateur à utiliser l’option d’effacement de tout le contenu et paramètres sur l’appareil.|
|**Autoriser l’utilisateur à activer les restrictions dans les paramètres du périphérique**|Autoriser l’utilisateur configurer les restrictions d’appareil (contrôle parental) sur l’appareil.|
|**Autoriser hôte le jumelage pour contrôler les appareils que peut jumeler un appareil iOS**|Autorisez hôte le jumelage pour permettre à l’administrateur contrôle les périphériques un appareil iOS pouvez jumeler.|
|**Autoriser l’utilisateur à installer des certificats et les profils de configuration**|Autoriser l’utilisateur à installer des certificats et les profils de configuration.|
|**Autoriser la modification de nom d’appareil**|Autoriser l’utilisateur à modifier le nom de l’appareil.|
|**Autoriser la modification du code secret**|Autoriser le mot de passe appareil à être ajoutées, modifiées ou supprimées.|
|**Autoriser le jumelage Apple Watch**|Autoriser le périphérique pour l’associer avec un Apple Watch.|
|**Autoriser la modification des paramètres de notification**|Autoriser l’utilisateur à modifier les paramètres de notification de périphérique.|
|**Autoriser la modification de papier peint**|Autoriser l’utilisateur à modifier le papier peint appareil.|

### Paramètres du mode contrôlés pour les restrictions de fonctionnalité

|Nom du paramètre|Plus d’informations|
|----------------|--------------------|
|**Autoriser largage**|Autoriser l’utilisation de la fonctionnalité largage pour échanger un contenu avec périphériques proches.|
|**Autoriser Siri au contenu générés par l’utilisateur de requête à partir d’Internet**|Autoriser Siri accéder aux sites Web pour répondre à des questions.|
|**Utiliser un filtre à inconvenances Siri**|Empêche Siri à partir de la dictée ou parlez vulgaires.|
|**Permettre la recherche Spotlight pour renvoyer les résultats à partir d’Internet**|Laisser recherche Spotlight se connecter à Internet pour fournir des résultats.|
|**Permettre la recherche de définition de word**|Autoriser la fonctionnalité iOS qui vous permet de sélectionner un mot et rechercher sa définition.|
|**Autoriser les claviers prédictives**|Permettre l’utilisation des claviers prédictives qui suggérer des mots que l’utilisateur peut souhaiter.|
|**Autoriser la correction automatique**|Permet au périphérique corriger automatiquement les mots mal orthographiés.|
|**Autoriser le clavier de la vérification orthographique**|Permet de vérifier l’orthographe de l’appareil.|
|**Autoriser les raccourcis clavier**|Permet d’utiliser des raccourcis clavier.|

### Paramètres du mode contrôlés pour les restrictions d’application

|Nom du paramètre|Plus d’informations|
|----------------|--------------------|
|**Autoriser la modification des paramètres de gestion de la confidentialité enterprise application**|Permet aux utilisateurs de modifier les paramètres de gestion de la confidentialité d’applications d’entreprise.|
|**Permettre l’installation des applications à l’aide de la Configuration de Apple et iTunes uniquement**|Active ou désactive l’App Store à partir de l’écran d’accueil appareil. Les utilisateurs peuvent toujours utiliser iTunes ou l’outil de configuration du Apple installer et mettre à jour des applications.|
|**Autoriser les téléchargements d’application automatique**|Autoriser d’acheter les applications sur les autres appareils pour télécharger automatiquement sur cet appareil. Ce paramètre n’affecte pas les mises à jour de l’application.|
|**Autoriser les modifications apportées aux paramètres de l’application de trouver mes amis**|Autoriser l’utilisateur à modifier les paramètres pour l’application de trouver mes amis.|
|**Autoriser l’accès au magasin iBook**|Autoriser l’utilisateur à parcourir et acheter des livres à partir du magasin iBook.|
|**Autoriser l’utilisation de l’application de Messages sur l’appareil**|Autoriser l’utilisation de l’application de Messages pour envoyer des messages texte.|
|**Autoriser l’utilisation de Podcasts**|Autoriser l’utilisation de l’application Podcasts.|
|**Autoriser l’utilisation du service de musique**|Autoriser l’utilisation de l’application de musique d’Apple.|
|**Autoriser le service de case d’option iTunes**|Autoriser l’utilisation de l’application de case d’option iTunes.|
|**Autoriser News Apple**|Autoriser l’utilisation de l’application de News d’Apple.|
|**Autoriser centre des jeux**|Autoriser l’utilisation de l’application Centre des jeux.|


### Afficher ou masquer applications

Utilisez les **cellules masquées et liste d’applications affichée** pour contrôler les opérations suivantes sur les appareils contrôlés exécutant iOS 9,3 ou version ultérieure :

- Spécifiez une liste des applications qui sont masqués pour les utilisateurs. Les utilisateurs ne peuvent pas afficher ou lancer ces applications.
- Spécifiez une liste des applications que les utilisateurs peuvent afficher et barre de lancement. Aucune autres applications peuvent être affichées ou lancées.


#### Comment créer une liste des applications masquées ou affichées

Spécifier les paramètres suivants :

|Nom du paramètre|Plus d’informations|
|-|-|
|**Liste d’applications masqués et affichés**|Activez ce paramètre si vous voulez créer une liste d’applications masquées ou affichées.|
|**Masquer les applications à partir d’utilisateurs répertoriées**|Sélectionnez cette option si vous voulez créer une liste des applications qui seront masquées auprès des utilisateurs.|
|**Afficher uniquement les applications répertoriées pour les utilisateurs**|Sélectionnez cette option si vous voulez créer une liste des applications qui sont présentées aux utilisateurs.<br>Lorsque vous créez ce type de liste, toutes les autres applications à l’exception des **paramètres** d’iOS et applications **Phone** (pour les iPhone) sont masquées.<br>En outre, vous devez ajouter le portail d’entreprise et toutes les applications que vous avez déployé et de gérez avec Intune à la liste.|
|**Ajouter**|Ajoute une application à la liste sélectionnée.<br>Pour obtenir la liste masquée, vous devez spécifier le **nom**, **Publisher**et **URL de l’application ou l’ID de l’ensemble de guides** de chaque application que vous voulez masquer.<br>Pour obtenir la liste affichée, vous pouvez soit **Sélectionner une application gérée** qui vous donne une liste des applications que vous gérez avec Intune pour sélectionner à partir de, ou sélectionnez une application du store, après quoi vous devez spécifier le **nom**, **Publisher**et **URL de l’application ou l’ID de l’ensemble de guides** de chaque application que vous voulez afficher.|
|**Importer des applications**|Importer une liste des applications que vous avez spécifié dans un fichier de valeurs séparées par des virgules. Utiliser la mise en forme, nom de l’application publisher, URL de l’application dans le fichier.|
|**Modifier**|Nous allons vous modifiez le nom, publisher et l’URL de l’application sélectionnée.|
|**Supprimer**|Supprime l’application sélectionnée dans la liste.|

#### Informations d’application pour les applications iOS intégrée

Utilisez les informations de cette liste pour identifier le nom, publisher et l’ID d’ensemble des applications iOS intégrée que vous pouvez afficher ou masquer. Si vous souhaitez afficher ou masquer toutes les applications dans la liste, vous pouvez copier les données ci-dessous dans un fichier texte avec l' extension **.csv**, puis utilisez l’option **Importer des applications** pour importer l’ensemble des applications simultanément.

```
App Store,Apple,com.apple.AppStore
Calculator,Apple,com.apple.calculator
Calendar,Apple,com.apple.mobilecal
Camera,Apple,com.apple.camera
Clock,Apple,com.apple.mobiletimer
Compass,Apple,com.apple.compass
Contacts,Apple,com.apple.MobileAddressBook
FaceTime,Apple,com.apple.facetime
Find Friends,Apple,com.apple.mobileme.fmf1
Find iPhone,Apple,com.apple.mobileme.fmip1
Game Center,Apple,com.apple.gamecenter
GarageBand,Apple,com.apple.mobilegarageband
Health,Apple,com.apple.Health
iBooks,Apple,com.apple.iBooks
iTunes Store,Apple,com.apple.MobileStore
iTunes U,Apple,com.apple.itunesu
Keynote,Apple,com.apple.Keynote
Mail,Apple,com.apple.mobilemail
Maps,Apple,com.apple.Maps
Messages,Apple,com.apple.MobileSMS
Music,Apple,com.apple.Music
News,Apple,com.apple.news
Notes,Apple,com.apple.mobilenotes
Numbers,Apple,com.apple.Numbers
Pages,Apple,com.apple.Pages
Photo Booth,Apple,com.apple.Photo-Booth
Photos,Apple,com.apple.mobileslideshow
Podcasts,Apple,com.apple.podcasts
Reminders,Apple,com.apple.reminders
Safari,Apple,com.apple.mobilesafari
Settings,Apple,com.apple.Preferences
Stocks,Apple,com.apple.stocks
Tips,Apple,com.apple.tips
Videos,Apple,com.apple.videos
VoiceMemos,Apple,com.apple.VoiceMemos
Wallet,Apple,com.apple.Passbook
Watch,Apple,com.apple.Bridge
Weather,Apple,com.apple.weather


```




## Paramètres de stratégie personnalisés

Utilisez la Microsoft Intune **stratégie personnalisée iOS** pour déployer les paramètres que vous avez créé à l’aide de l' [outil de configuration du Apple](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) pour les appareils iOS. Cet outil vous permet de créer de nombreux paramètres qui contrôlent le fonctionnement de ces périphériques et les exporter vers un profil de configuration. Vous pouvez importer ce profil de configuration dans une stratégie de personnalisé Intune iOS et déployer les paramètres pour les utilisateurs et périphériques de votre organisation.

Cette fonctionnalité permet de déployer des paramètres d’iOS qui ne peuvent pas être configurés avec les stratégies de configuration générale Intune.

### Conditions préalables
Avant de commencer, vous devez avoir installé l’outil de configuration Apple et créé un fichier de configuration qui contient les paramètres que vous voulez déployer à des utilisateurs ou des appareils mobiles. Vous pouvez télécharger et en savoir plus sur la configuration du Apple à partir [Du Mac App Store](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12).

> [!NOTE]
> Intune ne signale pas la conformité des paramètres individuels dans une stratégie personnalisée iOS. Toutefois, la conformité globale de la stratégie est signalée.

### Paramètres généraux

|Nom du paramètre|Plus d’informations|
    |----------------|--------------------|
    |**Nom**|Entrez un nom unique pour la stratégie personnalisée iOS pour vous aider à identifier dans la console Intune.|
    |**Description**|Fournir une description qui offre une vue d’ensemble d’iOS stratégie personnalisée et autres informations pertinentes qui vous aide à rechercher.|

### Paramètres personnalisés

|Nom du paramètre|Plus d’informations|
    |----------------|--------------------|
|**Nom du profil configuration personnalisée (présenté aux utilisateurs)**|Indiquez un nom pour la stratégie tel qu’il s’affichera sur l’appareil et dans les rapports de stratégie Intune.|
|**Fichier de configuration de profil**|Cliquez sur **Importer**, puis puis naviguez vers le profil de configuration que vous avez créé à l’aide de l’outil de configuration d’Apple. **Remarque :** Vérifiez que les paramètres que vous exportez à partir de l’outil de configuration du Apple sont compatibles avec la version d’iOS sur les appareils sur lesquels vous déployez la stratégie personnalisée iOS. Pour les informations sur les paramètres comment incompatibles sont résolus, recherchez **Référence du profil de Configuration** et de **Référence de protocole Mobile Device Management** sur le site Web [Pour les développeurs Apple](https://developer.apple.com/) .|
    |**Détails de profil de configuration**|Affichez le code XML pour le profil de configuration que vous avez importés.|

### Voir aussi
[Gérer les paramètres et fonctionnalités sur vos appareils avec stratégies Intune Microsoft](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
