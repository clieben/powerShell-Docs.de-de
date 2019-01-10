---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Konfigurieren des lokalen Konfigurations-Managers in früheren Versionen von Windows PowerShell
ms.openlocfilehash: 31ba2ecdaa5a2ff7fcfddb1791c4d00343f4b5d5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401466"
---
# <a name="configuring-the-local-configuration-manager-in-previous-versions-of-windows-powershell"></a><span data-ttu-id="a33bf-103">Konfigurieren des lokalen Konfigurations-Managers in früheren Versionen von Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a33bf-103">Configuring the Local Configuration Manager in Previous Versions of Windows PowerShell</span></span>

><span data-ttu-id="a33bf-104">Gilt für: Windows PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="a33bf-104">Applies To: Windows PowerShell 4.0</span></span>

<span data-ttu-id="a33bf-105">**Informationen, die sich auf Windows PowerShell 5.0 und höher beziehen, finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](metaConfig.md).**</span><span class="sxs-lookup"><span data-stu-id="a33bf-105">**For information related to Windows PowerShell 5.0 and later, see [Configuring the Local Configuration Manager](metaConfig.md).**</span></span>

<span data-ttu-id="a33bf-106">Der lokale Konfigurations-Manager (Local Configuration Manager, LCM) ist die Windows PowerShell DSC-Engine (Desired State Configuration, Konfiguration des gewünschten Zustands).</span><span class="sxs-lookup"><span data-stu-id="a33bf-106">Local Configuration Manager is the Windows PowerShell Desired State Configuration (DSC) engine.</span></span>
<span data-ttu-id="a33bf-107">Dieses Modul wird auf allen Zielknoten ausgeführt und ist zuständig für das Aufrufen der Konfigurationsressourcen, die in einem DSC-Konfigurationsskript enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="a33bf-107">It runs on all target nodes, and it is responsible for calling the configuration resources that are included in a DSC configuration script.</span></span>
<span data-ttu-id="a33bf-108">In diesem Thema werden die Eigenschaften des lokalen Konfigurations-Managers (LCM) aufgelistet, und Sie erfahren, wie Sie die LCM-Einstellungen auf einem Zielknoten ändern können.</span><span class="sxs-lookup"><span data-stu-id="a33bf-108">This topic lists the properties of Local Configuration Manager and describes how you can modify the Local Configuration Manager settings on a target node.</span></span>

## <a name="local-configuration-manager-properties"></a><span data-ttu-id="a33bf-109">Eigenschaften des lokalen Konfigurations-Managers</span><span class="sxs-lookup"><span data-stu-id="a33bf-109">Local Configuration Manager properties</span></span>

<span data-ttu-id="a33bf-110">Nachstehend sind die LCM-Eigenschaften aufgelistet, die Sie festlegen oder abrufen können.</span><span class="sxs-lookup"><span data-stu-id="a33bf-110">The following lists the Local Configuration Manager properties that you can set or retrieve.</span></span>

