---
ms.openlocfilehash: 6be98e7ced6608ba0793c635adfe61c8b1a7e9d9
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275265"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="3f555-101">SignalR: Os construtores do HubConnectionContext mudaram</span><span class="sxs-lookup"><span data-stu-id="3f555-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="3f555-102">Os construtores `HubConnectionContext` do SignalR mudaram para aceitar um tipo de opções, em vez de vários parâmetros, para opções de adição à prova de futuro.</span><span class="sxs-lookup"><span data-stu-id="3f555-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="3f555-103">Esta mudança substitui dois construtores por um único construtor que aceita um tipo de opções.</span><span class="sxs-lookup"><span data-stu-id="3f555-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3f555-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="3f555-104">Version introduced</span></span>

<span data-ttu-id="3f555-105">3.0</span><span class="sxs-lookup"><span data-stu-id="3f555-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3f555-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="3f555-106">Old behavior</span></span>

<span data-ttu-id="3f555-107">`HubConnectionContext`tem dois construtores:</span><span class="sxs-lookup"><span data-stu-id="3f555-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="3f555-108">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="3f555-108">New behavior</span></span>

<span data-ttu-id="3f555-109">Os dois construtores foram removidos e substituídos por um construtor:</span><span class="sxs-lookup"><span data-stu-id="3f555-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="3f555-110">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="3f555-110">Reason for change</span></span>

<span data-ttu-id="3f555-111">O novo construtor usa um novo objeto de opções.</span><span class="sxs-lookup"><span data-stu-id="3f555-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="3f555-112">Consequentemente, as `HubConnectionContext` características podem ser expandidas no futuro sem fazer mais construtores e quebrar mudanças.</span><span class="sxs-lookup"><span data-stu-id="3f555-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3f555-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="3f555-113">Recommended action</span></span>

<span data-ttu-id="3f555-114">Em vez de usar o seguinte construtor:</span><span class="sxs-lookup"><span data-stu-id="3f555-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext,
    keepAliveInterval: TimeSpan.FromSeconds(15),
    loggerFactory,
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="3f555-115">Use o seguinte construtor:</span><span class="sxs-lookup"><span data-stu-id="3f555-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="3f555-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="3f555-116">Category</span></span>

<span data-ttu-id="3f555-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3f555-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3f555-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="3f555-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
