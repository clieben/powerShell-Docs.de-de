---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Einführung in die Windows PowerShell ISE"
ms.assetid: a0de70ca-909a-4807-94d1-6da86e5b52a0
ms.openlocfilehash: 61d31fc2555d91bc7872d7b90cfb1f2a9832ff9c
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="introducing-the-windows-powershell-ise"></a><span data-ttu-id="e2bcf-103">Einführung in die Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="e2bcf-103">Introducing the Windows PowerShell ISE</span></span>
<span data-ttu-id="e2bcf-104">Windows PowerShell Integrated Scripting Environment (ISE) ist eine Hostanwendung für Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="e2bcf-105">In der Windows PowerShell ISE können Sie Befehle ausführen und Skripts schreiben, testen und debuggen, und zwar auf einer einzigen Windows-basierten grafischen Benutzeroberfläche mit mehrzeiliger Bearbeitung, Vervollständigung mit der TAB-TASTE, Syntaxfarben, selektiver Ausführung, kontextbezogener Hilfe und Unterstützung für von rechts nach links geschriebene Sprachen.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-105">In Windows PowerShell ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface with multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span>
<span data-ttu-id="e2bcf-106">Sie können Menüelemente und Tastenkombinationen für viele der Aufgaben nutzen, die Sie auch in der Windows PowerShell-Konsole ausführen würden.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-106">You can use menu items and keyboard shortcuts to perform many of the same tasks that you would perform in the Windows PowerShell console.</span></span>  <span data-ttu-id="e2bcf-107">Um beispielsweise beim Debuggen eines Skripts in der Windows PowerShell ISE einen Zeilenhaltepunkt in einem Skript festzulegen, klicken Sie mit der rechten Maustaste auf die Codezeile, und klicken Sie anschließende auf **Haltepunkt umschalten**.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-107">For example, when you debug a script in the Windows PowerShell ISE, to set a line breakpoint in a script, right-click the line of code, and then click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="e2bcf-108">Testen Sie diese neuen Features in der Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-108">Try these features in Windows PowerShell ISE.</span></span>

-   <span data-ttu-id="e2bcf-109">Mehrzeilige Bearbeitung: Drücken Sie zum Einfügen einer leeren Zeile unter der aktuellen Zeile im Befehlsbereich UMSCHALT+EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-109">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>

-   <span data-ttu-id="e2bcf-110">Selektive Ausführung: Um einen Teil eines Skripts auszuführen, markieren Sie den Text, den Sie ausführen möchten, und klicken Sie dann auf die Schaltfläche **Skript ausführen**.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-110">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="e2bcf-111">Oder drücken Sie F5.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-111">Or, press F5.</span></span>

-   <span data-ttu-id="e2bcf-112">Kontextbezogene Hilfe: Geben Sie **Invoke-Item** ein, und drücken Sie dann F1.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-112">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="e2bcf-113">Die Hilfedatei wird mit dem Hilfethema für das Cmdlet **Invoke-Item** geöffnet.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-113">The Help file opens to the Help topic for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="e2bcf-114">Die Windows PowerShell ISE ermöglicht Ihnen das Anpassen einiger Aspekte ihrer Darstellung.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-114">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="e2bcf-115">Sie hat auch ein eigenes Windows PowerShell-Profil, in dem Sie Funktionen, Aliase, Variablen und Befehle speichern können, die Sie in der Windows PowerShell ISE verwenden.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-115">It also has its own Windows PowerShell profile, where you can store functions, aliases, variables, and commands you use in the Windows PowerShell ISE.</span></span>

### <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="e2bcf-116">So starten Sie die Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="e2bcf-116">To start the Windows PowerShell ISE</span></span>

1.  <span data-ttu-id="e2bcf-117">Führen Sie eines der folgenden Verfahren aus:</span><span class="sxs-lookup"><span data-stu-id="e2bcf-117">Do one of the following:</span></span>

    -   <span data-ttu-id="e2bcf-118">Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, dann auf **Windows PowerShell 2.0**, und klicken Sie dann auf **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-118">Click **Start**, point to **All Programs**, point to **Windows PowerShell V2**, and then click **Windows PowerShell ISE**.</span></span>

    -   <span data-ttu-id="e2bcf-119">Geben Sie in der Windows PowerShell-Konsole „Cmd.exe“ oder im Feld „Ausführen“ **powershell_ise.exe** ein.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-119">In the Windows PowerShell console Cmd.exe, or in the Run box, type, **powershell_ise.exe**.</span></span>

### <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="e2bcf-120">So rufen Sie Hilfe in der Windows PowerShell ISE ab</span><span class="sxs-lookup"><span data-stu-id="e2bcf-120">To get Help in the Windows PowerShell ISE</span></span>

-   <span data-ttu-id="e2bcf-121">Klicken Sie im Menü **Hilfe** auf **Windows PowerShell-Hilfe**.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-121">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="e2bcf-122">Oder drücken Sie F1.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-122">Or, press F1.</span></span> <span data-ttu-id="e2bcf-123">Die Datei, die geöffnet wird, beschreibt die Windows PowerShell ISE und Windows PowerShell, einschließlich sämtlicher Hilfe, die über das Cmdlet „Get-Help“ verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="e2bcf-123">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>
