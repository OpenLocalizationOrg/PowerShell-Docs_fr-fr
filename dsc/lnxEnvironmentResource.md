# DSC pour Linux nxEnvironment ressource

La ressource **nxEnvironment** dans PowerShell souhaité état Configuration (DSC) fournit un mécanisme de gestion des variables d’environnement système sur un nœud Linux.

## Syntaxe

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## Propriétés

|  Propriété |  Description | 
|---|---|
| Nom| Indique le nom de la variable d’environnement pour lequel vous voulez vous assurer un état spécifique.| 
| Valeur| Valeur à affecter à la variable d’environnement.| 
| Garantir| Détermine s’il faut vérifier l’existence de la variable. Définissez cette propriété sur « Heure actuelle » pour garantir que la variable existe. Définissez-la à « Absent » pour garantir que la variable n’existe pas. La valeur par défaut est « Heure actuelle ».| 
| Chemin d’accès| Définir la variable d’environnement en cours de configuration. Définir cette propriété sur **$true** si la variable est le **chemin d’accès** ; dans le cas contraire, définissez-la sur **$false**. La valeur par défaut est **$false**. Si la variable en cours de configuration est le **chemin d’accès** , la valeur fournie via la propriété **valeur** sera ajoutée à la valeur existante.| 
| DependsOn | Indique que la configuration d’une autre ressource doit s’exécuter avant que cette ressource est configurée. Par exemple, si l' **ID** du bloc de script de configuration de ressources que vous voulez exécuter tout d’abord est **ResourceName** et son type est le **type de ressource**, la syntaxe pour l’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 

## Informations supplémentaires

* Si le **chemin d’accès** est absent ou défini sur **$false**, variables d’environnement sont gérées dans `/etc/environment`. Vos programmes ou des scripts peuvent nécessiter une configuration de source de la `/etc/environment` fichier accéder aux variables d’environnement géré.
* Si le **chemin d’accès** est défini sur **$true**, la variable d’environnement est gérée dans le fichier `/etc/profile.d/DSCenvironment.sh`. Ce fichier sera créé s’il n’existe pas. Si **s’assurer** qu’est défini sur « Absent » et le **chemin d’accès** est défini sur **$true**, une variable d’environnement existante sera uniquement supprimée de `/etc/profile.d/DSCenvironment.sh` et non à partir d’autres fichiers.

## Exemple

L’exemple suivant montre comment utiliser la ressource **nxEnvironment** pour vous assurer que **TestEnvironmentVariable** est présente et a la valeur « Test-valeur ». Si **TestEnvironmentVariable** n’apparaît pas, il sera créé.

```
Import-DSCResource -Module nx 


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```


