---
ms.openlocfilehash: fb23418816abcae125106c93b339a546aa9bc2ee
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721168"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="766ef-101">Kestrel: abstrações de transporte removidas e tornadas públicas</span><span class="sxs-lookup"><span data-stu-id="766ef-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="766ef-102">Como parte da afastamento das APIs "pubternal", as APIs da camada de transporte do Kestrel são expostas como uma interface pública na `Microsoft.AspNetCore.Connections.Abstractions` biblioteca.</span><span class="sxs-lookup"><span data-stu-id="766ef-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="766ef-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="766ef-103">Version introduced</span></span>

<span data-ttu-id="766ef-104">3.0</span><span class="sxs-lookup"><span data-stu-id="766ef-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="766ef-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="766ef-105">Old behavior</span></span>

- <span data-ttu-id="766ef-106">Abstrações relacionadas ao transporte estavam disponíveis na `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` biblioteca.</span><span class="sxs-lookup"><span data-stu-id="766ef-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="766ef-107">A `ListenOptions.NoDelay` Propriedade estava disponível.</span><span class="sxs-lookup"><span data-stu-id="766ef-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="766ef-108">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="766ef-108">New behavior</span></span>

- <span data-ttu-id="766ef-109">A `IConnectionListener` interface foi introduzida na `Microsoft.AspNetCore.Connections.Abstractions` biblioteca para expor a funcionalidade mais usada da `...Transport.Abstractions` biblioteca.</span><span class="sxs-lookup"><span data-stu-id="766ef-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="766ef-110">O `NoDelay` agora está disponível em opções de transporte ( `LibuvTransportOptions` e `SocketTransportOptions` ).</span><span class="sxs-lookup"><span data-stu-id="766ef-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="766ef-111">`SchedulingMode`Não está mais disponível.</span><span class="sxs-lookup"><span data-stu-id="766ef-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="766ef-112">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="766ef-112">Reason for change</span></span>

<span data-ttu-id="766ef-113">ASP.NET Core 3,0 foi afastado das APIs "pubternal".</span><span class="sxs-lookup"><span data-stu-id="766ef-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="766ef-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="766ef-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="766ef-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="766ef-115">Category</span></span>

<span data-ttu-id="766ef-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="766ef-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="766ef-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="766ef-117">Affected APIs</span></span>

<span data-ttu-id="766ef-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="766ef-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
