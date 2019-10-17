---
ms.openlocfilehash: 8cc2e1436059f92564d4c3ec534632674081ae75
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394452"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="ebbcf-101">Signalr: construtores HubConnectionContext alterados</span><span class="sxs-lookup"><span data-stu-id="ebbcf-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="ebbcf-102">Os construtores `HubConnectionContext` do signalr foram alterados para aceitar um tipo de opções, em vez de vários parâmetros, para a adição de opções à prova de futuro.</span><span class="sxs-lookup"><span data-stu-id="ebbcf-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="ebbcf-103">Essa alteração substitui dois construtores por um único Construtor que aceita um tipo de opções.</span><span class="sxs-lookup"><span data-stu-id="ebbcf-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ebbcf-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ebbcf-104">Version introduced</span></span>

<span data-ttu-id="ebbcf-105">3.0</span><span class="sxs-lookup"><span data-stu-id="ebbcf-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ebbcf-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="ebbcf-106">Old behavior</span></span>

<span data-ttu-id="ebbcf-107">`HubConnectionContext` tem dois construtores:</span><span class="sxs-lookup"><span data-stu-id="ebbcf-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="ebbcf-108">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="ebbcf-108">New behavior</span></span>

<span data-ttu-id="ebbcf-109">Os dois construtores foram removidos e substituídos por um construtor:</span><span class="sxs-lookup"><span data-stu-id="ebbcf-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="ebbcf-110">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="ebbcf-110">Reason for change</span></span>

<span data-ttu-id="ebbcf-111">O novo construtor usa um novo objeto Options.</span><span class="sxs-lookup"><span data-stu-id="ebbcf-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="ebbcf-112">Consequentemente, os recursos de `HubConnectionContext` podem ser expandidos no futuro sem fazer mais construtores e alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="ebbcf-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ebbcf-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ebbcf-113">Recommended action</span></span>

<span data-ttu-id="ebbcf-114">Em vez de usar o Construtor a seguir:</span><span class="sxs-lookup"><span data-stu-id="ebbcf-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext, 
    keepAliveInterval: TimeSpan.FromSeconds(15), 
    loggerFactory, 
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="ebbcf-115">Use o seguinte construtor:</span><span class="sxs-lookup"><span data-stu-id="ebbcf-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="ebbcf-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="ebbcf-116">Category</span></span>

<span data-ttu-id="ebbcf-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ebbcf-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ebbcf-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ebbcf-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