- <span data-ttu-id="a33bf-111">AllowModuleOverwrite Steuert, ob neue vom Konfigurationsdienst heruntergeladene Konfigurationen die alten Konfigurationen auf dem Zielknoten überschreiben dürfen.</span><span class="sxs-lookup"><span data-stu-id="a33bf-111">**AllowModuleOverwrite**: Controls whether new configurations downloaded from the configuration service are allowed to overwrite the old ones on the target node.</span></span> <span data-ttu-id="a33bf-112">Mögliche Werte sind „True“ und „False“.</span><span class="sxs-lookup"><span data-stu-id="a33bf-112">Possible values are True and False.</span></span>
- <span data-ttu-id="a33bf-113">**CertificateID**: Der Fingerabdruck eines Zertifikats zur Sicherung von Anmeldeinformationen, die in einer Konfiguration übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="a33bf-113">**CertificateID**: The thumbprint of a certificate used to secure credentials passed in a configuration.</span></span> <span data-ttu-id="a33bf-114">Weitere Informationen finden Sie unter [Möchten Sie Anmeldeinformationen in Windows PowerShell DSC schützen?](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/).</span><span class="sxs-lookup"><span data-stu-id="a33bf-114">For more information see [Want to secure credentials in Windows PowerShell Desired State Configuration?](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/).</span></span>
- <span data-ttu-id="a33bf-115">ConfigurationID Gibt an, eine GUID, die zum Abrufen einer bestimmten Konfigurationsdatei von einem pulldienst verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a33bf-115">**ConfigurationID**: Indicates a GUID which is used to get a particular configuration file from a pull service.</span></span> <span data-ttu-id="a33bf-116">Die GUID stellt sicher, dass auf die richtige Konfigurationsdatei zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="a33bf-116">The GUID ensures that the correct configuration file is accessed.</span></span>
- <span data-ttu-id="a33bf-117">ConfigurationMode Gibt an, wie die lokalen Konfigurations-Managers die Konfiguration tatsächlich auf die Zielknoten anwendet.</span><span class="sxs-lookup"><span data-stu-id="a33bf-117">**ConfigurationMode**: Specifies how the Local Configuration Manager actually applies the configuration to the target nodes.</span></span> <span data-ttu-id="a33bf-118">Die folgenden Werte sind möglich:</span><span class="sxs-lookup"><span data-stu-id="a33bf-118">It can take the following values:</span></span>
  - <span data-ttu-id="a33bf-119">**ApplyOnly**: Bei dieser Option wendet DSC die Konfiguration an und führt nur dann weitere Aktionen durch, wenn eine neue Konfiguration ermittelt wird – entweder indem Sie eine neue Konfiguration direkt an den Zielknoten senden oder indem Sie eine Verbindung mit einem Pulldienst herstellen und DSC bei der Abfrage des Pulldiensts eine neue Konfiguration ermittelt.</span><span class="sxs-lookup"><span data-stu-id="a33bf-119">**ApplyOnly**: With this option, DSC applies the configuration and does nothing further unless a new configuration is detected, either by you sending a new configuration directly to the target node or if you are connecting to a pull service and DSC discovers a new configuration when it checks with the pull service.</span></span> <span data-ttu-id="a33bf-120">Wenn die Konfiguration des Zielknotens abweicht, erfolgt keine Aktion.</span><span class="sxs-lookup"><span data-stu-id="a33bf-120">If the target node’s configuration drifts, no action is taken.</span></span>
  - <span data-ttu-id="a33bf-121">ApplyAndMonitor Mit dieser Option (der Standard ist), DSC wendet neue Konfigurationen, ob von Ihnen direkt zum Zielknoten gesendet oder in einem pulldienst ermittelt.</span><span class="sxs-lookup"><span data-stu-id="a33bf-121">**ApplyAndMonitor**: With this option (which is the default), DSC applies any new configurations, whether sent by you directly to the target node or discovered on a pull service.</span></span> <span data-ttu-id="a33bf-122">Wenn sich im Anschluss die Konfiguration des Zielknotens von der Konfigurationsdatei unterscheidet, meldet DSC die Diskrepanz in Protokollen.</span><span class="sxs-lookup"><span data-stu-id="a33bf-122">Thereafter, if the configuration of the target node drifts from the configuration file, DSC reports the discrepancy in logs.</span></span> <span data-ttu-id="a33bf-123">Weitere Informationen zur DSC-Protokollierung finden Sie unter [Verwenden von Ereignisprotokollen zum Untersuchen von Fehlern in DSC](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).</span><span class="sxs-lookup"><span data-stu-id="a33bf-123">For more about DSC logging, see [Using Event Logs to Diagnose Errors in Desired State Configuration](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).</span></span>
  - <span data-ttu-id="a33bf-124">ApplyAndAutoCorrect Mit dieser Option wendet DSC neue Konfigurationen,, ob die von Ihnen direkt zum Zielknoten gesendet oder in einem pulldienst ermittelt.</span><span class="sxs-lookup"><span data-stu-id="a33bf-124">**ApplyAndAutoCorrect**: With this option, DSC applies any new configurations, whether sent by you directly to the target node or discovered on a pull service.</span></span> <span data-ttu-id="a33bf-125">Wenn sich im Anschluss die Konfiguration des Zielknotens von der Konfigurationsdatei unterscheidet, meldet DSC die Diskrepanz in Protokollen. Anschließend wird versucht, die Zielknotenkonfiguration in Übereinstimmung mit der Konfigurationsdatei zu bringen.</span><span class="sxs-lookup"><span data-stu-id="a33bf-125">Thereafter, if the configuration of the target node drifts from the configuration file, DSC reports the discrepancy in logs, and then attempts to adjust the target node configuration to bring in compliance with the configuration file.</span></span>
