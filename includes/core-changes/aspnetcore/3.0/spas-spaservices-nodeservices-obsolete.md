---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394117"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a><span data-ttu-id="0a0d8-101">SPAs: SpaServices e Nodeservices marcados como obsoletos</span><span class="sxs-lookup"><span data-stu-id="0a0d8-101">SPAs: SpaServices and NodeServices marked obsolete</span></span>

<span data-ttu-id="0a0d8-102">Todos os conteúdos dos pacotes NuGet a seguir foram desnecessários desde ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-102">The contents of the following NuGet packages have all been unnecessary since ASP.NET Core 2.1.</span></span> <span data-ttu-id="0a0d8-103">Consequentemente, os seguintes pacotes estão sendo marcados como obsoletos:</span><span class="sxs-lookup"><span data-stu-id="0a0d8-103">Consequently, the following packages are being marked as obsolete:</span></span>

- [<span data-ttu-id="0a0d8-104">Microsoft. AspNetCore. SpaServices</span><span class="sxs-lookup"><span data-stu-id="0a0d8-104">Microsoft.AspNetCore.SpaServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [<span data-ttu-id="0a0d8-105">Microsoft. AspNetCore. Nodeservices</span><span class="sxs-lookup"><span data-stu-id="0a0d8-105">Microsoft.AspNetCore.NodeServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

<span data-ttu-id="0a0d8-106">Pelo mesmo motivo, os seguintes módulos NPM estão sendo marcados como preteridos:</span><span class="sxs-lookup"><span data-stu-id="0a0d8-106">For the same reason, the following npm modules are being marked as deprecated:</span></span>

- [<span data-ttu-id="0a0d8-107">ASPNET-angular</span><span class="sxs-lookup"><span data-stu-id="0a0d8-107">aspnet-angular</span></span>](https://www.npmjs.com/package/aspnet-angular)
- [<span data-ttu-id="0a0d8-108">ASPNET-pré-processamento</span><span class="sxs-lookup"><span data-stu-id="0a0d8-108">aspnet-prerendering</span></span>](https://www.npmjs.com/package/aspnet-prerendering)
- [<span data-ttu-id="0a0d8-109">ASPNET-webpack</span><span class="sxs-lookup"><span data-stu-id="0a0d8-109">aspnet-webpack</span></span>](https://www.npmjs.com/package/aspnet-webpack)
- [<span data-ttu-id="0a0d8-110">ASPNET-webpack – reagir</span><span class="sxs-lookup"><span data-stu-id="0a0d8-110">aspnet-webpack-react</span></span>](https://www.npmjs.com/package/aspnet-webpack-react)
- [<span data-ttu-id="0a0d8-111">tarefa de domínio</span><span class="sxs-lookup"><span data-stu-id="0a0d8-111">domain-task</span></span>](https://www.npmjs.com/package/domain-task)

<span data-ttu-id="0a0d8-112">Os pacotes anteriores e os módulos NPM serão removidos posteriormente no .NET 5.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-112">The preceding packages and npm modules will later be removed in .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0a0d8-113">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="0a0d8-113">Version introduced</span></span>

<span data-ttu-id="0a0d8-114">3,0</span><span class="sxs-lookup"><span data-stu-id="0a0d8-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0a0d8-115">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="0a0d8-115">Old behavior</span></span>

<span data-ttu-id="0a0d8-116">Os pacotes preteridos e os módulos NPM foram destinados a integrar ASP.NET Core com várias estruturas de SPA (aplicativo de página única).</span><span class="sxs-lookup"><span data-stu-id="0a0d8-116">The deprecated packages and npm modules were intended to integrate ASP.NET Core with various Single-Page App (SPA) frameworks.</span></span> <span data-ttu-id="0a0d8-117">Tais estruturas incluem angular, reagir e reagir com Redux.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-117">Such frameworks include Angular, React, and React with Redux.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0a0d8-118">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="0a0d8-118">New behavior</span></span>

<span data-ttu-id="0a0d8-119">Existe um novo mecanismo de integração no pacote NuGet [Microsoft. AspNetCore. SpaServices. Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) .</span><span class="sxs-lookup"><span data-stu-id="0a0d8-119">A new integration mechanism exists in the [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet package.</span></span> <span data-ttu-id="0a0d8-120">O pacote permanece a base dos modelos de projeto angular e reajam desde o ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-120">The package remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0a0d8-121">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="0a0d8-121">Reason for change</span></span>

<span data-ttu-id="0a0d8-122">O ASP.NET Core dá suporte à integração com várias estruturas de SPA (aplicativo de página única), incluindo angular, reagir e reagir com Redux.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-122">ASP.NET Core supports integration with various Single-Page App (SPA) frameworks, including Angular, React, and React with Redux.</span></span> <span data-ttu-id="0a0d8-123">Inicialmente, a integração com essas estruturas foi realizada com componentes específicos do ASP.NET Core que manipulavam cenários como o pré-processamento do lado do servidor e a integração com o webpack.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-123">Initially, integration with these frameworks was accomplished with ASP.NET Core-specific components that handled scenarios like server-side prerendering and integration with Webpack.</span></span> <span data-ttu-id="0a0d8-124">À medida que o tempo passou, os padrões do setor mudaram.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-124">As time went on, industry standards changed.</span></span> <span data-ttu-id="0a0d8-125">Cada uma das estruturas de SPA lançou suas próprias interfaces de linha de comando padrão.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-125">Each of the SPA frameworks released their own standard command-line interfaces.</span></span> <span data-ttu-id="0a0d8-126">Por exemplo, CLI angular e Create-reajam-app.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-126">For example, Angular CLI and create-react-app.</span></span>

<span data-ttu-id="0a0d8-127">Quando ASP.NET Core 2,1 foi lançado em maio de 2018, a equipe respondeu à alteração nos padrões.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-127">When ASP.NET Core 2.1 was released in May 2018, the team responded to the change in standards.</span></span> <span data-ttu-id="0a0d8-128">Foi fornecida uma maneira mais nova e mais simples de integrar com o próprio cadeias das estruturas do SPA.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-128">A newer and simpler way to integrate with the SPA frameworks' own toolchains was provided.</span></span> <span data-ttu-id="0a0d8-129">O novo mecanismo de integração existe no pacote `Microsoft.AspNetCore.SpaServices.Extensions` e permanece a base dos modelos de projeto angulares e reajam desde o ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-129">The new integration mechanism exists in the package `Microsoft.AspNetCore.SpaServices.Extensions` and remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

<span data-ttu-id="0a0d8-130">Para esclarecer que os componentes mais antigos ASP.NET Core específicos são irrelevantes e não são recomendados:</span><span class="sxs-lookup"><span data-stu-id="0a0d8-130">To clarify that the older ASP.NET Core-specific components are irrelevant and not recommended:</span></span>

- <span data-ttu-id="0a0d8-131">O mecanismo de integração anterior ao 2,1 é marcado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-131">The pre-2.1 integration mechanism is marked as obsolete.</span></span>
- <span data-ttu-id="0a0d8-132">Os pacotes NPM de suporte são marcados como preteridos.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-132">The supporting npm packages are marked as deprecated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0a0d8-133">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="0a0d8-133">Recommended action</span></span>

<span data-ttu-id="0a0d8-134">Se você estiver usando esses pacotes, atualize seus aplicativos para usar a funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="0a0d8-134">If you're using these packages, update your apps to use the functionality:</span></span>

- <span data-ttu-id="0a0d8-135">No `Microsoft.AspNetCore.SpaServices.Extensions` pacote.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-135">In the `Microsoft.AspNetCore.SpaServices.Extensions` package.</span></span>
- <span data-ttu-id="0a0d8-136">Fornecido pelas estruturas SPA que você está usando</span><span class="sxs-lookup"><span data-stu-id="0a0d8-136">Provided by the SPA frameworks you're using</span></span>

<span data-ttu-id="0a0d8-137">Para habilitar recursos como o pré-processamento do lado do servidor e a recarga de módulo quente, consulte a documentação da estrutura SPA correspondente.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-137">To enable features like server-side prerendering and hot module reload, see the documentation for the corresponding SPA framework.</span></span> <span data-ttu-id="0a0d8-138">A funcionalidade no `Microsoft.AspNetCore.SpaServices.Extensions` *não* está obsoleta e continuará a receber suporte.</span><span class="sxs-lookup"><span data-stu-id="0a0d8-138">The functionality in `Microsoft.AspNetCore.SpaServices.Extensions` is *not* obsolete and will continue to be supported.</span></span>

#### <a name="category"></a><span data-ttu-id="0a0d8-139">Categoria</span><span class="sxs-lookup"><span data-stu-id="0a0d8-139">Category</span></span>

<span data-ttu-id="0a0d8-140">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0a0d8-140">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0a0d8-141">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0a0d8-141">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.SpaRouteExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.WebpackDevMiddleware?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.INodeServices?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesFactory?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesOptions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.StringAsTempFile?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions?displayProperty=nameWithType>

- <xref:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Builder.SpaRouteExtensions`
- `T:Microsoft.AspNetCore.Builder.WebpackDevMiddleware`

- `T:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader`
- `T:Microsoft.AspNetCore.NodeServices.INodeServices`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesFactory`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesOptions`
- `T:Microsoft.AspNetCore.NodeServices.StringAsTempFile`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance`

- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult`
- `T:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions`

- `T:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions`
- `T:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions`

-->
