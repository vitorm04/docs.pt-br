---
ms.openlocfilehash: 41e80a9dbcfa2a857e0b52674ef0724a542458a0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539437"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a><span data-ttu-id="8c6c6-101">Localização: classe ResourceManagerWithCultureStringLocalizer e membro da interface WithCulture removidos</span><span class="sxs-lookup"><span data-stu-id="8c6c6-101">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>

<span data-ttu-id="8c6c6-102">A classe [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) e o método [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) foram removidos no .NET 5,0 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="8c6c6-102">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were removed in .NET 5.0 Preview 1.</span></span>

<span data-ttu-id="8c6c6-103">Para contexto, consulte [ASPNET/comunicados # 346](https://github.com/aspnet/Announcements/issues/346) e [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="8c6c6-103">For context, see [aspnet/Announcements#346](https://github.com/aspnet/Announcements/issues/346) and [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="8c6c6-104">Para discussão sobre essa alteração, consulte [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="8c6c6-104">For discussion on this change, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8c6c6-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8c6c6-105">Version introduced</span></span>

<span data-ttu-id="8c6c6-106">5,0 visualização 1</span><span class="sxs-lookup"><span data-stu-id="8c6c6-106">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8c6c6-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="8c6c6-107">Old behavior</span></span>

<span data-ttu-id="8c6c6-108">A `ResourceManagerWithCultureStringLocalizer` classe e o `ResourceManagerStringLocalizer.WithCulture` método são [obsoletos no .NET Core 3,0 Preview 3 e posterior](../../../../docs/core/compatibility/2.2-3.0.md#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span><span class="sxs-lookup"><span data-stu-id="8c6c6-108">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method are [obsolete in .NET Core 3.0 Preview 3 and later](../../../../docs/core/compatibility/2.2-3.0.md#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8c6c6-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="8c6c6-109">New behavior</span></span>

<span data-ttu-id="8c6c6-110">A `ResourceManagerWithCultureStringLocalizer` classe e o `ResourceManagerStringLocalizer.WithCulture` método foram removidos no .NET 5,0 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="8c6c6-110">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method have been removed in .NET 5.0 Preview 1.</span></span> <span data-ttu-id="8c6c6-111">Para obter um inventário das alterações feitas, consulte a solicitação pull em [dotnet/Extensions # 2562](https://github.com/dotnet/extensions/pull/2562/files).</span><span class="sxs-lookup"><span data-stu-id="8c6c6-111">For an inventory of the changes made, see the pull request at [dotnet/extensions#2562](https://github.com/dotnet/extensions/pull/2562/files).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8c6c6-112">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="8c6c6-112">Reason for change</span></span>

<span data-ttu-id="8c6c6-113">A classe [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) e o método [ResourceManagerStringLocalizer. WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) geralmente eram fontes de confusão para os usuários da localização.</span><span class="sxs-lookup"><span data-stu-id="8c6c6-113">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were often sources of confusion for users of localization.</span></span> <span data-ttu-id="8c6c6-114">A confusão era especialmente alta ao criar uma <xref:Microsoft.Extensions.Localization.IStringLocalizer> implementação personalizada.</span><span class="sxs-lookup"><span data-stu-id="8c6c6-114">The confusion was especially high when creating a custom <xref:Microsoft.Extensions.Localization.IStringLocalizer> implementation.</span></span> <span data-ttu-id="8c6c6-115">Essa classe e o método dão aos consumidores a impressão de que uma `IStringLocalizer` instância deve ser "por idioma, por recurso".</span><span class="sxs-lookup"><span data-stu-id="8c6c6-115">This class and method give consumers the impression that an `IStringLocalizer` instance is expected to be "per-language, per-resource".</span></span> <span data-ttu-id="8c6c6-116">Na realidade, a instância só deve ser "por recurso".</span><span class="sxs-lookup"><span data-stu-id="8c6c6-116">In reality, the instance should only be "per-resource".</span></span> <span data-ttu-id="8c6c6-117">Em tempo de execução, a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> propriedade determina o idioma a ser usado.</span><span class="sxs-lookup"><span data-stu-id="8c6c6-117">At run time, the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> property determines the language to be used.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8c6c6-118">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="8c6c6-118">Recommended action</span></span>

<span data-ttu-id="8c6c6-119">Pare de usar a `ResourceManagerWithCultureStringLocalizer` classe e o `ResourceManagerStringLocalizer.WithCulture` método.</span><span class="sxs-lookup"><span data-stu-id="8c6c6-119">Stop using the `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method.</span></span>

#### <a name="category"></a><span data-ttu-id="8c6c6-120">Categoria</span><span class="sxs-lookup"><span data-stu-id="8c6c6-120">Category</span></span>

<span data-ttu-id="8c6c6-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8c6c6-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8c6c6-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8c6c6-122">Affected APIs</span></span>

- [<span data-ttu-id="8c6c6-123">ResourceManagerWithCultureStringLocalizer</span><span class="sxs-lookup"><span data-stu-id="8c6c6-123">ResourceManagerWithCultureStringLocalizer</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [<span data-ttu-id="8c6c6-124">ResourceManagerStringLocalizer.WithCulture</span><span class="sxs-lookup"><span data-stu-id="8c6c6-124">ResourceManagerStringLocalizer.WithCulture</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
