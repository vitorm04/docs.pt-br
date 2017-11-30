---
title: "Como escrever uma função agregada PLINQ personalizada"
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
helpviewer_keywords: PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b098f21e29d0d59cd99ddbb64af6246d9953a3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="da0c9-102">Como escrever uma função agregada PLINQ personalizada</span><span class="sxs-lookup"><span data-stu-id="da0c9-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="da0c9-103">Este exemplo mostra como usar o <xref:System.Linq.ParallelEnumerable.Aggregate%2A> método para aplicar uma função de agregação personalizada a uma sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="da0c9-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="da0c9-104">Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente.</span><span class="sxs-lookup"><span data-stu-id="da0c9-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="da0c9-105">Para obter mais informações sobre velocidade, consulte [Noções básicas sobre agilização em PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="da0c9-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="da0c9-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="da0c9-106">Example</span></span>  
 <span data-ttu-id="da0c9-107">O exemplo a seguir calcula o desvio padrão de uma sequência de números inteiros.</span><span class="sxs-lookup"><span data-stu-id="da0c9-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="da0c9-108">Este exemplo usa uma sobrecarga do operador de agregação padrão de consulta que é exclusivo para PLINQ.</span><span class="sxs-lookup"><span data-stu-id="da0c9-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="da0c9-109">Essa sobrecarga toma um extra <xref:System.Func%603?displayProperty=nameWithType> como o terceiro parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="da0c9-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="da0c9-110">Este delegado combina os resultados de todos os threads antes de executar o cálculo final nos resultados agregados.</span><span class="sxs-lookup"><span data-stu-id="da0c9-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="da0c9-111">Neste exemplo, some a soma de todos os threads.</span><span class="sxs-lookup"><span data-stu-id="da0c9-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="da0c9-112">Observe que, quando um corpo da expressão lambda consiste em uma única expressão, o valor de retorno de <xref:System.Func%602?displayProperty=nameWithType> delegado é o valor da expressão.</span><span class="sxs-lookup"><span data-stu-id="da0c9-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da0c9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da0c9-113">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="da0c9-114">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="da0c9-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
