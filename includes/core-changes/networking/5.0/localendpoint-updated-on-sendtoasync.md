---
ms.openlocfilehash: 8de70b0c445aa48fc4c3249ccfc8c095890fb14c
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050503"
---
### <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a><span data-ttu-id="52c2b-101">Socket. LocalEndPoint é atualizado após chamar SendToAsync</span><span class="sxs-lookup"><span data-stu-id="52c2b-101">Socket.LocalEndPoint is updated after calling SendToAsync</span></span>

<span data-ttu-id="52c2b-102"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> Agora atualiza o valor da <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> propriedade para o endereço local do soquete.</span><span class="sxs-lookup"><span data-stu-id="52c2b-102"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> now updates the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property to the socket's local address.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="52c2b-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="52c2b-103">Version introduced</span></span>

<span data-ttu-id="52c2b-104">RC1 5,0</span><span class="sxs-lookup"><span data-stu-id="52c2b-104">5.0 RC1</span></span>

#### <a name="change-description"></a><span data-ttu-id="52c2b-105">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="52c2b-105">Change description</span></span>

<span data-ttu-id="52c2b-106">Nas versões anteriores do .NET, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> o não altera o valor da <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> Propriedade na instância de soquete.</span><span class="sxs-lookup"><span data-stu-id="52c2b-106">In previous .NET versions, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> does not alter the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property on the socket instance.</span></span> <span data-ttu-id="52c2b-107">A partir do .NET 5,0, quando é <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> concluído com êxito, o valor de <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> é o endereço local do soquete implicitamente ligado.</span><span class="sxs-lookup"><span data-stu-id="52c2b-107">Starting in .NET 5.0, when <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> successfully completes, the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> is the implicitly bound socket's local address.</span></span> <span data-ttu-id="52c2b-108">Esse novo comportamento é consistente com o comportamento de <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> e <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)> / <xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)> .</span><span class="sxs-lookup"><span data-stu-id="52c2b-108">This new behavior is consistent with the behavior of <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> and <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)>/<xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="52c2b-109">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="52c2b-109">Reason for change</span></span>

<span data-ttu-id="52c2b-110">Essa alteração [corrige um bug](https://github.com/dotnet/runtime/issues/915) e torna o comportamento consistente entre `SendTo` variantes.</span><span class="sxs-lookup"><span data-stu-id="52c2b-110">This change [fixes a bug](https://github.com/dotnet/runtime/issues/915) and makes the behavior consistent across `SendTo` variants.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="52c2b-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="52c2b-111">Recommended action</span></span>

<span data-ttu-id="52c2b-112">Altere qualquer código que assuma que <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> não alterará o valor de <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="52c2b-112">Alter any code that assumes that <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> won't alter the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="52c2b-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="52c2b-113">Category</span></span>

<span data-ttu-id="52c2b-114">Rede</span><span class="sxs-lookup"><span data-stu-id="52c2b-114">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="52c2b-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="52c2b-115">Affected APIs</span></span>

- <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)`

-->
