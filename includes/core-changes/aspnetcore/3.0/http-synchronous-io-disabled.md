---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901683"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="679ba-101">HTTP: IO síncrono desativado em todos os servidores</span><span class="sxs-lookup"><span data-stu-id="679ba-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="679ba-102">Começando com ASP.NET Core 3.0, as operações síncronas do servidor são desativadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="679ba-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="679ba-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="679ba-103">Change description</span></span>

<span data-ttu-id="679ba-104">`AllowSynchronousIO`é uma opção em cada servidor que ativa ou desativa APIs síncronas de IO como `HttpRequest.Body.Read`, `HttpResponse.Body.Write`e `Stream.Flush`.</span><span class="sxs-lookup"><span data-stu-id="679ba-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="679ba-105">Essas APIs têm sido há muito uma fonte de fome de thread saem.</span><span class="sxs-lookup"><span data-stu-id="679ba-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="679ba-106">A partir de ASP.NET Pré-visualização do Core 3.0 3, essas operações síncronas são desativadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="679ba-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="679ba-107">Servidores afetados:</span><span class="sxs-lookup"><span data-stu-id="679ba-107">Affected servers:</span></span>

- <span data-ttu-id="679ba-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="679ba-108">Kestrel</span></span>
- <span data-ttu-id="679ba-109">HttpSys</span><span class="sxs-lookup"><span data-stu-id="679ba-109">HttpSys</span></span>
- <span data-ttu-id="679ba-110">IIS em processo</span><span class="sxs-lookup"><span data-stu-id="679ba-110">IIS in-process</span></span>
- <span data-ttu-id="679ba-111">TestServer</span><span class="sxs-lookup"><span data-stu-id="679ba-111">TestServer</span></span>

<span data-ttu-id="679ba-112">Espere erros semelhantes aos:</span><span class="sxs-lookup"><span data-stu-id="679ba-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="679ba-113">Cada servidor `AllowSynchronousIO` tem uma opção que controla esse comportamento `false`e o padrão para todos eles é agora .</span><span class="sxs-lookup"><span data-stu-id="679ba-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="679ba-114">O comportamento também pode ser substituído por solicitação como uma mitigação temporária.</span><span class="sxs-lookup"><span data-stu-id="679ba-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="679ba-115">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="679ba-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="679ba-116">Se você tiver `TextWriter` problemas com um ou outro `Dispose`fluxo chamando `DisposeAsync` uma API síncrona, chame a nova API em vez disso.</span><span class="sxs-lookup"><span data-stu-id="679ba-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="679ba-117">Para discussão, consulte [dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).</span><span class="sxs-lookup"><span data-stu-id="679ba-117">For discussion, see [dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="679ba-118">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="679ba-118">Version introduced</span></span>

<span data-ttu-id="679ba-119">3.0</span><span class="sxs-lookup"><span data-stu-id="679ba-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="679ba-120">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="679ba-120">Old behavior</span></span>

<span data-ttu-id="679ba-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`e `Stream.Flush` foram permitidos por padrão.</span><span class="sxs-lookup"><span data-stu-id="679ba-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="679ba-122">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="679ba-122">New behavior</span></span>

<span data-ttu-id="679ba-123">Essas APIs síncronas são proibidas por padrão:</span><span class="sxs-lookup"><span data-stu-id="679ba-123">These synchronous APIs are disallowed by default:</span></span>

<span data-ttu-id="679ba-124">Espere erros semelhantes aos:</span><span class="sxs-lookup"><span data-stu-id="679ba-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="679ba-125">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="679ba-125">Reason for change</span></span>

<span data-ttu-id="679ba-126">Essas APIs síncronas têm sido há muito uma fonte de fome de segmentos e travamentos de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="679ba-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="679ba-127">A partir ASP.NET pré-visualização do Núcleo 3.0, as operações síncronas são desativadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="679ba-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="679ba-128">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="679ba-128">Recommended action</span></span>

<span data-ttu-id="679ba-129">Use as versões assíncronas dos métodos.</span><span class="sxs-lookup"><span data-stu-id="679ba-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="679ba-130">O comportamento também pode ser substituído por solicitação como uma mitigação temporária.</span><span class="sxs-lookup"><span data-stu-id="679ba-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="679ba-131">Categoria</span><span class="sxs-lookup"><span data-stu-id="679ba-131">Category</span></span>

<span data-ttu-id="679ba-132">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="679ba-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="679ba-133">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="679ba-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
