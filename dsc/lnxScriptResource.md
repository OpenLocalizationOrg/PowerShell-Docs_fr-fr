# DSC pour Linux nxScript ressource

La ressource **nxScript** dans PowerShell souhaité état Configuration (DSC) fournit un mécanisme pour exécuter des scripts de Linux sur un nœud Linux.

## Syntaxe

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    { Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Propriétés

|  Propriété |  Description | 
|---|---|
| GetScript| Fournit un script qui s’exécute lorsque vous appelez l’applet de commande [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) . Le script doit commencer par un shebang, tels que #! / bin/bash.| 
| SetScript| Fournit un script. Lorsque vous appelez l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) , le **TestScript** s’exécute en premier. Si le bloc **TestScript** retourne un code de sortie autre que 0, le bloc de **SetScript** s’exécutera. Si la **TestScript** retourne un code de sortie de 0, le **SetScript** ne s’exécutera pas. Le script doit commencer par un shebang, tel que `#!/bin/bash`.| 
| TestScript| Fournit un script. Lorsque vous appelez l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) , ce script est exécuté. Si elle retourne un code de sortie différent de 0, la SetScript s’exécutera. Si elle retourne un code de sortie de 0, le **SetScript** ne s’exécutera pas. Le **TestScript** s’exécute également lorsque vous appelez l’applet de commande [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) . Toutefois, dans ce cas, le **SetScript** ne fonctionnera pas, quel que soit le code de sortie est renvoyé à partir de la **TestScript**. L' **TestScript** doit renvoyer un code de sortie 0 si la configuration réelle correspond à la configuration de l’état souhaité en cours et un code de sortie différent de 0 si elle ne correspond pas. (La configuration de l’état souhaité en cours est la dernière configuration entrent en vigueur sur le nœud qui est à l’aide de DSC). Le script doit commencer par un shebang, par exemple 1#!/bin/bash.1| 
| User| L’utilisateur d’exécuter le script comme.| 
| Group| Le groupe pour exécuter le script en tant que.| 
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant que cette ressource est configurée. Par exemple, si l' **ID de** la ressource configuration du bloc de script que vous souhaitez exécuter est tout d’abord **ResourceName** et son type est **ResourceType**, la syntaxe d’utilisation de cette propriété est `DependsOn = "[ResourceType]ResourceName"`.| 

## Exemple

L’exemple suivant illustre l’utilisation de la ressource **nxScript** pour effectuer la gestion de configuration supplémentaires...

```
Import-DSCResource -Module nx 

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
} 
}
```
