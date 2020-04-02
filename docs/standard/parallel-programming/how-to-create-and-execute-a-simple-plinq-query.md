---
title: Como criar e executar uma consulta PLINQ simples
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
ms.openlocfilehash: 0cdef6d3826e4e7522bf3f6ed69060b8ef1c5e1b
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588292"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="c084e-102">Como criar e executar uma consulta PLINQ simples</span><span class="sxs-lookup"><span data-stu-id="c084e-102">How to: Create and Execute a Simple PLINQ Query</span></span>
<span data-ttu-id="c084e-103">O exemplo a seguir mostra como criar uma consulta Parallel LINQ simples usando o método de extensão <xref:System.Linq.ParallelEnumerable.AsParallel%2A> na sequência de origem e executando a consulta usando o método <xref:System.Linq.ParallelEnumerable.ForAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="c084e-103">The following example shows how to create a simple Parallel LINQ query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A> extension method on the source sequence, and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c084e-104">Esta documentação usa expressões lambda para definir representantes na PLINQ.</span><span class="sxs-lookup"><span data-stu-id="c084e-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="c084e-105">Se você não estiver familiarizado com expressões lambda em C# ou Visual Basic, consulte [Expressões Lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="c084e-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c084e-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c084e-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="c084e-107">Este exemplo demonstra o padrão básico para criar e executar qualquer consulta Parallel LINQ quando a ordenação da sequência de resultado não é importante. Geralmente, as consultas não ordenadas são mais rápidas que as ordenadas.</span><span class="sxs-lookup"><span data-stu-id="c084e-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important; unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="c084e-108">A consulta particiona a origem em tarefas executadas de maneira assíncrona em vários threads.</span><span class="sxs-lookup"><span data-stu-id="c084e-108">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="c084e-109">A ordem em que cada tarefa é concluída depende não apenas da quantidade de trabalho envolvido para processar os elementos na partição, mas também de fatores externos como a maneira que o sistema operacional agenda cada thread.</span><span class="sxs-lookup"><span data-stu-id="c084e-109">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="c084e-110">Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente.</span><span class="sxs-lookup"><span data-stu-id="c084e-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="c084e-111">Para saber mais sobre agilização, confira [Noções básicas sobre agilização no PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="c084e-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="c084e-112">Para saber mais sobre como preservar a ordenação de elementos em uma consulta, consulte [Como controlar a ordem em uma consulta PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="c084e-112">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c084e-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="c084e-113">See also</span></span>

- [<span data-ttu-id="c084e-114">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="c084e-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
