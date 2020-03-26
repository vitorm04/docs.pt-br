---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291662"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a><span data-ttu-id="49069-101">SignalR: UseSignalR e UseConnections métodos removidos</span><span class="sxs-lookup"><span data-stu-id="49069-101">SignalR: UseSignalR and UseConnections methods removed</span></span>

<span data-ttu-id="49069-102">Em ASP.NET Núcleo 3.0, o SignalR adotou o roteamento de ponto final.</span><span class="sxs-lookup"><span data-stu-id="49069-102">In ASP.NET Core 3.0, SignalR adopted endpoint routing.</span></span> <span data-ttu-id="49069-103">Como parte dessa mudança, os <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>métodos <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>relacionados foram marcados como obsoletos.</span><span class="sxs-lookup"><span data-stu-id="49069-103">As part of that change, the <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, and some related methods were marked as obsolete.</span></span> <span data-ttu-id="49069-104">Em ASP.NET Núcleo 5.0, esses métodos obsoletos foram removidos.</span><span class="sxs-lookup"><span data-stu-id="49069-104">In ASP.NET Core 5.0, those obsolete methods were removed.</span></span> <span data-ttu-id="49069-105">Para obter a lista completa de métodos, consulte [APIs afetados](#affected-apis).</span><span class="sxs-lookup"><span data-stu-id="49069-105">For the full list of methods, see [Affected APIs](#affected-apis).</span></span>

<span data-ttu-id="49069-106">Para discussão sobre este assunto, consulte [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span><span class="sxs-lookup"><span data-stu-id="49069-106">For discussion on this issue, see [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="49069-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="49069-107">Version introduced</span></span>

<span data-ttu-id="49069-108">5.0 Pré-visualização 3</span><span class="sxs-lookup"><span data-stu-id="49069-108">5.0 Preview 3</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="49069-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="49069-109">Old behavior</span></span>

<span data-ttu-id="49069-110">Os hubs SignalR e os manipuladores de conexão `UseSignalR` `UseConnections` podem ser registrados no pipeline de middleware usando os métodos ou.</span><span class="sxs-lookup"><span data-stu-id="49069-110">SignalR hubs and connection handlers could be registered in the middleware pipeline using the `UseSignalR` or `UseConnections` methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="49069-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="49069-111">New behavior</span></span>

<span data-ttu-id="49069-112">Os hubs SignalR e os manipuladores <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> de <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> conexão <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>devem ser registrados dentro <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> dos métodos de extensão e de extensão em .</span><span class="sxs-lookup"><span data-stu-id="49069-112">SignalR hubs and connection handlers should be registered within <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> using the <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> and <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> extension methods on <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="49069-113">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="49069-113">Reason for change</span></span>

<span data-ttu-id="49069-114">Os métodos antigos tinham lógica de roteamento personalizado que não interagia com outros componentes de roteamento no ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="49069-114">The old methods had custom routing logic that didn't interact with other routing components in ASP.NET Core.</span></span> <span data-ttu-id="49069-115">Em ASP.NET Core 3.0, um novo sistema de roteamento de uso geral, chamado de roteamento de ponto final, foi introduzido.</span><span class="sxs-lookup"><span data-stu-id="49069-115">In ASP.NET Core 3.0, a new general-purpose routing system, called endpoint routing, was introduced.</span></span> <span data-ttu-id="49069-116">O roteamento de ponto final permitiu que o SignalR interagisse com outros componentes de roteamento.</span><span class="sxs-lookup"><span data-stu-id="49069-116">Endpoint routing enabled SignalR to interact with other routing components.</span></span> <span data-ttu-id="49069-117">Mudar para este modelo permite que os usuários percebam todos os benefícios do roteamento de ponto final.</span><span class="sxs-lookup"><span data-stu-id="49069-117">Switching to this model allows users to realize the full benefits of endpoint routing.</span></span> <span data-ttu-id="49069-118">Consequentemente, os métodos antigos foram removidos.</span><span class="sxs-lookup"><span data-stu-id="49069-118">Consequently, the old methods have been removed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="49069-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="49069-119">Recommended action</span></span>

<span data-ttu-id="49069-120">Remova o `UseSignalR` código `UseConnections` que chama `Startup.Configure` ou do método do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="49069-120">Remove code that calls `UseSignalR` or `UseConnections` from your project's `Startup.Configure` method.</span></span> <span data-ttu-id="49069-121">Substitua-o `MapHub` por `MapConnectionHandler`chamadas para ou, respectivamente, `UseEndpoints`dentro do corpo de uma chamada para .</span><span class="sxs-lookup"><span data-stu-id="49069-121">Replace it with calls to `MapHub` or `MapConnectionHandler`, respectively, within the body of a call to `UseEndpoints`.</span></span> <span data-ttu-id="49069-122">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="49069-122">For example:</span></span>

<span data-ttu-id="49069-123">**Código antigo:**</span><span class="sxs-lookup"><span data-stu-id="49069-123">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="49069-124">**Novo código:**</span><span class="sxs-lookup"><span data-stu-id="49069-124">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="49069-125">Em geral, `MapHub` suas `MapConnectionHandler` chamadas anteriores e podem `UseSignalR` `UseConnections` ser `UseEndpoints` transferidas diretamente do corpo de e para com pouca ou nenhuma mudança necessária.</span><span class="sxs-lookup"><span data-stu-id="49069-125">In general, your previous `MapHub` and `MapConnectionHandler` calls can be transferred directly from the body of `UseSignalR` and `UseConnections` to `UseEndpoints` with little-to-no change needed.</span></span>

#### <a name="category"></a><span data-ttu-id="49069-126">Categoria</span><span class="sxs-lookup"><span data-stu-id="49069-126">Category</span></span>

<span data-ttu-id="49069-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="49069-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="49069-128">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="49069-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->
