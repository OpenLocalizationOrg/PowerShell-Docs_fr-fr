#Ressource DSC utilisateur#

 
>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0


La ressource __d’utilisateur__ dans le module Windows PowerShell vous le souhaitez état Configuration (DSC) fournit un mécanisme pour gérer les comptes d’utilisateurs locaux sur le nœud cible.


##Syntaxe##

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## Propriétés
|  Propriété  |  Description   | 
|---|---| 
| Nom d’utilisateur| Indique le nom du compte pour lequel vous voulez vous assurer un état spécifique.| 
| Description| Indique la description que vous souhaitez utiliser pour le compte d’utilisateur.| 
| Désactivé| Indique si le compte est activé. Définir cette propriété sur __$true__ pour vous assurer que ce compte est désactivé et défini sur __$false__ pour vous assurer qu’il est activé.| 
| Garantir| Indique si le compte existe. Définissez cette propriété sur « Heure actuelle » pour vous assurer que le compte existe et défini sur « Absent » pour vous assurer que le compte n’existe pas.| 
| Nom complet| Représente une chaîne avec le nom complet que vous souhaitez utiliser pour le compte d’utilisateur.| 
| Mot de passe| Indique le mot de passe que vous souhaitez utiliser pour ce compte. | 
| PasswordChangeNotAllowed| Indique si l’utilisateur peut modifier le mot de passe. Définir cette propriété sur __$true__ pour vous assurer que l’utilisateur ne peut pas modifier le mot de passe et défini sur __$false__ pour autoriser l’utilisateur à modifier le mot de passe. La valeur par défaut est __$false__.| 
| PasswordChangeRequired| Indique si l’utilisateur doit changer le mot de passe à la prochaine ouverture de session. Définir cette propriété sur __$true__ si l’utilisateur doit changer le mot de passe. La valeur par défaut est __$true__.| 
| PasswordNeverExpires| Indique si le mot de passe arrive à expiration. Pour vous assurer que le mot de passe pour ce compte sera jamais arriver à expiration, définissez cette propriété sur __$true__et défini sur __$false__ si le mot de passe va expirer. La valeur par défaut est __$false__.| 
| DependsOn | Indique que la configuration d’une autre ressource doit s’exécuter avant que cette ressource est configurée. Par exemple, si l’ID de la ressource configuration du bloc de script que vous voulez exécuter tout d’abord est __ResourceName__ et son type est le __type de ressource__, la syntaxe pour l’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 

## Exemple

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = “[Group]GroupExample" # Configures GroupExample first
}
```
