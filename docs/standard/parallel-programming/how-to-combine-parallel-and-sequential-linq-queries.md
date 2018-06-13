---
title: Como combinar consultas LINQ paralelas e sequenciais
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c69d4d423bbdf72f2af7dad38812aa508df0067c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580244"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="5a36a-102">Como combinar consultas LINQ paralelas e sequenciais</span><span class="sxs-lookup"><span data-stu-id="5a36a-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="5a36a-103">Este exemplo mostra como usar o método <xref:System.Linq.ParallelEnumerable.AsSequential%2A> para instruir o PLINQ para processar todos os operadores subsequentes na consulta em sequência.</span><span class="sxs-lookup"><span data-stu-id="5a36a-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="5a36a-104">Embora o processamento sequencial seja geralmente mais lento que o paralelo, às vezes, ele é necessário para gerar resultados corretos.</span><span class="sxs-lookup"><span data-stu-id="5a36a-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="5a36a-105">Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente.</span><span class="sxs-lookup"><span data-stu-id="5a36a-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="5a36a-106">Para saber mais sobre agilização, confira [Noções básicas sobre agilização no PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="5a36a-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a36a-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a36a-107">Example</span></span>  
 <span data-ttu-id="5a36a-108">O exemplo a seguir mostra um cenário em que <xref:System.Linq.ParallelEnumerable.AsSequential%2A> é necessário, ou seja, para preservar a ordem que foi estabelecida em uma cláusula anterior da consulta.</span><span class="sxs-lookup"><span data-stu-id="5a36a-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5a36a-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5a36a-109">Compiling the Code</span></span>  
 <span data-ttu-id="5a36a-110">Para compilar e executar esse código, cole-o no projeto [Exemplo de Dados PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md), adicione uma linha para chamar o método `Main` e pressione F5.</span><span class="sxs-lookup"><span data-stu-id="5a36a-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a36a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a36a-111">See Also</span></span>  
 [<span data-ttu-id="5a36a-112">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="5a36a-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
