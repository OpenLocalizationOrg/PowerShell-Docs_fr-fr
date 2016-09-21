# Ressource de Service DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0


La ressource de **Service** dans le module Windows PowerShell vous le souhaitez état Configuration (DSC) fournit un mécanisme pour gérer les services sur le nœud cible.

## Syntaxe

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
}
```

## Propriétés

|  Propriété  |  Description   | 
|---|---| 
| Nom| Indique le nom du service. Notez que parfois cela est la différence entre le nom d’affichage. Vous pouvez obtenir une liste des services et leur état actuel avec l’applet de commande Get-Service.| 
| BuiltInAccount| Indique le compte de connexion à utiliser pour le service. Les valeurs autorisées pour cette propriété sont : **service local**, **système local**et **service réseau**.| 
| Informations d’identification| Indique les informations d’identification pour le compte que le service s’exécutera sous. Cette propriété et la propriété __BuiltinAccount__ ne peuvent pas être utilisés ensemble.| 
| DependsOn| Indique que la configuration d’une autre ressource doit s’exécuter avant que cette ressource est configurée. Par exemple, si l’ID de la ressource configuration du bloc de script que vous voulez exécuter tout d’abord est __ResourceName__ et son type est le __type de ressource__, la syntaxe pour l’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 
| StartupType| Indique le type de démarrage pour le service. Les valeurs autorisées pour cette propriété sont : **automatique**, **désactivé**et **manuel**| 
| État| Indique l’état que vous voulez veiller à pour le service.| 

## Exemple

```powershell
Service ServiceExample
{
    Name = "TermService"
    StartupType = "Manual"
    State = "Running"
} 
```
