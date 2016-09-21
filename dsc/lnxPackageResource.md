# DSC pour Linux nxPackage ressource

La ressource **nxPackage** dans PowerShell souhaité état Configuration (DSC) fournit un mécanisme pour gérer les packages sur un nœud Linux.

## Syntaxe

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]
    
}
```

## Propriétés

|  Propriété |  Description | 
|---|---|
| Nom| Le nom du package pour lequel vous voulez vous assurer un état spécifique.| 
| Garantir| Détermine s’il faut vérifier l’existence du package. Définissez cette propriété sur « Heure actuelle » pour garantir que le package existe. Définissez-la à « Absent » pour garantir que le package n’existe pas. La valeur par défaut est « Heure actuelle ».|  
| PackageManager n’est| Valeurs prises en charge sont « yum », « nature » et « zypper ». Spécifie le Gestionnaire de package à utiliser lors de l’installation des packages. Si le **chemin d’accès** est spécifié, le chemin d’accès fourni servira à installer le package. Dans le cas contraire, un gestionnaire de Package servira à installer le package à partir d’un référentiel préconfiguré. Si ni **PackageManager n’est** ni **chemin d’accès** est fourni, le Gestionnaire de package par défaut pour le système est utilisé.| 
| Chemin d’accès| Le chemin d’accès du fichier dans lequel se trouve le package| 
| PackageGroup| Si **$true**, le **nom** doit correspondre au nom d’un groupe de package pour une utilisation avec un **PackageManager n’est**. **PacakgeGroup** n’est pas valide lorsque vous fournissez un **chemin d’accès**.| 
| Arguments| Chaîne d’arguments qui seront passées au lot exactement comme prévu.| 
| Code retour| Le code de retour attendu. Si le rendement effectif code ne correspond pas à que la valeur attendue fournies ici, que la configuration renverra une erreur.| 
| DependsOn | Indique que la configuration d’une autre ressource doit s’exécuter avant que cette ressource est configurée. Par exemple, si l' **ID** du bloc de script de configuration de ressources que vous voulez exécuter tout d’abord est **ResourceName** et son type est le **type de ressource**, la syntaxe pour l’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 

## Exemple

L’exemple suivant vérifie que le package nommé « httpd » est installé sur un ordinateur Linux, l’utilisation du Gestionnaire de package « Yum ».

```
Import-DSCResource -Module nx 

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```
