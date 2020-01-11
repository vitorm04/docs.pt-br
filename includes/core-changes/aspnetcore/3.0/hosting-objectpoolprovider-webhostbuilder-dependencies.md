---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901587"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="1f37c-101">Hospedagem: objectpoolprovider removido de dependências WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="1f37c-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="1f37c-102">Como parte de fazer ASP.NET Core mais Pay for Play, o `ObjectPoolProvider` foi removido do conjunto principal de dependências.</span><span class="sxs-lookup"><span data-stu-id="1f37c-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="1f37c-103">Os componentes específicos que dependem de `ObjectPoolProvider` agora o adicionam.</span><span class="sxs-lookup"><span data-stu-id="1f37c-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="1f37c-104">Para obter uma discussão, consulte [dotnet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944).</span><span class="sxs-lookup"><span data-stu-id="1f37c-104">For discussion, see [dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1f37c-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="1f37c-105">Version introduced</span></span>

<span data-ttu-id="1f37c-106">3.0</span><span class="sxs-lookup"><span data-stu-id="1f37c-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1f37c-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="1f37c-107">Old behavior</span></span>

<span data-ttu-id="1f37c-108">`WebHostBuilder` fornece `ObjectPoolProvider` por padrão no contêiner DI.</span><span class="sxs-lookup"><span data-stu-id="1f37c-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1f37c-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="1f37c-109">New behavior</span></span>

<span data-ttu-id="1f37c-110">`WebHostBuilder` não fornece mais `ObjectPoolProvider` por padrão no contêiner DI.</span><span class="sxs-lookup"><span data-stu-id="1f37c-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1f37c-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="1f37c-111">Reason for change</span></span>

<span data-ttu-id="1f37c-112">Essa alteração foi feita para fazer ASP.NET Core mais Pay for Play.</span><span class="sxs-lookup"><span data-stu-id="1f37c-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1f37c-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="1f37c-113">Recommended action</span></span>

<span data-ttu-id="1f37c-114">Se seu componente exigir `ObjectPoolProvider`, ele precisará ser adicionado às suas dependências por meio do `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="1f37c-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="1f37c-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="1f37c-115">Category</span></span>

<span data-ttu-id="1f37c-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1f37c-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1f37c-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1f37c-117">Affected APIs</span></span>

<span data-ttu-id="1f37c-118">{1&gt;Nenhum&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1f37c-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
