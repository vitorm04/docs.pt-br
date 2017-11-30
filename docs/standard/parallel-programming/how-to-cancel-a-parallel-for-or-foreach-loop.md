---
title: Como cancelar um loop Parallel.For ou ForEach
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
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f82c5758e02b4beebf035fe8f43f856447855a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="20e9a-102">Como cancelar um loop Parallel.For ou ForEach</span><span class="sxs-lookup"><span data-stu-id="20e9a-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="20e9a-103">O <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> métodos dão suporte ao cancelamento com o uso de tokens de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="20e9a-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="20e9a-104">Para obter mais informações sobre cancelamento em geral, consulte [cancelamento](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="20e9a-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="20e9a-105">Em um loop paralelo, você deve fornecer o <xref:System.Threading.CancellationToken> para o método de <xref:System.Threading.Tasks.ParallelOptions> parâmetro e, em seguida, coloque a chamada paralela em um bloco try-catch.</span><span class="sxs-lookup"><span data-stu-id="20e9a-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20e9a-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="20e9a-106">Example</span></span>  
 <span data-ttu-id="20e9a-107">O exemplo a seguir mostra como cancelar uma chamada para <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="20e9a-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="20e9a-108">Você pode aplicar a mesma abordagem para um <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> chamar.</span><span class="sxs-lookup"><span data-stu-id="20e9a-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="20e9a-109">Se o token que sinaliza o cancelamento é o mesmo token que é especificado no <xref:System.Threading.Tasks.ParallelOptions> instância, em seguida, o loop paralelo lançará um único <xref:System.OperationCanceledException> no cancelamento.</span><span class="sxs-lookup"><span data-stu-id="20e9a-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="20e9a-110">Se algum outro token faz com que o cancelamento, o loop lançará um <xref:System.AggregateException> com um <xref:System.OperationCanceledException> como um InnerException.</span><span class="sxs-lookup"><span data-stu-id="20e9a-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e9a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20e9a-111">See Also</span></span>  
 [<span data-ttu-id="20e9a-112">Paralelismo de dados</span><span class="sxs-lookup"><span data-stu-id="20e9a-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="20e9a-113">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="20e9a-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
