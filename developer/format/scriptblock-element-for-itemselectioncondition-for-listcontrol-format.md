---
title: ScriptBlock-Element für ItemSelectionCondition für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855416"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="ab85f-102">Element „ScriptBlock“ für ItemSeclectionCondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ab85f-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="ab85f-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="ab85f-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="ab85f-104">Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und das Element der Liste wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="ab85f-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="ab85f-105">Dieses Element wird verwendet, wenn Sie eine Ansicht zu definieren.</span><span class="sxs-lookup"><span data-stu-id="ab85f-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="ab85f-106">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries Konfigurationselement für ListEntry-Element für ListEntries für ListControl (Format) ListItems-Element für ListEntry ListControl (Format) für ListControl (Format) ListItem-Element für ListItems für Liste (Format) ItemSelectionCondition Steuerelement für den ListItem für ListControl (Format)-ScriptBlock-Element für ItemSelectionCondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ab85f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab85f-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ab85f-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab85f-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="ab85f-108">Attributes and Elements</span></span>

<span data-ttu-id="ab85f-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und die übergeordneten Elemente der `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="ab85f-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab85f-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="ab85f-110">Attributes</span></span>

<span data-ttu-id="ab85f-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="ab85f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ab85f-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ab85f-112">Child Elements</span></span>

<span data-ttu-id="ab85f-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="ab85f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ab85f-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ab85f-114">Parent Elements</span></span>

|<span data-ttu-id="ab85f-115">Element</span><span class="sxs-lookup"><span data-stu-id="ab85f-115">Element</span></span>|<span data-ttu-id="ab85f-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ab85f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab85f-117">ItemSelectionCondition-Element für den ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ab85f-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="ab85f-118">Definiert die Bedingung, die für dieses Listenelement zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="ab85f-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ab85f-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="ab85f-119">Text Value</span></span>

<span data-ttu-id="ab85f-120">Geben Sie das Skript aus, das ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="ab85f-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab85f-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ab85f-121">Remarks</span></span>

<span data-ttu-id="ab85f-122">Wenn dieses Element verwendet wird, Sie können nicht angeben, die `PropertyName` -Element, wenn die auswahlbedingung zu definieren.</span><span class="sxs-lookup"><span data-stu-id="ab85f-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab85f-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ab85f-123">See Also</span></span>

[<span data-ttu-id="ab85f-124">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab85f-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)