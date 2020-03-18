---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901826"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="f27f4-101">Localização: ResourceManagerWithCultureStringLocalizer e WithCulture marcados como obsoletos</span><span class="sxs-lookup"><span data-stu-id="f27f4-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="f27f4-102">A classe [ResourceManagerWithCultureCultureLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) e o membro da interface [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) são muitas vezes `IStringLocalizer` fontes de confusão para os usuários de localização, especialmente quando criam sua própria implementação.</span><span class="sxs-lookup"><span data-stu-id="f27f4-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="f27f4-103">Esses itens dão ao usuário a `IStringLocalizer` impressão de que uma instância é "por idioma, por recurso".</span><span class="sxs-lookup"><span data-stu-id="f27f4-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="f27f4-104">Na realidade, as instâncias devem ser apenas "por recurso".</span><span class="sxs-lookup"><span data-stu-id="f27f4-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="f27f4-105">A linguagem pesquisada é `CultureInfo.CurrentUICulture` determinada pelo momento da execução.</span><span class="sxs-lookup"><span data-stu-id="f27f4-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="f27f4-106">Para eliminar a fonte da confusão, as APIs foram marcadas como obsoletas em ASP.NET O Core 3.0 Preview 3.</span><span class="sxs-lookup"><span data-stu-id="f27f4-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="f27f4-107">As APIs serão removidas em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="f27f4-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="f27f4-108">Para o contexto, consulte [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="f27f4-108">For context, see [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="f27f4-109">Para discussão, consulte [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="f27f4-109">For discussion, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f27f4-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="f27f4-110">Version introduced</span></span>

<span data-ttu-id="f27f4-111">3.0</span><span class="sxs-lookup"><span data-stu-id="f27f4-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f27f4-112">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="f27f4-112">Old behavior</span></span>

<span data-ttu-id="f27f4-113">Os métodos não `Obsolete`foram marcados como .</span><span class="sxs-lookup"><span data-stu-id="f27f4-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f27f4-114">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="f27f4-114">New behavior</span></span>

<span data-ttu-id="f27f4-115">Os métodos `Obsolete`são marcados .</span><span class="sxs-lookup"><span data-stu-id="f27f4-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f27f4-116">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="f27f4-116">Reason for change</span></span>

<span data-ttu-id="f27f4-117">As APIs representaram um caso de uso que não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="f27f4-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="f27f4-118">Houve confusão sobre o projeto da localização.</span><span class="sxs-lookup"><span data-stu-id="f27f4-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f27f4-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="f27f4-119">Recommended action</span></span>

<span data-ttu-id="f27f4-120">A recomendação `ResourceManagerStringLocalizer` é usar em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="f27f4-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="f27f4-121">Que a cultura seja `CurrentCulture`definida pelo.</span><span class="sxs-lookup"><span data-stu-id="f27f4-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="f27f4-122">Se isso não for uma opção, crie e use uma cópia do [ResourceManagerWithCultureCultureLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span><span class="sxs-lookup"><span data-stu-id="f27f4-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="f27f4-123">Categoria</span><span class="sxs-lookup"><span data-stu-id="f27f4-123">Category</span></span>

<span data-ttu-id="f27f4-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f27f4-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f27f4-125">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="f27f4-125">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
