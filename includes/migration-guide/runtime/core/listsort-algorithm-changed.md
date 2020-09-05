---
ms.openlocfilehash: 09bd2c6312493f8b6369d05d8f1c4e88e4c05ece
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497879"
---
### <a name="listsort-algorithm-changed"></a><span data-ttu-id="21501-101">O algoritmo List.Sort foi alterado</span><span class="sxs-lookup"><span data-stu-id="21501-101">List.Sort algorithm changed</span></span>

#### <a name="details"></a><span data-ttu-id="21501-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="21501-102">Details</span></span>

<span data-ttu-id="21501-103">A partir do .NET Framework 4.5, o algoritmo de classificação de <xref:System.Collections.Generic.List%601?displayProperty=fullName> foi alterado (para ser uma classificação introspectiva em vez de uma classificação rápida).</span><span class="sxs-lookup"><span data-stu-id="21501-103">Beginning in .NET Framework 4.5, <xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort algorithm has changed (to be an introspective sort instead of a quick sort).</span></span> <span data-ttu-id="21501-104">A classificação de <xref:System.Collections.Generic.List%601?displayProperty=fullName> nunca foi estável, mas essa alteração pode fazer com que cenários diferentes sejam classificados de maneiras instáveis.</span><span class="sxs-lookup"><span data-stu-id="21501-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort has never been stable, but this change may cause different scenarios to sort in unstable ways.</span></span> <span data-ttu-id="21501-105">Isso significa apenas que itens equivalentes podem ser classificados em ordens diferentes em chamadas posteriores da API.</span><span class="sxs-lookup"><span data-stu-id="21501-105">That simply means that equivalent items may sort in different orders in subsequent calls of the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="21501-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="21501-106">Suggestion</span></span>

<span data-ttu-id="21501-107">Como o algoritmo de classificação antigo também era instável (embora de maneiras ligeiramente diferentes), não deve haver nenhum código que dependa de itens equivalentes sempre serem classificados em uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="21501-107">Because the old sort algorithm was also unstable (though in slightly different ways), there should be no code that depends on equivalent items always sorting in a particular order.</span></span> <span data-ttu-id="21501-108">Se houver casos de códigos que dependem disso e que tinham sorte com o comportamento antigo, esses códigos deverão ser atualizados para usar um comparador que classifique de forma determinista os itens na ordem desejada.</span><span class="sxs-lookup"><span data-stu-id="21501-108">If there are instances of code depending upon that and being lucky with the old behavior, that code should be updated to use a comparer that will deterministically sort the items in the desired order.</span></span>

| <span data-ttu-id="21501-109">Nome</span><span class="sxs-lookup"><span data-stu-id="21501-109">Name</span></span>    | <span data-ttu-id="21501-110">Valor</span><span class="sxs-lookup"><span data-stu-id="21501-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="21501-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="21501-111">Scope</span></span>   |<span data-ttu-id="21501-112">Transparente</span><span class="sxs-lookup"><span data-stu-id="21501-112">Transparent</span></span>|
|<span data-ttu-id="21501-113">Versão</span><span class="sxs-lookup"><span data-stu-id="21501-113">Version</span></span>|<span data-ttu-id="21501-114">4.5</span><span class="sxs-lookup"><span data-stu-id="21501-114">4.5</span></span>|
|<span data-ttu-id="21501-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="21501-115">Type</span></span>|<span data-ttu-id="21501-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="21501-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="21501-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="21501-117">Affected APIs</span></span>

- <xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Generic.List`1.Sort``
- ``M:System.Collections.Generic.List`1.Sort(System.Collections.Generic.IComparer{`0})``
- ``M:System.Collections.Generic.List`1.Sort(System.Comparison{`0})``
- ``M:System.Collections.Generic.List`1.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{`0})``

-->
