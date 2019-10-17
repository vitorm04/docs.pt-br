---
ms.openlocfilehash: 7d40324e6b0bc4afab9dd39b236f0909f360cc9b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394275"
---
### <a name="caching-compactonmemorypressure-property-removed"></a><span data-ttu-id="7b583-101">Caching: Propriedade CompactOnMemoryPressure removida</span><span class="sxs-lookup"><span data-stu-id="7b583-101">Caching: CompactOnMemoryPressure property removed</span></span>

<span data-ttu-id="7b583-102">A versão ASP.NET Core 3,0 removeu as [APIs MemoryCacheOptions obsoletas](https://github.com/aspnet/Extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span><span class="sxs-lookup"><span data-stu-id="7b583-102">The ASP.NET Core 3.0 release removed the [obsolete MemoryCacheOptions APIs](https://github.com/aspnet/Extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span></span>

#### <a name="change-description"></a><span data-ttu-id="7b583-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="7b583-103">Change description</span></span>

<span data-ttu-id="7b583-104">Essa alteração é um acompanhamento do [ASPNET/Caching # 221](https://github.com/aspnet/Caching/issues/221).</span><span class="sxs-lookup"><span data-stu-id="7b583-104">This change is a follow-up to [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span></span> <span data-ttu-id="7b583-105">Para obter uma discussão, consulte [ASPNET/Extensions # 1062](https://github.com/aspnet/Extensions/issues/1062).</span><span class="sxs-lookup"><span data-stu-id="7b583-105">For discussion, see [aspnet/Extensions#1062](https://github.com/aspnet/Extensions/issues/1062).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7b583-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7b583-106">Version introduced</span></span>

<span data-ttu-id="7b583-107">3.0</span><span class="sxs-lookup"><span data-stu-id="7b583-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7b583-108">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="7b583-108">Old behavior</span></span>

<span data-ttu-id="7b583-109">a propriedade `MemoryCacheOptions.CompactOnMemoryPressure` estava disponível.</span><span class="sxs-lookup"><span data-stu-id="7b583-109">`MemoryCacheOptions.CompactOnMemoryPressure` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7b583-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="7b583-110">New behavior</span></span>

<span data-ttu-id="7b583-111">A propriedade `MemoryCacheOptions.CompactOnMemoryPressure` foi removida.</span><span class="sxs-lookup"><span data-stu-id="7b583-111">The `MemoryCacheOptions.CompactOnMemoryPressure` property has been removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7b583-112">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="7b583-112">Reason for change</span></span>

<span data-ttu-id="7b583-113">A compactação automática do cache causou problemas.</span><span class="sxs-lookup"><span data-stu-id="7b583-113">Automatically compacting the cache caused problems.</span></span> <span data-ttu-id="7b583-114">Para evitar um comportamento inesperado, o cache só deve ser compactado quando necessário.</span><span class="sxs-lookup"><span data-stu-id="7b583-114">To avoid unexpected behavior, the cache should only be compacted when needed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7b583-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="7b583-115">Recommended action</span></span>

<span data-ttu-id="7b583-116">Para compactar o cache, downcast para `MemoryCache` e chamar `Compact` quando necessário.</span><span class="sxs-lookup"><span data-stu-id="7b583-116">To compact the cache, downcast to `MemoryCache` and call `Compact` when needed.</span></span>

#### <a name="category"></a><span data-ttu-id="7b583-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="7b583-117">Category</span></span>

<span data-ttu-id="7b583-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7b583-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7b583-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="7b583-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
