# Ressource de journal DSC 

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource de __journal__ dans le module Windows PowerShell vous le souhaitez état Configuration (DSC) fournit un mécanisme pour écrire des messages dans le journal des événements Microsoft-Windows-souhaité état Configuration/analyse.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

## Propriétés
|  Propriété  |  Description   | 
|---|---| 
| Message| Indique le message que vous souhaitez écrire dans le journal des événements Microsoft-Windows-Desired état Configuration/analyse.| 
| DependsOn | Indique que la configuration d’une autre ressource doit s’exécuter avant ce message du journal est écrit. Par exemple, si l’ID de la ressource configuration du bloc de script que vous voulez exécuter tout d’abord est __ResourceName__ et son type est le __type de ressource__, la syntaxe pour l’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 

## Exemple

L’exemple suivant montre comment inclure un message dans le journal des événements Microsoft-Windows-Desired état Configuration/analyse.

> **Remarque**: Si vous exécutez [DscConfiguration de Test](https://technet.microsoft.com/en-us/library/dn407382.aspx) avec cette ressource configurée, elle retourne toujours **$false**.

```powershell 
Log LogExample
{
    Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
} 
```

