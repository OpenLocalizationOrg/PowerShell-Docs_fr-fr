# Ressources d’environnement DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Les ressources de __l’environnement__ dans le module Windows PowerShell vous le souhaitez état Configuration (DSC) fournit un mécanisme pour gérer les variables d’environnement système.

## Syntaxe
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| Nom| Indique le nom de la variable d’environnement pour lequel vous souhaitez garantir un état spécifique.| 
| Vérifiez| Indique si une variable existe. Définir cette propriété à __présent__ pour créer la variable d’environnement si elle n’existe pas ou pour s’assurer que sa valeur correspond à ce qui est fourni par le biais de la propriété __Value__ si la variable existe déjà. Définissez-la sur __Absent__ pour supprimer la variable si elle existe.| 
| Path| Définit la variable d’environnement est configurée. Définir cette propriété sur __$true__ si la variable est le __chemin d’accès__ ; Sinon, affectez-lui __$false__. La valeur par défaut est __$false__. Si la variable en cours de configuration est le __chemin d’accès__ , la valeur fournie par le biais de la propriété __Value__ sera ajoutée à la valeur existante.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant que cette ressource est configurée. Par exemple, si l’ID de la ressource configuration du bloc de script que vous souhaitez exécuter est tout d’abord __ResourceName__ et son type est __ResourceType__, la syntaxe d’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 
| Valeur| Valeur à affecter à la variable d’environnement.| 

## Exemple

L’exemple suivant vérifie que __TestEnvironmentVariable__ n’est présente et qu’elle a la valeur __TestValue__. Si elle n’est pas présent, il le crée.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
