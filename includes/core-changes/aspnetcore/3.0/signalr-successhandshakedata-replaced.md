---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901722"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="812f5-101">Signalr: HandshakeProtocol. SuccessHandshakeData substituído</span><span class="sxs-lookup"><span data-stu-id="812f5-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="812f5-102">O campo [HandshakeProtocol. SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) foi removido e substituído por um método auxiliar que gera uma resposta de handshake bem-sucedida devido a um `IHubProtocol`específico.</span><span class="sxs-lookup"><span data-stu-id="812f5-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="812f5-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="812f5-103">Version introduced</span></span>

<span data-ttu-id="812f5-104">3.0</span><span class="sxs-lookup"><span data-stu-id="812f5-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="812f5-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="812f5-105">Old behavior</span></span>

<span data-ttu-id="812f5-106">`HandshakeProtocol.SuccessHandshakeData` foi um campo de `public static ReadOnlyMemory<byte>`.</span><span class="sxs-lookup"><span data-stu-id="812f5-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="812f5-107">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="812f5-107">New behavior</span></span>

<span data-ttu-id="812f5-108">`HandshakeProtocol.SuccessHandshakeData` foi substituído por um método de `GetSuccessfulHandshake(IHubProtocol protocol)` de `static` que retorna uma `ReadOnlyMemory<byte>` com base no protocolo especificado.</span><span class="sxs-lookup"><span data-stu-id="812f5-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="812f5-109">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="812f5-109">Reason for change</span></span>

<span data-ttu-id="812f5-110">Campos adicionais foram adicionados à _resposta_ de handshake que são não constantes e mudam dependendo do protocolo selecionado.</span><span class="sxs-lookup"><span data-stu-id="812f5-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="812f5-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="812f5-111">Recommended action</span></span>

<span data-ttu-id="812f5-112">Nenhuma.</span><span class="sxs-lookup"><span data-stu-id="812f5-112">None.</span></span> <span data-ttu-id="812f5-113">Esse tipo não é projetado para uso do código do usuário.</span><span class="sxs-lookup"><span data-stu-id="812f5-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="812f5-114">É `public`, portanto, pode ser compartilhado entre o servidor e o cliente do Signalr.</span><span class="sxs-lookup"><span data-stu-id="812f5-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="812f5-115">Ele também pode ser usado por clientes do Signalr do cliente escritos em .NET.</span><span class="sxs-lookup"><span data-stu-id="812f5-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="812f5-116">**Os usuários** do signalr não devem ser afetados por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="812f5-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="812f5-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="812f5-117">Category</span></span>

<span data-ttu-id="812f5-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="812f5-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="812f5-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="812f5-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
