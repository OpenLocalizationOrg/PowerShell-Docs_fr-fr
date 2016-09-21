# DSC Registre ressource

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource de **Registre** dans le module Windows PowerShell vous le souhaitez état Configuration (DSC) fournit un mécanisme pour gérer des clés de Registre et des valeurs dans un nœud cible.

## Syntaxe

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## Propriétés
|  Propriété  |  Description   | 
|---|---| 
| Clé| Indique le chemin d’accès de la clé de Registre pour laquelle vous voulez vous assurer un état spécifique. Ce chemin d’accès doit inclure le hive.| 
| Nom de valeur| Indique le nom de la valeur de Registre.| 
| Garantir| Indique si la clé et la valeur existent. Pour vous assurer qu’elles ne, définissent cette propriété à « Heure actuelle ». Pour vous assurer qu’elles n’existent pas, définissez la propriété à « Absent ». La valeur par défaut est « Heure actuelle ».| 
| Force| Si la clé de Registre spécifiée est présente, __forcer__ le remplace par la nouvelle valeur.| 
| Hex| Indique si les données seront être exprimées au format hexadécimal. Si spécifié, les données de valeur DWORD/numération sont présentées dans un format hexadécimal. Non valide pour les autres types. La valeur par défaut est __$false__.| 
| DependsOn| Indique que la configuration d’une autre ressource doit s’exécuter avant que cette ressource est configurée. Par exemple, si l’ID de la ressource configuration du bloc de script que vous voulez exécuter tout d’abord est __ResourceName__ et son type est le __type de ressource__, la syntaxe pour l’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 
| ValueData| Les données de la valeur de Registre.| 
| Type valeur| Indique le type de la valeur. Les types pris en charge sont : 
<ul><li>Chaîne (REG_SZ)</li>


<li>Fichier binaire (Registre binaire)</li>


<li>DWORD 32 bits (REG_DWORD)</li>


<li>Numération 64 bits (REG_QWORD)</li>


<li>Chaînes multiples (REG_MULTI_SZ)</li>


<li>Chaîne extensible (REG_EXPAND_SZ)</li></ul>

## Exemple
```powershell
Registry RegistryExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Key = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
    ValueName = "TestValue"
    ValueData = "TestData"
}
```

