---
title: Como usar ForEach para remover itens de uma BlockingCollection
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7683e295bd1d898e112a754b06993dabf4483871
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="97201-102">Como usar ForEach para remover itens de uma BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="97201-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>
<span data-ttu-id="97201-103">Além de extrair itens de uma <xref:System.Collections.Concurrent.BlockingCollection%601> usando o método <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> e <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A>, também é possível usar um [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) em Visual Basic), para remover itens até que a adição seja concluída e a coleção esteja vazia.</span><span class="sxs-lookup"><span data-stu-id="97201-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="97201-104">Isso é chamado de *enumeração de mutação* ou de *mutação consumidora* porque, ao contrário de um loop típico `foreach` (`For Each`), esse enumerador modifica a coleção de origem, removendo itens.</span><span class="sxs-lookup"><span data-stu-id="97201-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97201-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="97201-105">Example</span></span>  
 <span data-ttu-id="97201-106">O exemplo a seguir mostra como remover todos os itens em um <xref:System.Collections.Concurrent.BlockingCollection%601> usando um loop `foreach` (`For Each`).</span><span class="sxs-lookup"><span data-stu-id="97201-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 <span data-ttu-id="97201-107">Este exemplo usa um loop `foreach` com o método <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> no thread consumidor, que faz com que cada item seja removido da coleção ao ser enumerado.</span><span class="sxs-lookup"><span data-stu-id="97201-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="97201-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limita o número máximo de itens que estão na coleção a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="97201-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="97201-109">Enumerar a coleção dessa maneira bloqueará o thread consumidor se nenhum item estiver disponível ou se a coleção estiver vazia.</span><span class="sxs-lookup"><span data-stu-id="97201-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="97201-110">Neste exemplo, o bloqueio não é um problema porque o thread produtor adiciona itens mais rápido do que eles podem ser consumidos.</span><span class="sxs-lookup"><span data-stu-id="97201-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>  
  
 <span data-ttu-id="97201-111">Não há nenhuma garantia de que os itens sejam enumerados na mesma ordem em que são adicionados por threads de produtor.</span><span class="sxs-lookup"><span data-stu-id="97201-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>  
  
 <span data-ttu-id="97201-112">Para enumerar a coleção sem modificá-la, basta usar `foreach` (`For Each`) sem o método <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="97201-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="97201-113">No entanto, é importante compreender que esse tipo de enumeração representa um instantâneo da coleção em um ponto preciso no tempo.</span><span class="sxs-lookup"><span data-stu-id="97201-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="97201-114">Se outros threads estiverem adicionando ou removendo itens simultaneamente enquanto você estiver executando o loop, o loop poderá não representar o estado real da coleção.</span><span class="sxs-lookup"><span data-stu-id="97201-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97201-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97201-115">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="97201-116">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="97201-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)
