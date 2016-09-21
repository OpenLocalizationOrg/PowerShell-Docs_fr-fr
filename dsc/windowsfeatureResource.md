# DSC WindowsFeature ressource

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource **WindowsFeature** dans le module Windows PowerShell vous le souhaitez état Configuration (DSC) fournit un mécanisme pour vous assurer que les rôles et les fonctionnalités sont ajoutées ou supprimées sur un nœud cible.

## Syntaxe

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| Nom| Indique le nom du rôle ou fonctionnalité que vous voulez être sûr est ajouté ou supprimé. Ceci est identique à la propriété __nom__ de l’applet de commande [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) et pas le nom d’affichage du rôle ou de fonctionnalité.| 
| Informations d’identification| Indique les informations d’identification à utiliser pour ajouter ou supprimer le rôle ou la fonctionnalité.| 
| Garantir| Indique si le rôle ou la fonctionnalité est ajoutée. Pour vous assurer que le rôle ou la fonctionnalité est ajoutée, définissez cette propriété à « Heure actuelle » pour vous assurer que le rôle ou la fonctionnalité est supprimée, définissez la propriété à « Absent ».| 
| IncludeAllSubFeature| Définir cette propriété sur __$true__ pour vérifier l’état de toutes ses sous-fonctionnalités requises avec l’état de la fonctionnalité que vous spécifiez avec la propriété __Name__ .| 
| Journaux| Indique le chemin d’accès à un fichier journal où vous souhaitez le fournisseur de ressources pour vous connecter à l’opération.| 
| DependsOn| Indique que la configuration d’une autre ressource doit s’exécuter avant que cette ressource est configurée. Par exemple, si l’ID de la ressource configuration du bloc de script que vous voulez exécuter tout d’abord est __ResourceName__ et son type est le __type de ressource__, la syntaxe pour l’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 
| Source| Indique l’emplacement du fichier source à utiliser pour l’installation, si nécessaire.| 

## Exemple
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```

