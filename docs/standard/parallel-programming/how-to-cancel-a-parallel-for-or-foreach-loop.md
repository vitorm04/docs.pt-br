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
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Como cancelar um loop Parallel.For ou ForEach
O <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> métodos dão suporte ao cancelamento com o uso de tokens de cancelamento. Para obter mais informações sobre cancelamento em geral, consulte [cancelamento](../../../docs/standard/threading/cancellation-in-managed-threads.md). Em um loop paralelo, você deve fornecer o <xref:System.Threading.CancellationToken> para o método de <xref:System.Threading.Tasks.ParallelOptions> parâmetro e, em seguida, coloque a chamada paralela em um bloco try-catch.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como cancelar uma chamada para <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Você pode aplicar a mesma abordagem para um <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> chamar.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 Se o token que sinaliza o cancelamento é o mesmo token que é especificado no <xref:System.Threading.Tasks.ParallelOptions> instância, em seguida, o loop paralelo lançará um único <xref:System.OperationCanceledException> no cancelamento. Se algum outro token faz com que o cancelamento, o loop lançará um <xref:System.AggregateException> com um <xref:System.OperationCanceledException> como um InnerException.  
  
## <a name="see-also"></a>Consulte também  
 [Paralelismo de dados](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
