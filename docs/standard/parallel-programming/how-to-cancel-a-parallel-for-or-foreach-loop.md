---
title: 'Como: Cancelar um loop Parallel.For ou ForEach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7cdb6e059fb1c7001bbe4da60e2936b1ad40cc1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618058"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="c5cc0-102">Como: Cancelar um loop Parallel.For ou ForEach</span><span class="sxs-lookup"><span data-stu-id="c5cc0-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="c5cc0-103">Os métodos <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> oferecem suporte ao cancelamento por meio do uso de tokens de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="c5cc0-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="c5cc0-104">Para saber mais sobre cancelamento em geral, confira [Cancelamento](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="c5cc0-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="c5cc0-105">Em um loop paralelo, você fornece <xref:System.Threading.CancellationToken> para o método no parâmetro <xref:System.Threading.Tasks.ParallelOptions> e, em seguida, coloca a chamada paralela em um bloco try-catch.</span><span class="sxs-lookup"><span data-stu-id="c5cc0-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5cc0-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c5cc0-106">Example</span></span>  
 <span data-ttu-id="c5cc0-107">O exemplo a seguir mostra como cancelar uma chamada para <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c5cc0-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c5cc0-108">Você pode aplicar a mesma abordagem a uma chamada <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c5cc0-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="c5cc0-109">Se o token que sinaliza o cancelamento for o mesmo token que é especificado na instância <xref:System.Threading.Tasks.ParallelOptions>, o loop paralelo lançará uma única <xref:System.OperationCanceledException> no cancelamento.</span><span class="sxs-lookup"><span data-stu-id="c5cc0-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="c5cc0-110">Se algum outro token causar o cancelamento, o loop lançará uma <xref:System.AggregateException> com uma <xref:System.OperationCanceledException> como um InnerException.</span><span class="sxs-lookup"><span data-stu-id="c5cc0-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5cc0-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5cc0-111">See also</span></span>

- [<span data-ttu-id="c5cc0-112">Paralelismo de dados</span><span class="sxs-lookup"><span data-stu-id="c5cc0-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="c5cc0-113">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="c5cc0-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
