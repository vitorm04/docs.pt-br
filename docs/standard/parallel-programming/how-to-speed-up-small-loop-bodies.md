---
title: Como agilizar corpos de loop pequenos
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
ms.openlocfilehash: 29d7fa8200ddd972c1a5c98ea6f30a7c8ff732e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139754"
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="ee157-102">Como agilizar corpos de loop pequenos</span><span class="sxs-lookup"><span data-stu-id="ee157-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="ee157-103">Quando um loop <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> tem um corpo pequeno, ele pode executar mais lentamente do que o loop sequencial equivalente, como o loop [para](../../csharp/language-reference/keywords/for.md) em c# e o loop [Para](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ee157-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](../../csharp/language-reference/keywords/for.md) loop in C# and the [For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) loop in Visual Basic.</span></span> <span data-ttu-id="ee157-104">O desempenho mais lento é causado pela sobrecarga envolvida no particionamento dos dados e do custo de invocação de um representante em cada iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="ee157-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="ee157-105">Para resolver esses cenários, a classe <xref:System.Collections.Concurrent.Partitioner> fornece o método <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType>, que permite que você forneça um loop sequencial do corpo do representante, de modo que o representante seja chamado apenas uma vez por partição, em vez de uma vez por iteração.</span><span class="sxs-lookup"><span data-stu-id="ee157-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="ee157-106">Para saber mais, veja [Particionadores personalizados para PLINQ e TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="ee157-106">For more information, see [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee157-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ee157-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="ee157-108">A abordagem demonstrada neste exemplo é útil quando o loop executa uma quantidade mínima de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ee157-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="ee157-109">Como o trabalho se torna mais dispendioso computacionalmente, você provavelmente obterá um desempenho igual ou melhor usando um loop <xref:System.Threading.Tasks.Parallel.For%2A> ou <xref:System.Threading.Tasks.Parallel.ForEach%2A> com o particionador padrão.</span><span class="sxs-lookup"><span data-stu-id="ee157-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee157-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee157-110">See also</span></span>

- [<span data-ttu-id="ee157-111">Paralelismo de dados</span><span class="sxs-lookup"><span data-stu-id="ee157-111">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="ee157-112">Particionadores personalizados para PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="ee157-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="ee157-113">Iteradores (C#)</span><span class="sxs-lookup"><span data-stu-id="ee157-113">Iterators (C#)</span></span>](../../csharp/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="ee157-114">Iteradores (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee157-114">Iterators (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="ee157-115">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="ee157-115">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
