---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901666"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a><span data-ttu-id="e1dfa-101">Signalr: métodos HubConnection ResetSendPing e ResetTimeout removidos</span><span class="sxs-lookup"><span data-stu-id="e1dfa-101">SignalR: HubConnection ResetSendPing and ResetTimeout methods removed</span></span>

<span data-ttu-id="e1dfa-102">Os `ResetSendPing` `ResetTimeout` métodos e foram removidos da API do signalr `HubConnection` .</span><span class="sxs-lookup"><span data-stu-id="e1dfa-102">The `ResetSendPing` and `ResetTimeout` methods were removed from the SignalR `HubConnection` API.</span></span> <span data-ttu-id="e1dfa-103">Esses métodos eram originalmente destinados apenas ao uso interno, mas foram disponibilizados para o público em ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e1dfa-103">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span> <span data-ttu-id="e1dfa-104">Esses métodos não estarão disponíveis a partir da versão ASP.NET Core 3,0 Preview 4.</span><span class="sxs-lookup"><span data-stu-id="e1dfa-104">These methods won't be available starting in the ASP.NET Core 3.0 Preview 4 release.</span></span> <span data-ttu-id="e1dfa-105">Para obter uma discussão, consulte [dotnet/aspnetcore # 8543](https://github.com/dotnet/aspnetcore/issues/8543).</span><span class="sxs-lookup"><span data-stu-id="e1dfa-105">For discussion, see [dotnet/aspnetcore#8543](https://github.com/dotnet/aspnetcore/issues/8543).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e1dfa-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="e1dfa-106">Version introduced</span></span>

<span data-ttu-id="e1dfa-107">3,0</span><span class="sxs-lookup"><span data-stu-id="e1dfa-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e1dfa-108">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="e1dfa-108">Old behavior</span></span>

<span data-ttu-id="e1dfa-109">APIs estavam disponíveis.</span><span class="sxs-lookup"><span data-stu-id="e1dfa-109">APIs were available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e1dfa-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="e1dfa-110">New behavior</span></span>

<span data-ttu-id="e1dfa-111">As APIs são removidas.</span><span class="sxs-lookup"><span data-stu-id="e1dfa-111">APIs are removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e1dfa-112">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="e1dfa-112">Reason for change</span></span>

<span data-ttu-id="e1dfa-113">Esses métodos eram originalmente destinados apenas ao uso interno, mas foram disponibilizados para o público em ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="e1dfa-113">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e1dfa-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="e1dfa-114">Recommended action</span></span>

<span data-ttu-id="e1dfa-115">Não use esses métodos.</span><span class="sxs-lookup"><span data-stu-id="e1dfa-115">Don't use these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="e1dfa-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="e1dfa-116">Category</span></span>

<span data-ttu-id="e1dfa-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e1dfa-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e1dfa-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e1dfa-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
