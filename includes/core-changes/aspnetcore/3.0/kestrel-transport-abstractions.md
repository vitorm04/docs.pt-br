---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393930"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="bede6-101">Kestrel: abstrações de transporte removidas e tornadas públicas</span><span class="sxs-lookup"><span data-stu-id="bede6-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="bede6-102">Como parte da afastamento das APIs "pubternal", as APIs da camada de transporte do Kestrel são expostas como uma interface pública na biblioteca `Microsoft.AspNetCore.Connections.Abstractions`.</span><span class="sxs-lookup"><span data-stu-id="bede6-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bede6-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="bede6-103">Version introduced</span></span>

<span data-ttu-id="bede6-104">3.0</span><span class="sxs-lookup"><span data-stu-id="bede6-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="bede6-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="bede6-105">Old behavior</span></span>

- <span data-ttu-id="bede6-106">Abstrações relacionadas ao transporte estavam disponíveis na biblioteca `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions`.</span><span class="sxs-lookup"><span data-stu-id="bede6-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="bede6-107">A propriedade `ListenOptions.NoDelay` estava disponível.</span><span class="sxs-lookup"><span data-stu-id="bede6-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="bede6-108">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="bede6-108">New behavior</span></span>

- <span data-ttu-id="bede6-109">A interface `IConnectionListener` foi introduzida na biblioteca `Microsoft.AspNetCore.Connections.Abstractions` para expor a funcionalidade mais usada da biblioteca `...Transport.Abstractions`.</span><span class="sxs-lookup"><span data-stu-id="bede6-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="bede6-110">O `NoDelay` agora está disponível nas opções de transporte (`LibuvTransportOptions` e `SocketTransportOptions`).</span><span class="sxs-lookup"><span data-stu-id="bede6-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="bede6-111">`SchedulingMode` não está mais disponível.</span><span class="sxs-lookup"><span data-stu-id="bede6-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="bede6-112">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="bede6-112">Reason for change</span></span>

<span data-ttu-id="bede6-113">ASP.NET Core 3,0 foi afastado das APIs "pubternal".</span><span class="sxs-lookup"><span data-stu-id="bede6-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bede6-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="bede6-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="bede6-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="bede6-115">Category</span></span>

<span data-ttu-id="bede6-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bede6-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bede6-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="bede6-117">Affected APIs</span></span>

<span data-ttu-id="bede6-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="bede6-118">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
