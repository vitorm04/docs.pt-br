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
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>Como escrever uma função agregada PLINQ personalizada
Este exemplo mostra como usar o <xref:System.Linq.ParallelEnumerable.Aggregate%2A> método para aplicar uma função de agregação personalizada a uma sequência de origem.  
  
> [!WARNING]
>  Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente. Para obter mais informações sobre velocidade, consulte [Noções básicas sobre agilização em PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir calcula o desvio padrão de uma sequência de números inteiros.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 Este exemplo usa uma sobrecarga do operador de agregação padrão de consulta que é exclusivo para PLINQ. Essa sobrecarga toma um extra <xref:System.Func%603?displayProperty=nameWithType> como o terceiro parâmetro de entrada. Este delegado combina os resultados de todos os threads antes de executar o cálculo final nos resultados agregados. Neste exemplo, some a soma de todos os threads.  
  
 Observe que, quando um corpo da expressão lambda consiste em uma única expressão, o valor de retorno de <xref:System.Func%602?displayProperty=nameWithType> delegado é o valor da expressão.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.ParallelEnumerable>  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
