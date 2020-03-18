---
ms.openlocfilehash: ae5a5fbf97ed4a03de7d35b9d5d5ca8de3aebc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393957"
---
### <a name="caching-responsecaching-pubternal-types-changed-to-internal"></a><span data-ttu-id="6842d-101">Cache: ResponseCaching tipos "pubternal" alterados para internos</span><span class="sxs-lookup"><span data-stu-id="6842d-101">Caching: ResponseCaching "pubternal" types changed to internal</span></span>

<span data-ttu-id="6842d-102">Em ASP.NET Núcleo 3.0, os tipos `ResponseCaching` "pubternais" foram alterados para `internal`.</span><span class="sxs-lookup"><span data-stu-id="6842d-102">In ASP.NET Core 3.0, "pubternal" types in `ResponseCaching` have been changed to `internal`.</span></span>

<span data-ttu-id="6842d-103">Além disso, implementações `IResponseCachingPolicyProvider` `IResponseCachingKeyProvider` padrão e não são mais `AddResponseCaching` adicionadas aos serviços como parte do método.</span><span class="sxs-lookup"><span data-stu-id="6842d-103">In addition, default implementations of `IResponseCachingPolicyProvider` and `IResponseCachingKeyProvider` are no longer added to services as part of the `AddResponseCaching` method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6842d-104">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="6842d-104">Change description</span></span>

<span data-ttu-id="6842d-105">Em ASP.NET Core, os tipos "pubternais" são declarados como `public` `.Internal`mas residem em um namespace sufixo com .</span><span class="sxs-lookup"><span data-stu-id="6842d-105">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a namespace suffixed with `.Internal`.</span></span> <span data-ttu-id="6842d-106">Embora esses tipos sejam públicos, eles não têm política de apoio e estão sujeitos a mudanças.</span><span class="sxs-lookup"><span data-stu-id="6842d-106">While these types are public, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="6842d-107">Infelizmente, o uso acidental desses tipos tem sido comum, resultando em mudanças nesses projetos e limitando a capacidade de manter o quadro.</span><span class="sxs-lookup"><span data-stu-id="6842d-107">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6842d-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="6842d-108">Version introduced</span></span>

<span data-ttu-id="6842d-109">3.0</span><span class="sxs-lookup"><span data-stu-id="6842d-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6842d-110">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="6842d-110">Old behavior</span></span>

<span data-ttu-id="6842d-111">Esses tipos eram publicamente visíveis, mas sem suporte.</span><span class="sxs-lookup"><span data-stu-id="6842d-111">These types were publicly visible, but unsupported.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6842d-112">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="6842d-112">New behavior</span></span>

<span data-ttu-id="6842d-113">Esses tipos `internal`são agora.</span><span class="sxs-lookup"><span data-stu-id="6842d-113">These types are now `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6842d-114">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="6842d-114">Reason for change</span></span>

<span data-ttu-id="6842d-115">O `internal` escopo reflete melhor a política sem fundamento.</span><span class="sxs-lookup"><span data-stu-id="6842d-115">The `internal` scope better reflects the unsupported policy.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6842d-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="6842d-116">Recommended action</span></span>

<span data-ttu-id="6842d-117">Copiar tipos que são usados pelo seu aplicativo ou biblioteca.</span><span class="sxs-lookup"><span data-stu-id="6842d-117">Copy types that are used by your app or library.</span></span>

#### <a name="category"></a><span data-ttu-id="6842d-118">Categoria</span><span class="sxs-lookup"><span data-stu-id="6842d-118">Category</span></span>

<span data-ttu-id="6842d-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6842d-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6842d-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6842d-120">Affected APIs</span></span>

- `Microsoft.AspNetCore.ResponseCaching.Internal.CachedResponse`
- `Microsoft.AspNetCore.ResponseCaching.Internal.CachedVaryByRules`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCacheEntry`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.MemoryResponseCache`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingContext`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingKeyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingPolicyProvider`
- <xref:Microsoft.AspNetCore.ResponseCaching.ResponseCachingMiddleware.%23ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.ResponseCaching.ResponseCachingOptions},Microsoft.Extensions.Logging.ILoggerFactory,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.ResponseCaching.Internal.CachedResponse`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.CachedVaryByRules`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCacheEntry`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.MemoryResponseCache`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingContext`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingKeyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingPolicyProvider`
- `M:Microsoft.AspNetCore.ResponseCaching.ResponseCachingMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.ResponseCaching.ResponseCachingOptions},Microsoft.Extensions.Logging.ILoggerFactory,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider)",
"nameWithType": "ResponseCachingMiddleware.ResponseCachingMiddleware(RequestDelegate, IOptions<ResponseCachingOptions>, ILoggerFactory, IResponseCachingPolicyProvider, IResponseCache, IResponseCachingKeyProvider)`

-->
