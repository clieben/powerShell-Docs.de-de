---
title: Genehmigte Verben für PowerShell-Befehle | Microsoft-Dokumentation
ms.date: 09/07/2018
helpviewer_keywords:
- action names [PowerShell SDK]
- verb names [PowerShell SDK]
- cmdlets [PowerShell SDK], verb names
ms.openlocfilehash: f065610b6e54c9a6a927948bc6b2ffe5a1671e0c
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88162476"
---
# <a name="approved-verbs-for-powershell-commands"></a>Genehmigte Verben für PowerShell-Befehle

PowerShell verwendet ein Verb-Substantiv-Paar für die Namen von Cmdlets und für deren abgeleitete Microsoft .net Frameworkklassen. Beispielsweise wird das `Get-Command` von PowerShell bereitgestellte Cmdlet zum Abrufen aller Befehle verwendet, die in PowerShell registriert sind. Der Verb-Teil des Namens identifiziert die Aktion, die das Cmdlet ausführt. Der Nomen-Teil des Namens identifiziert die Entität, für die die Aktion ausgeführt wird.

> [!NOTE]
> PowerShell verwendet den Begriff " _Verb_ ", um ein Wort zu beschreiben, das eine Aktion impliziert, auch wenn dieses Wort kein Standard Verb in englischer Sprache ist. Der Begriff " _New_ " ist beispielsweise ein gültiger PowerShell-Verb Name, da er eine Aktion impliziert, obwohl es sich nicht um ein Verb in englischer Sprache handelt.

<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->

Für jedes genehmigte Verb ist ein entsprechendes _Alias Präfix_ definiert.
Dieses Alias Präfix wird häufig verwendet, um Aliase für Befehle zu benennen, die dieses Verb verwenden.
Beispielsweise ist das Alias Präfix für, `Import` `ip` und entsprechend lautet der Alias für `Import-Module` `ipmo` .  Dabei handelt es sich um eine Empfehlung, aber nicht um eine Regel. insbesondere muss Sie nicht für Befehls Aliase beachtet werden, die bekannte Befehle aus anderen Umgebungen imitieren.

## <a name="verb-naming-rules"></a>Verb Benennungs Regeln

Die folgende Liste enthält Richtlinien, die Sie beachten sollten, wenn Sie das Verb für einen Cmdlet-Namen auswählen:

- Wenn Sie das Verb angeben, empfiehlt es sich, einen der vordefinierten Verb Namen zu verwenden, die von PowerShell bereitgestellt werden (Aliase für diese vordefinierten Verben sind in den folgenden Tabellen enthalten). Wenn Sie ein vordefiniertes Verb verwenden, gewährleisten Sie die Konsistenz zwischen den Cmdlets, die Sie erstellen, den von PowerShell bereitgestellten Cmdlets und den von anderen entworfenen Cmdlets.

- Verwenden Sie die vordefinierten Verben, um den allgemeinen Bereich der Aktion zu beschreiben, und verwenden Sie Parameter, um die Aktion des Cmdlets weiter zu verfeinern.

- Um Konsistenz zwischen Cmdlets zu erzwingen, verwenden Sie kein Synonym eines genehmigten Verbs.

- Verwenden Sie nur die Form jedes Verbs, das in diesem Thema aufgeführt ist. Verwenden Sie z. b. "Get", aber nicht "Get" oder "Gets".

- Verwenden Sie Pascal-Schreibweise für Verben. In der Schreibweise von Pascal wird der anfängliche Buchstabe jedes Worts groß geschrieben, z. b. "foreach".

- Verwenden Sie nicht die folgenden reservierten Verben oder Aliase. Diese Verben werden von der PowerShell-Sprache oder von Cmdlets in speziellen Fällen verwendet, die von PowerShell bereitgestellt werden.
  - Foreach (ForEach)
  - Format (f)
  - Gruppe (GP)
  - Sortieren (SR)
  - Tee (TE)
  - Where (Wh)

Mithilfe des Cmdlets kann eine komplette Liste der Verben angezeigt werden `Get-Verb` .

## <a name="similar-verbs-for-different-actions"></a>Ähnliche Verben für verschiedene Aktionen

Die folgenden ähnlichen Verben stellen verschiedene Aktionen dar.

### <a name="new-vs-set"></a>Neu und festgelegt

