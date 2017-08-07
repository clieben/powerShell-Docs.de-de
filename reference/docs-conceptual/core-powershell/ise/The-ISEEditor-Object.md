---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Das ISEEditor-Objekt
ms.assetid: 0101daf8-4e31-4e4c-ab89-01d95dcb8f46
ms.openlocfilehash: 41f2a6f7684275ad9d6d967ea67b64ca02c1c100
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="8626f-103">Das ISEEditor-Objekt</span><span class="sxs-lookup"><span data-stu-id="8626f-103">The ISEEditor Object</span></span>
  <span data-ttu-id="8626f-104">Ein **ISEEditor**-Objekt ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEEditor-Klasse.</span><span class="sxs-lookup"><span data-stu-id="8626f-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="8626f-105">Der Konsolenbereich ist ein **ISEEditor**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="8626f-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="8626f-106">Jedes [ISEFile](The-ISEFile-Object.md)-Objekt verfügt über ein zugeordnetes **ISEEditor**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="8626f-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="8626f-107">In den folgenden Abschnitten werden die Methoden und Eigenschaften eines **ISEEditor**-Objekts aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="8626f-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="8626f-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="8626f-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="8626f-109">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="8626f-109">Clear\(\)</span></span>
  <span data-ttu-id="8626f-110">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8626f-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8626f-111">Löscht den Text im Editor.</span><span class="sxs-lookup"><span data-stu-id="8626f-111">Clears the text in the editor.</span></span>

```PowerShell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="8626f-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="8626f-112">EnsureVisible\(int lineNumber\)</span></span>
  <span data-ttu-id="8626f-113">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8626f-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8626f-114">Führt einen Bildlauf im Editor aus, sodass die Zeile, die dem angegebenen Wert des **lineNumber**-Parameters entspricht, angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8626f-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="8626f-115">Es wird eine Ausnahme ausgelöst, wenn die angegebene Zeilennummer nicht zwischen 1 und der Nummer der letzten Zeile liegt. Dieser Bereich definiert die gültigen Zeilennummern.</span><span class="sxs-lookup"><span data-stu-id="8626f-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

 <span data-ttu-id="8626f-116">**lineNumber**
 Die Nummer der Zeile, die angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="8626f-116">**lineNumber**
 The number of the line that is to be made visible.</span></span>

```PowerShell
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="8626f-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="8626f-117">Focus\(\)</span></span>
  <span data-ttu-id="8626f-118">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8626f-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8626f-119">Legt den Fokus auf den Editor fest.</span><span class="sxs-lookup"><span data-stu-id="8626f-119">Sets the focus to the editor.</span></span>

