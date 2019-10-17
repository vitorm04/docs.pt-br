---
ms.openlocfilehash: a4bf8cff59ffe01b7465e227c0b1d1e7d93f16e7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394182"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="42e4f-101">Estrutura compartilhada: assemblies removidos do Microsoft. AspNetCore. app</span><span class="sxs-lookup"><span data-stu-id="42e4f-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="42e4f-102">A partir do ASP.NET Core 3,0, a estrutura compartilhada ASP.NET Core (`Microsoft.AspNetCore.App`) contém apenas assemblies de terceiros que são totalmente desenvolvidos, com suporte e podem ser atendidos pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="42e4f-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span> 

#### <a name="change-description"></a><span data-ttu-id="42e4f-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="42e4f-103">Change description</span></span>

<span data-ttu-id="42e4f-104">Imagine a alteração como a redefinição de limites para a ASP.NET Core "plataforma".</span><span class="sxs-lookup"><span data-stu-id="42e4f-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="42e4f-105">A estrutura compartilhada será [criada de origem por qualquer pessoa por meio do GitHub](https://github.com/dotnet/source-build) e continuará a oferecer os benefícios existentes das estruturas compartilhadas do .NET Core para seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="42e4f-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="42e4f-106">Alguns benefícios incluem tamanho de implantação menor, aplicação de patch centralizada e tempo de inicialização mais rápido.</span><span class="sxs-lookup"><span data-stu-id="42e4f-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="42e4f-107">Como parte da alteração, algumas alterações significativas importantes são introduzidas em `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="42e4f-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="42e4f-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="42e4f-108">Version introduced</span></span>

<span data-ttu-id="42e4f-109">3.0</span><span class="sxs-lookup"><span data-stu-id="42e4f-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="42e4f-110">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="42e4f-110">Old behavior</span></span>

<span data-ttu-id="42e4f-111">Projetos referenciados `Microsoft.AspNetCore.App` por meio de um elemento `<PackageReference>` no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="42e4f-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="42e4f-112">Além disso, `Microsoft.AspNetCore.App` continha os seguintes subcomponentes:</span><span class="sxs-lookup"><span data-stu-id="42e4f-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="42e4f-113">Json.NET (`Newtonsoft.Json`)</span><span class="sxs-lookup"><span data-stu-id="42e4f-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="42e4f-114">Entity Framework Core (assemblies prefixados com `Microsoft.EntityFrameworkCore.`)</span><span class="sxs-lookup"><span data-stu-id="42e4f-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="42e4f-115">Roslyn (`Microsoft.CodeAnalysis`)</span><span class="sxs-lookup"><span data-stu-id="42e4f-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="42e4f-116">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="42e4f-116">New behavior</span></span>

