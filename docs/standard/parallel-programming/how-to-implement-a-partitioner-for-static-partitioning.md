---
title: "Como implementar um particionador para particionamento estático"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b28ff0bb8436fefc4956918889435e258ae98b12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="d1727-102">Como implementar um particionador para particionamento estático</span><span class="sxs-lookup"><span data-stu-id="d1727-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="d1727-103">O exemplo a seguir mostra uma maneira de implementar um particionador personalizado simple para PLINQ que executa o particionamento estático.</span><span class="sxs-lookup"><span data-stu-id="d1727-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="d1727-104">Porque o particionador não oferece suporte a partições dinâmicas, não é consumido de <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d1727-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d1727-105">Este particionador específico pode fornecer o aumento de velocidade sobre o particionador de intervalo padrão para fontes de dados para os quais cada elemento requer um volume crescente de tempo de processamento.</span><span class="sxs-lookup"><span data-stu-id="d1727-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1727-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d1727-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="d1727-107">As partições neste exemplo são baseadas na suposição de um aumento linear no tempo de processamento para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="d1727-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="d1727-108">No mundo real, pode ser difícil de prever os tempos de processamento dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="d1727-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="d1727-109">Se você estiver usando um particionador estático com uma fonte de dados específico, você pode otimizar a fórmula de particionamento para a fonte de, adicionar lógica de balanceamento de carga ou use um bloco abordagem de particionamento, conforme demonstrado no [como: implementar as partições dinâmicas](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="d1727-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1727-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1727-110">See Also</span></span>  
 [<span data-ttu-id="d1727-111">Particionadores personalizados para PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="d1727-111">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
