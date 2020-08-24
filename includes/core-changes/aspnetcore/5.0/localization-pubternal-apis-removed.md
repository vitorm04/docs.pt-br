---
ms.openlocfilehash: 2094da7ec94028c112d6683620ac1146a1544dab
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446960"
---
### <a name="localization-pubternal-apis-removed"></a><span data-ttu-id="59c2f-101">Localização: APIs "Pubternal" removidas</span><span class="sxs-lookup"><span data-stu-id="59c2f-101">Localization: "Pubternal" APIs removed</span></span>

<span data-ttu-id="59c2f-102">Para manter melhor a superfície da API pública do ASP.NET Core, algumas :::no-loc text="\"pubternal\""::: APIs de localização foram removidas.</span><span class="sxs-lookup"><span data-stu-id="59c2f-102">To better maintain the public API surface of ASP.NET Core, some :::no-loc text="\"pubternal\""::: localization APIs were removed.</span></span> <span data-ttu-id="59c2f-103">Uma :::no-loc text="\"pubternal\""::: API tem um `public` modificador de acesso e é definida em um namespace que implica uma intenção [interna](/dotnet/csharp/language-reference/keywords/internal) .</span><span class="sxs-lookup"><span data-stu-id="59c2f-103">A :::no-loc text="\"pubternal\""::: API has a `public` access modifier and is defined in a namespace that implies an [internal](/dotnet/csharp/language-reference/keywords/internal) intent.</span></span>

<span data-ttu-id="59c2f-104">Para obter uma discussão, consulte [dotnet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291).</span><span class="sxs-lookup"><span data-stu-id="59c2f-104">For discussion, see [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="59c2f-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="59c2f-105">Version introduced</span></span>

<span data-ttu-id="59c2f-106">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="59c2f-106">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="59c2f-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="59c2f-107">Old behavior</span></span>

<span data-ttu-id="59c2f-108">As seguintes APIs foram `public` :</span><span class="sxs-lookup"><span data-stu-id="59c2f-108">The following APIs were `public`:</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <span data-ttu-id="59c2f-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` sobrecargas de Construtor aceitam qualquer um dos seguintes tipos de parâmetro:</span><span class="sxs-lookup"><span data-stu-id="59c2f-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="new-behavior"></a><span data-ttu-id="59c2f-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="59c2f-110">New behavior</span></span>

<span data-ttu-id="59c2f-111">A lista a seguir descreve as alterações:</span><span class="sxs-lookup"><span data-stu-id="59c2f-111">The following list outlines the changes:</span></span>

- <span data-ttu-id="59c2f-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper``Microsoft.Extensions.Localization.AssemblyWrapper`já se tornou e agora é `internal` .</span><span class="sxs-lookup"><span data-stu-id="59c2f-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` became `Microsoft.Extensions.Localization.AssemblyWrapper` and is now `internal`.</span></span>
- <span data-ttu-id="59c2f-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider``Microsoft.Extensions.Localization.Internal.IResourceStringProvider`já se tornou e agora é `internal` .</span><span class="sxs-lookup"><span data-stu-id="59c2f-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` became `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` and is now `internal`.</span></span>
- <span data-ttu-id="59c2f-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` as sobrecargas de construtor que aceitam qualquer um dos seguintes tipos de parâmetro agora são `internal` :</span><span class="sxs-lookup"><span data-stu-id="59c2f-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types are now `internal`:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="reason-for-change"></a><span data-ttu-id="59c2f-115">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="59c2f-115">Reason for change</span></span>

<span data-ttu-id="59c2f-116">Explicado mais detalhadamente em [ASPNET/comunicados # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), os :::no-loc text="\"pubternal\""::: tipos foram removidos da `public` superfície da API.</span><span class="sxs-lookup"><span data-stu-id="59c2f-116">Explained more thoroughly at [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: types were removed from the `public` API surface.</span></span> <span data-ttu-id="59c2f-117">Essas alterações se adaptam a mais classes para essa decisão de design.</span><span class="sxs-lookup"><span data-stu-id="59c2f-117">These changes adapt more classes to that design decision.</span></span> <span data-ttu-id="59c2f-118">As classes em questão eram pretendidas como pontos de extensão para os testes internos da equipe.</span><span class="sxs-lookup"><span data-stu-id="59c2f-118">The classes in question were intended as extension points for the team's internal testing.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="59c2f-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="59c2f-119">Recommended action</span></span>

<span data-ttu-id="59c2f-120">Embora seja improvável, alguns aplicativos podem depender intencionalmente ou acidentalmente, dependendo dos :::no-loc text="\"pubternal\""::: tipos.</span><span class="sxs-lookup"><span data-stu-id="59c2f-120">Although it's unlikely, some apps may intentionally or accidentally depend upon the :::no-loc text="\"pubternal\""::: types.</span></span> <span data-ttu-id="59c2f-121">Consulte as [novas](#new-behavior) seções de comportamento para determinar como migrar para fora dos tipos.</span><span class="sxs-lookup"><span data-stu-id="59c2f-121">See the [New behavior](#new-behavior) sections to determine how to migrate away from the types.</span></span>

<span data-ttu-id="59c2f-122">Se você identificou um cenário que a API pública permitiu antes dessa alteração, mas não agora, execute um problema em [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="59c2f-122">If you've identified a scenario which the public API allowed before this change but doesn't now, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="59c2f-123">Categoria</span><span class="sxs-lookup"><span data-stu-id="59c2f-123">Category</span></span>

<span data-ttu-id="59c2f-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="59c2f-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="59c2f-125">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="59c2f-125">Affected APIs</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
