---
title: Como agilizar corpos de loop pequenos
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
helpviewer_keywords: parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d38d8beedf342720d4dc68026297edb457f5ed35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="ae901-102">Como agilizar corpos de loop pequenos</span><span class="sxs-lookup"><span data-stu-id="ae901-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="ae901-103">Quando um <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop tem um corpo de pequeno, poderá executar mais lentamente do que o loop sequencial equivalente, como o [para](~/docs/csharp/language-reference/keywords/for.md) loop em c# e o [para](http://msdn.microsoft.com/en-us/c470a263-9b49-4308-8fd6-8592b84a7980) loop no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ae901-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](~/docs/csharp/language-reference/keywords/for.md) loop in C# and the [For](http://msdn.microsoft.com/en-us/c470a263-9b49-4308-8fd6-8592b84a7980) loop in Visual Basic.</span></span> <span data-ttu-id="ae901-104">Desempenho mais lento é causado por sobrecarga envolvida no particionamento de dados e o custo de invocação de um representante em cada iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="ae901-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="ae901-105">Para resolver esses cenários, o <xref:System.Collections.Concurrent.Partitioner> classe fornece a <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> método, que permite que você forneça um loop sequencial do corpo do delegado, para que o delegado é chamado apenas uma vez por partição, em vez de uma vez a cada iteração.</span><span class="sxs-lookup"><span data-stu-id="ae901-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="ae901-106">Para saber mais, veja [Particionadores personalizados para PLINQ e TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="ae901-106">For more information, see [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae901-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae901-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="ae901-108">A abordagem demonstrada neste exemplo é útil quando o loop executa uma quantidade mínima de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ae901-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="ae901-109">Como o trabalho se torna mais dispendioso, você provavelmente obterá o desempenho igual ou melhor usando um <xref:System.Threading.Tasks.Parallel.For%2A> ou <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop com o particionador padrão.</span><span class="sxs-lookup"><span data-stu-id="ae901-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae901-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae901-110">See Also</span></span>  
 [<span data-ttu-id="ae901-111">Paralelismo de dados</span><span class="sxs-lookup"><span data-stu-id="ae901-111">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="ae901-112">Particionadores personalizados para PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="ae901-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [<span data-ttu-id="ae901-113">Iteradores</span><span class="sxs-lookup"><span data-stu-id="ae901-113">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [<span data-ttu-id="ae901-114">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="ae901-114">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
