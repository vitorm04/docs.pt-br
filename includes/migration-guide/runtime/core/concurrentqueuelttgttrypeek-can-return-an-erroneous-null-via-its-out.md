---
ms.openlocfilehash: 004e2d1883b631e88ab5e164b1120c3b081b7041
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497645"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a><span data-ttu-id="23bd2-101">ConcurrentQueue&lt;T&gt;.TryPeek pode retornar um nulo errado por meio de seus parâmetros de saída</span><span class="sxs-lookup"><span data-stu-id="23bd2-101">ConcurrentQueue&lt;T&gt;.TryPeek can return an erroneous null via its out parameter</span></span>

#### <a name="details"></a><span data-ttu-id="23bd2-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="23bd2-102">Details</span></span>

<span data-ttu-id="23bd2-103">Em alguns cenários multithread, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> pode retornar true, mas popular o parâmetro de saída com um valor nulo (em vez do valor correto, inspecionado).</span><span class="sxs-lookup"><span data-stu-id="23bd2-103">In some multi-threaded scenarios, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> can return true, but populate the out parameter with a null value (instead of the correct, peeked value).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="23bd2-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="23bd2-104">Suggestion</span></span>

<span data-ttu-id="23bd2-105">Esse problema foi corrigido no .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="23bd2-105">This issue is fixed in the .NET Framework 4.5.1.</span></span> <span data-ttu-id="23bd2-106">O upgrade para esse Framework resolverá o problema.</span><span class="sxs-lookup"><span data-stu-id="23bd2-106">Upgrading to that Framework will solve the issue.</span></span>

| <span data-ttu-id="23bd2-107">Nome</span><span class="sxs-lookup"><span data-stu-id="23bd2-107">Name</span></span>    | <span data-ttu-id="23bd2-108">Valor</span><span class="sxs-lookup"><span data-stu-id="23bd2-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="23bd2-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="23bd2-109">Scope</span></span>   |<span data-ttu-id="23bd2-110">Principal</span><span class="sxs-lookup"><span data-stu-id="23bd2-110">Major</span></span>|
|<span data-ttu-id="23bd2-111">Versão</span><span class="sxs-lookup"><span data-stu-id="23bd2-111">Version</span></span>|<span data-ttu-id="23bd2-112">4.5</span><span class="sxs-lookup"><span data-stu-id="23bd2-112">4.5</span></span>|
|<span data-ttu-id="23bd2-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="23bd2-113">Type</span></span>|<span data-ttu-id="23bd2-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="23bd2-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="23bd2-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="23bd2-115">Affected APIs</span></span>

- <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Concurrent.ConcurrentQueue`1.TryPeek(`0@)``

-->
