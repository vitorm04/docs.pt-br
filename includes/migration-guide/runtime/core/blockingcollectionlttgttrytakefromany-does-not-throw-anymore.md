---
ms.openlocfilehash: 277a91fbfbf0c6aaaa0dc044ef0c079ad8607699
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496339"
---
### <a name="blockingcollectionlttgttrytakefromany-does-not-throw-anymore"></a><span data-ttu-id="8395d-101">BlockingCollection&lt;T&gt;.TryTakeFromAny não é mais gerado</span><span class="sxs-lookup"><span data-stu-id="8395d-101">BlockingCollection&lt;T&gt;.TryTakeFromAny does not throw anymore</span></span>

#### <a name="details"></a><span data-ttu-id="8395d-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8395d-102">Details</span></span>

<span data-ttu-id="8395d-103">Se uma das coleções de entrada for marcada como concluída, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> não retornará mais -1 e <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> não vai mais gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="8395d-103">If one of the input collections is marked completed, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer returns -1 and <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer throws an exception.</span></span> <span data-ttu-id="8395d-104">Essa alteração possibilita trabalhar com coleções quando uma das coleções está vazia ou concluída, mas a outra coleção ainda possui itens que podem ser recuperados.</span><span class="sxs-lookup"><span data-stu-id="8395d-104">This change makes it possible to work with collections when one of the collections is either empty or completed, but the other collection still has items that can be retrieved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8395d-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8395d-105">Suggestion</span></span>

<span data-ttu-id="8395d-106">Se o retorno de -1 de TryTakeFromAny ou a geração de TakeFromAny foram usados para fins de fluxo de controle no caso de conclusão de uma coleção de blocos, tal código agora deverá ser alterado para usar <code>.Any(b =&gt; b.IsCompleted)</code> a fim de detectar essa condição.</span><span class="sxs-lookup"><span data-stu-id="8395d-106">If TryTakeFromAny returning -1 or TakeFromAny throwing were used for control-flow purposes in cases of a blocking collection being completed, such code should now be changed to use <code>.Any(b =&gt; b.IsCompleted)</code> to detect that condition.</span></span>

| <span data-ttu-id="8395d-107">Nome</span><span class="sxs-lookup"><span data-stu-id="8395d-107">Name</span></span>    | <span data-ttu-id="8395d-108">Valor</span><span class="sxs-lookup"><span data-stu-id="8395d-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8395d-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="8395d-109">Scope</span></span>   |<span data-ttu-id="8395d-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="8395d-110">Minor</span></span>|
|<span data-ttu-id="8395d-111">Versão</span><span class="sxs-lookup"><span data-stu-id="8395d-111">Version</span></span>|<span data-ttu-id="8395d-112">4.5</span><span class="sxs-lookup"><span data-stu-id="8395d-112">4.5</span></span>|
|<span data-ttu-id="8395d-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="8395d-113">Type</span></span>|<span data-ttu-id="8395d-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="8395d-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="8395d-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8395d-115">Affected APIs</span></span>

- <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Int32)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Concurrent.BlockingCollection`1.TakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.Threading.CancellationToken)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.Int32)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.TimeSpan)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.TimeSpan)``

-->
