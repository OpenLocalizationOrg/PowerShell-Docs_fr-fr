# Ressource DSC Group

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource de groupe dans le module Windows PowerShell vous le souhaitez état Configuration (DSC) fournit un mécanisme pour gérer des groupes locaux sur le nœud cible.

##Syntaxe##
```
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
}
```

## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| Propriété GroupName| Indique le nom du groupe pour lequel vous souhaitez garantir un état spécifique.| 
| Credential| Indique les informations d’identification nécessaires pour accéder aux ressources distantes. **Remarque**: ce compte doit disposer des autorisations Active Directory appropriées pour ajouter tous les comptes non local au groupe. dans le cas contraire, une erreur se produit.
| Description| Indique la description du groupe.| 
| Vérifiez| Indique si le groupe existe. Définir cette propriété à « Absent » pour s’assurer que le groupe n’existe pas. Affectation de « Présenter » (valeur par défaut) garantit que le groupe existe.| 
| Membres| Indique que vous souhaitez vérifier que ces membres du groupe de formulaire.| 
| MembersToExclude| Indique les utilisateurs qui souhaitent garantir ne sont pas membres de ce groupe.| 
| MembersToInclude| Indique que les utilisateurs auxquels vous voulez vous assurer sont membres du groupe.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant que cette ressource est configurée. Par exemple, si l’ID de la ressource configuration du bloc de script que vous souhaitez exécuter est tout d’abord __ResourceName__ et son type est __ResourceType__, la syntaxe pour l’utilisation de cette propriété est « DependsOn = « ResourceName [ResourceType] » ".| 

## Exemple

L’exemple suivant montre comment vérifier qu’un groupe appelé TestGroup est absent. 

```powershell
Group GroupExample
{
    # This will remove TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
