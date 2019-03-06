---
title: Hinzufügen und Aufrufen von Befehlen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 31371797ee57f07075da3436e0b42b2ca01aaffd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857346"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="eeab5-102">Hinzufügen und Aufrufen von Befehlen</span><span class="sxs-lookup"><span data-stu-id="eeab5-102">Adding and invoking commands</span></span>

<span data-ttu-id="eeab5-103">Nachdem ein Runspace erstellt haben, können Sie Windows PowerShellcommands und Skripts hinzufügen, um eine Pipeline und rufen Sie dann die Pipeline synchron oder asynchron.</span><span class="sxs-lookup"><span data-stu-id="eeab5-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="eeab5-104">Erstellen einer pipeline</span><span class="sxs-lookup"><span data-stu-id="eeab5-104">Creating a pipeline</span></span>

 <span data-ttu-id="eeab5-105">Die [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Klasse bietet mehrere Methoden, um Befehle, Parameter und Skripts zur Pipeline hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="eeab5-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="eeab5-106">Sie können die Pipeline synchron durch Aufruf einer Überladung von Aufrufen der [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) -Methode, oder asynchron durch Aufruf einer Überladung der der [ System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) und klicken Sie dann die [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) Methode.</span><span class="sxs-lookup"><span data-stu-id="eeab5-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="eeab5-107">AddCommand</span><span class="sxs-lookup"><span data-stu-id="eeab5-107">AddCommand</span></span>

1. <span data-ttu-id="eeab5-108">Erstellen Sie eine [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Objekt.</span><span class="sxs-lookup"><span data-stu-id="eeab5-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="eeab5-109">Fügen Sie den Befehl aus, dem Sie ausführen möchten.</span><span class="sxs-lookup"><span data-stu-id="eeab5-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="eeab5-110">Rufen Sie den Befehl.</span><span class="sxs-lookup"><span data-stu-id="eeab5-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="eeab5-111">Aufrufen der [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) Methode, die mehr als einmal vor dem Aufruf der [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) -Methode, die das Ergebnis der ersten Befehl wird über die Pipeline zum zweiten und So weiter.</span><span class="sxs-lookup"><span data-stu-id="eeab5-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="eeab5-112">Wenn Sie nicht das Ergebnis eines vorherigen Befehls an einen Befehl übergeben möchten, fügen Sie ihn durch Aufrufen der [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) stattdessen.</span><span class="sxs-lookup"><span data-stu-id="eeab5-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="eeab5-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="eeab5-113">AddParameter</span></span>

 <span data-ttu-id="eeab5-114">Im vorherige Beispiel führt einen einzelnen Befehl ohne Parameter aus.</span><span class="sxs-lookup"><span data-stu-id="eeab5-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="eeab5-115">Sie können Parameter an den Befehl hinzufügen, mit der [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) z. B. der folgende Code ruft Methode eine Liste aller Prozesse mit dem Namen `PowerShell` unter der Computer.</span><span class="sxs-lookup"><span data-stu-id="eeab5-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="eeab5-116">Sie können zusätzliche Parameter hinzufügen, durch den Aufruf [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) wiederholt.</span><span class="sxs-lookup"><span data-stu-id="eeab5-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="eeab5-117">Sie können auch ein Wörterbuch von Parameternamen und Werte hinzufügen, durch den Aufruf der [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) Methode.</span><span class="sxs-lookup"><span data-stu-id="eeab5-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="eeab5-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="eeab5-118">AddStatement</span></span>

 <span data-ttu-id="eeab5-119">Sie können mithilfe von Batchverarbeitung simulieren die [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) -Methode, die an das Ende der Pipeline eine zusätzliche Anweisung der folgende Code eine Liste fügt ruft der ausgeführten Prozesse mit dem Namen `PowerShell`, und ruft anschließend die Liste der ausgeführten Dienste.</span><span class="sxs-lookup"><span data-stu-id="eeab5-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="eeab5-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="eeab5-120">AddScript</span></span>

 <span data-ttu-id="eeab5-121">Sie können ein vorhandenes Skript ausführen, durch den Aufruf der [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) Methode.</span><span class="sxs-lookup"><span data-stu-id="eeab5-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="eeab5-122">Im folgenden Beispiel wird die Pipeline ein Skript hinzugefügt und wird ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="eeab5-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="eeab5-123">In diesem Beispiel wird vorausgesetzt, es ist bereits ein Skript namens `MyScript.ps1` in einem Ordner namens `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="eeab5-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="eeab5-124">Es gibt auch eine Version der [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) -Methode, die einen booleschen namens Parameter `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="eeab5-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="eeab5-125">Wenn dieser Parameter, um festgelegt wird `true`, und klicken Sie dann das Skript im lokalen Bereich ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="eeab5-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="eeab5-126">Der folgende Code führt das Skript im lokalen Bereich.</span><span class="sxs-lookup"><span data-stu-id="eeab5-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="eeab5-127">Synchron Aufrufen einer pipeline</span><span class="sxs-lookup"><span data-stu-id="eeab5-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="eeab5-128">Nachdem Sie die Pipeline Elemente hinzuzufügen, rufen Sie es.</span><span class="sxs-lookup"><span data-stu-id="eeab5-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="eeab5-129">Um die Pipeline synchron aufzurufen, rufen Sie eine Überladung von der [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) Methode.</span><span class="sxs-lookup"><span data-stu-id="eeab5-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="eeab5-130">Das folgende Beispiel zeigt, wie Sie eine Pipeline synchron aufrufen.</span><span class="sxs-lookup"><span data-stu-id="eeab5-130">The following example shows how to synchronously invoke a pipeline.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="eeab5-131">Aufrufen einer Pipeline asynchron</span><span class="sxs-lookup"><span data-stu-id="eeab5-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="eeab5-132">Sie rufen eine Pipeline asynchron durch Aufruf einer Überladung der der [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) zum Erstellen einer [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) , und klicken Sie dann durch Aufrufen der [ System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) Methode.</span><span class="sxs-lookup"><span data-stu-id="eeab5-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="eeab5-133">Das folgende Beispiel zeigt, wie Sie eine Pipeline Asynchronoulsy aufrufen.</span><span class="sxs-lookup"><span data-stu-id="eeab5-133">The following example shows how to invoke a pipeline asynchronoulsy.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediatly
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a><span data-ttu-id="eeab5-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="eeab5-134">See Also</span></span>

 [<span data-ttu-id="eeab5-135">Erstellen eine InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="eeab5-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="eeab5-136">Erstellen einen eingeschränkten runspace</span><span class="sxs-lookup"><span data-stu-id="eeab5-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)