- <span data-ttu-id="a33bf-126">ConfigurationModeFrequencyMins Gibt die Frequenz (in Minuten), die mit der die hintergrundanwendung von DSC versucht, um die aktuelle Konfiguration auf dem Zielknoten zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="a33bf-126">**ConfigurationModeFrequencyMins**: Represents the frequency (in minutes) at which the background application of DSC attempts to implement the current configuration on the target node.</span></span> <span data-ttu-id="a33bf-127">Der Standardwert ist 15.</span><span class="sxs-lookup"><span data-stu-id="a33bf-127">The default value is 15.</span></span> <span data-ttu-id="a33bf-128">Dieser Wert kann in Verbindung mit „RefreshMode“ festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="a33bf-128">This value can be set in conjunction with RefreshMode.</span></span> <span data-ttu-id="a33bf-129">Wenn „RefreshMode“ auf PULL festgelegt ist, kontaktiert der Zielknoten den Konfigurationsdienst in einem von „RefreshFrequencyMins“ festgelegten Intervall und lädt die aktuelle Konfiguration herunter.</span><span class="sxs-lookup"><span data-stu-id="a33bf-129">When RefreshMode is set to PULL, the target node contacts the configuration service at an interval set by RefreshFrequencyMins and downloads the current configuration.</span></span> <span data-ttu-id="a33bf-130">Unabhängig vom Wert von „RefreshMode“ wendet die Konsistenz-Engine im von „ConfigurationModeFrequencyMins“ festgelegten Intervall die neueste Konfiguration an, die auf den Zielknoten heruntergeladen wurde.</span><span class="sxs-lookup"><span data-stu-id="a33bf-130">Regardless of the RefreshMode value, at the interval set by ConfigurationModeFrequencyMins, the consistency engine applies the latest configuration that was downloaded to the target node.</span></span> <span data-ttu-id="a33bf-131">„RefreshFrequencyMins“ muss auf ein Vielfaches in Form einer ganzen Zahl von „ConfigurationModeFrequencyMins“ festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="a33bf-131">RefreshFrequencyMins should be set to an integer multiple of ConfigurationModeFrequencyMins.</span></span>
- <span data-ttu-id="a33bf-132">-Credential Gibt die Anmeldeinformationen (wie bei Get-Credential) erforderlich sind, z. B. den Zugriff auf Remoteressourcen an um den Konfigurationsdienst zu kontaktieren.</span><span class="sxs-lookup"><span data-stu-id="a33bf-132">**Credential**: Indicates credentials (as with Get-Credential) required to access remote resources, such as to contact the configuration service.</span></span>
- <span data-ttu-id="a33bf-133">**DownloadManagerCustomData**: Stellt ein Array mit benutzerdefinierten Daten, die spezifisch für den Download-Manager dar.</span><span class="sxs-lookup"><span data-stu-id="a33bf-133">**DownloadManagerCustomData**: Represents an array that contains custom data specific to the download manager.</span></span>
- <span data-ttu-id="a33bf-134">**DownloadManagerName**: Gibt den Namen der Konfiguration und der Modul-Download-Manager.</span><span class="sxs-lookup"><span data-stu-id="a33bf-134">**DownloadManagerName**: Indicates the name of the configuration and module download manager.</span></span>
- <span data-ttu-id="a33bf-135">RebootNodeIfNeeded Bestimmte Änderungen an der Konfiguration auf einem Zielknoten möglicherweise neu gestartet werden, damit die Änderungen angewendet werden erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a33bf-135">**RebootNodeIfNeeded**: Certain configuration changes on a target node might require it to be restarted for the changes to be applied.</span></span> <span data-ttu-id="a33bf-136">Bei Festlegen auf **True** startet diese Eigenschaft den Knoten ohne vorherige Warnung neu, sobald die Konfiguration vollständig angewendet wurde.</span><span class="sxs-lookup"><span data-stu-id="a33bf-136">With the value **True**, this property will restart the node as soon as the configuration has been completely applies, without further warning.</span></span> <span data-ttu-id="a33bf-137">Falls **False** (Standardwert), wird die Konfiguration abgeschlossen, aber der Knoten muss manuell neu gestartet werden, damit die Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="a33bf-137">If **False** (the default value), the configuration will be completed, but the node must be restarted manually for the changes to take effect.</span></span>
- <span data-ttu-id="a33bf-138">RefreshFrequencyMins Verwendet, wenn Sie einen pulldienst eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="a33bf-138">**RefreshFrequencyMins**: Used when you have set up a pull service.</span></span> <span data-ttu-id="a33bf-139">Stellt die Häufigkeit (in Minuten) dar, mit der der lokale Konfigurations-Manager einen Pulldienst kontaktiert, um die aktuelle Konfiguration herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="a33bf-139">Represents the frequency (in minutes) at which the Local Configuration Manager contacts a pull service to download the current configuration.</span></span> <span data-ttu-id="a33bf-140">Dieser Wert kann in Verbindung mit „ConfigurationModeFrequencyMins“ festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="a33bf-140">This value can be set in conjunction with ConfigurationModeFrequencyMins.</span></span> <span data-ttu-id="a33bf-141">Wenn „RefreshMode“ auf PULL festgelegt ist, kontaktiert der Zielknoten den Pulldienst in einem von „RefreshFrequencyMins“ festgelegten Intervall und lädt die aktuelle Konfiguration herunter.</span><span class="sxs-lookup"><span data-stu-id="a33bf-141">When RefreshMode is set to PULL, the target node contacts the pull service at an interval set by RefreshFrequencyMins and downloads the current configuration.</span></span> <span data-ttu-id="a33bf-142">Die Konsistenz-Engine wendet im von „ConfigurationModeFrequencyMins“ festgelegten Intervall die neueste Konfiguration an, die auf den Zielknoten heruntergeladen wurde.</span><span class="sxs-lookup"><span data-stu-id="a33bf-142">At the interval set by ConfigurationModeFrequencyMins, the consistency engine then applies the latest configuration that was downloaded to the target node.</span></span> <span data-ttu-id="a33bf-143">Wenn „RefreshFrequencyMins“ nicht in Form einer ganzen Zahl auf ein Vielfaches von „ConfigurationModeFrequencyMins“ festgelegt wurde, rundet das System den Wert auf.</span><span class="sxs-lookup"><span data-stu-id="a33bf-143">If RefreshFrequencyMins is not set to an integer multiple of ConfigurationModeFrequencyMins, the system will round it up.</span></span> <span data-ttu-id="a33bf-144">Der Standardwert ist 30.</span><span class="sxs-lookup"><span data-stu-id="a33bf-144">The default value is 30.</span></span>
- <span data-ttu-id="a33bf-145">RefreshMode Mögliche Werte sind **Push** (Standard) und **Pull**.</span><span class="sxs-lookup"><span data-stu-id="a33bf-145">**RefreshMode**: Possible values are **Push** (the default) and **Pull**.</span></span> <span data-ttu-id="a33bf-146">Bei der Pushkonfiguration müssen Sie mithilfe eines beliebigen Clientcomputers eine Konfigurationsdatei auf jedem Zielknoten ablegen.</span><span class="sxs-lookup"><span data-stu-id="a33bf-146">In the “push” configuration, you must place a configuration file on each target node, using any client computer.</span></span> <span data-ttu-id="a33bf-147">Im Pullmodus müssen Sie einen Pulldienst für den lokalen Konfigurations-Manager einrichten, der für den Zugriff auf die Konfigurationsdateien kontaktiert werden muss.</span><span class="sxs-lookup"><span data-stu-id="a33bf-147">In the “pull” mode, you must set up a pull service for Local Configuration Manager to contact and access the configuration files.</span></span>

