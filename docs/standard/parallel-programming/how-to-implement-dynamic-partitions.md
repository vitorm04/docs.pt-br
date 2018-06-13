---
title: como implementar partições dinâmicas
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bffc25cb5c3ae3671fdf6018158b81549c360e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580426"
---
# <a name="how-to-implement-dynamic-partitions"></a>como implementar partições dinâmicas
O exemplo a seguir mostra como implementar um <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> personalizado que implementa o particionamento dinâmico e pode ser usado de determinadas sobrecargas <xref:System.Threading.Tasks.Parallel.ForEach%2A> e do PLINQ.  
  
## <a name="example"></a>Exemplo  
 Cada vez que uma partição chama <xref:System.Collections.IEnumerator.MoveNext%2A> no enumerador, o enumerador fornece a partição com um elemento de lista. No caso do PLINQ e do <xref:System.Threading.Tasks.Parallel.ForEach%2A>, a partição é uma instância de <xref:System.Threading.Tasks.Task>. Como as solicitações ocorrem simultaneamente em vários threads, o acesso ao índice atual é sincronizado.  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 Este é um exemplo de particionamento, com cada parte consistindo em um elemento. Ao fornecer mais elementos de uma vez, você pode reduzir a contenção no bloqueio e, teoricamente, alcançar um desempenho mais rápido. No entanto, em algum momento, partes maiores podem exigir lógica de balanceamento de carga adicional para manter todos os threads ocupados até que todo o trabalho seja concluído.  
  
## <a name="see-also"></a>Consulte também  
 [Particionadores personalizados para PLINQ e TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [Como implementar um particionador para particionamento estático](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
