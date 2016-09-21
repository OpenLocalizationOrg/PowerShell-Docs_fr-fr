# DSC pour Linux nxFileLine ressource

La ressource **nxFileLine** dans PowerShell souhaité état Configuration (DSC) fournit un mécanisme de gestion des lignes dans un fichier de configuration sur un nœud Linux.

## Syntaxe

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Propriétés

|  Propriété |  Description | 
|---|---|
| Chemin d’accès| Chemin d’accès complet au fichier à gérer des lignes dans sur le nœud cible.| 
| ContainsLine| Une ligne pour garantir existe dans le fichier. Cette ligne sera ajoutée au fichier s’il n’existe pas dans le fichier. **ContainsLine** est obligatoire, mais peuvent être définies pour une chaîne vide (« ContainsLine = "') s’il n’est pas nécessaire.| 
| DoesNotContainPattern| Un modèle d’expression régulière pour les lignes qui ne doit pas exister dans le fichier. Pour toutes les lignes qui existent dans le fichier qui correspondent à cette expression régulière, la ligne a supprimé à partir du fichier.| 
| DependsOn | Indique que la configuration d’une autre ressource doit s’exécuter avant que cette ressource est configurée. Par exemple, si l' **ID** du bloc de script de configuration de ressources que vous voulez exécuter tout d’abord est **ResourceName** et son type est le **type de ressource**, la syntaxe pour l’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 

## Exemple

Cet exemple illustre l’utilisation de la ressource **nxFileLine** pour configurer le `/etc/sudoers` fichier, veiller à ce que l’utilisateur : monuser est configuré pour requiretty pas.

```
Import-DSCResource -Module nx 

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
} 
```

