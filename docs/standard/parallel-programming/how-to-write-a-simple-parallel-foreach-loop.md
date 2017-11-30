---
title: Como escrever um loop arallel.ForEach simples
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
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16d8cd3c3c01c2f9d83786e78f0eb1c45a38a49b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="2cb2a-102">Como escrever um loop arallel.ForEach simples</span><span class="sxs-lookup"><span data-stu-id="2cb2a-102">How to: Write a Simple Parallel.ForEach Loop</span></span>
<span data-ttu-id="2cb2a-103">Este exemplo mostra como usar um <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop para permitir o paralelismo de dados em relação a qualquer <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="2cb2a-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2cb2a-104">Esta documentação usa expressões lambda para definir representantes na PLINQ.</span><span class="sxs-lookup"><span data-stu-id="2cb2a-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="2cb2a-105">Se você não estiver familiarizado com expressões lambda no C# ou no Visual Basic, veja [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="2cb2a-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cb2a-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2cb2a-106">Example</span></span>  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 <span data-ttu-id="2cb2a-107">Um <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop funciona como um <xref:System.Threading.Tasks.Parallel.For%2A> loop.</span><span class="sxs-lookup"><span data-stu-id="2cb2a-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A> loop.</span></span> <span data-ttu-id="2cb2a-108">A coleção de origem está particionada e o trabalho agendado em vários segmentos, com base no ambiente do sistema.</span><span class="sxs-lookup"><span data-stu-id="2cb2a-108">The source collection is partitioned and the work is scheduled on multiple threads based on the system environment.</span></span> <span data-ttu-id="2cb2a-109">Quanto mais processadores no sistema, é executado mais rápido do método paralelo.</span><span class="sxs-lookup"><span data-stu-id="2cb2a-109">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="2cb2a-110">Para alguns conjuntos de origem, um loop sequencial pode ser mais rápido, dependendo do tamanho de origem e o tipo de trabalho que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="2cb2a-110">For some source collections, a sequential loop may be faster, depending on the size of the source, and the kind of work being performed.</span></span> <span data-ttu-id="2cb2a-111">Para obter mais informações sobre o desempenho, consulte [armadilhas em potencial em dados e paralelismo da tarefa](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span><span class="sxs-lookup"><span data-stu-id="2cb2a-111">For more information about performance, see [Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span></span>  
  
 <span data-ttu-id="2cb2a-112">Para obter mais informações sobre loops paralelos, consulte [como: gravar um Loop Parallel. for simples](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="2cb2a-112">For more information about parallel loops, see [How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>  
  
 <span data-ttu-id="2cb2a-113">Para usar <xref:System.Threading.Tasks.Parallel.ForEach%2A> com uma coleção não genérica, você pode usar o <xref:System.Linq.Enumerable.Cast%2A> método de extensão para converter a coleção para uma coleção genérica, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2cb2a-113">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 <span data-ttu-id="2cb2a-114">Você também pode usar o LINQ paralelo (PLINQ) para efetuar a paralelização de processamento de <xref:System.Collections.Generic.IEnumerable%601> fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="2cb2a-114">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="2cb2a-115">PLINQ permite que você use a sintaxe de consulta declarativa para expressar o comportamento de loop.</span><span class="sxs-lookup"><span data-stu-id="2cb2a-115">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="2cb2a-116">Para obter mais informações, consulte [PLINQ (Parallel LINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="2cb2a-116">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2cb2a-117">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="2cb2a-117">Compiling the Code</span></span>  
  
-   <span data-ttu-id="2cb2a-118">Copie e cole este código em um [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 2010 projeto de aplicativo de Console.</span><span class="sxs-lookup"><span data-stu-id="2cb2a-118">Copy and paste this code into a [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 2010 Console Application project.</span></span>  
  
-   <span data-ttu-id="2cb2a-119">Adicione uma referência ao System.Drawing.dll</span><span class="sxs-lookup"><span data-stu-id="2cb2a-119">Add a reference to System.Drawing.dll</span></span>  
  
-   <span data-ttu-id="2cb2a-120">Pressione F5</span><span class="sxs-lookup"><span data-stu-id="2cb2a-120">Press F5</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb2a-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cb2a-121">See Also</span></span>  
 [<span data-ttu-id="2cb2a-122">Paralelismo de dados</span><span class="sxs-lookup"><span data-stu-id="2cb2a-122">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="2cb2a-123">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="2cb2a-123">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="2cb2a-124">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="2cb2a-124">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
