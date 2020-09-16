---
title: 'Como: criar e executar uma consulta PLINQ simples'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
ms.openlocfilehash: a5f6a26ada321bd351249c5179d050ee571b550c
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679325"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="c1170-102">Como: criar e executar uma consulta PLINQ simples</span><span class="sxs-lookup"><span data-stu-id="c1170-102">How to: Create and Execute a Simple PLINQ Query</span></span>

<span data-ttu-id="c1170-103">O exemplo neste artigo mostra como criar uma consulta LINQ (consulta integrada de linguagem paralela) simples usando o método de <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> extensão na sequência de origem e executando a consulta usando o <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="c1170-103">The example in this article shows how to create a simple Parallel Language Integrated Query (LINQ) query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> extension method on the source sequence and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1170-104">Esta documentação usa expressões lambda para definir representantes na PLINQ.</span><span class="sxs-lookup"><span data-stu-id="c1170-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="c1170-105">Se você não estiver familiarizado com expressões lambda em C# ou Visual Basic, consulte [expressões lambda em PLINQ e TPL](lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="c1170-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1170-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c1170-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="c1170-107">Este exemplo demonstra o padrão básico para criar e executar qualquer consulta LINQ paralela quando a ordenação da sequência de resultados não é importante.</span><span class="sxs-lookup"><span data-stu-id="c1170-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important.</span></span> <span data-ttu-id="c1170-108">As consultas não ordenadas são geralmente mais rápidas do que as consultas ordenadas.</span><span class="sxs-lookup"><span data-stu-id="c1170-108">Unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="c1170-109">A consulta particiona a origem em tarefas executadas de maneira assíncrona em vários threads.</span><span class="sxs-lookup"><span data-stu-id="c1170-109">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="c1170-110">A ordem em que cada tarefa é concluída depende não apenas da quantidade de trabalho envolvido para processar os elementos na partição, mas também de fatores externos como a maneira que o sistema operacional agenda cada thread.</span><span class="sxs-lookup"><span data-stu-id="c1170-110">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="c1170-111">Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente.</span><span class="sxs-lookup"><span data-stu-id="c1170-111">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="c1170-112">Para saber mais sobre agilização, confira [Noções básicas sobre agilização no PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="c1170-112">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="c1170-113">Para saber mais sobre como preservar a ordenação de elementos em uma consulta, consulte [Como controlar a ordem em uma consulta PLINQ](how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="c1170-113">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1170-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="c1170-114">See also</span></span>

- [<span data-ttu-id="c1170-115">LINQ paralelo (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="c1170-115">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
