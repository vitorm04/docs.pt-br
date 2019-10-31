---
ms.openlocfilehash: c861d61cbbe8075db4b17a702e863336ea621f2b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198333"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="9adba-101">HTTP: e/s síncrona desabilitada em todos os servidores</span><span class="sxs-lookup"><span data-stu-id="9adba-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="9adba-102">A partir do ASP.NET Core 3,0, as operações de servidor síncronas são desabilitadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="9adba-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9adba-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="9adba-103">Change description</span></span>

<span data-ttu-id="9adba-104">`AllowSynchronousIO` é uma opção em cada servidor que habilita ou desabilita APIs de e/s síncronas como `HttpRequest.Body.Read`, `HttpResponse.Body.Write` e `Stream.Flush`.</span><span class="sxs-lookup"><span data-stu-id="9adba-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="9adba-105">Essas APIs têm sido uma origem de privação de threads e bloqueios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9adba-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="9adba-106">A partir do ASP.NET Core 3,0 Preview 3, essas operações síncronas são desabilitadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="9adba-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="9adba-107">Servidores afetados:</span><span class="sxs-lookup"><span data-stu-id="9adba-107">Affected servers:</span></span>

- <span data-ttu-id="9adba-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="9adba-108">Kestrel</span></span>
- <span data-ttu-id="9adba-109">HttpSys</span><span class="sxs-lookup"><span data-stu-id="9adba-109">HttpSys</span></span>
- <span data-ttu-id="9adba-110">IIS em processo</span><span class="sxs-lookup"><span data-stu-id="9adba-110">IIS in-process</span></span>
- <span data-ttu-id="9adba-111">TestServer</span><span class="sxs-lookup"><span data-stu-id="9adba-111">TestServer</span></span>

<span data-ttu-id="9adba-112">Esperar erros semelhantes a:</span><span class="sxs-lookup"><span data-stu-id="9adba-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="9adba-113">Cada servidor tem uma opção `AllowSynchronousIO` que controla esse comportamento e o padrão para todos eles agora é `false`.</span><span class="sxs-lookup"><span data-stu-id="9adba-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="9adba-114">O comportamento também pode ser substituído em uma base por solicitação como uma mitigação temporária.</span><span class="sxs-lookup"><span data-stu-id="9adba-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="9adba-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9adba-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="9adba-116">Se você tiver problemas com um `TextWriter` ou outro fluxo chamando uma API síncrona no `Dispose`, chame a nova API `DisposeAsync` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="9adba-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="9adba-117">Para obter uma discussão, consulte [ASPNET/AspNetCore # 7644](https://github.com/aspnet/AspNetCore/issues/7644).</span><span class="sxs-lookup"><span data-stu-id="9adba-117">For discussion, see [aspnet/AspNetCore#7644](https://github.com/aspnet/AspNetCore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9adba-118">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9adba-118">Version introduced</span></span>

<span data-ttu-id="9adba-119">3.0</span><span class="sxs-lookup"><span data-stu-id="9adba-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9adba-120">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="9adba-120">Old behavior</span></span>

<span data-ttu-id="9adba-121">os `HttpRequest.Body.Read`, `HttpResponse.Body.Write` e `Stream.Flush` eram permitidos por padrão.</span><span class="sxs-lookup"><span data-stu-id="9adba-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9adba-122">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="9adba-122">New behavior</span></span>

<span data-ttu-id="9adba-123">Essas APIs síncronas não são permitidas por padrão:</span><span class="sxs-lookup"><span data-stu-id="9adba-123">These synchronous APIs are disallowed by default:</span></span>

<span data-ttu-id="9adba-124">Esperar erros semelhantes a:</span><span class="sxs-lookup"><span data-stu-id="9adba-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="9adba-125">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="9adba-125">Reason for change</span></span>

<span data-ttu-id="9adba-126">Essas APIs síncronas têm sido uma origem de privação de threads e bloqueios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9adba-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="9adba-127">A partir do ASP.NET Core 3,0 Preview 3, as operações síncronas são desabilitadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="9adba-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9adba-128">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="9adba-128">Recommended action</span></span>

<span data-ttu-id="9adba-129">Use as versões assíncronas dos métodos.</span><span class="sxs-lookup"><span data-stu-id="9adba-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="9adba-130">O comportamento também pode ser substituído em uma base por solicitação como uma mitigação temporária.</span><span class="sxs-lookup"><span data-stu-id="9adba-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="9adba-131">Categoria</span><span class="sxs-lookup"><span data-stu-id="9adba-131">Category</span></span>

<span data-ttu-id="9adba-132">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9adba-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9adba-133">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="9adba-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