```PowerShell
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="8626f-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="8626f-120">GetLineLength\(int lineNumber \)</span></span>
  <span data-ttu-id="8626f-121">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8626f-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8626f-122">Ruft für die durch die Zeilennummer angegebene Zeile die Länge der Zeile als ganze Zahl ab.</span><span class="sxs-lookup"><span data-stu-id="8626f-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

 <span data-ttu-id="8626f-123">**lineNumber**
 Die Nummer der Zeile, deren Länge abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="8626f-123">**lineNumber**
 The number of the line of which to get the length.</span></span>

 <span data-ttu-id="8626f-124">**Returns**
 Die Zeilenlänge für die Zeile mit der angegebenen Zeilennummer.</span><span class="sxs-lookup"><span data-stu-id="8626f-124">**Returns**
 The line length for the line at the specified line number.</span></span>

```PowerShell
# Gets the length of the first line in the text of the Command pane. 
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="8626f-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="8626f-125">GoToMatch\(\)</span></span>
  <span data-ttu-id="8626f-126">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="8626f-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="8626f-127">Verschiebt den Textcursor zum entsprechenden Zeichen, wenn die Eigenschaft **CanGoToMatch** des Editorobjekts **$true** ist. Dies tritt ein, wenn sich der Textcursor direkt vor einer öffnenden, eckigen oder geschweiften Klammer – \(, \[, { – oder unmittelbar nach einer schließenden, eckigen oder geschweiften Klammer befindet – \), \], }.</span><span class="sxs-lookup"><span data-stu-id="8626f-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="8626f-128">Der Textcursor wird vor einer öffnenden bzw. nach einer schließenden Klammer platziert.</span><span class="sxs-lookup"><span data-stu-id="8626f-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="8626f-129">Wenn die **CanGoToMatch**-Eigenschaft **$false** ist, wird mit dieser Methode keine Aktion ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="8626f-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span> <span data-ttu-id="8626f-130">Siehe [CanGoToMatch](#cangotomatch).</span><span class="sxs-lookup"><span data-stu-id="8626f-130">See [CanGoToMatch](#cangotomatch).</span></span>

```PowerShell
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### <a name="inserttext-text-"></a><span data-ttu-id="8626f-131">InsertText\( Text \)</span><span class="sxs-lookup"><span data-stu-id="8626f-131">InsertText\( text \)</span></span>
  <span data-ttu-id="8626f-132">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8626f-132">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8626f-133">Ersetzt die Markierung durch Text oder fügt Text an der aktuellen Position des Textcursors ein.</span><span class="sxs-lookup"><span data-stu-id="8626f-133">Replaces the selection with text or inserts text at the current caret position.</span></span>

 <span data-ttu-id="8626f-134">**text**: Zeichenfolge – der einzufügende Text.</span><span class="sxs-lookup"><span data-stu-id="8626f-134">**text** - String The text to insert.</span></span>

 <span data-ttu-id="8626f-135">Weitere Informationen finden Sie im [Beispielskript](#example) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="8626f-135">See the [Scripting Example](#example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="8626f-136">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="8626f-136">Select\( startLine, startColumn, endLine, endColumn \)</span></span>
  <span data-ttu-id="8626f-137">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8626f-137">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8626f-138">Wählt den Text anhand der Parameter **startLine**, **startColumn**, **endLine** und **endColumn** aus.</span><span class="sxs-lookup"><span data-stu-id="8626f-138">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

 <span data-ttu-id="8626f-139">**startLine**: ganze Zahl – die Zeile, in der die Auswahl beginnt.</span><span class="sxs-lookup"><span data-stu-id="8626f-139">**startLine** - Integer The line where the selection starts.</span></span>

 <span data-ttu-id="8626f-140">**startColumn**: ganze Zahl – die Spalte in der Startzeile, in der die Auswahl beginnt.</span><span class="sxs-lookup"><span data-stu-id="8626f-140">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

 <span data-ttu-id="8626f-141">**endLine**: ganze Zahl – die Zeile, in der die Auswahl endet.</span><span class="sxs-lookup"><span data-stu-id="8626f-141">**endLine** - Integer The line where the selection ends.</span></span>

 <span data-ttu-id="8626f-142">**endColumn**: ganze Zahl – die Spalte in der Endzeile, in der die Auswahl endet.</span><span class="sxs-lookup"><span data-stu-id="8626f-142">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

 <span data-ttu-id="8626f-143">Weitere Informationen finden Sie im [Beispielskript](#example) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="8626f-143">See the  [Scripting Example](#example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="8626f-144">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="8626f-144">SelectCaretLine\(\)</span></span>
  <span data-ttu-id="8626f-145">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8626f-145">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8626f-146">Wählt die gesamte Textzeile aus, in der sich der Textcursor gerade befindet.</span><span class="sxs-lookup"><span data-stu-id="8626f-146">Selects the entire line of text that currently contains the caret.</span></span>

```PowerShell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="8626f-147">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="8626f-147">SetCaretPosition\( lineNumber, columnNumber \)</span></span>
  <span data-ttu-id="8626f-148">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8626f-148">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8626f-149">Legt die Position des Textcursors auf die Zeilennummer und die Spaltennummer fest.</span><span class="sxs-lookup"><span data-stu-id="8626f-149">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="8626f-150">Es wird eine Ausnahme ausgelöst, wenn die Zeilennummer des Textcursors oder die Spaltennummer des Textcursors außerhalb des jeweils gültigen Bereichs liegt.</span><span class="sxs-lookup"><span data-stu-id="8626f-150">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

 <span data-ttu-id="8626f-151">**lineNumber**: ganze Zahl – die Zeilennummer des Textcursors.</span><span class="sxs-lookup"><span data-stu-id="8626f-151">**lineNumber** - Integer The caret line number.</span></span>

 <span data-ttu-id="8626f-152">**columnNumber**: ganze Zahl – die Spaltennummer des Textcursors.</span><span class="sxs-lookup"><span data-stu-id="8626f-152">**columnNumber** - Integer The caret column number.</span></span>

```PowerShell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="8626f-153">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="8626f-153">ToggleOutliningExpansion\(\)</span></span>
  <span data-ttu-id="8626f-154">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="8626f-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="8626f-155">Führt dazu, dass alle Gliederungsabschnitte erweitert oder reduziert werden.</span><span class="sxs-lookup"><span data-stu-id="8626f-155">Causes all the outline sections to expand or collapse.</span></span>

```PowerShell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="8626f-156">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="8626f-156">Properties</span></span>

###  <span data-ttu-id="8626f-157"><a name="CanGoToMatch"></a> CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="8626f-157"><a name="CanGoToMatch"></a> CanGoToMatch</span></span>
  <span data-ttu-id="8626f-158">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="8626f-158">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="8626f-159">Die schreibgeschützte boolesche Eigenschaft, die angibt, ob der Textcursor sich neben einer Klammer, eckigen Klammer oder geschweiften Klammer befindet – \(\), \[\], {}.</span><span class="sxs-lookup"><span data-stu-id="8626f-159">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="8626f-160">Wenn der Textcursor sich direkt vor der öffnenden Klammer oder unmittelbar nach der schließenden Klammer eines Klammerpaars befindet, lautet der Wert dieser Eigenschaft **$true**.</span><span class="sxs-lookup"><span data-stu-id="8626f-160">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="8626f-161">Andernfalls lautet er **$false**.</span><span class="sxs-lookup"><span data-stu-id="8626f-161">Otherwise, it is **$false**.</span></span>

```PowerShell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

###  <span data-ttu-id="8626f-162"><a name="CaretColumn"></a> CaretColumn</span><span class="sxs-lookup"><span data-stu-id="8626f-162"><a name="CaretColumn"></a> CaretColumn</span></span>
  <span data-ttu-id="8626f-163">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8626f-163">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8626f-164">Die schreibgeschützte Eigenschaft, die die Spaltennummer abruft, die der Position des Textcursors entspricht.</span><span class="sxs-lookup"><span data-stu-id="8626f-164">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```PowerShell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

###  <span data-ttu-id="8626f-165"><a name="CaretLine"></a> CaretLine</span><span class="sxs-lookup"><span data-stu-id="8626f-165"><a name="CaretLine"></a> CaretLine</span></span>
  <span data-ttu-id="8626f-166">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8626f-166">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8626f-167">Die schreibgeschützte Eigenschaft, die die Nummer der Zeile mit dem Textcursor abruft.</span><span class="sxs-lookup"><span data-stu-id="8626f-167">The read-only property that gets the number of the line that contains the caret.</span></span>

```PowerShell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

###  <span data-ttu-id="8626f-168"><a name="CaretLineText"></a> CaretLineText</span><span class="sxs-lookup"><span data-stu-id="8626f-168"><a name="CaretLineText"></a> CaretLineText</span></span>
  <span data-ttu-id="8626f-169">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8626f-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8626f-170">Die schreibgeschützte Eigenschaft, die die vollständige Textzeile abruft, die den Textcursor enthält.</span><span class="sxs-lookup"><span data-stu-id="8626f-170">The read-only property that gets the complete line of text that contains the caret.</span></span>

```PowerShell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

###  <span data-ttu-id="8626f-171"><a name="LineCount"></a> LineCount</span><span class="sxs-lookup"><span data-stu-id="8626f-171"><a name="LineCount"></a> LineCount</span></span>
  <span data-ttu-id="8626f-172">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8626f-172">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8626f-173">Die schreibgeschützte Eigenschaft, die die Anzahl der Zeilen aus dem Editor abruft.</span><span class="sxs-lookup"><span data-stu-id="8626f-173">The read-only property that gets the line count from the editor.</span></span>

```PowerShell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

###  <span data-ttu-id="8626f-174"><a name="SelectedText"></a> SelectedText</span><span class="sxs-lookup"><span data-stu-id="8626f-174"><a name="SelectedText"></a> SelectedText</span></span>
  <span data-ttu-id="8626f-175">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8626f-175">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8626f-176">Die schreibgeschützte Eigenschaft, die den ausgewählten Text aus dem Editor abruft.</span><span class="sxs-lookup"><span data-stu-id="8626f-176">The read-only property that gets the selected text from the editor.</span></span>

 <span data-ttu-id="8626f-177">Weitere Informationen finden Sie im [Beispielskript](#example) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="8626f-177">See the  [Scripting Example](#example) later in this topic.</span></span>

###  <span data-ttu-id="8626f-178"><a name="Text"></a> Text</span><span class="sxs-lookup"><span data-stu-id="8626f-178"><a name="Text"></a> Text</span></span>
  <span data-ttu-id="8626f-179">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8626f-179">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="8626f-180">Die Lese-/Schreibeigenschaft, die den Text im Editor abruft oder festlegt.</span><span class="sxs-lookup"><span data-stu-id="8626f-180">The read/write property that gets or sets the text in the editor.</span></span>

 <span data-ttu-id="8626f-181">Weitere Informationen finden Sie im [Beispielskript](#example) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="8626f-181">See the [Scripting Example](#example) later in this topic.</span></span>

##  <span data-ttu-id="8626f-182"><a name="example"></a> Beispielskript</span><span class="sxs-lookup"><span data-stu-id="8626f-182"><a name="example"></a> Scripting Example</span></span>

```PowerShell
# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase. 
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor = $psISE.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line. 
$endColumn= $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1,1,3,$endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a><span data-ttu-id="8626f-183">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8626f-183">See Also</span></span>
- [<span data-ttu-id="8626f-184">Das ISEFile-Objekt</span><span class="sxs-lookup"><span data-stu-id="8626f-184">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="8626f-185">Das PowerShellTab-Objekt</span><span class="sxs-lookup"><span data-stu-id="8626f-185">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="8626f-186">Das Windows PowerShell ISE-Skriptobjektmodell</span><span class="sxs-lookup"><span data-stu-id="8626f-186">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="8626f-187">Referenz zum Windows PowerShell ISE-Objektmodell</span><span class="sxs-lookup"><span data-stu-id="8626f-187">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="8626f-188">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="8626f-188">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  