Das `New` Verb wird zum Erstellen einer neuen Ressource verwendet. Das `Set` Verb wird zum Ändern einer vorhandenen Ressource verwendet, wobei optional die Ressource erstellt wird, wenn Sie nicht vorhanden ist, z `Set-Variable` . b. das Cmdlet.

### <a name="find-vs-search"></a>Suchen und suchen

Das `Find` Verb wird verwendet, um nach einem Objekt zu suchen. Das `Search` Verb wird verwendet, um einen Verweis auf eine Ressource in einem Container zu erstellen.

### <a name="get-vs-read"></a>Get und Read

Das `Get` Verb wird zum Abrufen einer Ressource verwendet, z. b. einer Datei. Das `Read` Verb wird verwendet, um Informationen aus einer Quelle, z. b. einer Datei, zu erhalten.

### <a name="invoke-vs-start"></a>Aufrufen und starten

Das `Invoke` Verb wird verwendet, um einen Vorgang auszuführen, bei dem es sich in der Regel um einen synchronen Vorgang handelt Das `Start` Verb wird verwendet, um einen Vorgang zu starten, der in der Regel ein asynchroner Vorgang ist, z. b. das Starten eines Prozesses.

### <a name="ping-vs-test"></a>Ping und Test

Verwenden Sie das `Test` Verb.

## <a name="common-verbs"></a>Allgemeine Verben

PowerShell verwendet die [System. Management. Automation. verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) -Enumerationsklasse, um generische Aktionen zu definieren, die auf fast alle Cmdlets angewendet werden können. In der folgenden Tabelle sind die meisten definierten Verben aufgeführt.

