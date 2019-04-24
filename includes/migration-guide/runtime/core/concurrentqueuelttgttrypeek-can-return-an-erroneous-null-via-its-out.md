---
ms.openlocfilehash: a93fbbd787aa50f080337a6170cf8f56d0d24e31
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803145"
---
### <a name="concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a><span data-ttu-id="1f3ba-101">ConcurrentQueue\<T>.TryPeek pode retornar um nulo errado por meio de seus parâmetros de saída</span><span class="sxs-lookup"><span data-stu-id="1f3ba-101">ConcurrentQueue\<T>.TryPeek can return an erroneous null via its out parameter</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1f3ba-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1f3ba-102">Details</span></span>|<span data-ttu-id="1f3ba-103">Em alguns cenários multithread, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> pode retornar true, mas popular o parâmetro de saída com um valor nulo (em vez do valor correto, inspecionado).</span><span class="sxs-lookup"><span data-stu-id="1f3ba-103">In some multi-threaded scenarios, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> can return true, but populate the out parameter with a null value (instead of the correct, peeked value).</span></span>|
|<span data-ttu-id="1f3ba-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1f3ba-104">Suggestion</span></span>|<span data-ttu-id="1f3ba-105">Esse problema foi corrigido no .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="1f3ba-105">This issue is fixed in the .NET Framework 4.5.1.</span></span> <span data-ttu-id="1f3ba-106">O upgrade para esse Framework resolverá o problema.</span><span class="sxs-lookup"><span data-stu-id="1f3ba-106">Upgrading to that Framework will solve the issue.</span></span>|
|<span data-ttu-id="1f3ba-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="1f3ba-107">Scope</span></span>|<span data-ttu-id="1f3ba-108">Principal</span><span class="sxs-lookup"><span data-stu-id="1f3ba-108">Major</span></span>|
|<span data-ttu-id="1f3ba-109">Versão</span><span class="sxs-lookup"><span data-stu-id="1f3ba-109">Version</span></span>|<span data-ttu-id="1f3ba-110">4.5</span><span class="sxs-lookup"><span data-stu-id="1f3ba-110">4.5</span></span>|
|<span data-ttu-id="1f3ba-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="1f3ba-111">Type</span></span>|<span data-ttu-id="1f3ba-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="1f3ba-112">Runtime</span></span>|
|<span data-ttu-id="1f3ba-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1f3ba-113">Affected APIs</span></span>|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
