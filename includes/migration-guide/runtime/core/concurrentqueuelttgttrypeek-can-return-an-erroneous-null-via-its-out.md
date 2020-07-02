---
ms.openlocfilehash: 02a15f6b9c02002b60c568b9e1d871af49744092
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621923"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a><span data-ttu-id="320dd-101">ConcurrentQueue&lt;T&gt;.TryPeek pode retornar um nulo errado por meio de seus parâmetros de saída</span><span class="sxs-lookup"><span data-stu-id="320dd-101">ConcurrentQueue&lt;T&gt;.TryPeek can return an erroneous null via its out parameter</span></span>

#### <a name="details"></a><span data-ttu-id="320dd-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="320dd-102">Details</span></span>

<span data-ttu-id="320dd-103">Em alguns cenários multithread, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> pode retornar true, mas popular o parâmetro de saída com um valor nulo (em vez do valor correto, inspecionado).</span><span class="sxs-lookup"><span data-stu-id="320dd-103">In some multi-threaded scenarios, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> can return true, but populate the out parameter with a null value (instead of the correct, peeked value).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="320dd-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="320dd-104">Suggestion</span></span>

<span data-ttu-id="320dd-105">Esse problema foi corrigido no .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="320dd-105">This issue is fixed in the .NET Framework 4.5.1.</span></span> <span data-ttu-id="320dd-106">O upgrade para esse Framework resolverá o problema.</span><span class="sxs-lookup"><span data-stu-id="320dd-106">Upgrading to that Framework will solve the issue.</span></span>

| <span data-ttu-id="320dd-107">Name</span><span class="sxs-lookup"><span data-stu-id="320dd-107">Name</span></span>    | <span data-ttu-id="320dd-108">Valor</span><span class="sxs-lookup"><span data-stu-id="320dd-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="320dd-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="320dd-109">Scope</span></span>   |<span data-ttu-id="320dd-110">Principal</span><span class="sxs-lookup"><span data-stu-id="320dd-110">Major</span></span>|
|<span data-ttu-id="320dd-111">Versão</span><span class="sxs-lookup"><span data-stu-id="320dd-111">Version</span></span>|<span data-ttu-id="320dd-112">4.5</span><span class="sxs-lookup"><span data-stu-id="320dd-112">4.5</span></span>|
|<span data-ttu-id="320dd-113">Type</span><span class="sxs-lookup"><span data-stu-id="320dd-113">Type</span></span>|<span data-ttu-id="320dd-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="320dd-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="320dd-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="320dd-115">Affected APIs</span></span>

-<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