|Verb (Alias)|Aktion|Kommentare|
|--------------------|------------|--------------|
|[Hinzufügen](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Fügt einem Container eine Ressource hinzu oder fügt ein Element an ein anderes Element an. Das- `Add-Content` Cmdlet fügt beispielsweise Inhalt zu einer Datei hinzu. Dieses Verb ist mit gekoppelt `Remove` .|Verwenden Sie für diese Aktion keine Verben wie z. b. anfügen, anfügen, verketten oder einfügen.|
|[Löschen](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (CL)|Entfernt alle Ressourcen aus einem Container, löscht den Container jedoch nicht. Beispielsweise entfernt das `Clear-Content` Cmdlet den Inhalt einer Datei, aber die Datei wird nicht gelöscht.|Verwenden Sie für diese Aktion keine Verben wie "Flush", "Erase", "Release", "UNMARK", "unset" oder "Nullify"|
|[Schließen](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (CS)|Ändert den Zustand einer Ressource, damit Sie nicht zugänglich, nicht verfügbar oder unbrauchbar ist. Dieses Verb ist mit `Open.`||
|[Kopieren](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (CP)|Kopiert eine Ressource in einen anderen Namen oder in einen anderen Container. Beispielsweise kopiert das `Copy-Item` Cmdlet, das für den Zugriff auf gespeicherte Daten verwendet wird, ein Element von einem Speicherort im Datenspeicher an einen anderen Speicherort.|Verwenden Sie für diese Aktion keine Verben wie z. b. duplizieren, Klonen, replizieren oder synchronisieren.|
|[Eingabe](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) Taste (et)|Gibt eine Aktion an, die dem Benutzer das Verschieben in eine Ressource ermöglicht. Beispielsweise wird `Enter-PSSession` der Benutzer mit dem-Cmdlet in eine interaktive Sitzung versetzt. Dieses Verb ist mit gekoppelt `Exit` .|Verwenden Sie für diese Aktion keine Verben wie Push oder into.|
|[Exit](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ex)|Legt die aktuelle Umgebung oder den aktuellen Kontext auf den zuletzt verwendeten Kontext fest. Beispielsweise wird der `Exit-PSSession` Benutzer mit dem-Cmdlet in der Sitzung abgelegt, die zum Starten der interaktiven Sitzung verwendet wurde. Dieses Verb ist mit gekoppelt `Enter` .|Verwenden Sie für diese Aktion keine Verben wie Pop oder out.|
|[Suchen](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (FD)|Sucht in einem unbekannten Container nach einem Objekt, das unbekannt, impliziert, optional oder angegeben ist.||
|[Format](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Ordnet Objekte in einem angegebenen Formular oder Layout an.||
|[Get](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Gibt eine Aktion an, die eine Ressource abruft. Dieses Verb ist mit gekoppelt `Set` .|Verwenden Sie für diese Aktion keine Verben wie z. b. "lesen", "Öffnen", "Cat", "Type", "dir", "Abruf", "abrufen", "suchen"|
|[Ausblenden](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Macht eine Ressource nicht erkennbar. Beispielsweise könnte ein Cmdlet, dessen Name das Hide-Verb enthält, einen Dienst von einem Benutzer verbergen. Dieses Verb ist mit gekoppelt `Show` .|Verwenden Sie für diese Aktion kein Verb, z. b. "Block".|
|[Join](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Kombiniert Ressourcen zu einer Ressource. Das `Join-Path` Cmdlet kombiniert z. b. einen Pfad mit einem seiner untergeordneten Pfade, um einen einzelnen Pfad zu erstellen. Dieses Verb ist mit gekoppelt `Split` .|Verwenden Sie für diese Aktion keine Verben wie z. b. kombinieren, vereinen, verbinden oder zuordnen.|
|[Sperre](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (LK)|Sichert eine Ressource. Dieses Verb ist mit gekoppelt `Unlock` .|Verwenden Sie für diese Aktion keine Verben wie "einschränken" oder "sicher".|
|[Verschieben](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Verschiebt eine Ressource von einem Speicherort zu einem anderen. Beispielsweise verschiebt das `Move-Item` Cmdlet ein Element von einem Speicherort im Datenspeicher an einen anderen Speicherort.|Verwenden Sie für diese Aktion keine Verben wie Übertragung, Name oder Migration.|
|[Neu](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Dient zum Erstellen einer Ressource. (Das `Set` Verb kann auch verwendet werden, wenn eine Ressource erstellt wird, die Daten enthält, z `Set-Variable` . b. das Cmdlet.)|Verwenden Sie für diese Aktion keine Verben wie CREATE, generate, Build, Make oder zuordnen.|
|[Öffnen](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (OP)|Ändert den Zustand einer Ressource, damit Sie zugänglich, verfügbar oder verwendbar ist. Dieses Verb ist mit gekoppelt `Close` .||
|[Optimieren](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (OM)|Steigert die Effektivität einer Ressource.||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (Pop)|Entfernt ein Element von der obersten Position eines Stapels. Das `Pop-Location` Cmdlet ändert z. b. den aktuellen Speicherort in den Speicherort, der zuletzt auf den Stapel verschoben wurde.||
|[Push](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (PU)|Fügt ein Element am Anfang eines Stapels hinzu. Das- `Push-Location` Cmdlet überträgt z. b. den aktuellen Speicherort auf den Stapel.||
|Wieder [holen](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (erneut)|Setzt eine Ressource auf den Zustand zurück, der rückgängig gemacht wurde.||
|[Entfernen](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Löscht eine Ressource aus einem Container. Beispielsweise löscht das `Remove-Variable` Cmdlet eine Variable und ihren Wert. Dieses Verb ist mit gekoppelt `Add` .|Verwenden Sie für diese Aktion keine Verben wie "Clear", "Cut", "verwerfen", "verwerfen" oder "Löschen".|
|[Umbenennen](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (RN)|Ändert den Namen einer Ressource. Beispielsweise wird mit dem- `Rename-Item` Cmdlet, das für den Zugriff auf gespeicherte Daten verwendet wird, der Name eines Elements im Datenspeicher geändert.|Verwenden Sie für diese Aktion kein Verb wie z. b. "ändern".|
|[Zurücksetzen](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (RS)|Setzt eine Ressource auf den ursprünglichen Zustand zurück.||
|[Resize](/dotnet/api/System.Management.Automation.VerbsCommon.Resize)(RZ)|Ändert die Größe einer Ressource.||
|[Suchen](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (SR)|Erstellt einen Verweis auf eine Ressource in einem Container.|Verwenden Sie für diese Aktion keine Verben wie Suchen oder suchen.|
|[Select](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (SC)|Gibt eine Ressource in einem Container an. Beispielsweise findet das `Select-String` Cmdlet Text in Zeichen folgen und Dateien.|Verwenden Sie für diese Aktion keine Verben wie Suchen oder suchen.|
|[Menge](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (e)|Ersetzt Daten für eine vorhandene Ressource oder erstellt eine Ressource, die Daten enthält. Das- `Set-Date` Cmdlet ändert z. b. die Systemzeit auf dem lokalen Computer. (Das `New` Verb kann auch verwendet werden, um eine Ressource zu erstellen.) Dieses Verb ist mit gekoppelt `Get` .|Verwenden Sie für diese Aktion keine Verben wie z. b. schreiben, zurücksetzen, zuweisen oder konfigurieren.|
|[Anzeigen](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (SH)|Macht eine Ressource für den Benutzer sichtbar. Dieses Verb ist mit gekoppelt `Hide` .|Verwenden Sie für diese Aktion keine Verben wie Anzeige oder Erzeugung.|
|[Skip](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (SK)|Umgeht eine oder mehrere Ressourcen oder Punkte in einer Sequenz.|Verwenden Sie für diese Aktion kein Verb, z. b. "Bypass" oder "springen".|
|[Split](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (SL)|Trennt Teile einer Ressource. Das- `Split-Path` Cmdlet gibt beispielsweise verschiedene Teile eines Pfads zurück. Dieses Verb ist mit gekoppelt `Join` .|Verwenden Sie für diese Aktion kein Verb wie separat.|
|[Schritt](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (St)|Wechselt zum nächsten Punkt oder zur nächsten Ressource in einer Sequenz.||
|[Switch](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (SW)|Gibt eine Aktion an, die zwischen zwei Ressourcen wechselt, z. b., um zwischen zwei Standorten, Zuständigkeiten oder Zuständen zu wechseln.||
|[Rückgängig machen](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (aufheben)|Legt eine Ressource auf den vorherigen Zustand fest.||
|[Entsperren](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (UK)|Gibt eine gesperrte Ressource frei. Dieses Verb ist mit gekoppelt `Lock` .|Verwenden Sie für diese Aktion keine Verben wie Release, Einschränkung oder unsichere Sicherheit.|
|[Ansehen](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (WC)|Überprüft oder überwacht eine Ressource ständig auf Änderungen.||

## <a name="communications-verbs"></a>Kommunikations Verben

PowerShell verwendet die [System. Management. Automation. verbscommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) -Klasse, um Aktionen zu definieren, die für die Kommunikation gelten. In der folgenden Tabelle sind die meisten definierten Verben aufgeführt.

|Verb (Alias)|Aktion|Kommentare|
|--------------------|------------|--------------|
|[Verbinden](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (CC)|Erstellt eine Verknüpfung zwischen einer Quelle und einem Ziel. Dieses Verb ist mit gekoppelt `Disconnect` .|Verwenden Sie für diese Aktion keine Verben wie z. b. Join oder Telnet.|
|Verbindung [trennen](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (DC)|Unterbricht den Link zwischen einer Quelle und einem Ziel. Dieses Verb ist mit gekoppelt `Connect` .|Verwenden Sie für diese Aktion keine Verben wie z. b. Break oder abmelden.|
|[Lesen](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (RD)|Ruft Informationen aus einer Quelle ab. Dieses Verb ist mit gekoppelt `Write` .|Verwenden Sie für diese Aktion keine Verben wie "Get", "Prompt" oder "Get".|
|[Empfangen](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (RC)|Akzeptiert Informationen, die von einer Quelle gesendet werden. Dieses Verb ist mit gekoppelt `Send` .|Verwenden Sie für diese Aktion keine Verben wie z. b. Read, Accept oder Peek.|
|[Senden](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (SD)|Übergibt Informationen an ein Ziel. Dieses Verb ist mit gekoppelt `Receive` .|Verwenden Sie für diese Aktion keine Verben wie Put, Broadcast, Mail oder Fax.|
|[Schreiben](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (WR)|Fügt einem Ziel Informationen hinzu. Dieses Verb ist mit gekoppelt `Read` .|Verwenden Sie für diese Aktion keine Verben wie z. b. Put oder Print.|

## <a name="data-verbs"></a>Daten Verben

PowerShell verwendet die [System. Management. Automation. verbsdata](/dotnet/api/System.Management.Automation.VerbsData) -Klasse, um Aktionen zu definieren, die für die Datenverarbeitung gelten. In der folgenden Tabelle sind die meisten definierten Verben aufgeführt.

|Verb Name (Alias)|Aktion|Kommentare|
|-------------------------|------------|--------------|
|[Sicherung](/dotnet/api/System.Management.Automation.VerbsData.Backup) (BA)|Speichert Daten durch replizieren.|Verwenden Sie für diese Aktion keine Verben wie z. b. speichern, brennen, replizieren oder synchronisieren.|
|[Prüfpunkt (CH](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) )|Erstellt eine Momentaufnahme des aktuellen Zustands der Daten oder Ihrer Konfiguration.|Verwenden Sie für diese Aktion kein Verb, z. b. diff.|
|[Vergleichen](/dotnet/api/System.Management.Automation.VerbsData.Compare) (CR)|Wertet die Daten aus einer Ressource anhand der Daten aus einer anderen Ressource aus.|Verwenden Sie für diese Aktion kein Verb, z. b. diff.|
|[Komprimieren](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Komprimiert die Daten einer Ressource. Paare mit `Expand` .|Verwenden Sie für diese Aktion kein Verb wie z. b. Compact.|
|[Konvertieren](/dotnet/api/System.Management.Automation.VerbsData.Convert) (CV)|Ändert die Daten von einer-Darstellung in eine andere, wenn das Cmdlet eine bidirektionale Konvertierung unterstützt oder wenn das Cmdlet die Konvertierung zwischen mehreren Datentypen unterstützt.|Verwenden Sie für diese Aktion keine Verben wie z. b. "Change", "Resize" oder "Resample".|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (CF)|Konvertiert einen primären Typ von Eingabe (das Cmdlet-Substantiv gibt die Eingabe an) für mindestens einen unterstützten Ausgabetypen.|Verwenden Sie für diese Aktion keine Verben wie "Export", "Output" oder "out".|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (CT)|Konvertiert von einem oder mehreren Eingabetypen in einen primären Ausgabetyp (das Cmdlet-Substantiv gibt den Ausgabetyp an).|Verwenden Sie für diese Aktion keine Verben wie "Import", "Input" oder "in".|
|Aufheben der [Einbindung (DM](/dotnet/api/System.Management.Automation.VerbsData.Dismount) )|Trennt eine benannte Entität von einem Speicherort. Dieses Verb ist mit gekoppelt `Mount` .|Verwenden Sie für diese Aktion keine Verben wie z. b. Aufheben der Bereitstellung oder Aufheben der Verknüpfung.|
|[Bearbeiten](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ED)|Ändert vorhandene Daten durch Hinzufügen oder Entfernen von Inhalt.|Verwenden Sie für diese Aktion keine Verben wie z. b. ändern, aktualisieren oder ändern.|
|[Erweitern](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|Stellt die Daten einer Ressource wieder her, die in ihren ursprünglichen Zustand komprimiert wurde. Dieses Verb ist mit gekoppelt `Compress` .|Verwenden Sie für diese Aktion keine Verben wie z. b. "Explode" oder "uncompress".|
|[Exportieren](/dotnet/api/System.Management.Automation.VerbsData.Export) (EP)|Kapselt die primäre Eingabe in einen persistenten Datenspeicher, z. b. eine Datei, oder in ein Austauschformat. Dieses Verb ist mit gekoppelt `Import` .|Verwenden Sie für diese Aktion keine Verben wie z. b. Extrahieren oder sichern.|
|[Gruppe](/dotnet/api/System.Management.Automation.VerbsData.Group) (GP)|Ordnet eine oder mehrere Ressourcen an oder ordnet sie zu.|Verwenden Sie für diese Aktion keine Verben wie z. b. Aggregate, anordnen, zuordnen oder korrelieren.|
|[Importieren](/dotnet/api/System.Management.Automation.VerbsData.Import) (IP)|Erstellt eine Ressource aus Daten, die in einem persistenten Datenspeicher (z. b. einer Datei) oder in einem Austauschformat gespeichert sind. Das- `Import-CSV` Cmdlet importiert z. b. Daten aus einer CSV-Datei (Comma-Separated Value) in Objekte, die von anderen Cmdlets verwendet werden können. Dieses Verb ist mit gekoppelt `Export` .|Verwenden Sie für diese Aktion keine Verben wie Bulkload oder Load.|
|[Initialisieren](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|Bereitet eine Ressource für die Verwendung vor und legt Sie auf einen Standardzustand fest.|Verwenden Sie für diese Aktion keine Verben wie Erase, init, Renew, Rebuild, Reinitialize oder Setup.|
|[Limit](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Wendet Einschränkungen auf eine Ressource an.|Verwenden Sie für diese Aktion kein Verb, z. b. Kontingent.|
|[Merge](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Erstellt eine einzelne Ressource aus mehreren Ressourcen.|Verwenden Sie für diese Aktion keine Verben wie z. b. Combine oder Join.|
|[Einbinden](/dotnet/api/System.Management.Automation.VerbsData.Mount) (MT)|Fügt eine benannte Entität an einen Speicherort an. Dieses Verb ist mit gekoppelt `Dismount` .|Verwenden Sie für diese Aktion nicht das Verb CONNECT.|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Sendet Daten aus der Umgebung. Beispielsweise sendet das `Out-Printer` Cmdlet Daten an einen Drucker.||
|[Veröffentlichen](/dotnet/api/System.Management.Automation.VerbsData.Publish) (PB)|Stellt eine Ressource für andere zur Verfügung. Dieses Verb ist mit gekoppelt `Unpublish` .|Verwenden Sie für diese Aktion keine Verben wie bereitstellen, freigeben oder installieren.|
|[Restore](/dotnet/api/System.Management.Automation.VerbsData.Restore) (RR)|Legt einen vordefinierten Zustand für eine Ressource fest, z. b. einen von festgelegten Zustand `Checkpoint` . Das- `Restore-Computer` Cmdlet startet z. b. eine Systemwiederherstellung auf dem lokalen Computer.|Verwenden Sie für diese Aktion keine Verben wie reparieren, Rückgängigmachen, Rückgängigmachen oder korrigieren.|
|[Speichern](/dotnet/api/System.Management.Automation.VerbsData.Save) (SV)|Behält Daten bei, um einen Verlust zu vermeiden.||
|[Synchronisieren](/dotnet/api/System.Management.Automation.VerbsData.Sync) (SY)|Stellt sicher, dass sich zwei oder mehr Ressourcen im gleichen Zustand befinden.|Verwenden Sie für diese Aktion keine Verben wie replizieren, erzwingen oder vergleichen.|
|[Veröffentlichung](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) aufheben (UB)|Macht eine Ressource für andere verfügbar. Dieses Verb ist mit gekoppelt `Publish` .|Verwenden Sie für diese Aktion keine Verben wie "deinstallieren", "Wiederherstellen" oder "ausblenden".|
|[Aktualisieren](/dotnet/api/System.Management.Automation.VerbsData.Update) (UD)|Bringt eine Ressource auf den neuesten Stand, um den Status, die Genauigkeit, Konformität oder Konformität aufrechtzuerhalten. Beispielsweise werden `Update-FormatData` mit dem Cmdlet Formatierungs Dateien aktualisiert und der aktuellen PowerShell-Konsole hinzugefügt.|Verwenden Sie für diese Aktion keine Verben wie aktualisieren, erneuern, neu berechnen oder neu indizieren.|

## <a name="diagnostic-verbs"></a>Diagnose Verben

PowerShell verwendet die [System. Management. Automation. verbsdiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) -Klasse, um Aktionen zu definieren, die für die Diagnose gelten. In der folgenden Tabelle sind die meisten definierten Verben aufgeführt.

|Verb (Alias)|Aktion|Kommentare|
|--------------------|------------|--------------|
|[Debuggen](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (DB)|Untersucht eine Ressource, um operative Probleme zu diagnostizieren.|Verwenden Sie für diese Aktion kein Verb wie z. b. "Diagnose".|
|[Measure](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (MS)|Identifiziert Ressourcen, die von einem angegebenen Vorgang genutzt werden, oder ruft Statistiken zu einer Ressource ab.|Verwenden Sie für diese Aktion keine Verben wie z. b. berechnen, bestimmen oder analysieren.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (PI)|Verwenden Sie das `Test` Verb.||
|[Reparieren](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (RP)|Stellt eine verwendbare Bedingung für eine Ressource wieder her.|Verwenden Sie für diese Aktion keine Verben wie korrigieren oder wiederherstellen.|
|[Auflösen](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (RV)|Ordnet eine kurz Darstellung einer Ressource einer ausführlicheren Darstellung zu.|Verwenden Sie für diese Aktion keine Verben wie z. b. Expand oder use.|
|[Test](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Überprüft den Vorgang oder die Konsistenz einer Ressource.|Verwenden Sie für diese Aktion keine Verben wie z. b. diagnostizieren, analysieren, retten oder überprüfen.|
|Ablauf [Verfolgung](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (TR)|Verfolgt die Aktivitäten einer Ressource.|Verwenden Sie für diese Aktion keine Verben wie "Track", "Follow", "überprüfen" oder "Dig".|

## <a name="lifecycle-verbs"></a>Lebenszyklus Verben

PowerShell verwendet die [System. Management. Automation. verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) -Klasse, um Aktionen zu definieren, die auf den Lebenszyklus einer Ressource angewendet werden. In der folgenden Tabelle sind die meisten definierten Verben aufgeführt.

|Verb (Alias)|Aktion|Kommentare|
|--------------------|------------|--------------|
|[Genehmigen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (AP)|Bestätigt oder akzeptiert den Status einer Ressource oder eines Prozesses.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (as)|Bestätigt den Zustand einer Ressource.|Verwenden Sie für diese Aktion kein Verb wie z. b. "zertifizieren".|
|[Build](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (BD)|Erstellt ein Element (in der Regel eine Binärdatei oder ein Dokument) aus einem Satz von Eingabedateien (in der Regel Quell Code oder deklarative Dokumente).|Dieses Verb wurde in PowerShell V6 hinzugefügt.|
|[Complete](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (CP)|Beendet einen Vorgang.||
|[Bestätigen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (CN)|Bestätigt, überprüft oder überprüft den Zustand einer Ressource oder eines Prozesses.|Verwenden Sie für diese Aktion keine Verben wie bestätigen, zustimmen, zertifizieren, validieren oder überprüfen.|
|[Verweigern](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (DN)|Lehnt,-Objekte oder-Blöcke ab oder stellt den Zustand einer Ressource oder eines Prozesses dar.|Verwenden Sie für diese Aktion keine Verben wie Block, Object, ablehnen oder ablehnen.|
|Bereit [stellen (DP](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) )|Sendet eine Anwendung, Website oder Lösung an ein Remote Ziel [s], sodass ein Consumer dieser Lösung nach Abschluss der Bereitstellung darauf zugreifen kann.|Dieses Verb wurde in PowerShell V6 hinzugefügt.|
|[Deaktivieren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Konfiguriert eine Ressource in einem nicht verfügbaren oder inaktiven Status. Beispielsweise wird ein Haltepunkt durch das `Disable-PSBreakpoint` Cmdlet inaktiv. Dieses Verb ist mit gekoppelt `Enable` .|Verwenden Sie für diese Aktion keine Verben wie z. b. anhalten oder ausblenden.|
|[Aktivieren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Konfiguriert eine Ressource mit einem verfügbaren oder aktiven Status. Beispielsweise macht das `Enable-PSBreakpoint` Cmdlet einen Haltepunkt aktiv. Dieses Verb ist mit gekoppelt `Disable` .|Verwenden Sie für diese Aktion keine Verben wie "Start" oder "BEGIN".|
|[Installieren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (ist)|Platziert eine Ressource an einem Speicherort und initialisiert Sie optional. Dieses Verb ist mit gekoppelt `Uninstall` .|Verwenden Sie für diese Aktion kein Verb, z. b. Setup.|
|[Aufrufen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Führt eine Aktion aus, z. b. das Ausführen eines Befehls oder einer Methode.|Verwenden Sie für diese Aktion keine Verben wie z. b. ausführen oder starten.|
|[Registrieren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (RG)|Erstellt einen Eintrag für eine Ressource in einem Repository, z. b. einer-Datenbank. Dieses Verb ist mit gekoppelt `Unregister` .||
|[Anforderung](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (RQ)|Fragt nach einer Ressource oder fordert Berechtigungen an.||
|[Neu starten](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (RT)|Beendet einen Vorgang und startet ihn dann erneut. Beispielsweise wird mit dem `Restart-Service` -Cmdlet ein Dienst angehalten und dann gestartet.|Verwenden Sie für diese Aktion kein Verb wie z. b. wieder verwenden.|
|Fort [setzen (ru](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) )|Startet einen Vorgang, der angehalten wurde. Das- `Resume-Service` Cmdlet startet z. b. einen Dienst, der angehalten wurde. Dieses Verb ist mit gekoppelt `Suspend` .||
|[Start](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (SA)|Initiiert einen Vorgang. Das- `Start-Service` Cmdlet startet z. b. einen Dienst. Dieses Verb ist mit gekoppelt `Stop` .|Verwenden Sie für diese Aktion keine Verben wie z. b. starten, initiieren oder starten.|
|[Beendigung](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (SP)|Beendet eine Aktivität. Dieses Verb ist mit gekoppelt `Start` .|Verwenden Sie für diese Aktion keine Verben wie z. b. beenden, beenden, beenden oder Abbrechen.|
|Über [Mitteln](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (SB)|Stellt eine Ressource für die Genehmigung dar.|Verwenden Sie für diese Aktion kein Verb wie z. b. "Post".|
|[Aussetzen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (SS)|Hält eine Aktivität an. Beispielsweise hält das `Suspend-Service` Cmdlet einen Dienst an. Dieses Verb ist mit gekoppelt `Resume` .|Verwenden Sie für diese Aktion kein Verb wie z. b. anhalten.|
|[Deinstallieren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (USA)|Entfernt eine Ressource von einem bestimmten Speicherort. Dieses Verb ist mit gekoppelt `Install` .||
|[Registrierung](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) aufheben (Ihre)|Entfernt den Eintrag für eine Ressource aus einem Repository. Dieses Verb ist mit gekoppelt `Register` .|Verwenden Sie für diese Aktion kein Verb, z. b. "entfernen".|
|[Warten](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Hält einen Vorgang an, bis ein angegebenes Ereignis auftritt. Beispielsweise hält das `Wait-Job` Cmdlet Vorgänge an, bis mindestens einer der Hintergrund Aufträge beendet ist.|Verwenden Sie für diese Aktion keine Verben wie z. b. Standby oder Pause.|

## <a name="security-verbs"></a>Sicherheits Verben

PowerShell verwendet die [System. Management. Automation. verbssecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) -Klasse, um Aktionen zu definieren, die sich auf die Sicherheit beziehen. In der folgenden Tabelle sind die meisten definierten Verben aufgeführt.

|Verb (Alias)|Aktion|Kommentare|
|--------------------|------------|--------------|
|[Block](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (BL)|Schränkt den Zugriff auf eine Ressource ein. Dieses Verb ist mit gekoppelt `Unblock` .|Verwenden Sie für diese Aktion keine Verben wie "Prevent", "Limit" oder "Deny".|
|[Grant](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (GR)|Ermöglicht den Zugriff auf eine Ressource. Dieses Verb ist mit gekoppelt `Revoke` .|Verwenden Sie für diese Aktion keine Verben wie Allow oder enable.|
|[Schützen](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (PT)|Schützt eine Ressource vor Angriffen oder Verlusten. Dieses Verb ist mit gekoppelt `Unprotect` .|Verwenden Sie für diese Aktion keine Verben wie z. b. verschlüsseln, schützen oder versiegeln.|
|[Widerrufen](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (RK)|Gibt eine Aktion an, die den Zugriff auf eine Ressource nicht zulässt. Dieses Verb ist mit gekoppelt `Grant` .|Verwenden Sie für diese Aktion keine Verben wie "Remove" oder "deaktivieren".|
|[Unblock](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (UL)|Entfernt Einschränkungen für eine Ressource. Dieses Verb ist mit gekoppelt `Block` .|Verwenden Sie für diese Aktion keine Verben wie z. b. Clear oder allow.|
|[Schutz](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) aufheben (up)|Entfernt Sicherheitsvorkehrungen aus einer Ressource, die hinzugefügt wurden, um Angriffe oder Verluste zu verhindern. Dieses Verb ist mit gekoppelt `Protect` .|Verwenden Sie für diese Aktion keine Verben wie z. b. entschlüsseln oder unversiegeln.|

## <a name="other-verbs"></a>Andere Verben

PowerShell verwendet die [System. Management. Automation. verbsother](/dotnet/api/System.Management.Automation.VerbsOther) -Klasse, um kanonische Verb Namen zu definieren, die nicht in eine bestimmte Verb Name-Kategorie passen, wie z. b. die Verben Common, Communications, Data, Lifecycle oder Security Verb Names.

|Verb (Alias)|Aktion|Kommentare|
|--------------------|------------|--------------|
|[Verwenden](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Verwendet oder enthält eine Ressource, um etwas zu tun.||

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System. Management. Automation. verbscommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System. Management. Automation. verbsdata](/dotnet/api/System.Management.Automation.VerbsData)

[System. Management. Automation. verbsdiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System. Management. Automation. verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System. Management. Automation. verbssecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System. Management. Automation. verbsother](/dotnet/api/System.Management.Automation.VerbsOther)

[Cmdlet-Deklaration](./cmdlet-class-declaration.md)

[Windows PowerShell-Programmiererhandbuch](../prog-guide/windows-powershell-programmer-s-guide.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
