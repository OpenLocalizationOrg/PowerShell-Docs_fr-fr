# DSC pour Linux nxUser ressource

La ressource **nxUser** dans PowerShell souhaité état Configuration (DSC) fournit un mécanisme pour gérer les utilisateurs locaux sur un nœud Linux.

## Syntaxe

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ Mode = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Propriétés

|  Propriété |  Indique le nom du compte pour lequel vous voulez vous assurer un état spécifique. | 
|---|---|
| Nom d’utilisateur| Spécifie l’emplacement où vous souhaitez vérifier l’état d’un fichier ou un répertoire.| 
| Garantir| Indique si le compte existe. Définissez cette propriété sur « Heure actuelle » pour vous assurer que le compte existe et défini sur « Absent » pour vous assurer que le compte n’existe pas.| 
| Nom complet| Une chaîne qui contient le nom complet à utiliser pour le compte d’utilisateur.| 
| Description| La description pour le compte d’utilisateur.| 
| Mot de passe| Le hachage du mot de passe des utilisateurs sous la forme appropriée pour l’ordinateur Linux. En règle générale, il s’agit d’un ça-256 salés ou hachage ça-512. Sous Debian et Ubuntu Linux, cette valeur peut être générée avec la commande mkpasswd. Pour les autres distros Linux, la méthode crypt d’une bibliothèque de Python Crypt peut être utilisée pour générer le hachage.| 
| Désactivé| Indique si le compte est activé. Définir cette propriété sur **$true** pour vous assurer que ce compte est désactivé et défini sur **$false** pour vous assurer qu’il est activé.| 
| PasswordChangeRequired| Indique si l’utilisateur peut modifier le mot de passe. Définir cette propriété sur **$true** pour vous assurer que l’utilisateur ne peut pas modifier le mot de passe et défini sur **$false** pour autoriser l’utilisateur à modifier le mot de passe. La valeur par défaut est **$false**. Cette propriété est évaluée uniquement si le compte d’utilisateur n’existe pas déjà et est en cours de création.| 
| HomeDirectory| Le répertoire de base pour l’utilisateur.| 
| GroupID| L’ID du groupe principal pour l’utilisateur.| 
| DependsOn | Indique que la configuration d’une autre ressource doit s’exécuter avant que cette ressource est configurée. Par exemple, si l’ID de la ressource configuration du bloc de script que vous voulez exécuter tout d’abord est « ResourceName » et son type est « Type de ressource », la syntaxe pour l’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 

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
