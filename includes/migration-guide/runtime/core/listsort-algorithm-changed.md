---
ms.openlocfilehash: 9dada93c3330331064b7a944d97d61edb4dea299
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619784"
---
### <a name="listsort-algorithm-changed"></a><span data-ttu-id="666f0-101">O algoritmo List.Sort foi alterado</span><span class="sxs-lookup"><span data-stu-id="666f0-101">List.Sort algorithm changed</span></span>

#### <a name="details"></a><span data-ttu-id="666f0-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="666f0-102">Details</span></span>

<span data-ttu-id="666f0-103">A partir do .NET Framework 4.5, o algoritmo de classificação de <xref:System.Collections.Generic.List%601?displayProperty=fullName> foi alterado (para ser uma classificação introspectiva em vez de uma classificação rápida).</span><span class="sxs-lookup"><span data-stu-id="666f0-103">Beginning in .NET Framework 4.5, <xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort algorithm has changed (to be an introspective sort instead of a quick sort).</span></span> <span data-ttu-id="666f0-104">A classificação de <xref:System.Collections.Generic.List%601?displayProperty=fullName> nunca foi estável, mas essa alteração pode fazer com que cenários diferentes sejam classificados de maneiras instáveis.</span><span class="sxs-lookup"><span data-stu-id="666f0-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort has never been stable, but this change may cause different scenarios to sort in unstable ways.</span></span> <span data-ttu-id="666f0-105">Isso significa apenas que itens equivalentes podem ser classificados em ordens diferentes em chamadas posteriores da API.</span><span class="sxs-lookup"><span data-stu-id="666f0-105">That simply means that equivalent items may sort in different orders in subsequent calls of the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="666f0-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="666f0-106">Suggestion</span></span>

<span data-ttu-id="666f0-107">Como o algoritmo de classificação antigo também era instável (embora de maneiras ligeiramente diferentes), não deve haver nenhum código que dependa de itens equivalentes sempre serem classificados em uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="666f0-107">Because the old sort algorithm was also unstable (though in slightly different ways), there should be no code that depends on equivalent items always sorting in a particular order.</span></span> <span data-ttu-id="666f0-108">Se houver casos de códigos que dependem disso e que tinham sorte com o comportamento antigo, esses códigos deverão ser atualizados para usar um comparador que classifique de forma determinista os itens na ordem desejada.</span><span class="sxs-lookup"><span data-stu-id="666f0-108">If there are instances of code depending upon that and being lucky with the old behavior, that code should be updated to use a comparer that will deterministically sort the items in the desired order.</span></span>

| <span data-ttu-id="666f0-109">Name</span><span class="sxs-lookup"><span data-stu-id="666f0-109">Name</span></span>    | <span data-ttu-id="666f0-110">Valor</span><span class="sxs-lookup"><span data-stu-id="666f0-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="666f0-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="666f0-111">Scope</span></span>   |<span data-ttu-id="666f0-112">Transparente</span><span class="sxs-lookup"><span data-stu-id="666f0-112">Transparent</span></span>|
|<span data-ttu-id="666f0-113">Versão</span><span class="sxs-lookup"><span data-stu-id="666f0-113">Version</span></span>|<span data-ttu-id="666f0-114">4.5</span><span class="sxs-lookup"><span data-stu-id="666f0-114">4.5</span></span>|
|<span data-ttu-id="666f0-115">Type</span><span class="sxs-lookup"><span data-stu-id="666f0-115">Type</span></span>|<span data-ttu-id="666f0-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="666f0-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="666f0-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="666f0-117">Affected APIs</span></span>

-<xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|
