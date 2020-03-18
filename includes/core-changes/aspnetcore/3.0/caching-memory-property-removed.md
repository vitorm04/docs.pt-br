---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901775"
---
### <a name="caching-compactonmemorypressure-property-removed"></a><span data-ttu-id="2b3f0-101">Cache: CompactOnMemoryPressure propriedade removido</span><span class="sxs-lookup"><span data-stu-id="2b3f0-101">Caching: CompactOnMemoryPressure property removed</span></span>

<span data-ttu-id="2b3f0-102">A versão ASP.NET Core 3.0 removeu as [APIs obsoletas MemoryCacheOptions](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span><span class="sxs-lookup"><span data-stu-id="2b3f0-102">The ASP.NET Core 3.0 release removed the [obsolete MemoryCacheOptions APIs](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span></span>

#### <a name="change-description"></a><span data-ttu-id="2b3f0-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="2b3f0-103">Change description</span></span>

<span data-ttu-id="2b3f0-104">Esta mudança é um acompanhamento para [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span><span class="sxs-lookup"><span data-stu-id="2b3f0-104">This change is a follow-up to [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span></span> <span data-ttu-id="2b3f0-105">Para discussão, consulte [dotnet/extensões#1062](https://github.com/dotnet/extensions/issues/1062).</span><span class="sxs-lookup"><span data-stu-id="2b3f0-105">For discussion, see [dotnet/extensions#1062](https://github.com/dotnet/extensions/issues/1062).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2b3f0-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="2b3f0-106">Version introduced</span></span>

<span data-ttu-id="2b3f0-107">3.0</span><span class="sxs-lookup"><span data-stu-id="2b3f0-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2b3f0-108">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="2b3f0-108">Old behavior</span></span>

<span data-ttu-id="2b3f0-109">`MemoryCacheOptions.CompactOnMemoryPressure`propriedade estava disponível.</span><span class="sxs-lookup"><span data-stu-id="2b3f0-109">`MemoryCacheOptions.CompactOnMemoryPressure` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2b3f0-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="2b3f0-110">New behavior</span></span>

<span data-ttu-id="2b3f0-111">A `MemoryCacheOptions.CompactOnMemoryPressure` propriedade foi removida.</span><span class="sxs-lookup"><span data-stu-id="2b3f0-111">The `MemoryCacheOptions.CompactOnMemoryPressure` property has been removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2b3f0-112">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="2b3f0-112">Reason for change</span></span>

<span data-ttu-id="2b3f0-113">Compactar automaticamente o cache causou problemas.</span><span class="sxs-lookup"><span data-stu-id="2b3f0-113">Automatically compacting the cache caused problems.</span></span> <span data-ttu-id="2b3f0-114">Para evitar comportamentos inesperados, o cache só deve ser compactado quando necessário.</span><span class="sxs-lookup"><span data-stu-id="2b3f0-114">To avoid unexpected behavior, the cache should only be compacted when needed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2b3f0-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="2b3f0-115">Recommended action</span></span>

<span data-ttu-id="2b3f0-116">Para compactar o cache, abaixado `MemoryCache` e ligar `Compact` quando necessário.</span><span class="sxs-lookup"><span data-stu-id="2b3f0-116">To compact the cache, downcast to `MemoryCache` and call `Compact` when needed.</span></span>

#### <a name="category"></a><span data-ttu-id="2b3f0-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="2b3f0-117">Category</span></span>

<span data-ttu-id="2b3f0-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2b3f0-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2b3f0-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2b3f0-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
