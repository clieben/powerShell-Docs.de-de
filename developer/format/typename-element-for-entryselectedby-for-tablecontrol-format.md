---
title: TypeName-Element für EntrySelectedBy für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855726"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="d7cea-102">Element „TypeName“ für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d7cea-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="d7cea-103">Gibt einen .NET-Typ, der dieser Eintrag der Tabellenansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="d7cea-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="d7cea-104">Es gibt keine Beschränkung der Anzahl von Typen, die für einen Tabelleneintrag angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="d7cea-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="d7cea-105">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries-Element (Format) TableRowEntry-Element (Format) EntrySelectedBy-Element (Format) TypeName Konfigurationselement für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d7cea-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d7cea-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d7cea-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d7cea-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="d7cea-107">Attributes and Elements</span></span>

<span data-ttu-id="d7cea-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="d7cea-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d7cea-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="d7cea-109">Attributes</span></span>

<span data-ttu-id="d7cea-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="d7cea-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d7cea-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d7cea-111">Child Elements</span></span>

<span data-ttu-id="d7cea-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="d7cea-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d7cea-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d7cea-113">Parent Elements</span></span>

|<span data-ttu-id="d7cea-114">Element</span><span class="sxs-lookup"><span data-stu-id="d7cea-114">Element</span></span>|<span data-ttu-id="d7cea-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d7cea-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7cea-116">EntrySelectedBy-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="d7cea-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="d7cea-117">Definiert die .NET-Typen, die diesen Eintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="d7cea-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d7cea-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="d7cea-118">Text Value</span></span>

<span data-ttu-id="d7cea-119">Geben Sie den Namen des .NET-Typs.</span><span class="sxs-lookup"><span data-stu-id="d7cea-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7cea-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d7cea-120">Remarks</span></span>

<span data-ttu-id="d7cea-121">Jeder Listeneintrag muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert haben.</span><span class="sxs-lookup"><span data-stu-id="d7cea-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="d7cea-122">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d7cea-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d7cea-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d7cea-123">See Also</span></span>

[<span data-ttu-id="d7cea-124">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="d7cea-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d7cea-125">EntrySelectedBy-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="d7cea-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="d7cea-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7cea-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)