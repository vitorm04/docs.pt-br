---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901824"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="25938-101">Kestrel: adaptadores de conexão removidos</span><span class="sxs-lookup"><span data-stu-id="25938-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="25938-102">Como parte da mudança para mover APIs "pubternal" para `public` o, o conceito de um `IConnectionAdapter` foi removido de Kestrel.</span><span class="sxs-lookup"><span data-stu-id="25938-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="25938-103">Os adaptadores de conexão estão sendo substituídos pelo middleware de conexão (semelhante ao middleware HTTP no pipeline de ASP.NET Core, mas para conexões de nível inferior).</span><span class="sxs-lookup"><span data-stu-id="25938-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="25938-104">O log de conexão e HTTPS foi movido dos adaptadores de conexão para o middleware de conexão.</span><span class="sxs-lookup"><span data-stu-id="25938-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="25938-105">Esses métodos de extensão devem continuar funcionando sem problemas, mas os detalhes da implementação foram alterados.</span><span class="sxs-lookup"><span data-stu-id="25938-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="25938-106">Para obter mais informações, consulte [dotnet/aspnetcore # 11412](https://github.com/dotnet/aspnetcore/pull/11412).</span><span class="sxs-lookup"><span data-stu-id="25938-106">For more information, see [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412).</span></span> <span data-ttu-id="25938-107">Para obter uma discussão, consulte [dotnet/aspnetcore # 11475](https://github.com/dotnet/aspnetcore/issues/11475).</span><span class="sxs-lookup"><span data-stu-id="25938-107">For discussion, see [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="25938-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="25938-108">Version introduced</span></span>

<span data-ttu-id="25938-109">3,0</span><span class="sxs-lookup"><span data-stu-id="25938-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="25938-110">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="25938-110">Old behavior</span></span>

<span data-ttu-id="25938-111">Os componentes de extensibilidade do Kestrel foram criados usando o `IConnectionAdapter` .</span><span class="sxs-lookup"><span data-stu-id="25938-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="25938-112">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="25938-112">New behavior</span></span>

<span data-ttu-id="25938-113">Os componentes de extensibilidade do Kestrel são criados como [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="25938-113">Kestrel extensibility components are created as [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="25938-114">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="25938-114">Reason for change</span></span>

<span data-ttu-id="25938-115">Essa alteração destina-se a fornecer uma arquitetura de extensibilidade mais flexível.</span><span class="sxs-lookup"><span data-stu-id="25938-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="25938-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="25938-116">Recommended action</span></span>

<span data-ttu-id="25938-117">Converta todas as implementações do `IConnectionAdapter` para usar o novo padrão de middleware, conforme mostrado [aqui](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="25938-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="25938-118">Categoria</span><span class="sxs-lookup"><span data-stu-id="25938-118">Category</span></span>

<span data-ttu-id="25938-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="25938-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="25938-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="25938-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
