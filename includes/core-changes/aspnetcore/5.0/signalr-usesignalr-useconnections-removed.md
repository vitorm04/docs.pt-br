---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291662"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a><span data-ttu-id="3141b-101">Signalr: métodos UseSignalR e UseConnections removidos</span><span class="sxs-lookup"><span data-stu-id="3141b-101">SignalR: UseSignalR and UseConnections methods removed</span></span>

<span data-ttu-id="3141b-102">No ASP.NET Core 3,0, o Signalr adotou o roteamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3141b-102">In ASP.NET Core 3.0, SignalR adopted endpoint routing.</span></span> <span data-ttu-id="3141b-103">Como parte dessa alteração, o <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> , <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A> e alguns métodos relacionados foram marcados como obsoletos.</span><span class="sxs-lookup"><span data-stu-id="3141b-103">As part of that change, the <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, and some related methods were marked as obsolete.</span></span> <span data-ttu-id="3141b-104">No ASP.NET Core 5,0, esses métodos obsoletos foram removidos.</span><span class="sxs-lookup"><span data-stu-id="3141b-104">In ASP.NET Core 5.0, those obsolete methods were removed.</span></span> <span data-ttu-id="3141b-105">Para obter a lista completa de métodos, consulte [APIs afetadas](#affected-apis).</span><span class="sxs-lookup"><span data-stu-id="3141b-105">For the full list of methods, see [Affected APIs](#affected-apis).</span></span>

<span data-ttu-id="3141b-106">Para obter uma discussão sobre esse problema, consulte [dotnet/aspnetcore # 20082](https://github.com/dotnet/aspnetcore/issues/20082).</span><span class="sxs-lookup"><span data-stu-id="3141b-106">For discussion on this issue, see [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3141b-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="3141b-107">Version introduced</span></span>

<span data-ttu-id="3141b-108">5,0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="3141b-108">5.0 Preview 3</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3141b-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="3141b-109">Old behavior</span></span>

<span data-ttu-id="3141b-110">Os hubs de sinalização e os manipuladores de conexão podem ser registrados no pipeline de middleware usando os `UseSignalR` `UseConnections` métodos ou.</span><span class="sxs-lookup"><span data-stu-id="3141b-110">SignalR hubs and connection handlers could be registered in the middleware pipeline using the `UseSignalR` or `UseConnections` methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3141b-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="3141b-111">New behavior</span></span>

<span data-ttu-id="3141b-112">Os hubs de sinalização e os manipuladores de conexão devem ser registrados no <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> usando os <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> métodos de extensão e no <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder> .</span><span class="sxs-lookup"><span data-stu-id="3141b-112">SignalR hubs and connection handlers should be registered within <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> using the <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> and <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> extension methods on <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3141b-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="3141b-113">Reason for change</span></span>

<span data-ttu-id="3141b-114">Os métodos antigos tinham lógica de roteamento personalizada que não interagia com outros componentes de roteamento em ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3141b-114">The old methods had custom routing logic that didn't interact with other routing components in ASP.NET Core.</span></span> <span data-ttu-id="3141b-115">No ASP.NET Core 3,0, um novo sistema de roteamento de uso geral, chamado de roteamento de ponto de extremidade, foi introduzido.</span><span class="sxs-lookup"><span data-stu-id="3141b-115">In ASP.NET Core 3.0, a new general-purpose routing system, called endpoint routing, was introduced.</span></span> <span data-ttu-id="3141b-116">O Signalr habilitado para roteamento de ponto de extremidade para interagir com outros componentes de roteamento.</span><span class="sxs-lookup"><span data-stu-id="3141b-116">Endpoint routing enabled SignalR to interact with other routing components.</span></span> <span data-ttu-id="3141b-117">Alternar para esse modelo permite que os usuários percebam os benefícios completos do roteamento do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3141b-117">Switching to this model allows users to realize the full benefits of endpoint routing.</span></span> <span data-ttu-id="3141b-118">Consequentemente, os métodos antigos foram removidos.</span><span class="sxs-lookup"><span data-stu-id="3141b-118">Consequently, the old methods have been removed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3141b-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="3141b-119">Recommended action</span></span>

<span data-ttu-id="3141b-120">Remova o código que chama `UseSignalR` ou `UseConnections` do método do projeto `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="3141b-120">Remove code that calls `UseSignalR` or `UseConnections` from your project's `Startup.Configure` method.</span></span> <span data-ttu-id="3141b-121">Substitua-o por chamadas para `MapHub` ou `MapConnectionHandler` , respectivamente, no corpo de uma chamada para `UseEndpoints` .</span><span class="sxs-lookup"><span data-stu-id="3141b-121">Replace it with calls to `MapHub` or `MapConnectionHandler`, respectively, within the body of a call to `UseEndpoints`.</span></span> <span data-ttu-id="3141b-122">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3141b-122">For example:</span></span>

<span data-ttu-id="3141b-123">**Código antigo:**</span><span class="sxs-lookup"><span data-stu-id="3141b-123">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="3141b-124">**Novo código:**</span><span class="sxs-lookup"><span data-stu-id="3141b-124">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="3141b-125">Em geral, suas `MapHub` chamadas e anteriores `MapConnectionHandler` podem ser transferidas diretamente do corpo de `UseSignalR` e `UseConnections` para `UseEndpoints` com pouca ou nenhuma alteração necessária.</span><span class="sxs-lookup"><span data-stu-id="3141b-125">In general, your previous `MapHub` and `MapConnectionHandler` calls can be transferred directly from the body of `UseSignalR` and `UseConnections` to `UseEndpoints` with little-to-no change needed.</span></span>

#### <a name="category"></a><span data-ttu-id="3141b-126">Categoria</span><span class="sxs-lookup"><span data-stu-id="3141b-126">Category</span></span>

<span data-ttu-id="3141b-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3141b-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3141b-128">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="3141b-128">Affected APIs</span></span>

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
