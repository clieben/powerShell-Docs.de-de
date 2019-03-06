---
title: PropertyName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860416"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="5573a-102">Element „PropertyName“ für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5573a-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="5573a-103">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="5573a-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="5573a-104">Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und die Definition verwendet.</span><span class="sxs-lookup"><span data-stu-id="5573a-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="5573a-105">Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) EntrySelectedBy Konfigurationselement für WideEntry (Format) SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)-PropertyName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5573a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5573a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5573a-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="5573a-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="5573a-107">Attributes and Elements</span></span>

<span data-ttu-id="5573a-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.</span><span class="sxs-lookup"><span data-stu-id="5573a-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5573a-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="5573a-109">Attributes</span></span>

<span data-ttu-id="5573a-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="5573a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5573a-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5573a-111">Child Elements</span></span>

<span data-ttu-id="5573a-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="5573a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5573a-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5573a-113">Parent Elements</span></span>

|<span data-ttu-id="5573a-114">Element</span><span class="sxs-lookup"><span data-stu-id="5573a-114">Element</span></span>|<span data-ttu-id="5573a-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5573a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5573a-116">SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5573a-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="5573a-117">Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5573a-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5573a-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="5573a-118">Text Value</span></span>

<span data-ttu-id="5573a-119">Geben Sie den Namen der .NET-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="5573a-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="5573a-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5573a-120">Remarks</span></span>

<span data-ttu-id="5573a-121">Die auswahlbedingung muss angeben, über mindestens einen Eigenschaftennamen oder ein Skript zu evaluieren, aber nicht beide angeben.</span><span class="sxs-lookup"><span data-stu-id="5573a-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="5573a-122">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5573a-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="5573a-123">Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [Breite Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="5573a-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5573a-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5573a-124">See Also</span></span>

[<span data-ttu-id="5573a-125">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="5573a-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="5573a-126">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="5573a-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5573a-127">ScriptBlock-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5573a-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="5573a-128">SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5573a-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="5573a-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="5573a-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)