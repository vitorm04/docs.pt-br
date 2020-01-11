---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901775"
---
### <a name="caching-compactonmemorypressure-property-removed"></a><span data-ttu-id="05447-101">Caching: Propriedade CompactOnMemoryPressure removida</span><span class="sxs-lookup"><span data-stu-id="05447-101">Caching: CompactOnMemoryPressure property removed</span></span>

<span data-ttu-id="05447-102">A versão ASP.NET Core 3,0 removeu as [APIs MemoryCacheOptions obsoletas](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span><span class="sxs-lookup"><span data-stu-id="05447-102">The ASP.NET Core 3.0 release removed the [obsolete MemoryCacheOptions APIs](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span></span>

#### <a name="change-description"></a><span data-ttu-id="05447-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="05447-103">Change description</span></span>

<span data-ttu-id="05447-104">Essa alteração é um acompanhamento do [ASPNET/Caching # 221](https://github.com/aspnet/Caching/issues/221).</span><span class="sxs-lookup"><span data-stu-id="05447-104">This change is a follow-up to [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span></span> <span data-ttu-id="05447-105">Para obter uma discussão, consulte [dotnet/Extensions # 1062](https://github.com/dotnet/extensions/issues/1062).</span><span class="sxs-lookup"><span data-stu-id="05447-105">For discussion, see [dotnet/extensions#1062](https://github.com/dotnet/extensions/issues/1062).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="05447-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="05447-106">Version introduced</span></span>

<span data-ttu-id="05447-107">3.0</span><span class="sxs-lookup"><span data-stu-id="05447-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="05447-108">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="05447-108">Old behavior</span></span>

<span data-ttu-id="05447-109">`MemoryCacheOptions.CompactOnMemoryPressure` Propriedade estava disponível.</span><span class="sxs-lookup"><span data-stu-id="05447-109">`MemoryCacheOptions.CompactOnMemoryPressure` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="05447-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="05447-110">New behavior</span></span>

<span data-ttu-id="05447-111">A propriedade `MemoryCacheOptions.CompactOnMemoryPressure` foi removida.</span><span class="sxs-lookup"><span data-stu-id="05447-111">The `MemoryCacheOptions.CompactOnMemoryPressure` property has been removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="05447-112">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="05447-112">Reason for change</span></span>

<span data-ttu-id="05447-113">A compactação automática do cache causou problemas.</span><span class="sxs-lookup"><span data-stu-id="05447-113">Automatically compacting the cache caused problems.</span></span> <span data-ttu-id="05447-114">Para evitar um comportamento inesperado, o cache só deve ser compactado quando necessário.</span><span class="sxs-lookup"><span data-stu-id="05447-114">To avoid unexpected behavior, the cache should only be compacted when needed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="05447-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="05447-115">Recommended action</span></span>

<span data-ttu-id="05447-116">Para compactar o cache, downcast para `MemoryCache` e chamar `Compact` quando necessário.</span><span class="sxs-lookup"><span data-stu-id="05447-116">To compact the cache, downcast to `MemoryCache` and call `Compact` when needed.</span></span>

#### <a name="category"></a><span data-ttu-id="05447-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="05447-117">Category</span></span>

<span data-ttu-id="05447-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="05447-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="05447-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="05447-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
