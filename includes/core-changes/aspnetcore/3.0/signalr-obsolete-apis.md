---
ms.openlocfilehash: 2a65caedea2af65796267aa145e275ebff814bf8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393916"
---
### <a name="signalr-usesignalr-and-useconnections-methods-marked-obsolete"></a><span data-ttu-id="26da1-101">Signalr: métodos UseSignalR e UseConnections marcados como obsoletos</span><span class="sxs-lookup"><span data-stu-id="26da1-101">SignalR: UseSignalR and UseConnections methods marked obsolete</span></span>

<span data-ttu-id="26da1-102">Os métodos `UseConnections` e `UseSignalR` e as classes `ConnectionsRouteBuilder` e `HubRouteBuilder` são marcados como obsoletos no ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="26da1-102">The methods `UseConnections` and `UseSignalR` and the classes `ConnectionsRouteBuilder` and `HubRouteBuilder` are marked as obsolete in ASP.NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="26da1-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="26da1-103">Version introduced</span></span>

<span data-ttu-id="26da1-104">3.0</span><span class="sxs-lookup"><span data-stu-id="26da1-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="26da1-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="26da1-105">Old behavior</span></span>

<span data-ttu-id="26da1-106">O roteamento de Hub do signalr foi configurado usando `UseSignalR` ou `UseConnections`.</span><span class="sxs-lookup"><span data-stu-id="26da1-106">SignalR hub routing was configured using `UseSignalR` or `UseConnections`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="26da1-107">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="26da1-107">New behavior</span></span>

<span data-ttu-id="26da1-108">A maneira antiga de configurar o roteamento foi obsoleta e substituída pelo roteamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="26da1-108">The old way of configuring routing has been obsoleted and replaced with endpoint routing.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="26da1-109">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="26da1-109">Reason for change</span></span>

<span data-ttu-id="26da1-110">O middleware está sendo movido para o novo sistema de roteamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="26da1-110">Middleware is being moved to the new endpoint routing system.</span></span> <span data-ttu-id="26da1-111">A maneira antiga de adicionar o middleware está sendo obsoleta.</span><span class="sxs-lookup"><span data-stu-id="26da1-111">The old way of adding middleware is being obsoleted.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="26da1-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="26da1-112">Recommended action</span></span>

<span data-ttu-id="26da1-113">Substituir `UseSignalR` por `UseEndpoints`:</span><span class="sxs-lookup"><span data-stu-id="26da1-113">Replace `UseSignalR` with `UseEndpoints`:</span></span>

<span data-ttu-id="26da1-114">**Código antigo:**</span><span class="sxs-lookup"><span data-stu-id="26da1-114">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="26da1-115">**Novo código:**</span><span class="sxs-lookup"><span data-stu-id="26da1-115">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

#### <a name="category"></a><span data-ttu-id="26da1-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="26da1-116">Category</span></span>

<span data-ttu-id="26da1-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="26da1-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="26da1-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="26da1-118">Affected APIs</span></span>

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
