---
title: Como agilizar corpos de loop pequenos
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
helpviewer_keywords: parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d38d8beedf342720d4dc68026297edb457f5ed35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Como agilizar corpos de loop pequenos
Quando um <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop tem um corpo de pequeno, poderá executar mais lentamente do que o loop sequencial equivalente, como o [para](~/docs/csharp/language-reference/keywords/for.md) loop em c# e o [para](http://msdn.microsoft.com/en-us/c470a263-9b49-4308-8fd6-8592b84a7980) loop no Visual Basic. Desempenho mais lento é causado por sobrecarga envolvida no particionamento de dados e o custo de invocação de um representante em cada iteração do loop. Para resolver esses cenários, o <xref:System.Collections.Concurrent.Partitioner> classe fornece a <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> método, que permite que você forneça um loop sequencial do corpo do delegado, para que o delegado é chamado apenas uma vez por partição, em vez de uma vez a cada iteração. Para saber mais, veja [Particionadores personalizados para PLINQ e TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 A abordagem demonstrada neste exemplo é útil quando o loop executa uma quantidade mínima de trabalho. Como o trabalho se torna mais dispendioso, você provavelmente obterá o desempenho igual ou melhor usando um <xref:System.Threading.Tasks.Parallel.For%2A> ou <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop com o particionador padrão.  
  
## <a name="see-also"></a>Consulte também  
 [Paralelismo de dados](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Particionadores personalizados para PLINQ e TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