### <a name="example-of-updating-local-configuration-manager-settings"></a><span data-ttu-id="a33bf-148">Beispiel der Aktualisierung der Einstellungen des lokalen Konfigurations-Managers</span><span class="sxs-lookup"><span data-stu-id="a33bf-148">Example of updating Local Configuration Manager settings</span></span>

<span data-ttu-id="a33bf-149">Sie können die Einstellungen des lokalen Konfigurations-Managers auf einem Zielknoten aktualisieren, indem Sie einen **LocalConfigurationManager**-Block dem „node“-Block in einem Konfigurationsskript hinzufügen (siehe das folgende Beispiel).</span><span class="sxs-lookup"><span data-stu-id="a33bf-149">You can update the Local Configuration Manager settings of a target node by including a **LocalConfigurationManager** block inside the node block in a configuration script, as shown in the following example.</span></span>

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
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
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

<span data-ttu-id="a33bf-150">Bei Ausführen des Skripts im vorherigen Beispiel wird eine MOF-Datei generiert, die die gewünschten Einstellungen angibt und speichert.</span><span class="sxs-lookup"><span data-stu-id="a33bf-150">Running the script in the previous example generates a MOF file that specifies and stores the desired settings.</span></span>
<span data-ttu-id="a33bf-151">Um die Einstellungen zu übernehmen, können Sie das Cmdlet **Set DscLocalConfigurationManager** verwenden (siehe das folgende Beispiel).</span><span class="sxs-lookup"><span data-stu-id="a33bf-151">To apply the settings, you can use the **Set-DscLocalConfigurationManager** cmdlet, as shown in the following example.</span></span>

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> <span data-ttu-id="a33bf-152">**Hinweis**: Für den **Path**-Parameter müssen Sie denselben Pfad angeben, den Sie für den **OutputPath**-Parameter angegeben haben, als Sie die Konfiguration im vorherigen Beispiel aufgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="a33bf-152">**Note**: For the **Path** parameter, you must specify the same path that you specified for the **OutputPath** parameter when you invoked the configuration in the previous example.</span></span>

<span data-ttu-id="a33bf-153">Mit dem Cmdlet **Get-DscLocalConfigurationManager** können Sie die aktuellen Einstellungen des lokalen Konfigurations-Managers anzeigen.</span><span class="sxs-lookup"><span data-stu-id="a33bf-153">To see the current Local Configuration Manager settings, you can use the **Get-DscLocalConfigurationManager** cmdlet.</span></span>
<span data-ttu-id="a33bf-154">Wenn Sie dieses Cmdlet ohne Parameter aufrufen, werden standardmäßig die Einstellungen des lokalen Konfigurations-Manager für den Knoten abgerufen, auf dem er ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a33bf-154">If you invoke this cmdlet with no parameters, by default it will get the Local Configuration Manager settings for the node on which you run it.</span></span>
<span data-ttu-id="a33bf-155">Um einen anderen Knoten anzugeben, verwenden Sie mit diesem Cmdlet den **CimSession**-Parameter.</span><span class="sxs-lookup"><span data-stu-id="a33bf-155">To specify another node, use the **CimSession** parameter with this cmdlet.</span></span>