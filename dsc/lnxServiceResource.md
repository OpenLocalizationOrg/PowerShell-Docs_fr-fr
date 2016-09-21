# DSC pour Linux nxService ressource

La ressource **nxService** dans PowerShell souhaité état Configuration (DSC) fournit un mécanisme pour gérer les services sur un nœud Linux.

## Syntaxe

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | system }  ]
    [ Enambled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## Propriétés
|  Propriété |  Description | 
|---|---|
| Nom| Le nom de la service/processus à configurer.| 
| Contrôleur| Le type de service contrôleur à utiliser lors de la configuration du service.| 
| Activé| Indique si le service démarre lors du démarrage.| 
| État| Indique si le service est en cours d’exécution. Définir cette propriété de la valeur « Arrêté » pour vous assurer que le service n’est pas en cours d’exécution. Définissez-la sur « Exécuter » pour vous assurer que le service n’est pas en cours d’exécution.| 
| DependsOn | Indique que la configuration d’une autre ressource doit s’exécuter avant que cette ressource est configurée. Par exemple, si l' **ID** du bloc de script de configuration de ressources que vous voulez exécuter tout d’abord est **ResourceName** et son type est le **type de ressource**, la syntaxe pour l’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 


## Informations supplémentaires

La ressource **nxService** ne crée pas une définition de service ou un script pour le service s’il n’existe pas. Vous pouvez utiliser la Configuration de l’état PowerShell souhaité **nxFile** ressource pour gérer l’existence ou le contenu du fichier de définition de service ou de script.

## Exemple

L’exemple suivant montre la configuration du service « httpd » (pour Apache HTTP Server), inscrite auprès du contrôleur de service **SystemD** .

```
Import-DSCResource -Module nx 

Node $node {
#Apache Service
nxService ApacheService 
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```
