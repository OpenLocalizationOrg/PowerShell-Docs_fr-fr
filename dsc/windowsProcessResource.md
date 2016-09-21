# DSC WindowsProcess ressource

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource **WindowsProcess** dans le module Windows PowerShell vous le souhaitez état Configuration (DSC) fournit un mécanisme pour configurer des processus sur un nœud cible.

## Syntaxe

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## Propriétés
|  Propriété  |  Description   | 
|---|---| 
| Arguments| Indique une chaîne d’arguments à passer au processus en tant que-est. Si vous avez besoin de passer plusieurs arguments, placées dans cette chaîne.| 
| Chemin d’accès| Indique le chemin d’accès à l’exécutable du processus. Si vous définissez cette propriété sur le nom du fichier exécutable, DSC se présentera dans la variable de __chemin d’accès__ . Si vous donnez un nom de domaine complet, le processus doivent exister il car DSC ne vérifie pas la variable de __chemin d’accès__ dans ce cas.| 
| Informations d’identification| Indique les informations d’identification pour démarrer le processus.| 
| Garantir| Indique si le processus existe. Définissez cette propriété sur « Heure actuelle » pour vous assurer que le processus existe. Dans le cas contraire, attribuez-lui « Absent ». La valeur par défaut est « Heure actuelle ».| 
| DependsOn | Indique que la configuration d’une autre ressource doit s’exécuter avant que cette ressource est configurée. Par exemple, si l’ID de la ressource configuration du bloc de script que vous voulez exécuter tout d’abord est __ResourceName__ et son type est le __type de ressource__, la syntaxe pour l’utilisation de cette propriété est « DependsOn = « [du type de ressource] ResourceName » « ».| 
| StandardErrorPath| Indique le chemin d’accès pour écrire l’erreur type. Il n’importe quel fichier existant est remplacé.| 
| StandardInputPath| Indique l’emplacement de l’entrée standard.| 
| StandardOutputPath| Indique l’emplacement pour écrire la sortie standard. Il n’importe quel fichier existant est remplacé.| 
| WorkingDirectory| Indique l’emplacement qui sera utilisé comme répertoire de travail actuel pour le processus.| 
