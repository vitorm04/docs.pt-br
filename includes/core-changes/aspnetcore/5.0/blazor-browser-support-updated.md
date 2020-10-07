---
ms.openlocfilehash: 584014572ab799e1e3ab2f02c9fbf4fe6b0c17e7
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804914"
---
### <a name="blazor-updated-browser-support"></a><span data-ttu-id="68312-101">Mais incrivelmente: suporte a navegador atualizado</span><span class="sxs-lookup"><span data-stu-id="68312-101">Blazor: Updated browser support</span></span>

<span data-ttu-id="68312-102">ASP.NET Core 5,0 apresenta [novos recursos mais avançados](https://github.com/dotnet/aspnetcore/issues/21514), alguns dos quais são incompatíveis com navegadores mais antigos.</span><span class="sxs-lookup"><span data-stu-id="68312-102">ASP.NET Core 5.0 introduces [new Blazor features](https://github.com/dotnet/aspnetcore/issues/21514), some of which are incompatible with older browsers.</span></span> <span data-ttu-id="68312-103">A lista de navegadores com suporte no mais 5,0 do ASP.NET Core foi atualizada de acordo.</span><span class="sxs-lookup"><span data-stu-id="68312-103">The list of browsers supported by Blazor in ASP.NET Core 5.0 has been updated accordingly.</span></span>

<span data-ttu-id="68312-104">Para obter uma discussão, consulte o problema do GitHub [dotnet/aspnetcore # 26475](https://github.com/dotnet/aspnetcore/issues/26475).</span><span class="sxs-lookup"><span data-stu-id="68312-104">For discussion, see GitHub issue [dotnet/aspnetcore#26475](https://github.com/dotnet/aspnetcore/issues/26475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="68312-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="68312-105">Version introduced</span></span>

<span data-ttu-id="68312-106">5,0</span><span class="sxs-lookup"><span data-stu-id="68312-106">5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="68312-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="68312-107">Old behavior</span></span>

<span data-ttu-id="68312-108">O servidor mais incrivelmente dá suporte ao Microsoft Internet Explorer 11 com suportes retroativos suficientes.</span><span class="sxs-lookup"><span data-stu-id="68312-108">Blazor Server supports Microsoft Internet Explorer 11 with sufficient polyfills.</span></span> <span data-ttu-id="68312-109">O servidor e Webassembly mais poseriais também são funcionais no [Microsoft Edge herdado](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).</span><span class="sxs-lookup"><span data-stu-id="68312-109">Blazor Server and Blazor WebAssembly are also functional in [Microsoft Edge Legacy](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="68312-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="68312-110">New behavior</span></span>

<span data-ttu-id="68312-111">Não há suporte para um servidor mais incrivelmente no ASP.NET Core 5,0 com o Microsoft Internet Explorer 11.</span><span class="sxs-lookup"><span data-stu-id="68312-111">Blazor Server in ASP.NET Core 5.0 isn't supported with Microsoft Internet Explorer 11.</span></span> <span data-ttu-id="68312-112">O servidor e o Webassembly mais completo não são totalmente funcionais no Microsoft Edge herdado.</span><span class="sxs-lookup"><span data-stu-id="68312-112">Blazor Server and Blazor WebAssembly aren't fully functional in Microsoft Edge Legacy.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="68312-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="68312-113">Reason for change</span></span>

<span data-ttu-id="68312-114">Novos recursos mais avançados do ASP.NET Core 5,0 são incompatíveis com esses navegadores mais antigos, e o uso desses navegadores mais antigos está diminuindo.</span><span class="sxs-lookup"><span data-stu-id="68312-114">New Blazor features in ASP.NET Core 5.0 are incompatible with these older browsers, and use of these older browsers is diminishing.</span></span> <span data-ttu-id="68312-115">Para saber mais, consulte os recursos a seguir:</span><span class="sxs-lookup"><span data-stu-id="68312-115">For more information, see the following resources:</span></span>

* [<span data-ttu-id="68312-116">O suporte do Windows para o Microsoft Edge herdado também está terminando em 9 de março de 2021</span><span class="sxs-lookup"><span data-stu-id="68312-116">Windows support for Microsoft Edge Legacy is also ending on March 9, 2021</span></span>](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)
* [<span data-ttu-id="68312-117">Microsoft 365 aplicativos e serviços encerrarão o suporte para o Microsoft Internet Explorer 11 de 17 de agosto de 2021</span><span class="sxs-lookup"><span data-stu-id="68312-117">Microsoft 365 apps and services will end support for Microsoft Internet Explorer 11 by August 17, 2021</span></span>](/lifecycle/announcements/m365-ie11-microsoft-edge-legacy)

#### <a name="recommended-action"></a><span data-ttu-id="68312-118">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="68312-118">Recommended action</span></span>

<span data-ttu-id="68312-119">Atualize esses navegadores mais antigos para o [novo Microsoft Edge baseado em Chromium](https://www.microsoft.com/edge).</span><span class="sxs-lookup"><span data-stu-id="68312-119">Upgrade from these older browsers to the [new, Chromium-based Microsoft Edge](https://www.microsoft.com/edge).</span></span> <span data-ttu-id="68312-120">Para aplicativos mais incrivelmente que precisam dar suporte a esses navegadores mais antigos, use ASP.NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="68312-120">For Blazor apps that need to support these older browsers, use ASP.NET Core 3.1.</span></span> <span data-ttu-id="68312-121">A lista de navegadores com suporte para um mais incrivelmente no ASP.NET Core 3,1 não foi alterada e está documentada em [plataformas com suporte](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).</span><span class="sxs-lookup"><span data-stu-id="68312-121">The supported browsers list for Blazor in ASP.NET Core 3.1 hasn't changed and is documented at [Supported platforms](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).</span></span>

#### <a name="category"></a><span data-ttu-id="68312-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="68312-122">Category</span></span>

<span data-ttu-id="68312-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="68312-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="68312-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="68312-124">Affected APIs</span></span>

<span data-ttu-id="68312-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="68312-125">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
