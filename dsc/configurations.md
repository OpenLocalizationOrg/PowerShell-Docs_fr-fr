# Configurations de DSC

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Configurations de DSC sont des scripts PowerShell qui définissent un type particulier de la fonction. Pour définir une configuration, vous utilisez le mot clé de PowerShell __Configuration__.

```powershell
Configuration MyDscConfiguration {

    Node “TEST-PC1” {
        WindowsFeature MyFeatureInstance {
            Ensure = “Present”
            Name =  “RSAT”
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = “Present”
            Name = “Bitlocker”
        }
    }
}
```

Enregistrez le script sous forme de fichier .ps1.

## Syntaxe de configuration

Un script de configuration se compose des éléments suivants :

- Le bloc de la **Configuration** . Il s’agit du bloc de script extérieur. Définissez-la en utilisant le mot clé de **Configuration** et en fournissant un nom. Dans ce cas, le nom de la configuration est « MyDscConfiguration ».
- Un ou plusieurs blocs de **nœud** . Elles définissent les nœuds (ordinateurs ou des ordinateurs virtuels) que vous configurez. Dans la configuration ci-dessus, il existe un bloc de **nœud** ciblant un ordinateur nommé « TEST-PC1 ».
- Un ou plusieurs blocs de ressources. Il s’agit d’où la configuration définit les propriétés pour les ressources qu’il consiste à configurer. Dans ce cas, il existe deux blocs de ressources, chacun d'entre eux appeler la ressource « WindowsFeature ».

Au sein d’un bloc de **Configuration** , vous pouvez effectuer tout ce que vous pourriez normalement dans une fonction PoweShell. Par exemple, dans l’exemple précédent, si vous ne souhaitez pas coder en dur le nom de l’ordinateur cible dans la configuration, vous pouvez ajouter un paramètre pour le nom du nœud :

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$computerName="localhost"
    )
    Node $computerName {
        WindowsFeature MyFeatureInstance {
            Ensure = “Present”
            Name =  “RSAT”
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = “Present”
            Name = “Bitlocker”
        }
    }
}
```

Dans cet exemple, vous spécifiez le nom du nœud s’il est passé en tant que paramètre $computerName lorsque vous [compilez la configuration](# Compiling the configuration). Le nom par défaut est « localhost ».

## Compilation de la configuration
Avant que vous pouvez appliquer une configuration, vous devez compiler dans un document MOF. Pour cela, en appelant la configuration comme vous le feriez pour une fonction PowerShell.
>__Remarque :__ Pour appeler une configuration, la fonction doit être dans l’étendue globale (comme avec n’importe quelle autre fonction PowerShell). Vous pouvez faire soit en « dot sourcing » le script, ou en exécutant le script de configuration en utilisant F5 ou en cliquant sur __Exécuter le Script__ située dans l’environnement ISE. Dot-source le script, exécutez la commande `. .\myConfig.ps1` où `myConfig.ps1` est le nom du fichier de script qui contient votre configuration.

Lorsque vous appelez la configuration, il crée :

- Un dossier dans le répertoire actif avec le même nom que la configuration.
- Un fichier nommé .mof _NodeName_dans le nouveau répertoire, où _NomNœud_ est le nom du nœud cible de la configuration. S’il existe plusieurs nœuds, un fichier MOF sera créé pour chaque nœud.

>__Remarque__: les fichiers MOF contient toutes les informations de configuration du nœud cible. Pour cette raison, il est important d’assurer la sécurité. Pour plus d’informations, voir [sécurisation du fichier MOF](secureMOF.md).

Compilation de la première configuration au-dessus des résultats dans la structure de dossiers suivants :

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 TEST-PC1.mof
```  

Si la configuration accepte un paramètre, comme dans le deuxième exemple, qui doit être fournie au moment de la compilation. Voici comment qui se présenterait :

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration -computerName 'MyTestNode'
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```      

## À l’aide de DependsOn
Mots clés DSC utile est __DependsOn__. En règle générale (mais pas nécessairement toujours), DSC applique les ressources dans l’ordre dans lequel ils apparaissent dans la configuration. Cependant, __DependsOn__ spécifie les ressources qui dépendent d’autres ressources et la méthode LCM garantit qu’ils sont appliqués dans l’ordre correct, quel que soit l’ordre dans les ressources instances sont définis. Par exemple, une configuration peut indiquer qu’une instance de la ressource __utilisateur__ dépend de l’existence d’une instance de __groupe__ :

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = “Present”
            GroupName = “TestGroup”
        }
User UserExample {
Ensure = “Present”
FullName = “TestUser”
DependsOn = “GroupExample”
}
    }
}
```

## À l’aide des nouvelles ressources dans votre Configuration
Si vous avez exécuté les exemples précédents, vous avez sans doute remarqué que vous ont été averti que vous utilisiez une ressource sans l’importer explicitement.
Aujourd'hui, DSC est livré avec 12 ressources dans le cadre du module PSDesiredStateConfiguration. Autres ressources dans les modules externes doivent être placés dans `$env:PSModulePath` pour pouvoir être reconnue par la méthode LCM. Une nouvelle applet de commande [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), peut être utilisé pour déterminer quelles ressources sont installés sur le système et disponibles pour une utilisation par la méthode LCM. Une fois ces modules ont été placés dans `$env:PSModulePath` et sont correctement reconnus par [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), ils doivent toujours être chargé dans votre configuration. __Import-DscResource__ est un mot clé dynamique qui peut uniquement être reconnu dans un bloc de __Configuration__ (par exemple, il n’est pas une applet de commande). __Import-DscResource__ prend en charge deux paramètres :
* __NomModule__ est recommandé d’utiliser __Import-DscResource__. Elle accepte le nom du module qui contient les ressources à importer (ainsi que d’un tableau de chaînes de noms de modules). 
* __Nom__ est le nom de la ressource à importer. Cela n’est pas le nom convivial retourné en tant que « Nom » par [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), mais le nom de classe utilisé lors de la définition du schéma de ressource (renvoyé par [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)en tant que __ResourceType__ ). 

## Voir aussi
* [Vue d’ensemble de la Configuration d’état vous le souhaitez Windows PowerShell](overview.md)
* [Ressources de DSC](resources.md)
* [Configuration du Gestionnaire de Configuration locale](metaconfig.md)