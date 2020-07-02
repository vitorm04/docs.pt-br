---
ms.openlocfilehash: a8f51dfa1c82e3b166449d2432dfe8a9b96564b9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619774"
---
### <a name="blockingcollectionlttgttrytakefromany-does-not-throw-anymore"></a><span data-ttu-id="99285-101">BlockingCollection&lt;T&gt;.TryTakeFromAny não é mais gerado</span><span class="sxs-lookup"><span data-stu-id="99285-101">BlockingCollection&lt;T&gt;.TryTakeFromAny does not throw anymore</span></span>

#### <a name="details"></a><span data-ttu-id="99285-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="99285-102">Details</span></span>

<span data-ttu-id="99285-103">Se uma das coleções de entrada for marcada como concluída, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> não retornará mais -1 e <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> não vai mais gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="99285-103">If one of the input collections is marked completed, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer returns -1 and <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer throws an exception.</span></span> <span data-ttu-id="99285-104">Essa alteração possibilita trabalhar com coleções quando uma das coleções está vazia ou concluída, mas a outra coleção ainda possui itens que podem ser recuperados.</span><span class="sxs-lookup"><span data-stu-id="99285-104">This change makes it possible to work with collections when one of the collections is either empty or completed, but the other collection still has items that can be retrieved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="99285-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="99285-105">Suggestion</span></span>

<span data-ttu-id="99285-106">Se o retorno de -1 de TryTakeFromAny ou a geração de TakeFromAny foram usados para fins de fluxo de controle no caso de conclusão de uma coleção de blocos, tal código agora deverá ser alterado para usar <code>.Any(b =&gt; b.IsCompleted)</code> a fim de detectar essa condição.</span><span class="sxs-lookup"><span data-stu-id="99285-106">If TryTakeFromAny returning -1 or TakeFromAny throwing were used for control-flow purposes in cases of a blocking collection being completed, such code should now be changed to use <code>.Any(b =&gt; b.IsCompleted)</code> to detect that condition.</span></span>

| <span data-ttu-id="99285-107">Name</span><span class="sxs-lookup"><span data-stu-id="99285-107">Name</span></span>    | <span data-ttu-id="99285-108">Valor</span><span class="sxs-lookup"><span data-stu-id="99285-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="99285-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="99285-109">Scope</span></span>   |<span data-ttu-id="99285-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="99285-110">Minor</span></span>|
|<span data-ttu-id="99285-111">Versão</span><span class="sxs-lookup"><span data-stu-id="99285-111">Version</span></span>|<span data-ttu-id="99285-112">4.5</span><span class="sxs-lookup"><span data-stu-id="99285-112">4.5</span></span>|
|<span data-ttu-id="99285-113">Type</span><span class="sxs-lookup"><span data-stu-id="99285-113">Type</span></span>|<span data-ttu-id="99285-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="99285-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="99285-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="99285-115">Affected APIs</span></span>

-<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li></ul>|
