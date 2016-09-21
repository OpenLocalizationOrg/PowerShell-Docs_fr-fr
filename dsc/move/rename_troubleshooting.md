# Résolution des problèmes de DSC222

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Cette rubrique décrit les méthodes permettant de publier vos scripts Configuration état souhaité (DSC) à être exécuté sans erreur. En utilisant efficacement les journaux pour analyser les erreurs et la compréhension de la Corbeille du cache pour afficher les résultats immédiates de vos modifications de ressources, vous pourrez résoudre les problèmes DSC plus efficacement. Ces techniques sont présentés dans deux sections :

* Mon script ne fonctionne pas : **les fichiers journaux à l’aide de DSC à diagnostiquer les erreurs de script**
* Mes ressources ne mettre à jour : **comment réinitialiser le cache**

## Mon script ne fonctionne pas : DSC à l’aide des journaux pour diagnostiquer les erreurs de script

Tels que tous les logiciels Windows enregistre les erreurs DSC et événements dans [les journaux](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) peuvent être affichés à partir de l' [Observateur d’événements](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer). Examen de ces fichiers journaux peut vous aider à comprendre pourquoi a échoué une opération particulière et comment éviter l’échec à l’avenir. Écriture de scripts configuration peut s’avérer difficile, donc faciliter le suivi des erreurs en tant qu’auteur vous, utilisez la ressource de journal DSC pour suivre la progression de votre configuration dans le journal des événements DSC analytique.

## Où se trouvent les journaux d’événements DSC ?

Dans l’Observateur d’événements, événements DSC se trouvent dans : **Configuration de l’état journaux/Microsoft/Windows/souhaité Services et d’Applications**

