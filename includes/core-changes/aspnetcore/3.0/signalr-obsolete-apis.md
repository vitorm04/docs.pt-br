---
ms.openlocfilehash: 2a65caedea2af65796267aa145e275ebff814bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393916"
---
### <a name="signalr-usesignalr-and-useconnections-methods-marked-obsolete"></a><span data-ttu-id="fefe4-101">SignalR: UseSignalR e UseConnections métodos marcados como obsoletos</span><span class="sxs-lookup"><span data-stu-id="fefe4-101">SignalR: UseSignalR and UseConnections methods marked obsolete</span></span>

<span data-ttu-id="fefe4-102">Os `UseConnections` métodos `UseSignalR` e `ConnectionsRouteBuilder` as `HubRouteBuilder` classes são marcados como obsoletos em ASP.NET Núcleo 3.0.</span><span class="sxs-lookup"><span data-stu-id="fefe4-102">The methods `UseConnections` and `UseSignalR` and the classes `ConnectionsRouteBuilder` and `HubRouteBuilder` are marked as obsolete in ASP.NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fefe4-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="fefe4-103">Version introduced</span></span>

<span data-ttu-id="fefe4-104">3.0</span><span class="sxs-lookup"><span data-stu-id="fefe4-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="fefe4-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="fefe4-105">Old behavior</span></span>

<span data-ttu-id="fefe4-106">O roteamento do hub `UseSignalR` `UseConnections`SignalR foi configurado usando ou .</span><span class="sxs-lookup"><span data-stu-id="fefe4-106">SignalR hub routing was configured using `UseSignalR` or `UseConnections`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="fefe4-107">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="fefe4-107">New behavior</span></span>

<span data-ttu-id="fefe4-108">A maneira antiga de configurar o roteamento foi obsoleta e substituída por roteamento de ponto final.</span><span class="sxs-lookup"><span data-stu-id="fefe4-108">The old way of configuring routing has been obsoleted and replaced with endpoint routing.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fefe4-109">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="fefe4-109">Reason for change</span></span>

<span data-ttu-id="fefe4-110">O Middleware está sendo movido para o novo sistema de roteamento de ponto final.</span><span class="sxs-lookup"><span data-stu-id="fefe4-110">Middleware is being moved to the new endpoint routing system.</span></span> <span data-ttu-id="fefe4-111">A velha maneira de adicionar middleware está sendo obsoleta.</span><span class="sxs-lookup"><span data-stu-id="fefe4-111">The old way of adding middleware is being obsoleted.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fefe4-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="fefe4-112">Recommended action</span></span>

<span data-ttu-id="fefe4-113">Substituir `UseSignalR` por `UseEndpoints`:</span><span class="sxs-lookup"><span data-stu-id="fefe4-113">Replace `UseSignalR` with `UseEndpoints`:</span></span>

<span data-ttu-id="fefe4-114">**Código antigo:**</span><span class="sxs-lookup"><span data-stu-id="fefe4-114">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="fefe4-115">**Novo código:**</span><span class="sxs-lookup"><span data-stu-id="fefe4-115">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

#### <a name="category"></a><span data-ttu-id="fefe4-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="fefe4-116">Category</span></span>

<span data-ttu-id="fefe4-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fefe4-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fefe4-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fefe4-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})`
- `M:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})`
- `T:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder`
- `T:Microsoft.AspNetCore.SignalR.HubRouteBuilder`

-->
