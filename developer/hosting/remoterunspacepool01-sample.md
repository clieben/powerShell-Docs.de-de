---
title: Beispiel für RemoteRunspacePool01 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dffedd31-c10d-4e11-a9ee-4fdfe9a869e8
caps.latest.revision: 8
ms.openlocfilehash: 980fbff49a3481d92c2ca8483772b1704462c499
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857596"
---
# <a name="remoterunspacepool01-sample"></a><span data-ttu-id="b4cbd-102">RemoteRunspacePool01-Beispiel</span><span class="sxs-lookup"><span data-stu-id="b4cbd-102">RemoteRunspacePool01 Sample</span></span>

<span data-ttu-id="b4cbd-103">Dieses Beispiel zeigt, wie Sie einen Remoterunspace-Pool zu erstellen und wie Sie mehrere Befehle gleichzeitig ausgeführt werden, mithilfe von diesem Pool.</span><span class="sxs-lookup"><span data-stu-id="b4cbd-103">This sample shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

## <a name="requirements"></a><span data-ttu-id="b4cbd-104">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="b4cbd-104">Requirements</span></span>

 <span data-ttu-id="b4cbd-105">Dieses Beispiel ist die Windows PowerShell 2.0 erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b4cbd-105">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b4cbd-106">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="b4cbd-106">Demonstrates</span></span>

