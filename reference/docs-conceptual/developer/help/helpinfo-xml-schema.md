---
title: Helpinfo-XML-Schema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 3e2a113e120c61fab1ba76c4fd897ded67d13319
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811519"
---
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="563fb-102">XML-Schema von HelpInfo</span><span class="sxs-lookup"><span data-stu-id="563fb-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="563fb-103">Dieses Thema enthält das XML-Schema für aktualisierbare Hilfe Informationsdateien, die häufig als "helpinfo-XML-Dateien" bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="563fb-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="563fb-104">XML-Schema von HelpInfo</span><span class="sxs-lookup"><span data-stu-id="563fb-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="563fb-105">Helpinfo-XML-Dateien basieren auf dem folgenden XML-Schema.</span><span class="sxs-lookup"><span data-stu-id="563fb-105">HelpInfo XML files are based on the following XML schema.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="https://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
  <element name="HelpInfo">
    <complexType>
      <sequence>
        <element name="HelpContentURI" type="anyURI" minOccurs="1" maxOccurs="1" />
        <element name="SupportedUICultures" minOccurs="1" maxOccurs="1">
          <complexType>
            <sequence>
              <element name="UICulture" minOccurs="1" maxOccurs="unbounded">
                <complexType>
                  <sequence>
                    <element name="UICultureName" type="language" minOccurs="1" maxOccurs="1" />
                    <element name="UICultureVersion" type="string" minOccurs="1" maxOccurs="1" />
                  </sequence>
                </complexType>
              </element>
            </sequence>
          </complexType>
        </element>
      </sequence>
    </complexType>
  </element>
</schema>
```

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="563fb-106">Helpinfo-XML-Elemente</span><span class="sxs-lookup"><span data-stu-id="563fb-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="563fb-107">Die helpinfo-XML-Datei enthält die folgenden Elemente:</span><span class="sxs-lookup"><span data-stu-id="563fb-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="563fb-108">Helpcontenturi enthält den URI des Speicher Orts der Hilfe-CAB-Dateien für das Modul.</span><span class="sxs-lookup"><span data-stu-id="563fb-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="563fb-109">Der URI muss mit "http" oder "https" beginnen.</span><span class="sxs-lookup"><span data-stu-id="563fb-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="563fb-110">Der URI sollte einen Internet Speicherort angeben, darf jedoch nicht den Namen der CAB-Datei enthalten.</span><span class="sxs-lookup"><span data-stu-id="563fb-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="563fb-111">Der **helpcontenturi** -Wert kann identisch oder vom **helpinfouri** -Wert abweichen.</span><span class="sxs-lookup"><span data-stu-id="563fb-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="563fb-112">Supporteduicultures stellt die Modul Hilfedateien in allen Benutzeroberflächen Kulturen dar.</span><span class="sxs-lookup"><span data-stu-id="563fb-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="563fb-113">Enthält **UICulture** -Elemente, von denen jede einen Satz von Hilfedateien für das Modul in einer angegebenen Benutzeroberflächen Kultur darstellt.</span><span class="sxs-lookup"><span data-stu-id="563fb-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="563fb-114">UICulture stellt einen Satz von Hilfedateien für das Modul in einer angegebenen Benutzeroberflächen Kultur dar.</span><span class="sxs-lookup"><span data-stu-id="563fb-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="563fb-115">Fügen Sie für jede Benutzeroberflächen Kultur, in der die Hilfedateien geschrieben werden, ein **UICulture** -Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="563fb-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="563fb-116">Uiculturename enthält den Sprachcode für die Benutzeroberflächen Kultur, in der die Hilfedateien geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="563fb-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="563fb-117">Uicultureversion enthält eine 4-teilige Versionsnummer in "N1. N2. N3. N4-Format, das die Version der Hilfe-CAB-Datei in der Benutzeroberflächen Kultur darstellt.</span><span class="sxs-lookup"><span data-stu-id="563fb-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="563fb-118">Erhöhen Sie diese Versionsnummer immer dann, wenn Sie neue Hilfe-CAB-Dateien in der Benutzeroberflächen Kultur hochladen, die von **uiculturename**angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="563fb-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="563fb-119">Weitere Informationen zu diesem Wert finden Sie unter "Versions Klasse (System)" in MSDN.</span><span class="sxs-lookup"><span data-stu-id="563fb-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>