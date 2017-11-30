---
title: "Como especificar o modo de execução em PLINQ"
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
helpviewer_keywords: PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 745ceae9832582c7b66a56075d128f9cf1c8ff69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Como especificar o modo de execução em PLINQ
Este exemplo mostra como forçar PLINQ para ignorar a heurística seu padrão e paralelizar uma consulta, independentemente da forma da consulta.  
  
> [!WARNING]
>  Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente. Para obter mais informações sobre velocidade, consulte [Noções básicas sobre agilização em PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ é projetado para explorar oportunidades de paralelização. No entanto, nem todas as consultas se beneficiar da execução paralela. Por exemplo, quando uma consulta contém um delegado de único usuário que faz muito pouco trabalho, a consulta será normalmente executada mais rapidamente em sequência. Isso ocorre porque a sobrecarga envolvida na habilitação de paralelização de execução é mais cara do que o aumento de velocidade é obtido. Portanto, o PLINQ não paralelizar automaticamente todas as consultas. Primeiro, ele examina a forma da consulta e vários operadores que o compõem. PLINQ no modo de execução padrão com base nesta análise, pode decidir executar algumas ou todas as consultas em sequência. No entanto, em alguns casos você pode saber mais sobre a consulta que o PLINQ é capaz de determinar a partir de sua análise. Por exemplo, você pode saber se um delegado é muito caro e que a consulta se beneficiam paralelização definitivamente. Nesses casos, você pode usar o <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> método e especifique o <xref:System.Linq.ParallelExecutionMode.ForceParallelism> valor para instruir o PLINQ sempre executar a consulta como paralelo.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Recorte e cole este código para o [exemplo de dados PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) e chame o método de `Main`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