- <span data-ttu-id="b4cbd-107">Erstellen einer [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) Objekt.</span><span class="sxs-lookup"><span data-stu-id="b4cbd-107">Creating a [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span>

- <span data-ttu-id="b4cbd-108">Festlegen der [System.Management.Automation.Runspaces.Runspaceconnectioninfo.Operationtimeout\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OperationTimeout) und [System.Management.Automation.Runspaces.Runspaceconnectioninfo.Opentimeout\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OpenTimeout) Eigenschaften der [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) Objekt.</span><span class="sxs-lookup"><span data-stu-id="b4cbd-108">Setting the [System.Management.Automation.Runspaces.Runspaceconnectioninfo.Operationtimeout\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OperationTimeout) and [System.Management.Automation.Runspaces.Runspaceconnectioninfo.Opentimeout\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OpenTimeout) properties of the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span>

- <span data-ttu-id="b4cbd-109">Erstellen einen Remoterunspace, verwendet der [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) Objekt, das Herstellen der Remoteverbindung.</span><span class="sxs-lookup"><span data-stu-id="b4cbd-109">Creating a remote runspace that uses the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object to establish the remote connection.</span></span>

- <span data-ttu-id="b4cbd-110">Ausführen der [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) und [Get-Service](/powershell/module/microsoft.powershell.management/get-service) Cmdlets gleichzeitig mit dem Remoterunspace-Pool.</span><span class="sxs-lookup"><span data-stu-id="b4cbd-110">Running the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlets concurrently by using the remote runspace pool.</span></span>
- <span data-ttu-id="b4cbd-111">Ausführen der [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) und [Get-Service](/powershell/module/microsoft.powershell.management/get-service) Cmdlets gleichzeitig mit dem Remoterunspace-Pool.</span><span class="sxs-lookup"><span data-stu-id="b4cbd-111">Running the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlets concurrently by using the remote runspace pool.</span></span>

- <span data-ttu-id="b4cbd-112">Schließen die Remoterunspace-Pool, um die Remoteverbindung freizugeben.</span><span class="sxs-lookup"><span data-stu-id="b4cbd-112">Closing the remote runspace pool to release the remote connection.</span></span>

## <a name="example"></a><span data-ttu-id="b4cbd-113">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b4cbd-113">Example</span></span>

 <span data-ttu-id="b4cbd-114">Dieses Beispiel zeigt, wie Sie einen Remoterunspace-Pool zu erstellen und wie Sie mehrere Befehle gleichzeitig ausgeführt werden, mithilfe von diesem Pool.</span><span class="sxs-lookup"><span data-stu-id="b4cbd-114">This sample shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

```csharp
namespace Samples
{
  using System;
  using System.Management.Automation;            // Windows PowerShell namespace.
  using System.Management.Automation.Runspaces;  // Windows PowerShell namespace.

  /// <summary>
  /// This class contains the Main enrty point for the application.
  /// </summary>
  internal class RemoteRunspacePool01
  {
    /// <summary>
    /// This sample shows how to construct a remote RunspacePool and how to
    /// concurrently run the get-process and get-service commands using the
    /// runspaces of the pool.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    public static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor to
      // connect to the "localhost". The WSManConnectionInfo object can also
      // specify connections to remote computers.
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

      // Create a remote runspace pool that uses the WSManConnectionInfo object.
      // The minimum runspaces value of 1 specifies that Windows PowerShell will
      // keep at least 1 runspace open. The maximum runspaces value of 2 specifies
      // that Windows PowerShell will allows 2 runspaces to be opened at the
      // same time so that two commands can be run concurrently.
      using (RunspacePool remoteRunspacePool =
             RunspaceFactory.CreateRunspacePool(1, 2, connectionInfo))
      {
        // Call the Open() method to open the runspace pool and establish
        // the connection.
        remoteRunspacePool.Open();

        // Call the Create() method to create a pipeline, call the AddCommand(string)
        // method to add the "get-process" command, and then call the BeginInvoke()
        // method to run the command asynchronously using a runspace of the pool.
        PowerShell gpsCommand = PowerShell.Create().AddCommand("get-process");
        gpsCommand.RunspacePool = remoteRunspacePool;
        IAsyncResult gpsCommandAsyncResult = gpsCommand.BeginInvoke();

        // The previous call does not block the current thread because it is
        // running asynchronously. Because the remote runspace pool can open two
        // runspaces, the second command can be run.
        PowerShell getServiceCommand = PowerShell.Create().AddCommand("get-service");
        getServiceCommand.RunspacePool = remoteRunspacePool;
        IAsyncResult getServiceCommandAsyncResult = getServiceCommand.BeginInvoke();

        // When you are ready to handle the output, wait for the command to complete
        // before extracting results. A call to the EndInvoke() method will block and return
        // the output.
        PSDataCollection<PSObject> gpsCommandOutput = gpsCommand.EndInvoke(gpsCommandAsyncResult);

        // Process the output from the first command.
        if ((gpsCommandOutput != null) && (gpsCommandOutput.Count > 0))
        {
          Console.WriteLine("The first output from running get-process command: ");
          Console.WriteLine(
                            "Process Name: {0} Process Id: {1}",
                            gpsCommandOutput[0].Properties["ProcessName"].Value,
                            gpsCommandOutput[0].Properties["Id"].Value);
          Console.WriteLine();
        }

        // Now process the output from the second command. As discussed previously, wait
        // for the command to complete before extracting the results.
        PSDataCollection<PSObject> getServiceCommandOutput = getServiceCommand.EndInvoke(
                                   getServiceCommandAsyncResult);

        // Process the output of the second command as needed.
        if ((getServiceCommandOutput != null) && (getServiceCommandOutput.Count > 0))
        {
          Console.WriteLine("The first output from running get-service command: ");
          Console.WriteLine(
                            "Service Name: {0} Description: {1} State: {2}",
                            getServiceCommandOutput[0].Properties["ServiceName"].Value,
                            getServiceCommandOutput[0].Properties["DisplayName"].Value,
                            getServiceCommandOutput[0].Properties["Status"].Value);
        }

        // Once done with running all the commands, close the remote runspace pool.
        // The Dispose() method (called by using primitive) will call Close(), if it
        // is not already called.
        remoteRunspacePool.Close();
      } // End Using.
    } // End Main.
  } // End RemoteRunspacePool01 class
}
```

## <a name="see-also"></a><span data-ttu-id="b4cbd-115">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b4cbd-115">See Also</span></span>