La cmdlet PowerShell correspondante, [Get-intercepteur](https://technet.microsoft.com/library/hh849682.aspx), vous pouvez également exécuter pour afficher les journaux d’événements :

```
PS C:\Users> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                                                                                  
-----------                     -- ---------------- -------                                                                                                  
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
```

Comme indiqué ci-dessus, nom du journal principal de DSC est **Microsoft -> Windows -> DSC** (autres noms de journal sous Windows ne figurent pas ici pour des raisons de concision). Le nom primaire est ajouté au nom du canal pour créer le nom de journal complet. Le moteur DSC écrit principalement dans trois types de journaux : [opérationnel, analyse et débogage se connecte](https://technet.microsoft.com/library/cc722404.aspx). Depuis l’analyse et les journaux de débogage sont désactivées par défaut, vous devez les activer dans l’Observateur d’événements. Pour ce faire, ouvrez l’Observateur d’événements en tapant eventvwr dans Windows PowerShell ; ou, cliquez sur le bouton **Démarrer** et cliquez sur **Le panneau de configuration**, cliquez sur **Outils d’administration**, puis cliquez sur **Observateur d’événements**. Dans le menu **affichage** dans l’Observateur d’événements, cliquez sur **Afficher les journaux et débogage**. Le nom du journal pour le canal analytique est **Microsoft-Windows-Dsc/analyse**et le canal déboguer est **Microsoft Windows-Dsc/débogage**. Vous pouvez également utiliser l’utilitaire [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) pour permettre les journaux comme le montre l’exemple suivant.

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## Que contiennent les journaux DSC ?

DSC journaux sont répartis entre les trois canaux de journal en fonction de l’importance du message. Le journal des opérations dans DSC contient tous les messages d’erreur et peut être utilisé pour identifier le problème. Le journal d’analyse comporte un volume plus important d’événements et peut identifier l’endroit où les erreurs se sont produites. Ce canal contient également des messages détaillés (le cas échéant). Le journal de débogage contient les journaux qui peuvent vous aider à comprendre comment les erreurs se sont produites. Messages d’événements DSC sont organisés telles que chaque message événement commence par un numéro de travail qui représente une opération de DSC de façon unique. L’exemple ci-dessous tente d’obtenir le message à partir de l’événement première enregistré dans le journal de DSC opérationnel.

```powershell
PS C:\Users> $AllDscOpEvents=get-winevent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\Users> $FirstOperationalEvent=$AllDscOpEvents[0]
PS C:\Users> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
Consistency engine was run successfully. 
```

DSC événements sont enregistrés dans une structure particulier qui permet à l’utilisateur pour regrouper les événements à partir d’une tâche DSC. La structure se présente comme suit :

**ID de la tâche : \<Guid\>**
**\<Message d’événement\> **

## Collecter des événements à partir d’une seule opération DSC

Les journaux d’événements DSC contiennent des événements générés par diverses opérations DSC. Toutefois, vous pouvez généralement concerné avec les détails sur une opération particulière. Tous les journaux DSC peuvent être regroupés par la propriété ID de travail qui est unique pour chaque opération DSC. L’ID de travail est affichée en tant que la première valeur de propriété de tous les événements DSC. Les étapes suivantes expliquent comment faire pour accumuler tous les événements dans une structure de tableau groupé.

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>
 
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
wevtutil.exe set-log “Microsoft-Windows-Dsc/Debug” /q:True /e:true
 
<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>
 
Get-DscLocalConfigurationManager
 
<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>
 
$DscEvents=[System.Array](Get-WinEvent "Microsoft-windows-dsc/operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-Winevent "Microsoft-Windows-Dsc/Debug" -Oldest)
 
 
<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations=$DscEvents | Group {$_.Properties[0].value}  
```

Cet exemple, la variable `$SeparateDscOperations` contient les journaux regroupés par les ID de travail. Chaque élément de tableau de cette variable représente un groupe d’événements enregistrés par une autre opération DSC, permettant d’accéder à plus d’informations sur les journaux.

```
PS C:\> $SeparateDscOperations
 
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
PS C:\> $SeparateDscOperations[0].Group
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...       
```

Vous pouvez extraire les données dans la variable `$SeparateDscOperations` à l’aide de [Where-Object](https://technet.microsoft.com/library/ee177028.aspx). Voici cinq scénarios dans lesquels vous pouvez souhaiter extraire les données de résoudre les problèmes DSC :

### 1 : défaillances d’opérations

Tous les événements ont des [niveaux de gravité](https://msdn.microsoft.com/library/dd996917(v=vs.85)). Ces informations peuvent être utilisées pour identifier les événements d’erreur :

```
PS C:\> $SeparateDscOperations  | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### 2 : exécutent détails des opérations dans la dernière demi-heure

`TimeCreated`, une propriété de tous les événements Windows, indique le temps de création de l’événement. Comparaison de cette propriété avec un objet particulier date/heure pouvant être utilisée pour filtrer tous les événements :

```powershell
PS C:\> $DateLatest=(Get-date).AddMinutes(-30)
PS C:\> $SeparateDscOperations  | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}   
```

### 3 : messages à partir de la dernière opération

La dernière opération est stockée dans le premier index du groupe tableau `$SeparateDscOperations`. Interroger des messages du groupe pour index 0 renvoie tous les messages pour la dernière opération :

```powershelll
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Consistency check completed. 
```

### 4 : messages d’erreur enregistrés pour les opérations échecs récentes

`$SeparateDscOperations[0].Group` contient un ensemble d’événements pour la dernière opération. Exécuter le `Where-Object` applet de commande pour filtrer les événements en fonction de leur nom complet niveau. Résultats sont stockés dans le `$myFailedEvent` variable, laquelle peut devraient être plus examinées pour obtenir le message d’événement :

```powershell
PS C:\> $myFailedEvent=($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})
 
PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
DSC Engine Error : 
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first. 
Error Code : 1 
```

### 5 : tous les événements générés pour un ID de travail particulier.

`$SeparateDscOperations` est un tableau de groupes, chacun d’eux ayant le nom que l’ID unique de la tâche. En exécutant la `Where-Object` applet de commande, vous pouvez extraire les groupes d’événements qui ont un ID de travail particulier :

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC
 
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...  
```

## À l’aide de xDscDiagnostics pour analyser DSC journaux

**xDscDiagnostics** est un module PowerShell qui se compose de deux opérations simples qui peuvent vous aider à analyser les échecs DSC sur votre ordinateur : `Get-xDscOperation` et `Trace-xDscOperation`. Ces fonctions peuvent vous aider à identifier tous les événements locaux de diverses opérations DSC précédentes ou événements DSC sur des ordinateurs distants (avec les informations d’identification valides). Ici, le terme que DSC opération permet de définir une exécution DSC unique unique à partir de son démarrage à la fin. Par exemple, `Test-DscConfiguration` serait une opération DSC distincte. De même, chaque autre applet de commande dans DSC (tel que `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) chacune a pu être identifié comme des opérations distinctes DSC. Les deux applets de commande sont décrites dans [xDscDiagnostics](https://powershellgallery.com/packages/xDscDiagnostics) PowerShell Module (Kit de ressources DSC) et plus en détail ci-dessous. L’aide est disponible en exécutant `Get-Help <cmdlet name>`.

## Get-xDscOperation

Cette applet de commande vous permet de rechercher les résultats des opérations DSC qui s’exécutent sur un ou plusieurs ordinateurs et renvoie un objet qui contient la collection des événements générés par chaque opération DSC. Par exemple, dans le résultat suivant, trois commandes ont été exécutées. La première partie passé, et l’autre deux a échoué. Ces résultats sont répertoriés dans le résultat de `Get-xDscOperation`.

TODO : Remplacez cette image présente la sortie de Get-xDscOperation

### Paramètres

* **Plus récent**: accepte une valeur entière pour indiquer le nombre d’opérations à afficher. Par défaut, elle renvoie 10 opérations plus récent. Par exemple, TODO : afficher Get-xDscOperation-5 plus récent
* **Nom_ordinateur**: paramètre qui accepte un tableau de chaînes, chacune contenant le nom d’un ordinateur à partir de l’endroit où vous voulez collecter les données du journal des événements DSC. Par défaut, il collecte des données à partir de l’ordinateur hôte. Pour activer cette fonctionnalité, vous devez exécuter la commande suivante dans les ordinateurs distants, en mode élevé afin que le permettra de collection d’événements
```powershell
  New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
* **Informations d’identification**: paramètre qui est de type PSCredential, afin d’accès pour les ordinateurs spécifiés dans le paramètre ComputerName.

### Objet renvoyé

L’applet de commande renvoie une matrice d’objets chacune de type **Microsoft.PowerShell.xDscDiagnostics.GroupedEvents**. Chaque objet dans ce tableau appartenant à une autre opération de DSC. L’affichage par défaut pour cet objet comporte les propriétés suivantes
* **SequenceID**: Spécifie le nombre incrémentiel associé à l’opération DSC en fonction de date. Par exemple, la dernière opération exécutée aurait SequenceID comme 1, la seconde à la dernière opération DSC aurait SequenceID de 2 et ainsi de suite. Ce nombre est un autre identificateur pour chaque objet dans le tableau retourné.
* **TimeCreated**: une valeur DateTime qui indique quand l’opération DSC a commencé.
* **Nom_ordinateur**: le nom d’ordinateur à partir de l’endroit où les résultats sont regroupées.
* **Résultat**: une chaîne avec la valeur **Échec** ou de **Réussite** qui indique si cette opération DSC a rencontré une erreur ou non, respectivement.
* **AllEvents**: un objet qui représente une collection d’événements générés par l’opération DSC.

Par exemple, le résultat suivant montre les résultats de la dernière opération à partir de plusieurs ordinateurs : TODO : remplacer l’image pour Get-xDscOperation afficher les journaux de l’ordinateur distant

## Suivi des xDscOperation

Cette applet de commande renvoie un objet qui contient une collection d’événements, de leurs types d’événements et de la sortie de message généré à partir d’une opération de DSC particulière. En règle générale, lorsque vous trouvez une erreur dans les opérations à l’aide de `Get-xDscOperation`, vous devez suivre cette opération pour rechercher des événements l’origine d’une défaillance.

### Paramètres

* **SequenceID**: il s’agit de la valeur entière affectée à n’importe quelle opération, relatifs à un ordinateur spécifique. En spécifiant un ID de séquence de par exemple, 4, la trace pour l’opération DSC qui a été 4e à partir de la dernière sera sortie

Trace-xDscOperation avec l’ID de séquence spécifié
* **Identificateur**: il s’agit de la valeur GUID affectée par PPCM xDscOperation à identifier de façon unique une opération. Lorsqu’un identificateur est spécifié, le suivi de l’opération DSC correspondant est sortie.
  TODO : Remplacer l’image pour repérer xDscOperation prise de travail en tant que paramètre
* **Nom_ordinateur** et **les informations d’identification**: ces paramètres permettent de la trace à être collectées à partir d’ordinateurs distants :
```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
  TODO : Remplacer l’image pour s’exécuter sur un cluster autre Trace-xDscOperation

Notez que, dans la mesure où `Trace-xDscOperation` regroupe des événements à partir de l’analyse, débogage et des journaux opérationnelles, il vous invite à activer ces journaux comme décrit ci-dessus.

### Objet renvoyé

L’applet de commande renvoie un tableau d’objets, chacune de type `Microsoft.PowerShell.xDscDiagnostics.TraceOutput`. Chaque objet dans ce tableau contient les champs suivants :
* **Nom_ordinateur**: le nom de l’ordinateur à partir de l’endroit où les journaux sont collectées.
* **Type d’événement**: il s’agit d’un champ de type énumérateur qui contient des informations sur le type d’événement. Cela peut être une des opérations suivantes :
  - *Opérationnel*: l’événement proviennent le journal opérationnel.
  - *Analyse*: l’événement est généré par le journal d’analyse.
  - *Déboguer*: l’événement est généré par le journal de débogage.
  - *Commentaires*: sortie événements sous forme de messages détaillées pendant l’exécution. Les messages détaillées facilitent l’Identifiez l’ordre des événements qui sont publiés.
  - *Erreur*: les événements d’erreur. En recherchant les événements d’erreur, vous trouverez généralement rapidement la raison de l’échec.
* **TimeCreated**: une valeur DateTime indiquant lorsque l’événement a été enregistré par DSC.
* **Message**: le message a été enregistré par DSC dans les journaux d’événements.

Voici des champs de cet objet qui peut être utilisée pour plus d’informations sur l’événement, mais ne sont pas affichés par défaut :

* **Identificateur**: l’ID du travail (format GUID) spécifique à cette opération DSC.
* **SequenceID**: le SequenceID unique à cette opération DSC dans cet ordinateur.
* **Événement**: il s’agit de l’événement réel enregistré par DSC, de type `System.Diagnostics.Eventing.Reader.EventLogRecord`. Cela peut également l’obtenus en exécutant l’applet de commande `Get-WinEvent`. Il contient plus d’informations, tels que la tâche, eventID et au niveau de l’événement.

Sinon, vous pouvez collecter des informations sur les événements en enregistrant la sortie de `Trace-xDscOperation` dans une variable. Vous pouvez utiliser la commande suivante pour afficher tous les événements pour une opération de DSC spécifique :

```powershell
(Trace-xDscOperation -SequenceID 3).Event
```

Ceci affiche les mêmes résultats que la `Get-WinEvent` applet de commande, par exemple, dans les résultats suivants : TODO : sortie ?

Dans l’idéal, commencez par utiliser `Get-xDscOperations` pour répertorier arrière le dernier DSC quelques configuration s’exécute sur vos ordinateurs. Ensuite, vous pouvez examiner une seule opération (à l’aide de son sequenceID ou identificateur) avec `Trace-xDscOperation` pour découvrir les tâches qu’elle a en coulisses.

## Mes ressources ne mettre à jour : comment réinitialiser le cache

Le moteur DSC met en cache les ressources implémentés sous la forme d’un module PowerShell pour des raisons d’efficacité. Toutefois, cela peut entraîner des problèmes lorsque vous êtes une ressource de création et test simultanément, car DSC charge la version mis en cache jusqu'à ce que le processus est redémarré. La seule façon de rendre DSC charger la version la plus récente consiste à supprimer explicitement le processus hébergeant le moteur DSC.

De même, lorsque vous exécutez `Start-DSCConfiguration`, après l’ajout et modification d’une ressource personnalisée, la modification s’exécutera ne peut-être pas à moins d’avoir, ou jusqu'à ce que, redémarrage de l’ordinateur. C’est parce que DSC s’exécute dans le processus hôte du fournisseur WMI (WmiPrvSE) et en règle générale, il existe plusieurs instances de WmiPrvSE en cours d’exécution en même temps. Lorsque vous redémarrez l’ordinateur, le processus de l’hôte est redémarré et le cache est désactivé.

Pour réussir la configuration de la Corbeille et vider le cache sans redémarrer l’ordinateur, vous devez arrêter et redémarrer puis le processus d’hôte. Pour cela, sur une base par instance, dans laquelle vous identifiez le processus, arrêtez et redémarrez. Vous pouvez également utiliser les `DebugMode`, comme illustré ci-dessous, pour recharger la ressource DSC PowerShell.

Pour identifier le processus qui héberge le moteur DSC et arrêter sur une base par instance, vous pouvez afficher l’ID du processus de la WmiPrvSE qui héberge le moteur DSC. Ensuite, pour mettre à jour le fournisseur, arrêter le processus WmiPrvSE en utilisant les commandes ci-dessous et puis réexécutez **Démarrer DscConfiguration** .

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers | 
Where-Object {$_.provider -like 'dsccore'} | 
Select-Object -ExpandProperty HostProcessIdentifier 

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## À l’aide de DebugMode

Vous pouvez configurer DSC Local Configuration Manager (PPCM) à utiliser `DebugMode` pour toujours vider le cache lors du redémarrage le processus d’hôte. Lorsque la valeur **Vrai**, elle indique au moteur de toujours charger la ressource DSC PowerShell. Une fois que vous avez fini de rédaction de la ressource, vous pouvez le configurer pour **FALSE** et le moteur revient à son comportement de mise en cache les modules.

Voici une démonstration pour afficher comment `DebugMode` pouvez actualiser automatiquement le cache. Tout d’abord, nous allons étudier la configuration par défaut :

```
PS C:\Users\WinVMAdmin\Desktop> Get-DscLocalConfigurationManager
 
 
AllowModuleOverwrite           : False
CertificateID                  : 
ConfigurationID                : 
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     : 
DebugMode                      : False
DownloadManagerCustomData      : 
DownloadManagerName            : 
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :  
```

Vous pouvez voir que `DebugMode` est définie sur **FALSE**.

Pour configurer le `DebugMode` démonstration, utiliser la ressource PowerShell suivante :

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1"|Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
} 
```

À présent, créez une configuration à l’aide de la ressource ci-dessus appelée `TestProviderDebugMode`:

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

Vous verrez que le contenu du fichier : «**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**» est **1**.

À présent, mettez à jour le code de fournisseur en utilisant le script suivant :

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput"|Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

Ce script génère un nombre aléatoire et le fournisseur cade mis à jour en conséquence. Avec `DebugMode` définie sur false, le contenu du fichier «**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**» n’est jamais modifié.

À présent, définissez `DebugMode` **TRUE** dans votre script de configuration :

```powershell
LocalConfigurationManager
{
    DebugMode = $true
} 
```

Lorsque vous exécutez à nouveau le script ci-dessus, vous verrez que le contenu du fichier est différent à chaque fois. (Vous pouvez exécuter `Get-DscConfiguration` activez-la). Voici le résultat de deux séries supplémentaires (vos résultats peuvent être différents lorsque vous exécutez le script) :

```powershell
PS C:\Users\WinVMAdmin\Desktop> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
20                                      localhost                              
 
PS C:\Users\WinVMAdmin\Desktop> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
14 
```

## Voir aussi

### Référence
* [Ressource de journal DSC](logResource.md)

### Concepts
* [Créer personnalisé Windows PowerShell que vous le souhaitez état Configuration ressources](authoringResource.md)

### Autres ressources
* [Applets de commande état Configuration vous le souhaitez Windows PowerShell](https://technet.microsoft.com/en-us/library/dn521624(v=wps.630).aspx)
