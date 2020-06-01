---
title: Helpinfo-XML-Beispieldatei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6544070f-5549-407f-8603-5df60fe9e013
caps.latest.revision: 7
ms.openlocfilehash: 3cf4790be3e26c8b55335da32152a4e2c1ee67b6
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811529"
---
# <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="54d81-102">XML-Beispieldatei HelpInfo</span><span class="sxs-lookup"><span data-stu-id="54d81-102">HelpInfo XML Sample File</span></span>

<span data-ttu-id="54d81-103">In diesem Thema wird ein Beispiel für eine wohlgeformte aktualisierbare Hilfe Informationsdatei angezeigt, die häufig als "helpinfo-XML-Datei" bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="54d81-103">This topic displays a sample of a well-formed Updatable Help Information file, commonly known as "HelpInfo XML file."</span></span> <span data-ttu-id="54d81-104">In dieser Beispieldatei werden die UI-Kulturelemente in alphabetischer Reihenfolge nach dem Namen der Benutzeroberflächen Kultur angeordnet.</span><span class="sxs-lookup"><span data-stu-id="54d81-104">In this sample file, the UI culture elements are arranged in alphabetical order by UI culture name.</span></span> <span data-ttu-id="54d81-105">Die alphabetische Reihenfolge ist eine bewährte Vorgehensweise, aber Sie ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="54d81-105">Alphabetical ordering is a best practice, but it is not required.</span></span>

## <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="54d81-106">XML-Beispieldatei HelpInfo</span><span class="sxs-lookup"><span data-stu-id="54d81-106">HelpInfo XML Sample File</span></span>

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="https://schemas.microsoft.com/powershell/help/2010/05">
   <HelpContentURI>https://go.microsoft.com/fwlink/?LinkID=141553</HelpContentURI>
   <SupportedUICultures>
    <UICulture>
      <UICultureName>de-DE</UICultureName>
      <UICultureVersion>2.15.0.10</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>en-US</UICultureName>
      <UICultureVersion>3.2.0.7</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>it-IT</UICultureName>
      <UICultureVersion>1.1.0.5</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>ja-JP</UICultureName>
      <UICultureVersion>3.2.0.4</UICultureVersion>
    </UICulture>
   </SupportedUICultures>
</HelpInfo>

```