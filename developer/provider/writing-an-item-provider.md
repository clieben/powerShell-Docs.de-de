---
title: Schreiben eines Datenanbieters Artikel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: e3289e9336b863b5e0998a2beb29353c82a31f79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856706"
---
# <a name="writing-an-item-provider"></a><span data-ttu-id="957ef-102">Schreiben eines Elementanbieters</span><span class="sxs-lookup"><span data-stu-id="957ef-102">Writing an item provider</span></span>

<span data-ttu-id="957ef-103">In diesem Thema wird beschrieben, wie die Methoden von einem Windows PowerShell-Anbieter implementiert, die Zugriff auf, und ändern die Elemente im Datenspeicher.</span><span class="sxs-lookup"><span data-stu-id="957ef-103">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="957ef-104">Um auf Elemente zugreifen können, muss ein Anbieter von abgeleitet werden die [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="957ef-104">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="957ef-105">Der Anbieter in den Beispielen in diesem Thema verwendet eine Access-Datenbank als Datenspeicher.</span><span class="sxs-lookup"><span data-stu-id="957ef-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="957ef-106">Es gibt mehrere Hilfsmethoden und Klassen, die verwendet werden, um die Interaktion mit der Datenbank.</span><span class="sxs-lookup"><span data-stu-id="957ef-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="957ef-107">Das vollständige Beispiel, das die Hilfsmethoden enthält, finden Sie unter [AccessDBProviderSample03](./accessdbprovidersample03.md)</span><span class="sxs-lookup"><span data-stu-id="957ef-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="957ef-108">Weitere Informationen zu Windows PowerShell-Anbietern finden Sie unter [Übersicht über Windows PowerShell-Anbieter](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="957ef-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="957ef-109">Implementierungsmethoden-Element</span><span class="sxs-lookup"><span data-stu-id="957ef-109">Implementing item methods</span></span>

<span data-ttu-id="957ef-110">Die [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse stellt mehrere Methoden, die zum zugreifen und diese bearbeiten die Elemente in einem Datenspeicher verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="957ef-110">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span> <span data-ttu-id="957ef-111">Eine vollständige Liste der folgenden Methoden, finden Sie unter [ItemCmdletProvider Methoden](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="957ef-111">For a complete list of these methods, see [ItemCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span></span> <span data-ttu-id="957ef-112">In diesem Beispiel werden wir vier der folgenden Methoden implementieren.</span><span class="sxs-lookup"><span data-stu-id="957ef-112">In this example, we will implement four of these methods.</span></span> <span data-ttu-id="957ef-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) Ruft ein Element in einem angegebenen Pfad ab.</span><span class="sxs-lookup"><span data-stu-id="957ef-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span> <span data-ttu-id="957ef-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) legt den Wert des angegebenen Elements fest.</span><span class="sxs-lookup"><span data-stu-id="957ef-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span> <span data-ttu-id="957ef-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) überprüft, ob ein Element am angegebenen Pfad vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="957ef-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span> <span data-ttu-id="957ef-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) überprüft einen Pfad, um festzustellen, ob es an einem Speicherort im Datenspeicher zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="957ef-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="957ef-117">Dieses Thema baut auf den Informationen in [Schnellstartanleitung zu Windows PowerShell-Anbieter](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="957ef-117">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="957ef-118">Dieses Thema deckt sich nicht auf die Grundlagen zum Einrichten eines Anbieter-Projekts und Gewusst wie: Implementieren der Methoden geerbt von der [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse, die erstellen und Entfernen von Laufwerken.</span><span class="sxs-lookup"><span data-stu-id="957ef-118">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="957ef-119">Die Anbieterklasse deklarieren</span><span class="sxs-lookup"><span data-stu-id="957ef-119">Declaring the provider class</span></span>

<span data-ttu-id="957ef-120">Deklarieren Sie den Anbieter für die Ableitung der [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse, und versehen Sie sie mit der [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="957ef-120">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="957ef-121">GetItem implementieren</span><span class="sxs-lookup"><span data-stu-id="957ef-121">Implementing GetItem</span></span>

<span data-ttu-id="957ef-122">Die [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) wird von der PowerShell-Engine aufgerufen, wenn ein Benutzer aufruft der [Microsoft.Powershell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) -Cmdlet für Ihre Anbieter.</span><span class="sxs-lookup"><span data-stu-id="957ef-122">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.Powershell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet on your provider.</span></span> <span data-ttu-id="957ef-123">Die Methode gibt das Element am angegebenen Pfad zurück.</span><span class="sxs-lookup"><span data-stu-id="957ef-123">The method returns the item at the specified path.</span></span> <span data-ttu-id="957ef-124">In der Access-Datenbank beispielsweise überprüft die Methode an, ob das Element dem Laufwerk selbst, eine Tabelle in der Datenbank oder eine Zeile in der Datenbank.</span><span class="sxs-lookup"><span data-stu-id="957ef-124">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="957ef-125">Die-Methode sendet das Element an der PowerShell-Engine, durch Aufrufen der [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) Methode.</span><span class="sxs-lookup"><span data-stu-id="957ef-125">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

```csharp
protected override void GetItem(string path)
      {
          // check if the path represented is a drive
          if (PathIsDrive(path))
          {
              WriteItemObject(this.PSDriveInfo, path, true);
              return;
          }// if (PathIsDrive...

           // Get table name and row information from the path and do
           // necessary actions
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               DatabaseTableInfo table = GetTable(tableName);
               WriteItemObject(table, path, true);
           }
           else if (type == PathType.Row)
           {
               DatabaseRowInfo row = GetRow(tableName, rowNumber);
               WriteItemObject(row, path, false);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

### <a name="implementing-setitem"></a><span data-ttu-id="957ef-126">Implementieren von SetItem</span><span class="sxs-lookup"><span data-stu-id="957ef-126">Implementing SetItem</span></span>

<span data-ttu-id="957ef-127">Die [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) Methode wird von der PowerShell-Engine ruft aufgerufen, wenn ein Benutzer ruft die [Microsoft.Powershell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) Cmdlet .</span><span class="sxs-lookup"><span data-stu-id="957ef-127">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.Powershell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet.</span></span> <span data-ttu-id="957ef-128">Es wird der Wert des Elements an, unter dem angegebenen Pfad.</span><span class="sxs-lookup"><span data-stu-id="957ef-128">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="957ef-129">In der Access-Datenbank beispielsweise ist es sinnvoll, Sie legen Sie den Wert eines Elements aus, nur dann, wenn das Element eine Zeile ist, sodass die Methode löst [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) Wenn das Element ist keine Zeile.</span><span class="sxs-lookup"><span data-stu-id="957ef-129">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) when the item is not a row.</span></span>

```csharp
protected override void SetItem(string path, object values)
       {
           // Get type, table name and row number from the path specified
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type != PathType.Row)
           {
               WriteError(new ErrorRecord(new NotSupportedException(
                     "SetNotSupported"), "",
                  ErrorCategory.InvalidOperation, path));

               return;
           }

           // Get in-memory representation of table
           OdbcDataAdapter da = GetAdapterForTable(tableName);

           if (da == null)
           {
               return;
           }
           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           if (rowNumber >= table.Rows.Count)
           {
               // The specified row number has to be available. If not
               // NewItem has to be used to add a new row
               throw new ArgumentException("Row specified is not available");
           } // if (rowNum...

           string[] colValues = (values as string).Split(',');

           // set the specified row
           DataRow row = table.Rows[rowNumber];

           for (int i = 0; i < colValues.Length; i++)
           {
               row[i] = colValues[i];
           }

           // Update the table
           if (ShouldProcess(path, "SetItem"))
           {
               da.Update(ds, tableName);
           }

       }
```

### <a name="implementing-itemexists"></a><span data-ttu-id="957ef-130">Implementieren von ItemExists</span><span class="sxs-lookup"><span data-stu-id="957ef-130">Implementing ItemExists</span></span>

<span data-ttu-id="957ef-131">Die [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) Methode wird von der PowerShell-Engine aufgerufen, wenn ein Benutzer ruft die [Microsoft.Powershell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="957ef-131">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.Powershell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span></span> <span data-ttu-id="957ef-132">Die Methode bestimmt, ob ein Element am angegebenen Pfad vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="957ef-132">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="957ef-133">Wenn das Element vorhanden ist, die Methode übergibt sie an der PowerShell-Engine durch Aufrufen von [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span><span class="sxs-lookup"><span data-stu-id="957ef-133">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

```csharp
protected override bool ItemExists(string path)
       {
           // check if the path represented is a drive
           if (PathIsDrive(path))
           {
               return true;
           }

           // Obtain type, table name and row number from path
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           DatabaseTableInfo table = GetTable(tableName);

           if (type == PathType.Table)
           {
               // if specified path represents a table then DatabaseTableInfo
               // object for the same should exist
               if (table != null)
               {
                   return true;
               }
           }
           else if (type == PathType.Row)
           {
               // if specified path represents a row then DatabaseTableInfo should
               // exist for the table and then specified row number must be within
               // the maximum row count in the table
               if (table != null && rowNumber < table.RowCount)
               {
                   return true;
               }
           }

           return false;

       }
```

### <a name="implementing-isvalidpath"></a><span data-ttu-id="957ef-134">Implementieren von IsValidPath</span><span class="sxs-lookup"><span data-stu-id="957ef-134">Implementing IsValidPath</span></span>

<span data-ttu-id="957ef-135">Die [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) Methode überprüft, ob der angegebene Pfad für den aktuellen Anbieter syntaktisch gültig ist.</span><span class="sxs-lookup"><span data-stu-id="957ef-135">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="957ef-136">Es wird nicht überprüft, ob ein Element im Pfad vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="957ef-136">It does not check whether an item exists at the path.</span></span>

```csharp
protected override bool IsValidPath(string path)
       {
           bool result = true;

           // check if the path is null or empty
           if (String.IsNullOrEmpty(path))
           {
               result = false;
           }

           // convert all separators in the path to a uniform one
           path = NormalizePath(path);

           // split the path into individual chunks
           string[] pathChunks = path.Split(pathSeparator.ToCharArray());

           foreach (string pathChunk in pathChunks)
           {
               if (pathChunk.Length == 0)
               {
                   result = false;
               }
           }
           return result;
       }
```

## <a name="next-steps"></a><span data-ttu-id="957ef-137">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="957ef-137">Next steps</span></span>

<span data-ttu-id="957ef-138">Ein typische realen-Anbieter ist für die Unterstützung von Elementen, die anderen Elemente enthalten, und Verschieben von Elementen aus einem Pfad zu einem anderen in das Laufwerk kann.</span><span class="sxs-lookup"><span data-stu-id="957ef-138">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="957ef-139">Ein Beispiel für einen Anbieter, Container unterstützt, finden Sie unter [Schreiben eines Anbieters Container](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="957ef-139">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="957ef-140">Ein Beispiel für einen Anbieter, Verschieben von Elementen unterstützt, finden Sie unter [Schreiben eines Anbieters für die Navigation](./writing-a-navigation-provider.md).</span><span class="sxs-lookup"><span data-stu-id="957ef-140">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="957ef-141">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="957ef-141">See Also</span></span>

[<span data-ttu-id="957ef-142">Schreiben eines Anbieters für container</span><span class="sxs-lookup"><span data-stu-id="957ef-142">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="957ef-143">Schreiben eines Anbieters für die navigation</span><span class="sxs-lookup"><span data-stu-id="957ef-143">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="957ef-144">Windows PowerShell-Anbieter (Übersicht)</span><span class="sxs-lookup"><span data-stu-id="957ef-144">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)