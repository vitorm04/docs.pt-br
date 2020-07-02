---
ms.openlocfilehash: 9131c91b34f4c24653dea37ea39af6be6e072287
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619801"
---
### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a><span data-ttu-id="1e9ab-101">Enumerable.Empty&lt;TResult&gt; sempre retorna instância em cache</span><span class="sxs-lookup"><span data-stu-id="1e9ab-101">Enumerable.Empty&lt;TResult&gt; always returns cached instance</span></span>

#### <a name="details"></a><span data-ttu-id="1e9ab-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1e9ab-102">Details</span></span>

<span data-ttu-id="1e9ab-103">Começando com o .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> sempre retorna um <xref:System.Collections.Generic.IEnumerable%601> de instância interna em cache. Anteriormente, o <xref:System.Linq.Enumerable.Empty%60%601> armazenava em cache um <xref:System.Collections.Generic.IEnumerable%601> vazio no momento em que a API era chamada, significando que, em algumas condições nas quais <xref:System.Linq.Enumerable.Empty%60%601> era chamado de forma rápida e simultânea, diferentes instâncias do tipo poderiam ser retornadas para diferentes chamadas à API.</span><span class="sxs-lookup"><span data-stu-id="1e9ab-103">Beginning in .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> always returns a cached internal instance <xref:System.Collections.Generic.IEnumerable%601>.Previously, <xref:System.Linq.Enumerable.Empty%60%601> would cache an empty <xref:System.Collections.Generic.IEnumerable%601> at the time the API was called, meaning that in some conditions in which <xref:System.Linq.Enumerable.Empty%60%601> was called rapidly and concurrently, different instances of the type could be returned for different calls to the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1e9ab-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1e9ab-104">Suggestion</span></span>

<span data-ttu-id="1e9ab-105">Como o comportamento anterior não era determinístico, é improvável que o código dependesse dele.</span><span class="sxs-lookup"><span data-stu-id="1e9ab-105">Because the previous behavior was non-deterministic, code is unlikely to depend on it.</span></span> <span data-ttu-id="1e9ab-106">No entanto, na improbabilidade de que enumeráveis vazios estivessem sendo comparados e, às vezes, esperados que fosse diferentes, matrizes vazias explícitas deviam ser criadas (<code>new T[0]</code>) em vez de usar <xref:System.Linq.Enumerable.Empty%60%601>.</span><span class="sxs-lookup"><span data-stu-id="1e9ab-106">However, in the unlikely case that empty enumerables are being compared and expected to sometimes be unequal, explicit empty arrays should be created (<code>new T[0]</code>) instead of using <xref:System.Linq.Enumerable.Empty%60%601>.</span></span>

| <span data-ttu-id="1e9ab-107">Name</span><span class="sxs-lookup"><span data-stu-id="1e9ab-107">Name</span></span>    | <span data-ttu-id="1e9ab-108">Valor</span><span class="sxs-lookup"><span data-stu-id="1e9ab-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1e9ab-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="1e9ab-109">Scope</span></span>   |<span data-ttu-id="1e9ab-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="1e9ab-110">Edge</span></span>|
|<span data-ttu-id="1e9ab-111">Versão</span><span class="sxs-lookup"><span data-stu-id="1e9ab-111">Version</span></span>|<span data-ttu-id="1e9ab-112">4.5</span><span class="sxs-lookup"><span data-stu-id="1e9ab-112">4.5</span></span>|
|<span data-ttu-id="1e9ab-113">Type</span><span class="sxs-lookup"><span data-stu-id="1e9ab-113">Type</span></span>|<span data-ttu-id="1e9ab-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="1e9ab-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1e9ab-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1e9ab-115">Affected APIs</span></span>

-<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|
