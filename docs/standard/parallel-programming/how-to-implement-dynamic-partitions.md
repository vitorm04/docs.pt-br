---
title: "como implementar partições dinâmicas"
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
helpviewer_keywords: tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1e5dc93997918e0f7da29fa1f94c434a556f19f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="9e88f-102">como implementar partições dinâmicas</span><span class="sxs-lookup"><span data-stu-id="9e88f-102">How to: Implement Dynamic Partitions</span></span>
<span data-ttu-id="9e88f-103">O exemplo a seguir mostra como implementar um personalizado <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> que implementa o particionamento dinâmico e pode ser usado em determinadas sobrecargas <xref:System.Threading.Tasks.Parallel.ForEach%2A> e do PLINQ.</span><span class="sxs-lookup"><span data-stu-id="9e88f-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e88f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e88f-104">Example</span></span>  
 <span data-ttu-id="9e88f-105">Cada vez que uma partição chama <xref:System.Collections.IEnumerator.MoveNext%2A> no enumerador, o enumerador fornece a partição com o elemento de uma lista.</span><span class="sxs-lookup"><span data-stu-id="9e88f-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="9e88f-106">No caso do PLINQ e <xref:System.Threading.Tasks.Parallel.ForEach%2A>, a partição é um <xref:System.Threading.Tasks.Task> instância.</span><span class="sxs-lookup"><span data-stu-id="9e88f-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="9e88f-107">Porque as solicitações estiverem ocorrendo simultaneamente em vários threads, o acesso para o índice atual é sincronizado.</span><span class="sxs-lookup"><span data-stu-id="9e88f-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 <span data-ttu-id="9e88f-108">Este é um exemplo de particionamento, com cada parte consiste em um elemento de bloco.</span><span class="sxs-lookup"><span data-stu-id="9e88f-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="9e88f-109">Fornecendo mais elementos em um momento, você pode reduzir a contenção de bloqueio e, teoricamente, alcançar um desempenho mais rápido.</span><span class="sxs-lookup"><span data-stu-id="9e88f-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="9e88f-110">No entanto, em algum momento, partes maiores podem exigir lógica de balanceamento de carga adicional para manter todos os threads ocupados até que todo o trabalho é feito.</span><span class="sxs-lookup"><span data-stu-id="9e88f-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e88f-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e88f-111">See Also</span></span>  
 [<span data-ttu-id="9e88f-112">Particionadores personalizados para PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="9e88f-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [<span data-ttu-id="9e88f-113">Como implementar um particionador para particionamento estático</span><span class="sxs-lookup"><span data-stu-id="9e88f-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
