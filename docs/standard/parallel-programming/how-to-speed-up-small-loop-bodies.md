---
title: 'Como: Acelerar corpos de loop pequenos'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06af0e10080977800479ed5aa444c63bde2d371e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726449"
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="999ca-102">Como: Acelerar corpos de loop pequenos</span><span class="sxs-lookup"><span data-stu-id="999ca-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="999ca-103">Quando um loop <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> tem um corpo pequeno, ele pode executar mais lentamente do que o loop sequencial equivalente, como o loop [para](~/docs/csharp/language-reference/keywords/for.md) em c# e o loop [Para](https://msdn.microsoft.com/library/c470a263-9b49-4308-8fd6-8592b84a7980) no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="999ca-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](~/docs/csharp/language-reference/keywords/for.md) loop in C# and the [For](https://msdn.microsoft.com/library/c470a263-9b49-4308-8fd6-8592b84a7980) loop in Visual Basic.</span></span> <span data-ttu-id="999ca-104">O desempenho mais lento é causado pela sobrecarga envolvida no particionamento dos dados e do custo de invocação de um representante em cada iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="999ca-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="999ca-105">Para resolver esses cenários, a classe <xref:System.Collections.Concurrent.Partitioner> fornece o método <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType>, que permite que você forneça um loop sequencial do corpo do representante, de modo que o representante seja chamado apenas uma vez por partição, em vez de uma vez por iteração.</span><span class="sxs-lookup"><span data-stu-id="999ca-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="999ca-106">Para saber mais, veja [Particionadores personalizados para PLINQ e TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="999ca-106">For more information, see [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="999ca-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="999ca-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="999ca-108">A abordagem demonstrada neste exemplo é útil quando o loop executa uma quantidade mínima de trabalho.</span><span class="sxs-lookup"><span data-stu-id="999ca-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="999ca-109">Como o trabalho se torna mais dispendioso computacionalmente, você provavelmente obterá um desempenho igual ou melhor usando um loop <xref:System.Threading.Tasks.Parallel.For%2A> ou <xref:System.Threading.Tasks.Parallel.ForEach%2A> com o particionador padrão.</span><span class="sxs-lookup"><span data-stu-id="999ca-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="999ca-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="999ca-110">See also</span></span>

- [<span data-ttu-id="999ca-111">Paralelismo de dados</span><span class="sxs-lookup"><span data-stu-id="999ca-111">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="999ca-112">Particionadores personalizados para PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="999ca-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="999ca-113">Iteradores</span><span class="sxs-lookup"><span data-stu-id="999ca-113">Iterators</span></span>](https://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
- [<span data-ttu-id="999ca-114">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="999ca-114">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
