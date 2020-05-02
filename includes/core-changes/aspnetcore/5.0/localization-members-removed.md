---
ms.openlocfilehash: 6deeb7debce9b731f3871b7de0ad8df8a8cdafea
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728282"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a><span data-ttu-id="0e568-101">Localização: classe ResourceManagerWithCultureStringLocalizer e membro da interface WithCulture removidos</span><span class="sxs-lookup"><span data-stu-id="0e568-101">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>

<span data-ttu-id="0e568-102">A classe [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) e o método [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) foram removidos no .NET 5,0 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="0e568-102">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were removed in .NET 5.0 Preview 1.</span></span>

<span data-ttu-id="0e568-103">Para contexto, consulte [ASPNET/comunicados # 346](https://github.com/aspnet/Announcements/issues/346) e [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="0e568-103">For context, see [aspnet/Announcements#346](https://github.com/aspnet/Announcements/issues/346) and [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="0e568-104">Para discussão sobre essa alteração, consulte [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="0e568-104">For discussion on this change, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0e568-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="0e568-105">Version introduced</span></span>

<span data-ttu-id="0e568-106">5,0 visualização 1</span><span class="sxs-lookup"><span data-stu-id="0e568-106">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0e568-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="0e568-107">Old behavior</span></span>

<span data-ttu-id="0e568-108">A `ResourceManagerWithCultureStringLocalizer` classe e o `ResourceManagerStringLocalizer.WithCulture` método são [obsoletos no .NET Core 3,0 Preview 3 e posterior](/dotnet/core/compatibility/2.2-3.0#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span><span class="sxs-lookup"><span data-stu-id="0e568-108">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method are [obsolete in .NET Core 3.0 Preview 3 and later](/dotnet/core/compatibility/2.2-3.0#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0e568-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="0e568-109">New behavior</span></span>

<span data-ttu-id="0e568-110">A `ResourceManagerWithCultureStringLocalizer` classe e o `ResourceManagerStringLocalizer.WithCulture` método foram removidos no .NET 5,0 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="0e568-110">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method have been removed in .NET 5.0 Preview 1.</span></span> <span data-ttu-id="0e568-111">Para obter um inventário das alterações feitas, consulte a solicitação pull em [dotnet/Extensions # 2562](https://github.com/dotnet/extensions/pull/2562/files).</span><span class="sxs-lookup"><span data-stu-id="0e568-111">For an inventory of the changes made, see the pull request at [dotnet/extensions#2562](https://github.com/dotnet/extensions/pull/2562/files).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0e568-112">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="0e568-112">Reason for change</span></span>

<span data-ttu-id="0e568-113">A classe [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) e o método [ResourceManagerStringLocalizer. WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) geralmente eram fontes de confusão para os usuários da localização.</span><span class="sxs-lookup"><span data-stu-id="0e568-113">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were often sources of confusion for users of localization.</span></span> <span data-ttu-id="0e568-114">A confusão era especialmente alta ao criar uma implementação <xref:Microsoft.Extensions.Localization.IStringLocalizer> personalizada.</span><span class="sxs-lookup"><span data-stu-id="0e568-114">The confusion was especially high when creating a custom <xref:Microsoft.Extensions.Localization.IStringLocalizer> implementation.</span></span> <span data-ttu-id="0e568-115">Essa classe e o método dão aos consumidores a impressão `IStringLocalizer` de que uma instância deve ser "por idioma, por recurso".</span><span class="sxs-lookup"><span data-stu-id="0e568-115">This class and method give consumers the impression that an `IStringLocalizer` instance is expected to be "per-language, per-resource".</span></span> <span data-ttu-id="0e568-116">Na realidade, a instância só deve ser "por recurso".</span><span class="sxs-lookup"><span data-stu-id="0e568-116">In reality, the instance should only be "per-resource".</span></span> <span data-ttu-id="0e568-117">Em tempo de execução, <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> a propriedade determina o idioma a ser usado.</span><span class="sxs-lookup"><span data-stu-id="0e568-117">At run time, the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> property determines the language to be used.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0e568-118">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="0e568-118">Recommended action</span></span>

<span data-ttu-id="0e568-119">Pare de usar `ResourceManagerWithCultureStringLocalizer` a classe e `ResourceManagerStringLocalizer.WithCulture` o método.</span><span class="sxs-lookup"><span data-stu-id="0e568-119">Stop using the `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method.</span></span>

#### <a name="category"></a><span data-ttu-id="0e568-120">Categoria</span><span class="sxs-lookup"><span data-stu-id="0e568-120">Category</span></span>

<span data-ttu-id="0e568-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0e568-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0e568-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0e568-122">Affected APIs</span></span>

- [<span data-ttu-id="0e568-123">ResourceManagerWithCultureStringLocalizer</span><span class="sxs-lookup"><span data-stu-id="0e568-123">ResourceManagerWithCultureStringLocalizer</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [<span data-ttu-id="0e568-124">ResourceManagerStringLocalizer.WithCulture</span><span class="sxs-lookup"><span data-stu-id="0e568-124">ResourceManagerStringLocalizer.WithCulture</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
