---
title: 'Como: Usar ForEach para remover itens de uma BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10fa77f6948a10959db5f79c37692eba67d47ecd
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666547"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="005ef-102">Como: Usar ForEach para remover itens de uma BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="005ef-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>

<span data-ttu-id="005ef-103">Além de extrair itens de uma <xref:System.Collections.Concurrent.BlockingCollection%601> usando o método <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> e <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A>, também é possível usar um [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) em Visual Basic), para remover itens até que a adição seja concluída e a coleção esteja vazia.</span><span class="sxs-lookup"><span data-stu-id="005ef-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="005ef-104">Isso é chamado de *enumeração de mutação* ou de *mutação consumidora* porque, ao contrário de um loop típico `foreach` (`For Each`), esse enumerador modifica a coleção de origem, removendo itens.</span><span class="sxs-lookup"><span data-stu-id="005ef-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>

## <a name="example"></a><span data-ttu-id="005ef-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="005ef-105">Example</span></span>

<span data-ttu-id="005ef-106">O exemplo a seguir mostra como remover todos os itens em um <xref:System.Collections.Concurrent.BlockingCollection%601> usando um loop `foreach` (`For Each`).</span><span class="sxs-lookup"><span data-stu-id="005ef-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

<span data-ttu-id="005ef-107">Este exemplo usa um loop `foreach` com o método <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> no thread consumidor, que faz com que cada item seja removido da coleção ao ser enumerado.</span><span class="sxs-lookup"><span data-stu-id="005ef-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="005ef-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limita o número máximo de itens que estão na coleção a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="005ef-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="005ef-109">Enumerar a coleção dessa maneira bloqueará o thread consumidor se nenhum item estiver disponível ou se a coleção estiver vazia.</span><span class="sxs-lookup"><span data-stu-id="005ef-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="005ef-110">Neste exemplo, o bloqueio não é um problema porque o thread produtor adiciona itens mais rápido do que eles podem ser consumidos.</span><span class="sxs-lookup"><span data-stu-id="005ef-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>

<span data-ttu-id="005ef-111">Não há nenhuma garantia de que os itens sejam enumerados na mesma ordem em que são adicionados por threads de produtor.</span><span class="sxs-lookup"><span data-stu-id="005ef-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>

<span data-ttu-id="005ef-112">Para enumerar a coleção sem modificá-la, basta usar `foreach` (`For Each`) sem o método <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="005ef-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="005ef-113">No entanto, é importante compreender que esse tipo de enumeração representa um instantâneo da coleção em um ponto preciso no tempo.</span><span class="sxs-lookup"><span data-stu-id="005ef-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="005ef-114">Se outros threads estiverem adicionando ou removendo itens simultaneamente enquanto você estiver executando o loop, o loop poderá não representar o estado real da coleção.</span><span class="sxs-lookup"><span data-stu-id="005ef-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="005ef-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="005ef-115">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="005ef-116">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="005ef-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)
