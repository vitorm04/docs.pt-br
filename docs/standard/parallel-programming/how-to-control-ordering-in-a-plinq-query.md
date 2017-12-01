---
title: Como controlar a ordem em uma consulta PLINQ
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
helpviewer_keywords: PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9e29aa825a68154e32a34a23ca170258092b88a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Como controlar a ordem em uma consulta PLINQ
Estes exemplos mostram como controlar a ordem em uma consulta PLINQ usando o <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> método de extensão.  
  
> [!WARNING]
>  Esses exemplos destinam-se principalmente para demonstrar o uso e podem ou não podem ser executada mais rápido do que o LINQ sequencial equivalente para consultas de objetos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir preserva a ordenação da sequência de origem. Isso às vezes é necessário; Por exemplo, alguns operadores de consulta exigem uma sequência ordenada de origem para produzir resultados corretos.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra alguns operadores sequência cuja origem provavelmente deve ser ordenados de consulta. Esses operadores funcionará em sequências não ordenadas, mas eles podem produzir resultados inesperados.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Para executar esse método, cole-a classe de PLINQDataSample o [exemplo de dados PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) do projeto e pressione F5.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como preservar a ordenação para a primeira parte de uma consulta, em seguida, remover a ordenação para aumentar o desempenho de uma cláusula join e reaplique pedidos à sequência de resultados final.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Para executar esse método, cole-a classe de PLINQDataSample o [exemplo de dados PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) do projeto e pressione F5.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.ParallelEnumerable>  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
