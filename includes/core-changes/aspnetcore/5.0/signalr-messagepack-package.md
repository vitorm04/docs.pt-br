---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345211"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a><span data-ttu-id="699bc-101">SignalR: MessagePack Hub Protocol mudou para o pacote MessagePack 2.x</span><span class="sxs-lookup"><span data-stu-id="699bc-101">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>

<span data-ttu-id="699bc-102">O [protocolo](/aspnet/core/signalr/messagepackhubprotocol) do Hub Do SignalR do ASP.NET usa o [pacote MessagePack NuGet](https://www.nuget.org/packages/MessagePack) para serialização messagePack.</span><span class="sxs-lookup"><span data-stu-id="699bc-102">The ASP.NET Core SignalR [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) uses the [MessagePack NuGet package](https://www.nuget.org/packages/MessagePack) for MessagePack serialization.</span></span> <span data-ttu-id="699bc-103">ASP.NET Core 5.0 atualiza o pacote de 1.x para a versão mais recente do pacote 2.x.</span><span class="sxs-lookup"><span data-stu-id="699bc-103">ASP.NET Core 5.0 upgrades the package from 1.x to the latest 2.x package version.</span></span>

<span data-ttu-id="699bc-104">Para discussão sobre este assunto, consulte [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span><span class="sxs-lookup"><span data-stu-id="699bc-104">For discussion on this issue, see [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="699bc-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="699bc-105">Version introduced</span></span>

<span data-ttu-id="699bc-106">5.0 Visualização 1</span><span class="sxs-lookup"><span data-stu-id="699bc-106">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="699bc-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="699bc-107">Old behavior</span></span>

<span data-ttu-id="699bc-108">ASP.NET Core SignalR usou o pacote MessagePack 1.x para serializar e desserializar mensagens messagePack.</span><span class="sxs-lookup"><span data-stu-id="699bc-108">ASP.NET Core SignalR used the MessagePack 1.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="699bc-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="699bc-109">New behavior</span></span>

<span data-ttu-id="699bc-110">ASP.NET Core SignalR usa o pacote MessagePack 2.x para serializar e desserializar mensagens messagePack.</span><span class="sxs-lookup"><span data-stu-id="699bc-110">ASP.NET Core SignalR uses the MessagePack 2.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="699bc-111">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="699bc-111">Reason for change</span></span>

<span data-ttu-id="699bc-112">As melhorias mais recentes no pacote MessagePack 2.x adicionam funcionalidade útil.</span><span class="sxs-lookup"><span data-stu-id="699bc-112">The latest improvements in the MessagePack 2.x package add useful functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="699bc-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="699bc-113">Recommended action</span></span>

<span data-ttu-id="699bc-114">Esta mudança de quebra se aplica quando:</span><span class="sxs-lookup"><span data-stu-id="699bc-114">This breaking change applies when:</span></span>

* <span data-ttu-id="699bc-115">Configuração ou configuração de valores em <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span><span class="sxs-lookup"><span data-stu-id="699bc-115">Setting or configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span>
* <span data-ttu-id="699bc-116">Usando as APIs messagePack diretamente e usando o protocolo do Hub do SignalR Do ASP.NET no mesmo projeto.</span><span class="sxs-lookup"><span data-stu-id="699bc-116">Using the MessagePack APIs directly and using the ASP.NET Core SignalR MessagePack Hub Protocol in the same project.</span></span> <span data-ttu-id="699bc-117">A versão mais recente será carregada em vez da versão anterior.</span><span class="sxs-lookup"><span data-stu-id="699bc-117">The newer version will be loaded instead of the previous version.</span></span>

<span data-ttu-id="699bc-118">Para obter orientação de migração dos autores do pacote, consulte [Migrando de MessagePack v1.x para MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span><span class="sxs-lookup"><span data-stu-id="699bc-118">For migration guidance from the package authors, see [Migrating from MessagePack v1.x to MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span></span> <span data-ttu-id="699bc-119">Alguns aspectos da serialização e desserialização das mensagens são afetados.</span><span class="sxs-lookup"><span data-stu-id="699bc-119">Some aspects of message serialization and deserialization are affected.</span></span> <span data-ttu-id="699bc-120">Especificamente, há [mudanças comportamentais na forma como os valores do DateTime são serializados](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span><span class="sxs-lookup"><span data-stu-id="699bc-120">Specifically, there are [behavioral changes to how DateTime values are serialized](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span></span>

#### <a name="category"></a><span data-ttu-id="699bc-121">Categoria</span><span class="sxs-lookup"><span data-stu-id="699bc-121">Category</span></span>

<span data-ttu-id="699bc-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="699bc-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="699bc-123">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="699bc-123">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
