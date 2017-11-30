---
title: "Como especificar opções de mesclagem em PLINQ"
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
helpviewer_keywords: PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec601e8bbefd31650fb91c438b032942cfc93101
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="c3ede-102">Como especificar opções de mesclagem em PLINQ</span><span class="sxs-lookup"><span data-stu-id="c3ede-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="c3ede-103">Este exemplo mostra como especificar as opções de mesclagem que se aplicam a todos os operadores subsequentes em uma consulta PLINQ.</span><span class="sxs-lookup"><span data-stu-id="c3ede-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="c3ede-104">Você não precisa definir as opções de mesclagem explicitamente, mas fazer assim pode melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="c3ede-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="c3ede-105">Para obter mais informações sobre opções de mesclagem, consulte [opções de mesclagem em PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="c3ede-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c3ede-106">Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente.</span><span class="sxs-lookup"><span data-stu-id="c3ede-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="c3ede-107">Para obter mais informações sobre velocidade, consulte [Noções básicas sobre agilização em PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="c3ede-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3ede-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3ede-108">Example</span></span>  
 <span data-ttu-id="c3ede-109">O exemplo a seguir demonstra o comportamento das opções de mesclagem em um cenário básico que tem uma fonte não ordenada e aplica uma função cara para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="c3ede-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="c3ede-110">Em casos onde o <xref:System.Linq.ParallelMergeOptions.AutoBuffered> opção resulta em uma latência indesejável antes do primeiro elemento é produzido, tente o <xref:System.Linq.ParallelMergeOptions.NotBuffered> opção para gerar elementos resultados mais rápido e mais suave.</span><span class="sxs-lookup"><span data-stu-id="c3ede-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ede-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3ede-111">See Also</span></span>  
 <xref:System.Linq.ParallelMergeOptions>  
 [<span data-ttu-id="c3ede-112">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="c3ede-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
