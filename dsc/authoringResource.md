# Build personnalisé Windows PowerShell Desired état Configuration ressources Test6 - test

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell vous le souhaitez état Configuration (DSC) dispose des ressources intégrés que vous pouvez utiliser pour configurer votre environnement. (Pour plus d’informations, voir [Intégré Windows PowerShell vous le souhaitez Configuration de ressources d’état](builtInResource.md).) Cette rubrique fournit une vue d’ensemble du développement des ressources et des liens vers des rubriques contenant des informations spécifiques et des exemples.

## Composants de la ressource DSC

Une ressource DSC est un module de Windows PowerShell. Le module contient le schéma (la définition des propriétés configurables) et l’implémentation (le code qui effectue le travail réel spécifié par une configuration) de la ressource. Un schéma de ressource DSC peut être défini dans un fichier MOF et la mise en œuvre est effectuée par un module de script. À partir de la prise en charge des classes de PowerShell dans la version 5, le schéma et la mise en œuvre les deux définissable dans une classe. Les rubriques suivantes décrivent plus en détail comment créer des ressources DSC.

* [Écriture d’une ressource DSC personnalisée avec MOF](authoringResourceMOF.md) 
* [L’implémentation d’une ressource DSC dans C#](authoringResourceMofCS.md) 
* [Écriture d’une ressource DSC personnalisée avec les classes de PowerShell](authoringResourceClass.md) 
* [Ressources de composite : à l’aide d’une configuration DSC en tant que ressource](authoringResourceComposite.md) 
* [À l’aide de l’outil Concepteur de ressources](authoringResourceMofDesigner.md) 
