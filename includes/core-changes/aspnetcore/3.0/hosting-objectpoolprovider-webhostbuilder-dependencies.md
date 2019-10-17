---
ms.openlocfilehash: 16b9fde49f513643a37f65f3e926a34fc991c55a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394316"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="df0e5-101">Hospedagem: objectpoolprovider removido de dependências WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="df0e5-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="df0e5-102">Como parte de fazer ASP.NET Core mais Pay for Play, o `ObjectPoolProvider` foi removido do conjunto principal de dependências.</span><span class="sxs-lookup"><span data-stu-id="df0e5-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="df0e5-103">Os componentes específicos que dependem de `ObjectPoolProvider` agora o adicionam.</span><span class="sxs-lookup"><span data-stu-id="df0e5-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="df0e5-104">Para obter uma discussão, consulte [ASPNET/AspNetCore # 5944](https://github.com/aspnet/AspNetCore/issues/5944).</span><span class="sxs-lookup"><span data-stu-id="df0e5-104">For discussion, see [aspnet/AspNetCore#5944](https://github.com/aspnet/AspNetCore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="df0e5-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="df0e5-105">Version introduced</span></span>

<span data-ttu-id="df0e5-106">3.0</span><span class="sxs-lookup"><span data-stu-id="df0e5-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="df0e5-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="df0e5-107">Old behavior</span></span>

<span data-ttu-id="df0e5-108">`WebHostBuilder` fornece `ObjectPoolProvider` por padrão no contêiner de DI.</span><span class="sxs-lookup"><span data-stu-id="df0e5-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="df0e5-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="df0e5-109">New behavior</span></span>

<span data-ttu-id="df0e5-110">o `WebHostBuilder` não fornece mais `ObjectPoolProvider` por padrão no contêiner de DI.</span><span class="sxs-lookup"><span data-stu-id="df0e5-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="df0e5-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="df0e5-111">Reason for change</span></span>

<span data-ttu-id="df0e5-112">Essa alteração foi feita para fazer ASP.NET Core mais Pay for Play.</span><span class="sxs-lookup"><span data-stu-id="df0e5-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="df0e5-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="df0e5-113">Recommended action</span></span>

<span data-ttu-id="df0e5-114">Se o componente exigir `ObjectPoolProvider`, ele precisará ser adicionado às suas dependências por meio do `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="df0e5-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="df0e5-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="df0e5-115">Category</span></span>

<span data-ttu-id="df0e5-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="df0e5-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="df0e5-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="df0e5-117">Affected APIs</span></span>

<span data-ttu-id="df0e5-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="df0e5-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
