# DSC pour Linux nxGroup ressource

La ressource **nxGroup** dans PowerShell souhaité état Configuration (DSC) fournit un mécanisme pour gérer des groupes locaux sur un nœud Linux.

## Syntaxe

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## Propriétés

|  Propriété |  Description | 
|---|---|
| Nom de groupe| Spécifie le nom du groupe pour lequel vous voulez vous assurer un état spécifique.| 
| Garantir| Détermine s’il faut vérifier l’existence du groupe. Définissez cette propriété sur « Heure actuelle » pour garantir que le groupe existe. Définissez-la à « Absent » pour garantir que le groupe n’existe pas. La valeur par défaut est « Heure actuelle ».| 
| Membres| Spécifie les membres qui constituent le groupe.| 
| MembersToInclude| Spécifie les utilisateurs pour lesquels vous voulez être sûr sont membres du groupe.| 
| MembersToExclude| Spécifie les utilisateurs pour lesquels vous voulez veiller à ne sont pas membres du groupe.| 
| PreferredGroupID| Définit l’id du groupe à la valeur fournie si possible. Si l’id de groupe est actuellement en cours d’utilisation, l’id du groupe disponible suivante est utilisée.| 
| DependsOn | Indique que la configuration d’une autre ressource doit s’exécuter avant que cette ressource est configurée. Par exemple, si l' **ID** du bloc de script de configuration de ressources que vous voulez exécuter tout d’abord est **ResourceName** et son type est le **type de ressource**, la syntaxe pour l’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 

## Exemple

L’exemple suivant vérifie que l’utilisateur « monuser » existe et est un membre du groupe « DBusers ».

```
Import-DSCResource -Module nx 

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}
 
nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"            
}
}
```
