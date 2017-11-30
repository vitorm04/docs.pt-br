---
title: Como combinar consultas LINQ paralelas e sequenciais
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
helpviewer_keywords: parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4da91ff535059b181baa637164a854cd75d06334
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="3bb7b-102">Como combinar consultas LINQ paralelas e sequenciais</span><span class="sxs-lookup"><span data-stu-id="3bb7b-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="3bb7b-103">Este exemplo mostra como usar o <xref:System.Linq.ParallelEnumerable.AsSequential%2A> método para instruir o PLINQ para processar todos os operadores subsequentes na consulta em sequência.</span><span class="sxs-lookup"><span data-stu-id="3bb7b-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="3bb7b-104">Embora o processamento sequencial é geralmente mais lento que paralelo, às vezes, é necessário para gerar resultados corretos.</span><span class="sxs-lookup"><span data-stu-id="3bb7b-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="3bb7b-105">Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente.</span><span class="sxs-lookup"><span data-stu-id="3bb7b-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="3bb7b-106">Para obter mais informações sobre velocidade, consulte [Noções básicas sobre agilização em PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="3bb7b-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bb7b-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3bb7b-107">Example</span></span>  
 <span data-ttu-id="3bb7b-108">O exemplo a seguir mostra um cenário em que <xref:System.Linq.ParallelEnumerable.AsSequential%2A> é necessária, ou seja, para preservar a ordem que foi estabelecido em uma cláusula anterior da consulta.</span><span class="sxs-lookup"><span data-stu-id="3bb7b-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3bb7b-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="3bb7b-109">Compiling the Code</span></span>  
 <span data-ttu-id="3bb7b-110">Para compilar e executar esse código, cole-o no [exemplo de dados PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) de projeto, adicione uma linha para chamar o método de `Main`, e pressione F5.</span><span class="sxs-lookup"><span data-stu-id="3bb7b-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb7b-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bb7b-111">See Also</span></span>  
 [<span data-ttu-id="3bb7b-112">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="3bb7b-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
