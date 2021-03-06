---
ms.date: 07/17/2020
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC für Linux-Resource „nxPackage“
ms.openlocfilehash: f61b337f6fbb8e2ea48128642874f050787fc576
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464484"
---
# <a name="dsc-for-linux-nxpackage-resource"></a>DSC für Linux-Resource „nxPackage“

Die Ressource **nxPackage** in PowerShell DSC bietet einen Mechanismus zum Verwalten von Paketen auf einem Linux-Knoten.

## <a name="syntax"></a>Syntax

```Syntax
nxPackage <string> #ResourceName
{
    Name = <string>
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ FilePath = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|Name |Der Name des Pakets, für das Sie einen bestimmten Zustand sicherstellen möchten. |
|PackageManager |Unterstützte Werte sind **yum**, **apt** und **zypper**. Gibt den Paket-Manager an, der zum Installieren von Paketen verwendet werden soll. Wenn **FilePath** angegeben ist, dient der angegebene Pfad zum Installieren des Pakets. Andernfalls wird ein Paket-Manager zum Installieren des Pakets aus einem vorkonfigurierten Repository verwendet. Wenn weder **PackageManager** noch **FilePath** angegeben ist, wird der standardmäßige Paket-Manager für das System verwendet. |
|PackageGroup |Falls `$true`, soll **Name** dem Namen einer Paketgruppe für die Verwendung mit einem **PackageManager** entsprechen. **PackageGroup** ist ungültig, wenn **FilePath** angegeben wird. |
|Argumente |Eine Zeichenfolge mit Argumenten, die exakt wie angegeben an das Paket übergeben wird. |
|ReturnCode |Der erwartete Rückgabecode. Wenn der tatsächliche Rückgabecode nicht dem erwarteten Wert entspricht, gibt die Konfiguration einen Fehler zurück. |
|FilePath |Der Dateipfad, in dem das Paket gespeichert ist. |

## <a name="common-properties"></a>Allgemeine Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|DependsOn |Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Bestimmt, ob das Vorhandensein des Pakets geprüft werden soll. Legen Sie diese Eigenschaft auf **Present** fest, um sicherzustellen, dass das Paket vorhanden ist. Legen Sie sie auf **Absent** fest, um sicherzustellen, dass das Paket nicht vorhanden ist. Der Standardwert ist **Present**. |

## <a name="example"></a>Beispiel

Im folgende Beispiel wird sichergestellt, dass das Paket mit dem Namen „httpd“ mit dem Paket-Manager „Yum“ auf einem Linux-Computer installiert wird.

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxPackage httpd
    {
        Name = "httpd"
        Ensure = "Present"
        PackageManager = "Yum"
    }
}
```
