---
title: Como especificar o modo de execução em PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: f035dbcd5091d81a3cce3b9e9e683d836fe84bb7
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635807"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="c2a28-102">Como especificar o modo de execução em PLINQ</span><span class="sxs-lookup"><span data-stu-id="c2a28-102">How to: Specify the Execution Mode in PLINQ</span></span>

<span data-ttu-id="c2a28-103">Este exemplo mostra como forçar o PLINQ a ignorar a heurística padrão e paralelizar uma consulta, independentemente da forma da consulta.</span><span class="sxs-lookup"><span data-stu-id="c2a28-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2a28-104">Este exemplo destina-se a demonstrar o uso e pode não ser executado mais rápido do que a consulta seqüencial equivalente LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="c2a28-104">This example is intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="c2a28-105">Para saber mais sobre agilização, confira [Noções básicas sobre agilização no PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="c2a28-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2a28-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c2a28-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="c2a28-107">O PLINQ foi projetado para explorar oportunidades de paralelização.</span><span class="sxs-lookup"><span data-stu-id="c2a28-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="c2a28-108">No entanto, nem todas as consultas se beneficiam da execução paralela.</span><span class="sxs-lookup"><span data-stu-id="c2a28-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="c2a28-109">Por exemplo, quando uma consulta contém um único delegado de usuário que faz pouco trabalho, a consulta geralmente é executada sequencialmente mais rápido.</span><span class="sxs-lookup"><span data-stu-id="c2a28-109">For example, when a query contains a single user delegate that does little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="c2a28-110">A execução sequencial é mais rápida porque a sobrecarga envolvida em permitir a execução paralela é mais cara do que a aceleração obtida.</span><span class="sxs-lookup"><span data-stu-id="c2a28-110">Sequential execution is faster because the overhead involved in enabling parallelizing execution is more expensive than the speedup that's obtained.</span></span> <span data-ttu-id="c2a28-111">Portanto, o PLINQ não paraleliza automaticamente todas as consultas.</span><span class="sxs-lookup"><span data-stu-id="c2a28-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="c2a28-112">Primeiro, examina a forma da consulta e os vários operadores que a compõem.</span><span class="sxs-lookup"><span data-stu-id="c2a28-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="c2a28-113">Com base nessa análise, o PLINQ no modo de execução padrão pode decidir executar algumas das consultas em sequência ou todas elas.</span><span class="sxs-lookup"><span data-stu-id="c2a28-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="c2a28-114">No entanto, em alguns casos, você pode saber mais sobre a consulta do que o PLINQ é capaz de determinar com base na análise.</span><span class="sxs-lookup"><span data-stu-id="c2a28-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="c2a28-115">Por exemplo, você pode saber que um delegado é caro e que a consulta definitivamente se beneficiará da paralelização.</span><span class="sxs-lookup"><span data-stu-id="c2a28-115">For example, you may know that a delegate is expensive and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="c2a28-116">Nesses casos, você pode usar o método <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> e especificar o valor <xref:System.Linq.ParallelExecutionMode.ForceParallelism> para instruir o PLINQ a sempre executar a consulta em paralelo.</span><span class="sxs-lookup"><span data-stu-id="c2a28-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c2a28-117">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c2a28-117">Compiling the Code</span></span>  
 <span data-ttu-id="c2a28-118">Recorte e cole este código para o [Exemplo de Dados do PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) e chame o método `Main`.</span><span class="sxs-lookup"><span data-stu-id="c2a28-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2a28-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="c2a28-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="c2a28-120">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="c2a28-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
