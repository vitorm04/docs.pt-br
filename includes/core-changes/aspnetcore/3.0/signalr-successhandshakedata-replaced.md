---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901722"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="78f9f-101">SignalR: HandshakeProtocol.SuccessHandshakeData substituído</span><span class="sxs-lookup"><span data-stu-id="78f9f-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="78f9f-102">O campo [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) foi removido e substituído por um método auxiliar `IHubProtocol`que gera uma resposta de aperto de mão bem sucedida dada uma resposta específica .</span><span class="sxs-lookup"><span data-stu-id="78f9f-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="78f9f-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="78f9f-103">Version introduced</span></span>

<span data-ttu-id="78f9f-104">3.0</span><span class="sxs-lookup"><span data-stu-id="78f9f-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="78f9f-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="78f9f-105">Old behavior</span></span>

<span data-ttu-id="78f9f-106">`HandshakeProtocol.SuccessHandshakeData`era `public static ReadOnlyMemory<byte>` um campo.</span><span class="sxs-lookup"><span data-stu-id="78f9f-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="78f9f-107">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="78f9f-107">New behavior</span></span>

<span data-ttu-id="78f9f-108">`HandshakeProtocol.SuccessHandshakeData`foi substituído por `static` `GetSuccessfulHandshake(IHubProtocol protocol)` um método `ReadOnlyMemory<byte>` que retorna um com base no protocolo especificado.</span><span class="sxs-lookup"><span data-stu-id="78f9f-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="78f9f-109">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="78f9f-109">Reason for change</span></span>

<span data-ttu-id="78f9f-110">Campos adicionais foram adicionados à _resposta_ de aperto de mão que não são constantes e mudam dependendo do protocolo selecionado.</span><span class="sxs-lookup"><span data-stu-id="78f9f-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="78f9f-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="78f9f-111">Recommended action</span></span>

<span data-ttu-id="78f9f-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="78f9f-112">None.</span></span> <span data-ttu-id="78f9f-113">Este tipo não foi projetado para ser usado a partir do código do usuário.</span><span class="sxs-lookup"><span data-stu-id="78f9f-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="78f9f-114">É `public`, para que possa ser compartilhado entre o servidor SignalR e o cliente.</span><span class="sxs-lookup"><span data-stu-id="78f9f-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="78f9f-115">Também pode ser usado por clientes SignalR gravados em .NET.</span><span class="sxs-lookup"><span data-stu-id="78f9f-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="78f9f-116">**Os usuários** do SignalR não devem ser afetados por essa mudança.</span><span class="sxs-lookup"><span data-stu-id="78f9f-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="78f9f-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="78f9f-117">Category</span></span>

<span data-ttu-id="78f9f-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="78f9f-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="78f9f-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="78f9f-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
