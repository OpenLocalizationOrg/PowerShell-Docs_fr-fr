# Windows PowerShell vous le souhaitez Test de présentation de l’état Configuration 3

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Cette rubrique décrit la fonctionnalité de Windows PowerShell vous le souhaitez état Configuration (DSC) dans Windows PowerShell. Vous pouvez utiliser cette rubrique pour obtenir une vue d’ensemble de DSC et pour rechercher les ressources de documentation que vous devez comprendre et utiliser les DSC.

## Description de la fonctionnalité
DSC est une nouvelle plateforme de gestion de Windows PowerShell qui permet de déploiement et la gestion des données de configuration pour les services et la gestion de l’environnement dans lequel ces services s’exécutent.

DSC propose un ensemble d’extensions de langage Windows PowerShell, de nouvelles applets de commande Windows PowerShell et de ressources que vous pouvez utiliser pour spécifier de manière déclarative comment vous souhaitez que votre environnement logiciel doit être configuré. Il fournit également un moyen de mettre à jour et gérer des configurations existantes.

## Applications pratiques
Voici quelques exemples de scénarios dans lequel vous pouvez utiliser des ressources de DSC intégrées pour configurer et gérer un ensemble d’ordinateurs (également appelés nœuds cible) dans une façon automatisée :

* Activation ou désactivation de fonctionnalités et les rôles de serveur
* Gérer les paramètres du Registre
* Gestion des fichiers et des répertoires
* Démarrer, arrêter et gestion des processus et des services
* Gestion des comptes d’utilisateurs et groupes
* Déploiement d’un nouveau logiciel
* Gestion des variables d’environnement
* En cours d’exécution de scripts Windows PowerShell
* Résolution d’une configuration a évolué en dehors de l’état souhaité
* Découverte de l’état de configuration sur un nœud donné

## Concepts clés
DSC est une plateforme déclarative utilisée pour la configuration, le déploiement et la gestion de systèmes. Il comprend trois composants principaux :

* [Les configurations](configurations.md) sont des scripts PowerShell déclaratives qui définissent et configurer les instances de ressources. Fonction s’exécutant la configuration, DSC (et les ressources appelés par la configuration) simplement « faire en sorte que », veiller à ce que le système existe dans l’état disposé par la configuration. DSC configurations sont également idempotent : le Gestionnaire de Configuration Local (PPCM) continuent à garantir que les ordinateurs sont configurés dans quelle que soit la configuration d’état déclare.
* Les ressources sont impératives blocs de construction de DSC qui sont écrits modéliser les divers composants d’un système sous-adresse et implémenter le flux de contrôle de leurs États de modifications. Ils se trouvent dans les modules PowerShell et peuvent être écrites pour modéliser une opération aussi précis qu’un serveur IIS ou un ordinateur exécutant dans Azure ou génériques comme un fichier ou un processus de Windows.
* Le Gestionnaire de Configuration Local (PPCM) est le moteur par lequel DSC facilite l’interaction entre les ressources et configurations. La PPCM consulte régulièrement au système en utilisant le flux de contrôle implémenté par des ressources pour vous assurer que l’état disposé par une Configuration est conservé. Si le système est en dehors de l’état, le PPCM utilise plus logique à l’intérieur les ressources pour « faire en sorte que « conformément à la déclaration de Configuration. 

DSC inclut également un nombre d’outils autoriser la création de configurations, générer aide ressources DSC, appeler configurations et gérer le PPCM, applets de commande et des mots clés de langue. La plupart de ces applets de commande vous pouvez trouver dans Windows 8.1 dans le cadre du module PsDesiredStateConfig (y compris `Start-DscConfiguration`, `Set-DscLocalConfigurationManager`, et `Get-DscResource`). La xDscResourceDesigner (figurant dans la [Galerie de PowerShell](https://www.powershellgallery.com/packages/xDSCResourceDesigner/)) est un ensemble d’applets de commande qui simplifient l’évolution des ressources DSC.

## Voir aussi
* [Configurations DSC](configurations.md)
* [DSC ressources](resources.md)
* [Configuration du Gestionnaire de Configuration Local](metaconfig.md)

