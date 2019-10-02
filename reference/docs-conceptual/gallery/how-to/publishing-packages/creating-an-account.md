---
ms.date: 09/11/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Erstellen eines PowerShell-Katalogkontos
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328281"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="2593a-103">Erstellen eines PowerShell-Katalogkontos</span><span class="sxs-lookup"><span data-stu-id="2593a-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="2593a-104">Bevor Sie Elemente im PowerShell-Katalog veröffentlichen können, müssen Sie ein PowerShell-Katalog-Konto einrichten.</span><span class="sxs-lookup"><span data-stu-id="2593a-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="2593a-105">PowerShell-Katalog-Konten müssen mit einem E-Mail-fähigen Anmeldekonto verknüpft sein.</span><span class="sxs-lookup"><span data-stu-id="2593a-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="2593a-106">Dieses Konto kann ein Azure Active Directory-Konto oder eine Microsoft-ID sein, wie etwa ein E-Mail-Konto von outlook.com oder hotmail.com.</span><span class="sxs-lookup"><span data-stu-id="2593a-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="2593a-107">Besuchen Sie [https://PowerShellGallery.com](https://PowerShellGallery.com), und klicken Sie auf **Sign in** (Anmelden), so wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="2593a-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![Registrieren eines neuen Kontos](../../Images/CreateAccount-Register.png)

<span data-ttu-id="2593a-109">Verwenden Sie ein Azure Active Directory-Konto, wählen Sie **Work or School Account** (Geschäfts-, Schul- oder Unikonto) aus, und melden Sie sich mit Ihrem Konto an.</span><span class="sxs-lookup"><span data-stu-id="2593a-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="2593a-110">Wählen Sie **Personal Account** (Persönliches Konto) aus, und melden Sie sich an, um eine Microsoft-ID zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="2593a-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="2593a-111">Als Nächstes werden Sie aufgefordert, einen Benutzernamen für den PowerShell-Katalog zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2593a-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="2593a-112">Lesen Sie die Nutzungsbestimmungen und die Datenschutzrichtlinie, geben Sie einen Benutzernamen ein, und klicken Sie dann auf **Register** (Registrieren).</span><span class="sxs-lookup"><span data-stu-id="2593a-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="2593a-113">Der Kontoname kann nach der Erstellung nicht mehr geändert werden.</span><span class="sxs-lookup"><span data-stu-id="2593a-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="2593a-114">Weitere Informationen finden Sie unter [Verwalten von Paketbesitzern](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="2593a-114">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="2593a-115">Empfohlene Vorgehensweisen für PowerShell-Katalog-Konten</span><span class="sxs-lookup"><span data-stu-id="2593a-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="2593a-116">Es ist wichtig, das mit Ihrem PowerShell-Katalog-Konto verwendete E-Mail-Konto aktiv zu überwachen.</span><span class="sxs-lookup"><span data-stu-id="2593a-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="2593a-117">Die gesamte Kommunikation mit Paketbesitzern im PowerShell-Katalog erfolgt über diese E-Mail-Adresse.</span><span class="sxs-lookup"><span data-stu-id="2593a-117">All communication with owners of PowerShell Gallery packages is through this email address.</span></span> <span data-ttu-id="2593a-118">Wenn das Betriebsteam des PowerShell-Katalogs einen Paketbesitzer nicht kontaktieren kann, wird das betreffende Paket ggf. gelöscht.</span><span class="sxs-lookup"><span data-stu-id="2593a-118">If the PowerShell Gallery Operations team is unable to contact a package owner, we may be required to delete a package.</span></span>

<span data-ttu-id="2593a-119">Organisationen, die Elemente im PowerShell-Katalog veröffentlichen, erstellen zu diesem Zweck häufig ein eindeutiges externes Konto.</span><span class="sxs-lookup"><span data-stu-id="2593a-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="2593a-120">Es wird empfohlen, die E-Mail-Weiterleitung zu nutzen, um Benachrichtigung an eine Adresse innerhalb Ihrer Organisation weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="2593a-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="2593a-121">Wenn einem Paket mehrere Besitzer zugeordnet sind, werden alle PowerShell-Katalogbenachrichtigungen an alle diese Besitzer gesendet.</span><span class="sxs-lookup"><span data-stu-id="2593a-121">When multiple owners are associated with a package, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="2593a-122">Weitere Informationen finden Sie unter [Verwalten von Paketbesitzern](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="2593a-122">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>