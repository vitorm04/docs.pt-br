---
title: Como controlar a ordem em uma consulta PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaa08106126212345bb594cdeabe6e7281cd7b5e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45668881"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="48e87-102">Como controlar a ordem em uma consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="48e87-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="48e87-103">Estes exemplos mostram como controlar a ordem em uma consulta PLINQ usando o método de extensão <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.</span><span class="sxs-lookup"><span data-stu-id="48e87-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="48e87-104">Esses exemplos têm como objetivo principal demonstrar o uso, e talvez não executem tão rápido quanto a consulta LINQ to Objects sequencial equivalente.</span><span class="sxs-lookup"><span data-stu-id="48e87-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48e87-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48e87-105">Example</span></span>  
 <span data-ttu-id="48e87-106">O exemplo a seguir preserva a ordem da sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="48e87-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="48e87-107">Às vezes, isso é necessário; por exemplo, alguns operadores de consulta exigem uma sequência de origem ordenada para produzir resultados corretos.</span><span class="sxs-lookup"><span data-stu-id="48e87-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="48e87-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48e87-108">Example</span></span>  
 <span data-ttu-id="48e87-109">A exemplo a seguir mostra alguns operadores de consulta cuja sequência de origem provavelmente deve ser ordenada.</span><span class="sxs-lookup"><span data-stu-id="48e87-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="48e87-110">Esses operadores funcionarão em sequências não ordenadas, mas podem produzir resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="48e87-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="48e87-111">Para executar esse método, cole-o na classe PLINQDataSample no projeto [Exemplo de dados PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) e pressione F5.</span><span class="sxs-lookup"><span data-stu-id="48e87-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48e87-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48e87-112">Example</span></span>  
 <span data-ttu-id="48e87-113">O exemplo a seguir mostra como preservar a ordem da primeira parte de uma consulta e, depois, remover a ordem para aumentar o desempenho de uma cláusula join. Em seguida, reaplicar a ordem à sequência final de resultados.</span><span class="sxs-lookup"><span data-stu-id="48e87-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="48e87-114">Para executar esse método, cole-o na classe PLINQDataSample no projeto [Exemplo de dados PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) e pressione F5.</span><span class="sxs-lookup"><span data-stu-id="48e87-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e87-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48e87-115">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>  
- [<span data-ttu-id="48e87-116">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="48e87-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
