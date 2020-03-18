---
ms.openlocfilehash: a8146db1fb54d63d4716b879ce793f7d817cef59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937273"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="1f409-101">Estrutura compartilhada: Assembléias removidas do Microsoft.AspNetCore.App</span><span class="sxs-lookup"><span data-stu-id="1f409-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="1f409-102">A partir de ASP.NET Core 3.0,`Microsoft.AspNetCore.App`o ASP.NET Core () contém apenas montagens de primeira parte que são totalmente desenvolvidas, suportadas e reparadas pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1f409-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1f409-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="1f409-103">Change description</span></span>

<span data-ttu-id="1f409-104">Pense na mudança como a redefinição de limites para a "plataforma" ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1f409-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="1f409-105">A estrutura compartilhada será [construída por qualquer pessoa via GitHub](https://github.com/dotnet/source-build) e continuará a oferecer os benefícios existentes das estruturas compartilhadas do .NET Core aos seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1f409-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="1f409-106">Alguns benefícios incluem menor tamanho de implantação, patches centralizados e tempo de inicialização mais rápido.</span><span class="sxs-lookup"><span data-stu-id="1f409-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="1f409-107">Como parte da mudança, algumas mudanças `Microsoft.AspNetCore.App`notáveis de quebra são introduzidas em .</span><span class="sxs-lookup"><span data-stu-id="1f409-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1f409-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="1f409-108">Version introduced</span></span>

<span data-ttu-id="1f409-109">3.0</span><span class="sxs-lookup"><span data-stu-id="1f409-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1f409-110">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="1f409-110">Old behavior</span></span>

<span data-ttu-id="1f409-111">Projetos referenciados `Microsoft.AspNetCore.App` `<PackageReference>` através de um elemento no arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="1f409-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="1f409-112">Além disso, `Microsoft.AspNetCore.App` continha os seguintes subcomponentes:</span><span class="sxs-lookup"><span data-stu-id="1f409-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="1f409-113">`Newtonsoft.Json`Json.NET</span><span class="sxs-lookup"><span data-stu-id="1f409-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="1f409-114">Núcleo de Quadro de Entidades (conjuntos prefixados com `Microsoft.EntityFrameworkCore.`)</span><span class="sxs-lookup"><span data-stu-id="1f409-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="1f409-115">Roslyn`Microsoft.CodeAnalysis`( )</span><span class="sxs-lookup"><span data-stu-id="1f409-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1f409-116">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="1f409-116">New behavior</span></span>

<span data-ttu-id="1f409-117">Uma referência `Microsoft.AspNetCore.App` a não `<PackageReference>` mais requer um elemento no arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="1f409-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="1f409-118">O .NET Core SDK suporta `<FrameworkReference>`um novo elemento chamado `<PackageReference>`, que substitui o uso de .</span><span class="sxs-lookup"><span data-stu-id="1f409-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="1f409-119">Para obter mais informações, consulte [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span><span class="sxs-lookup"><span data-stu-id="1f409-119">For more information, see [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span></span>

<span data-ttu-id="1f409-120">Entity Framework Core é enviado como pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="1f409-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="1f409-121">Essa alteração alinha o modelo de envio com todas as outras bibliotecas de acesso a dados no .NET.</span><span class="sxs-lookup"><span data-stu-id="1f409-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="1f409-122">Ele fornece ao Entity Framework Core o caminho mais simples para continuar inovando enquanto suporta as várias plataformas .NET.</span><span class="sxs-lookup"><span data-stu-id="1f409-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="1f409-123">A mudança do Entity Framework Core para fora da estrutura compartilhada não tem impacto em seu status como uma biblioteca desenvolvida pela Microsoft, suportada e útil.</span><span class="sxs-lookup"><span data-stu-id="1f409-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="1f409-124">A [política de suporte do .NET Core](https://www.microsoft.com/net/platform/support-policy) continua a cobri-la.</span><span class="sxs-lookup"><span data-stu-id="1f409-124">The [.NET Core support policy](https://www.microsoft.com/net/platform/support-policy) continues to cover it.</span></span>

<span data-ttu-id="1f409-125">Json.NET e Entity Framework Core continuam a trabalhar com ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1f409-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="1f409-126">Eles não serão, no entanto, incluídos no quadro compartilhado.</span><span class="sxs-lookup"><span data-stu-id="1f409-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="1f409-127">Para obter mais informações, consulte [O futuro do JSON no .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span><span class="sxs-lookup"><span data-stu-id="1f409-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="1f409-128">Veja também [a lista completa de binários removidos](https://github.com/dotnet/aspnetcore/issues/3755) da estrutura compartilhada.</span><span class="sxs-lookup"><span data-stu-id="1f409-128">Also see [the complete list of binaries](https://github.com/dotnet/aspnetcore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1f409-129">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="1f409-129">Reason for change</span></span>

<span data-ttu-id="1f409-130">Essa alteração simplifica o `Microsoft.AspNetCore.App` consumo e reduz a duplicação entre pacotes NuGet e frameworks compartilhados.</span><span class="sxs-lookup"><span data-stu-id="1f409-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="1f409-131">Para obter mais informações sobre a motivação dessa mudança, consulte [este post no blog](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="1f409-131">For more information on the motivation for this change, see [this blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1f409-132">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="1f409-132">Recommended action</span></span>

<span data-ttu-id="1f409-133">Não será necessário que os projetos consumam montagens como `Microsoft.AspNetCore.App` pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="1f409-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="1f409-134">Para simplificar a segmentação e o uso da estrutura compartilhada ASP.NET Core, muitos pacotes NuGet enviados desde ASP.NET Core 1.0 não são mais produzidos.</span><span class="sxs-lookup"><span data-stu-id="1f409-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="1f409-135">As APIs que esses pacotes fornecem ainda `<FrameworkReference>` `Microsoft.AspNetCore.App`estão disponíveis para os aplicativos usando um a.</span><span class="sxs-lookup"><span data-stu-id="1f409-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="1f409-136">Exemplos comuns de API incluem Kestrel, MVC e Razor.</span><span class="sxs-lookup"><span data-stu-id="1f409-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="1f409-137">Esta alteração não se aplica a todos `Microsoft.AspNetCore.App` os binários referenciados através de ASP.NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="1f409-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="1f409-138">Exceções notáveis incluem:</span><span class="sxs-lookup"><span data-stu-id="1f409-138">Notable exceptions include:</span></span>

- <span data-ttu-id="1f409-139">`Microsoft.Extensions`bibliotecas que continuam a segmentar .NET Standard estarão https://github.com/dotnet/extensions)disponíveis como pacotes NuGet (veja .</span><span class="sxs-lookup"><span data-stu-id="1f409-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see https://github.com/dotnet/extensions).</span></span>
- <span data-ttu-id="1f409-140">APIs produzidas pela equipe do ASP.NET `Microsoft.AspNetCore.App`Core que não fazem parte de .</span><span class="sxs-lookup"><span data-stu-id="1f409-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="1f409-141">Por exemplo, os seguintes componentes estão disponíveis como pacotes NuGet:</span><span class="sxs-lookup"><span data-stu-id="1f409-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="1f409-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="1f409-142">Entity Framework Core</span></span>
  - <span data-ttu-id="1f409-143">APIs que fornecem integração de terceiros</span><span class="sxs-lookup"><span data-stu-id="1f409-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="1f409-144">Recursos experimentais</span><span class="sxs-lookup"><span data-stu-id="1f409-144">Experimental features</span></span>
  - <span data-ttu-id="1f409-145">APIs com dependências que não poderiam [cumprir os requisitos para estar no quadro compartilhado](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span><span class="sxs-lookup"><span data-stu-id="1f409-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="1f409-146">Extensões ao MVC que mantêm suporte para Json.NET.</span><span class="sxs-lookup"><span data-stu-id="1f409-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="1f409-147">Uma API será fornecida como um pacote NuGet para suportar o uso de Json.NET e MVC.</span><span class="sxs-lookup"><span data-stu-id="1f409-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="1f409-148">O cliente SignalR .NET continuará a suportar o .NET Standard e a enviar como um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="1f409-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="1f409-149">Destina-se a ser usado em muitos runtimes .NET, como Xamarin e UWP.</span><span class="sxs-lookup"><span data-stu-id="1f409-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="1f409-150">Para obter mais informações, consulte [Pare de produzir pacotes para montagens de quadros compartilhados em 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span><span class="sxs-lookup"><span data-stu-id="1f409-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span></span> <span data-ttu-id="1f409-151">Para discussão, consulte [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span><span class="sxs-lookup"><span data-stu-id="1f409-151">For discussion, see [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="1f409-152">Categoria</span><span class="sxs-lookup"><span data-stu-id="1f409-152">Category</span></span>

<span data-ttu-id="1f409-153">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1f409-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1f409-154">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1f409-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
