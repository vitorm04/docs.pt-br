---
ms.openlocfilehash: a9545c66d3873b5114fe66e13c77ddc28e20020e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077599"
---
### <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a><span data-ttu-id="e1116-101">Mais incrivelmente: o recurso ProtectedBrowserStorage mudou para a estrutura compartilhada</span><span class="sxs-lookup"><span data-stu-id="e1116-101">Blazor: ProtectedBrowserStorage feature moved to shared framework</span></span>

<span data-ttu-id="e1116-102">Como parte da versão do ASP.NET Core RC2 5,0, o `ProtectedBrowserStorage` recurso foi movido para a estrutura compartilhada ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e1116-102">As part of the ASP.NET Core 5.0 RC2 release, the `ProtectedBrowserStorage` feature moved to the ASP.NET Core shared framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e1116-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="e1116-103">Version introduced</span></span>

<span data-ttu-id="e1116-104">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="e1116-104">5.0 RC2</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e1116-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="e1116-105">Old behavior</span></span>

<span data-ttu-id="e1116-106">No ASP.NET Core 5,0 Preview 8, o recurso está disponível como parte do pacote [Microsoft. AspNetCore. Components. Web. Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) , mas só pode ser usado no Webassembly de mais incrivelmente.</span><span class="sxs-lookup"><span data-stu-id="e1116-106">In ASP.NET Core 5.0 Preview 8, the feature is available as a part of the [Microsoft.AspNetCore.Components.Web.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) package but was only usable in Blazor WebAssembly.</span></span>

<span data-ttu-id="e1116-107">No ASP.NET Core 5,0 RC1, o recurso está disponível como parte do pacote [Microsoft. AspNetCore. Components. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) , que faz referência à `Microsoft.AspNetCore.App` estrutura compartilhada.</span><span class="sxs-lookup"><span data-stu-id="e1116-107">In ASP.NET Core 5.0 RC1, the feature is available as part of the [Microsoft.AspNetCore.Components.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) package, which references the `Microsoft.AspNetCore.App` shared framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e1116-108">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="e1116-108">New behavior</span></span>

<span data-ttu-id="e1116-109">No ASP.NET Core 5,0 RC2, uma referência de pacote NuGet não é mais necessária para referenciar e usar o recurso.</span><span class="sxs-lookup"><span data-stu-id="e1116-109">In ASP.NET Core 5.0 RC2, a NuGet package reference is no longer needed to reference and use the feature.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e1116-110">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="e1116-110">Reason for change</span></span>

<span data-ttu-id="e1116-111">A mudança para a estrutura compartilhada é uma melhor opção para a experiência do usuário que os clientes esperam.</span><span class="sxs-lookup"><span data-stu-id="e1116-111">The move to the shared framework is a better fit for the user experience customers expect.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e1116-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="e1116-112">Recommended action</span></span>

<span data-ttu-id="e1116-113">Se estiver atualizando do ASP.NET Core 5,0 RC1, conclua as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="e1116-113">If upgrading from ASP.NET Core 5.0 RC1, complete the following steps:</span></span>

1. <span data-ttu-id="e1116-114">Remova a `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` referência do pacote do projeto.</span><span class="sxs-lookup"><span data-stu-id="e1116-114">Remove the `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` package reference from the project.</span></span>
1. <span data-ttu-id="e1116-115">Substitua `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` por `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span><span class="sxs-lookup"><span data-stu-id="e1116-115">Replace `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="e1116-116">Remova a chamada de `AddProtectedBrowserStorage` de sua `Startup` classe.</span><span class="sxs-lookup"><span data-stu-id="e1116-116">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

<span data-ttu-id="e1116-117">Se estiver atualizando do ASP.NET Core 5,0 Preview 8, conclua as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="e1116-117">If upgrading from ASP.NET Core 5.0 Preview 8, complete the following steps:</span></span>

1. <span data-ttu-id="e1116-118">Remova a `Microsoft.AspNetCore.Components.Web.Extensions` referência do pacote do projeto.</span><span class="sxs-lookup"><span data-stu-id="e1116-118">Remove the `Microsoft.AspNetCore.Components.Web.Extensions` package reference from the project.</span></span>
1. <span data-ttu-id="e1116-119">Substitua `using Microsoft.AspNetCore.Components.Web.Extensions;` por `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span><span class="sxs-lookup"><span data-stu-id="e1116-119">Replace `using Microsoft.AspNetCore.Components.Web.Extensions;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="e1116-120">Remova a chamada de `AddProtectedBrowserStorage` de sua `Startup` classe.</span><span class="sxs-lookup"><span data-stu-id="e1116-120">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

#### <a name="category"></a><span data-ttu-id="e1116-121">Categoria</span><span class="sxs-lookup"><span data-stu-id="e1116-121">Category</span></span>

<span data-ttu-id="e1116-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e1116-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e1116-123">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e1116-123">Affected APIs</span></span>

<span data-ttu-id="e1116-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e1116-124">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
