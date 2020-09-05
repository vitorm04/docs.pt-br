---
ms.openlocfilehash: 05f60978f5380c406c43aa98ded0c812b1d50694
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497942"
---
### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a><span data-ttu-id="32bb4-101">Enumerable.Empty&lt;TResult&gt; sempre retorna instância em cache</span><span class="sxs-lookup"><span data-stu-id="32bb4-101">Enumerable.Empty&lt;TResult&gt; always returns cached instance</span></span>

#### <a name="details"></a><span data-ttu-id="32bb4-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="32bb4-102">Details</span></span>

<span data-ttu-id="32bb4-103">Começando com o .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> sempre retorna um <xref:System.Collections.Generic.IEnumerable%601> de instância interna em cache. Anteriormente, o <xref:System.Linq.Enumerable.Empty%60%601> armazenava em cache um <xref:System.Collections.Generic.IEnumerable%601> vazio no momento em que a API era chamada, significando que, em algumas condições nas quais <xref:System.Linq.Enumerable.Empty%60%601> era chamado de forma rápida e simultânea, diferentes instâncias do tipo poderiam ser retornadas para diferentes chamadas à API.</span><span class="sxs-lookup"><span data-stu-id="32bb4-103">Beginning in .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> always returns a cached internal instance <xref:System.Collections.Generic.IEnumerable%601>.Previously, <xref:System.Linq.Enumerable.Empty%60%601> would cache an empty <xref:System.Collections.Generic.IEnumerable%601> at the time the API was called, meaning that in some conditions in which <xref:System.Linq.Enumerable.Empty%60%601> was called rapidly and concurrently, different instances of the type could be returned for different calls to the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="32bb4-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="32bb4-104">Suggestion</span></span>

<span data-ttu-id="32bb4-105">Como o comportamento anterior não era determinístico, é improvável que o código dependesse dele.</span><span class="sxs-lookup"><span data-stu-id="32bb4-105">Because the previous behavior was non-deterministic, code is unlikely to depend on it.</span></span> <span data-ttu-id="32bb4-106">No entanto, na improbabilidade de que enumeráveis vazios estivessem sendo comparados e, às vezes, esperados que fosse diferentes, matrizes vazias explícitas deviam ser criadas (<code>new T[0]</code>) em vez de usar <xref:System.Linq.Enumerable.Empty%60%601>.</span><span class="sxs-lookup"><span data-stu-id="32bb4-106">However, in the unlikely case that empty enumerables are being compared and expected to sometimes be unequal, explicit empty arrays should be created (<code>new T[0]</code>) instead of using <xref:System.Linq.Enumerable.Empty%60%601>.</span></span>

| <span data-ttu-id="32bb4-107">Nome</span><span class="sxs-lookup"><span data-stu-id="32bb4-107">Name</span></span>    | <span data-ttu-id="32bb4-108">Valor</span><span class="sxs-lookup"><span data-stu-id="32bb4-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="32bb4-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="32bb4-109">Scope</span></span>   |<span data-ttu-id="32bb4-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="32bb4-110">Edge</span></span>|
|<span data-ttu-id="32bb4-111">Versão</span><span class="sxs-lookup"><span data-stu-id="32bb4-111">Version</span></span>|<span data-ttu-id="32bb4-112">4.5</span><span class="sxs-lookup"><span data-stu-id="32bb4-112">4.5</span></span>|
|<span data-ttu-id="32bb4-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="32bb4-113">Type</span></span>|<span data-ttu-id="32bb4-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="32bb4-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="32bb4-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="32bb4-115">Affected APIs</span></span>

- <xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Linq.Enumerable.Empty``1``

-->
