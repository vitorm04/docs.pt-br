---
title: "Como especificar o modo de execução em PLINQ"
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
helpviewer_keywords: PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 745ceae9832582c7b66a56075d128f9cf1c8ff69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="0144b-102">Como especificar o modo de execução em PLINQ</span><span class="sxs-lookup"><span data-stu-id="0144b-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="0144b-103">Este exemplo mostra como forçar PLINQ para ignorar a heurística seu padrão e paralelizar uma consulta, independentemente da forma da consulta.</span><span class="sxs-lookup"><span data-stu-id="0144b-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="0144b-104">Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente.</span><span class="sxs-lookup"><span data-stu-id="0144b-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="0144b-105">Para obter mais informações sobre velocidade, consulte [Noções básicas sobre agilização em PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="0144b-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0144b-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0144b-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="0144b-107">PLINQ é projetado para explorar oportunidades de paralelização.</span><span class="sxs-lookup"><span data-stu-id="0144b-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="0144b-108">No entanto, nem todas as consultas se beneficiar da execução paralela.</span><span class="sxs-lookup"><span data-stu-id="0144b-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="0144b-109">Por exemplo, quando uma consulta contém um delegado de único usuário que faz muito pouco trabalho, a consulta será normalmente executada mais rapidamente em sequência.</span><span class="sxs-lookup"><span data-stu-id="0144b-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="0144b-110">Isso ocorre porque a sobrecarga envolvida na habilitação de paralelização de execução é mais cara do que o aumento de velocidade é obtido.</span><span class="sxs-lookup"><span data-stu-id="0144b-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="0144b-111">Portanto, o PLINQ não paralelizar automaticamente todas as consultas.</span><span class="sxs-lookup"><span data-stu-id="0144b-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="0144b-112">Primeiro, ele examina a forma da consulta e vários operadores que o compõem.</span><span class="sxs-lookup"><span data-stu-id="0144b-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="0144b-113">PLINQ no modo de execução padrão com base nesta análise, pode decidir executar algumas ou todas as consultas em sequência.</span><span class="sxs-lookup"><span data-stu-id="0144b-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="0144b-114">No entanto, em alguns casos você pode saber mais sobre a consulta que o PLINQ é capaz de determinar a partir de sua análise.</span><span class="sxs-lookup"><span data-stu-id="0144b-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="0144b-115">Por exemplo, você pode saber se um delegado é muito caro e que a consulta se beneficiam paralelização definitivamente.</span><span class="sxs-lookup"><span data-stu-id="0144b-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="0144b-116">Nesses casos, você pode usar o <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> método e especifique o <xref:System.Linq.ParallelExecutionMode.ForceParallelism> valor para instruir o PLINQ sempre executar a consulta como paralelo.</span><span class="sxs-lookup"><span data-stu-id="0144b-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0144b-117">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0144b-117">Compiling the Code</span></span>  
 <span data-ttu-id="0144b-118">Recorte e cole este código para o [exemplo de dados PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) e chame o método de `Main`.</span><span class="sxs-lookup"><span data-stu-id="0144b-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0144b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0144b-119">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
 [<span data-ttu-id="0144b-120">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="0144b-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