<span data-ttu-id="42e4f-117">Uma referência a `Microsoft.AspNetCore.App` não requer mais um elemento `<PackageReference>` no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="42e4f-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="42e4f-118">O SDK do .NET Core dá suporte a um novo elemento chamado `<FrameworkReference>`, que substitui o uso de `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="42e4f-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="42e4f-119">Para obter mais informações, consulte [ASPNET/AspNetCore # 3612](https://github.com/aspnet/AspNetCore/issues/3612).</span><span class="sxs-lookup"><span data-stu-id="42e4f-119">For more information, see [aspnet/AspNetCore#3612](https://github.com/aspnet/AspNetCore/issues/3612).</span></span>

<span data-ttu-id="42e4f-120">Entity Framework Core são fornecidos como pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="42e4f-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="42e4f-121">Essa alteração alinha o modelo de envio com todas as outras bibliotecas de acesso a dados no .NET.</span><span class="sxs-lookup"><span data-stu-id="42e4f-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="42e4f-122">Ele fornece Entity Framework Core caminho mais simples para continuar inovação enquanto dá suporte a várias plataformas .NET.</span><span class="sxs-lookup"><span data-stu-id="42e4f-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="42e4f-123">A mudança de Entity Framework Core da estrutura compartilhada não tem impacto sobre seu status como uma biblioteca de serviços desenvolvidos, com suporte e desenvolvido pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="42e4f-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="42e4f-124">A [política de suporte do .NET Core](https://www.microsoft.com/net/platform/support-policy) continua a cobrir.</span><span class="sxs-lookup"><span data-stu-id="42e4f-124">The [.NET Core support policy](https://www.microsoft.com/net/platform/support-policy) continues to cover it.</span></span>

<span data-ttu-id="42e4f-125">Json.NET e Entity Framework Core continuam trabalhando com ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="42e4f-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="42e4f-126">No entanto, eles não serão incluídos na estrutura compartilhada.</span><span class="sxs-lookup"><span data-stu-id="42e4f-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="42e4f-127">Para obter mais informações, consulte [o futuro do JSON no .NET Core 3,0](https://github.com/dotnet/announcements/issues/90).</span><span class="sxs-lookup"><span data-stu-id="42e4f-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="42e4f-128">Consulte também [a lista completa de binários](https://github.com/aspnet/AspNetCore/issues/3755) removidos da estrutura compartilhada.</span><span class="sxs-lookup"><span data-stu-id="42e4f-128">Also see [the complete list of binaries](https://github.com/aspnet/AspNetCore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="42e4f-129">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="42e4f-129">Reason for change</span></span>

<span data-ttu-id="42e4f-130">Essa alteração simplifica o consumo de `Microsoft.AspNetCore.App` e reduz a duplicação entre pacotes do NuGet e estruturas compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="42e4f-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="42e4f-131">Para obter mais informações sobre a motivação para essa alteração, consulte [esta postagem no blog](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).</span><span class="sxs-lookup"><span data-stu-id="42e4f-131">For more information on the motivation for this change, see [this blog post](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="42e4f-132">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="42e4f-132">Recommended action</span></span>

<span data-ttu-id="42e4f-133">Não será necessário que os projetos consumam assemblies em `Microsoft.AspNetCore.App` como pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="42e4f-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="42e4f-134">Para simplificar o direcionamento e o uso da estrutura ASP.NET Core compartilhada, muitos pacotes NuGet fornecidos desde ASP.NET Core 1,0 não são mais produzidos.</span><span class="sxs-lookup"><span data-stu-id="42e4f-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="42e4f-135">As APIs que esses pacotes fornecem ainda estão disponíveis para aplicativos usando um `<FrameworkReference>` a `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="42e4f-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="42e4f-136">Exemplos comuns de API incluem Kestrel, MVC e Razor.</span><span class="sxs-lookup"><span data-stu-id="42e4f-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="42e4f-137">Essa alteração não se aplica a todos os binários referenciados por meio de `Microsoft.AspNetCore.App` em ASP.NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="42e4f-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="42e4f-138">As exceções notáveis incluem:</span><span class="sxs-lookup"><span data-stu-id="42e4f-138">Notable exceptions include:</span></span>

- <span data-ttu-id="42e4f-139">as bibliotecas `Microsoft.Extensions` que continuam a direcionar .NET Standard estarão disponíveis como pacotes NuGet (consulte https://github.com/aspnet/Extensions).</span><span class="sxs-lookup"><span data-stu-id="42e4f-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see https://github.com/aspnet/Extensions).</span></span>
- <span data-ttu-id="42e4f-140">APIs produzidas pela equipe de ASP.NET Core que não fazem parte do `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="42e4f-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="42e4f-141">Por exemplo, os seguintes componentes estão disponíveis como pacotes NuGet:</span><span class="sxs-lookup"><span data-stu-id="42e4f-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="42e4f-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="42e4f-142">Entity Framework Core</span></span>
  - <span data-ttu-id="42e4f-143">APIs que fornecem integração de terceiros</span><span class="sxs-lookup"><span data-stu-id="42e4f-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="42e4f-144">Recursos experimentais</span><span class="sxs-lookup"><span data-stu-id="42e4f-144">Experimental features</span></span>
  - <span data-ttu-id="42e4f-145">APIs com dependências que não puderam [atender aos requisitos para estar na estrutura compartilhada](https://github.com/aspnet/AspNetCore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span><span class="sxs-lookup"><span data-stu-id="42e4f-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/aspnet/AspNetCore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="42e4f-146">Extensões para MVC que mantêm suporte para Json.NET.</span><span class="sxs-lookup"><span data-stu-id="42e4f-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="42e4f-147">Uma API será fornecida como um pacote NuGet para dar suporte ao uso do Json.NET e MVC.</span><span class="sxs-lookup"><span data-stu-id="42e4f-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="42e4f-148">O cliente do sinalizador .NET continuará a dar suporte a .NET Standard e enviará como um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="42e4f-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="42e4f-149">Ele é destinado ao uso em vários tempos de execução do .NET, como Xamarin e UWP.</span><span class="sxs-lookup"><span data-stu-id="42e4f-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="42e4f-150">Para obter mais informações, consulte [parar de produzir pacotes para assemblies de estrutura compartilhada em 3,0](https://github.com/aspnet/AspNetCore/issues/3756).</span><span class="sxs-lookup"><span data-stu-id="42e4f-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/aspnet/AspNetCore/issues/3756).</span></span> <span data-ttu-id="42e4f-151">Para obter uma discussão, consulte [ASPNET/AspNetCore # 3757](https://github.com/aspnet/AspNetCore/issues/3757).</span><span class="sxs-lookup"><span data-stu-id="42e4f-151">For discussion, see [aspnet/AspNetCore#3757](https://github.com/aspnet/AspNetCore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="42e4f-152">Categoria</span><span class="sxs-lookup"><span data-stu-id="42e4f-152">Category</span></span>

<span data-ttu-id="42e4f-153">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="42e4f-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="42e4f-154">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="42e4f-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
