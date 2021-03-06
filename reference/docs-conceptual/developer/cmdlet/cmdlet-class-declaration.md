---
title: Cmdlet-Klassen Deklaration | Microsoft-Dokumentation
ms.date: 09/13/2016
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.openlocfilehash: 96ce8144795346b6f46878ee6163ce69cdb1799a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784502"
---
# <a name="cmdlet-class-declaration"></a>Deklaration der Cmdlet-Klasse

Eine Microsoft .NET Framework-Klasse wird als Cmdlet deklariert, indem das **Cmdlet** -Attribut als Metadaten für die-Klasse angegeben wird. (Das **Cmdlet** -Attribut ist das einzige erforderliche Attribut für alle Cmdlets).
Wenn Sie das **Cmdlet** -Attribut angeben, müssen Sie das Verb-und-Substantiv-Paar angeben, das das Cmdlet für den Benutzer identifiziert. Und Sie müssen die Windows PowerShell-Funktionalität beschreiben, die vom Cmdlet unterstützt wird. Weitere Informationen zur Deklarations Syntax, die zum Angeben des **Cmdlet** -Attributs verwendet wird, finden Sie unter [Cmdlet-Attribut Deklaration](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Das **Cmdlet** -Attribut wird von der [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) -Klasse definiert. Die Eigenschaften dieser Klasse entsprechen den Deklarations Parametern, die beim Deklarieren des Attributs verwendet werden.

## <a name="nouns"></a>Nomen

Das Substantiv des Cmdlets gibt die Ressourcen an, auf die das Cmdlet angewendet wird. Das Substantiv unterscheidet Ihre Cmdlets von anderen Cmdlets.

Nomen in Cmdlet-Namen müssen spezifisch sein, und im Fall von generischen Substantiven, wie z. b. *Server*, ist es am besten, ein kurzes Präfix hinzuzufügen, das Ihre Ressource von anderen ähnlichen Ressourcen unterscheidet. Beispielsweise ist ein Cmdlet-Name, der ein Substantiv mit einem Präfix enthält, `Get-SQLServer` . Die Kombination eines bestimmten Substantiv mit einem allgemeineren Verb ermöglicht dem Benutzer, das Cmdlet anhand seiner Aktion schnell zu finden und dann das Cmdlet anhand seiner Ressource zu identifizieren, während unnötige Cmdlet-namens Duplikate vermieden werden.

Eine Liste von Sonderzeichen, die in Cmdlet-Namen nicht verwendet werden können, finden Sie unter [erforderliche Entwicklungs Richtlinien](./required-development-guidelines.md).

## <a name="verbs"></a>Verben

Wenn Sie ein Verb angeben, müssen Sie für die Entwicklungs Richtlinien eines der vordefinierten Verben verwenden, die von Windows PowerShell bereitgestellt werden. Wenn Sie eines dieser vordefinierten Verben verwenden, gewährleisten Sie die Konsistenz zwischen den Cmdlets, die Sie schreiben, und den Cmdlets, die von Microsoft und anderen geschrieben wurden. Beispielsweise wird das Verb "Get" für Cmdlets verwendet, mit denen Daten abgerufen werden.

Weitere Informationen zu den Richtlinien für Verben finden [Sie unter Cmdlet-Verb Namen](./approved-verbs-for-windows-powershell-commands.md). Eine Liste von Sonderzeichen, die in Cmdlet-Namen nicht verwendet werden können, finden Sie unter [erforderliche Entwicklungs Richtlinien](./required-development-guidelines.md).

## <a name="supporting-windows-powershell-functionality"></a>Unterstützung der Windows PowerShell-Funktionalität

Mit dem **Cmdlet** -Attribut können Sie auch angeben, dass das Cmdlet einige der allgemeinen Funktionen unterstützt, die von Windows PowerShell bereitgestellt werden. Dies umfasst die Unterstützung allgemeiner Funktionen, wie z. b. die Bestätigung von Benutzer Feedback (als Unterstützung für die Funktion "Schulter verarbeiten" bezeichnet) und die Unterstützung von Transaktionen. (Die Unterstützung für Transaktionen wurde in Windows PowerShell 2,0 eingeführt.)

Weitere Informationen zur Deklarations Syntax, die zum Angeben des **Cmdlet** -Attributs verwendet wird, finden Sie unter [Cmdlet-Attribut Deklaration](./cmdlet-attribute-declaration.md).

## <a name="cmdlet-class-definition"></a>Cmdlet-Klassen Definition

Der folgende Code ist die Definition für eine getproc-Cmdlet-Klasse. Beachten Sie, dass die Pascal-Schreibweise verwendet wird und dass der Name der Klasse das Verb und das Substantiv des Cmdlets enthält.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="33-34":::

## <a name="pascal-casing"></a>Pascal-Schreibweise

Wenn Sie Cmdlets benennen, verwenden Sie die Pascal-Schreibweise. Die `Get-Item` `Get-ItemProperty` Cmdlets und zeigen z. b. die richtige Methode für die Verwendung von Groß-und Kleinschreibung, wenn Sie Cmdlets benennen.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[CmdletAttribute-Deklaration](./cmdlet-attribute-declaration.md)

[Cmdlet-Verb Namen](./approved-verbs-for-windows-powershell-commands.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
