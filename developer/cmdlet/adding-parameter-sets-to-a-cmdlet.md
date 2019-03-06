---
title: Parameter hinzufügen zu einem Cmdlet legt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: b02a2e0d4b0a27c261b0bc05febda7826ad5276e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859266"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="c085f-102">Hinzufügen von Parametersätzen zu einem Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c085f-102">Adding Parameter Sets to a Cmdlet</span></span>

<span data-ttu-id="c085f-103">Dieser Abschnitt beschreibt das Hinzufügen der Parameter legt fest, an das Stop-Proc-Cmdlet (beschrieben [ein Cmdlets zu erstellen, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="c085f-103">This section describes how to add parameter sets to the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span> <span data-ttu-id="c085f-104">Ähnlich wie die anderen in diesem Programmer's Guide beschriebenen Stop-Proc-Cmdlets, mit diesem Cmdlet versucht, Prozesse zu beenden, die mit dem Get-Proc-Cmdlet abgerufen werden (beschrieben [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="c085f-104">Similar to the other Stop-Proc cmdlets described in this Programmer's Guide, this cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="c085f-105">Die folgenden: Themen in diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="c085f-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="c085f-106">Wissenswerte Fakten über Parametersätze</span><span class="sxs-lookup"><span data-stu-id="c085f-106">Things to Know About Parameter Sets</span></span>](#Adding-Parameter-Sets-to-a-Cmdlet)

- [<span data-ttu-id="c085f-107">Deklarieren Sie die Cmdlet-Klasse</span><span class="sxs-lookup"><span data-stu-id="c085f-107">Declaring the Cmdlet Class</span></span>](#Declaring-the-Cmdlet-Class)

- [<span data-ttu-id="c085f-108">Deklarieren Sie die Parameter des Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c085f-108">Declaring the Parameters of the Cmdlet</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="c085f-109">Überschreiben einer Eingabeverarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="c085f-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="c085f-110">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="c085f-110">Code Sample</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="c085f-111">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="c085f-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="c085f-112">Erstellen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c085f-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="c085f-113">Testen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c085f-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="c085f-114">Wissenswerte Fakten über Parametersätze</span><span class="sxs-lookup"><span data-stu-id="c085f-114">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="c085f-115">Windows PowerShell definiert einen Parameter, die als einer Gruppenstatus von Parametern, die zusammen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c085f-115">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="c085f-116">Durch Gruppieren von den Parametern eines Cmdlets, können Sie ein einzelnes Cmdlet erstellen, das seine Funktionalität, die basierend auf der gibt an, welche Gruppe von Parametern an der Benutzer geändert werden können.</span><span class="sxs-lookup"><span data-stu-id="c085f-116">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="c085f-117">Ein Beispiel für ein Cmdlet, das zwei Parametersätze verwendet, um Funktionen zu definieren ist die `Get-EventLog` -Cmdlet, das von Windows PowerShell bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="c085f-117">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="c085f-118">Dieses Cmdlet gibt unterschiedliche Informationen zurück, wenn der Benutzer gibt die `List` oder `LogName` Parameter.</span><span class="sxs-lookup"><span data-stu-id="c085f-118">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="c085f-119">Wenn die `LogName` -Parameter angegeben wird, das Cmdlet gibt Informationen zu den Ereignissen in einem bestimmten Ereignisprotokoll zurück.</span><span class="sxs-lookup"><span data-stu-id="c085f-119">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="c085f-120">Wenn die `List` -Parameter angegeben wird, mit dem-Cmdlet gibt Informationen über die Log-Dateien selbst (nicht die Ereignisinformationen, die sie enthalten).</span><span class="sxs-lookup"><span data-stu-id="c085f-120">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="c085f-121">In diesem Fall die `List` und `LogName` Parameter zu identifizieren, zwei separate Parametersätze.</span><span class="sxs-lookup"><span data-stu-id="c085f-121">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="c085f-122">Zwei wichtige Punkte zu erinnern Parametersätze ist, dass die Windows PowerShell-Laufzeit verwendet nur einen Parameter für eine bestimmte Eingabe festgelegt, und dass jeder Parametersatz mindestens einen Parameter verfügen muss, die für diese Parametersatz eindeutig.</span><span class="sxs-lookup"><span data-stu-id="c085f-122">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="c085f-123">Um diesen letzten Punkt zu veranschaulichen, das Stop-Proc-Cmdlet verwendet drei Parametersätze: `ProcessName`, `ProcessId`, und `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="c085f-123">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="c085f-124">All diese Parameter verfügt über einen Parameter, die nicht in den anderen Parameter vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="c085f-124">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="c085f-125">Die Parametersätze können andere Parameter freigeben, aber das Cmdlet verwendet die eindeutigen Parameter `ProcessName`, `ProcessId`, und `InputObject` , welche Parameter zu identifizieren, die die Windows PowerShell-Laufzeit verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="c085f-125">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="c085f-126">Deklarieren Sie die Cmdlet-Klasse</span><span class="sxs-lookup"><span data-stu-id="c085f-126">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="c085f-127">Der erste Schritt bei der Cmdlet-Erstellung ist immer benennen das Cmdlet und .NET implementiert die Klasse, mit dem-Cmdlet deklarieren.</span><span class="sxs-lookup"><span data-stu-id="c085f-127">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="c085f-128">Bei diesem Cmdlet ist das Lebenszyklus-Verb "Stop" verwendet, da das Cmdlet Systemprozesse beendet.</span><span class="sxs-lookup"><span data-stu-id="c085f-128">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="c085f-129">Der Namen der Nomen "Proc" wird verwendet, da das-Cmdlet für Prozesse verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="c085f-129">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="c085f-130">Beachten Sie, dass der cmdletnamen Verb- und den Namen der Cmdlet-Klasse übernommen werden, in der folgenden Deklaration.</span><span class="sxs-lookup"><span data-stu-id="c085f-130">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="c085f-131">Weitere Informationen zu genehmigten Verb cmdletnamen, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="c085f-131">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="c085f-132">Der folgende Code ist die Definition der Klasse für dieses Cmdlet Stop-Prozessor.</span><span class="sxs-lookup"><span data-stu-id="c085f-132">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="c085f-133">Deklarieren Sie die Parameter des Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c085f-133">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="c085f-134">Dieses Cmdlet definiert drei Parameter, die erforderlich sind, als Eingabe an das Cmdlet (dieser Parameter definieren auch die Parametersätze), als auch eine `Force` Parameter, der verwaltet wird, was das Cmdlet durchführt und eine `PassThru` Parameter, der bestimmt, ob das Cmdlet sendet eine Ausgabeobjekt über die Pipeline.</span><span class="sxs-lookup"><span data-stu-id="c085f-134">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="c085f-135">Standardmäßig wird mit diesem Cmdlet nicht auf ein Objekt über die Pipeline übergeben.</span><span class="sxs-lookup"><span data-stu-id="c085f-135">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="c085f-136">Weitere Informationen zu diesen beiden letzten Parameter, finden Sie unter [ein Cmdlets zu erstellen, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="c085f-136">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="c085f-137">Deklarieren Sie den Name-Parameter</span><span class="sxs-lookup"><span data-stu-id="c085f-137">Declaring the Name Parameter</span></span>

<span data-ttu-id="c085f-138">Dieser Eingabeparameter ermöglicht den Benutzer die Namen der zu beendenden Prozesse an.</span><span class="sxs-lookup"><span data-stu-id="c085f-138">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="c085f-139">Beachten Sie, dass die `ParameterSetName` -Schlüsselwort von Attribut der [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attribut gibt an, die `ProcessName` Parametersatz für diesen Parameter.</span><span class="sxs-lookup"><span data-stu-id="c085f-139">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

<span data-ttu-id="c085f-140">Beachten Sie außerdem, dass der Alias "ProcessName" für diesen Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="c085f-140">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="c085f-141">Deklarieren Sie den Id-Parameter</span><span class="sxs-lookup"><span data-stu-id="c085f-141">Declaring the Id Parameter</span></span>

<span data-ttu-id="c085f-142">Dieser Eingabeparameter kann der Benutzer geben die Bezeichner der zu beendenden Prozesse an.</span><span class="sxs-lookup"><span data-stu-id="c085f-142">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="c085f-143">Beachten Sie, dass die `ParameterSetName` -Schlüsselwort von Attribut der [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attribut gibt an, die `ProcessId` Parametersatz.</span><span class="sxs-lookup"><span data-stu-id="c085f-143">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

<span data-ttu-id="c085f-144">Beachten Sie außerdem, dass der Alias "ProcessId" für diesen Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="c085f-144">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="c085f-145">Deklarieren Sie den InputObject-Parameter</span><span class="sxs-lookup"><span data-stu-id="c085f-145">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="c085f-146">Dieser Eingabeparameter ermöglicht die Angabe ein input-Objekt, das Informationen über die Prozesse beendet werden, enthält.</span><span class="sxs-lookup"><span data-stu-id="c085f-146">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="c085f-147">Beachten Sie, dass die `ParameterSetName` -Schlüsselwort von Attribut der [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attribut gibt an, die `InputObject` Parametersatz für diesen Parameter.</span><span class="sxs-lookup"><span data-stu-id="c085f-147">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

<span data-ttu-id="c085f-148">Beachten Sie, dass dieser Parameter kein Alias hat.</span><span class="sxs-lookup"><span data-stu-id="c085f-148">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="c085f-149">Deklarieren von Parametern in mehrere Parametersätze</span><span class="sxs-lookup"><span data-stu-id="c085f-149">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="c085f-150">Obwohl ein unique-Parameter für jeden Parameter vorhanden sein muss, können Parameter mehr als einem Parametersatz angehören.</span><span class="sxs-lookup"><span data-stu-id="c085f-150">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="c085f-151">Geben Sie in diesen Fällen "freigegebenen Parameter" ein [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) Attributdeklaration für jeweils den Wert, den Parameter gehört.</span><span class="sxs-lookup"><span data-stu-id="c085f-151">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="c085f-152">Wenn ein Parameter in der alle Parametersätze, nur einmal das Parameter-Attribut deklarieren und müssen nicht angeben, dass der Parameter Name festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c085f-152">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="c085f-153">Überschreiben einer Eingabeverarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="c085f-153">Overriding an Input Processing Method</span></span>

<span data-ttu-id="c085f-154">Jedes Cmdlet eine eingabeverarbeitungsmethode muss überschrieben werden, den meisten Fällen die [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode.</span><span class="sxs-lookup"><span data-stu-id="c085f-154">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="c085f-155">In diesem Cmdlet die [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode wird überschrieben, sodass das Cmdlet eine beliebige Anzahl von Prozessen verarbeitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="c085f-155">In this cmdlet, the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="c085f-156">Sie enthält eine Select-Anweisung, die Aufrufe an, dass eine andere Methode festlegen, für die Parameter der Benutzerbasis wurde angegeben.</span><span class="sxs-lookup"><span data-stu-id="c085f-156">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

<span data-ttu-id="c085f-157">Die Hilfsmethoden, die von der Select-Anweisung aufgerufen werden hier nicht beschrieben, aber Sie können ihre Implementierung in das vollständige Codebeispiel im nächsten Abschnitt sehen.</span><span class="sxs-lookup"><span data-stu-id="c085f-157">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c085f-158">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="c085f-158">Code Sample</span></span>

<span data-ttu-id="c085f-159">Für die vollständige C# Beispielcode, finden Sie unter [StopProcessSample04 Beispiel](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c085f-159">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="c085f-160">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="c085f-160">Defining Object Types and Formatting</span></span>

<span data-ttu-id="c085f-161">Windows PowerShell übergibt Informationen zwischen Cmdlets, die mithilfe von .NET-Objekten.</span><span class="sxs-lookup"><span data-stu-id="c085f-161">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="c085f-162">Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren, oder das-Cmdlet zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet angegeben müssen.</span><span class="sxs-lookup"><span data-stu-id="c085f-162">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="c085f-163">Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="c085f-163">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="c085f-164">Erstellen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c085f-164">Building the Cmdlet</span></span>

<span data-ttu-id="c085f-165">Nach der Implementierung eines Cmdlets, müssen Sie es mit Windows PowerShell über eine Windows PowerShell-Snap-in registrieren.</span><span class="sxs-lookup"><span data-stu-id="c085f-165">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="c085f-166">Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="c085f-166">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="c085f-167">Testen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c085f-167">Testing the Cmdlet</span></span>

<span data-ttu-id="c085f-168">Wenn Ihr Cmdlet in Windows PowerShell registriert wurde, testen Sie es in der Befehlszeile aus ausführen.</span><span class="sxs-lookup"><span data-stu-id="c085f-168">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="c085f-169">Hier sind einige Tests, die zeigen, wie die `ProcessId` und `InputObject` Parameter können verwendet werden, um ihre Parametersätze beim Beenden eines Prozesses zu testen.</span><span class="sxs-lookup"><span data-stu-id="c085f-169">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="c085f-170">Mit Windows PowerShell, die gestartet, führen Sie das Stop-Proc-Cmdlet mit dem `ProcessId` Parametersatz beim Beenden eines Prozesses, der auf Grundlage seines Bezeichners.</span><span class="sxs-lookup"><span data-stu-id="c085f-170">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="c085f-171">In diesem Fall verwendet das Cmdlet die `ProcessId` Parameter festgelegt wird, um den Vorgang zu beenden.</span><span class="sxs-lookup"><span data-stu-id="c085f-171">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="c085f-172">Mit Windows PowerShell, die gestartet, führen Sie das Stop-Proc-Cmdlet mit dem `InputObject` Parameter festgelegt wird, beenden Sie Prozesse für das Editor-Objekt abgerufen, indem die `Get-Process` Befehl.</span><span class="sxs-lookup"><span data-stu-id="c085f-172">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="c085f-173">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c085f-173">See Also</span></span>

[<span data-ttu-id="c085f-174">Erstellen ein Cmdlet, ändert das System</span><span class="sxs-lookup"><span data-stu-id="c085f-174">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="c085f-175">Vorgehensweise: Erstellen eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c085f-175">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="c085f-176">Erweitern die Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="c085f-176">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="c085f-177">So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="c085f-177">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="c085f-178">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c085f-178">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)