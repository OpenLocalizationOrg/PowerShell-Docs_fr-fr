# Windows PowerShell 4.0 souhaité Gestionnaire de Configuration Local de l’état Configuration (PPCM)

>S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Gestionnaire de Configuration local est le moteur de Windows PowerShell vous le souhaitez état Configuration (DSC). Il s’exécute sur tous les nœuds cible, et il est chargé d’appeler les ressources de configuration incluses dans un script de configuration DSC. Cette rubrique répertorie les propriétés du Gestionnaire de Configuration locale et décrit comment vous pouvez modifier les paramètres du Gestionnaire de Configuration Local sur un nœud cible.

## Propriétés du Gestionnaire de Configuration local
Voici une liste les propriétés du Gestionnaire de Configuration locale que vous pouvez définir ou à récupérer.
 
* **AllowModuleOverwrite**: contrôles si nouvelles configurations téléchargement à partir du serveur de configuration sont autorisés à remplacent les anciens sur le nœud cible. Les valeurs possibles sont VRAI et faux.
* **CertificateID**: GUID un certificat utilisé pour sécuriser les informations d’identification pour l’accès à la configuration. Pour plus d’informations, voir [à sécuriser les informations d’identification dans Windows PowerShell vous le souhaitez état Configuration ?](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx).
* **Id_de_configuration**: indique un GUID qui est utilisé pour obtenir un fichier de configuration d’un serveur configurée en tant qu’un serveur « extraire ». GUID garantit que le fichier de configuration correcte est accessible.
* **ConfigurationMode**: indique comment le Gestionnaire de Configuration Local réellement s’applique la configuration et les nœuds cible. Cela peut prendre les valeurs suivantes :
    - **ApplyOnly**: avec cette option, DSC applique la configuration et n’a aucun effet supplémentaire sauf si une nouvelle configuration est détectée, soit par vous envoyer une nouvelle configuration directement à la cible nœud (« Pousser ») ou si vous avez configuré un serveur « extraire » et DSC détecte une nouvelle configuration lorsqu’il vérifie avec le serveur « extraire ». Si la cible configuration du nœud passe automatiquement, aucune action n’est considérée.
    - **ApplyAndMonitor**: avec cette option (qui est la valeur par défaut), DSC s’applique les nouvelles configurations, si vous envoyez directement au nœud cible ou découvert sur un serveur « extraire ». Par la suite, si la configuration du nœud cible passe automatiquement à partir du fichier de configuration, DSC indique la différence dans les journaux. Pour plus d’informations sur la journalisation DSC, voir [journaux d’événements à l’aide pour diagnostiquer les erreurs dans la Configuration de l’état souhaité](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
    - **ApplyAndAutoCorrect**: avec cette option, DSC applique les nouvelles configurations, si vous envoyez directement au nœud cible ou découvert sur un serveur « extraire ». Par la suite, si la configuration du nœud cible passe automatiquement à partir du fichier de configuration, DSC l’écart dans les journaux des rapports et tente d’ajuster la configuration de nœud cible pour mettre en conformité avec le fichier de configuration.
* **ConfigurationModeFrequencyMins**: représente la fréquence (en minutes) à laquelle l’application de l’arrière-plan de DSC tente d’implémenter la configuration en cours sur le nœud cible. La valeur par défaut est 15. Cette valeur peut être définie en association avec RefreshMode. Lorsque RefreshMode est défini sur Extraire, le nœud cible contacte le serveur de configuration à un intervalle défini par RefreshFrequencyMins et téléchargements la configuration en cours. Quelle que soit la valeur RefreshMode, à l’intervalle défini par ConfigurationModeFrequencyMins, le moteur de cohérence applique la dernière configuration qui a été téléchargée vers le nœud cible. RefreshFrequencyMins doit être définie sur un nombre entier multiple de ConfigurationModeFrequencyMins.
* **Informations d’identification**: indique les informations d’identification (comme avec Get-Credential) permettant d’accéder à des ressources distantes, tels que de contacter le serveur de configuration.
* **DownloadManagerCustomData**: représente un tableau qui contient des données personnalisées spécifiques pour le Gestionnaire de téléchargement.
* **DownloadManagerName**: indique le nom de la configuration et le Gestionnaire de téléchargement du module.
* **RebootNodeIfNeeded**: certaines modifications de configuration sur un nœud cible peuvent nécessiter pour être redémarré pour que les modifications soient appliquées. Avec la valeur **True**, cette propriété redémarrez le nœud dès que la configuration a été complètement s’applique, sans en avertir. Si **False** (valeur par défaut), la configuration aura lieu, mais le nœud doit être redémarré manuellement pour que les modifications prennent effet.
* **RefreshFrequencyMins**: utilisé lorsque vous avez configuré un serveur « extraire ». Représente la fréquence (en minutes) à laquelle le Gestionnaire de Configuration Local contacte un serveur de « extraire » pour télécharger la configuration en cours. Cette valeur peut être définie en association avec ConfigurationModeFrequencyMins. Lorsque RefreshMode est défini sur Extraire, le nœud cible contacte le serveur de « extraire » à un intervalle défini par RefreshFrequencyMins et téléchargements la configuration en cours. À l’intervalle défini par ConfigurationModeFrequencyMins, le moteur de cohérence applique ensuite la configuration la plus récente qui a été téléchargée vers le nœud cible. Si RefreshFrequencyMins n’est pas définie sur un nombre entier multiple de ConfigurationModeFrequencyMins, le système arrondit les. La valeur par défaut est de 30.
* **RefreshMode**: valeurs possibles sont **Push** (par défaut) et **Extraire**. Dans la configuration « push », vous devez placer un fichier de configuration sur chaque nœud cible, à l’aide de n’importe quel ordinateur client. Dans le mode « extraire », vous devez configurer un serveur « extraire » pour le Gestionnaire de Configuration Local pour contacter et accéder aux fichiers de configuration.

### Exemple de mise à jour les paramètres du Gestionnaire de Configuration Local

Vous pouvez mettre à jour le Gestionnaire de Configuration Local bloquent les paramètres d’un nœud cible en incluant un bloc de **LocalConfigurationManager** le nœud dans un script de configuration, comme illustré dans l’exemple suivant.

```powershell
Configuration ExampleConfig
{
    Node “Server001”
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullServer/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"  
```

Exécuter le script dans l’exemple précédent génère un fichier MOF qui spécifie et stocke les paramètres de votre choix. Pour appliquer les paramètres, vous pouvez utiliser l’applet de commande **Set-DscLocalConfigurationManager** , comme le montre l’exemple suivant.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **Remarque**: pour le paramètre de **chemin d’accès** , vous devez spécifier le même chemin d’accès que vous avez spécifié pour le paramètre **OutputPath** lorsque vous avez appelé la configuration de l’exemple précédent.

Pour afficher les paramètres du Gestionnaire de Configuration locale actuelle, vous pouvez utiliser l’applet de commande **Get-DscLocalConfigurationManager** . Si vous appelez cette applet de commande sans paramètres, par défaut se présente les paramètres du Gestionnaire de Configuration Local pour le nœud sur lequel vous l’exécuter. Pour spécifier un autre nœud, utilisez le paramètre **CimSession** avec cette applet de commande.