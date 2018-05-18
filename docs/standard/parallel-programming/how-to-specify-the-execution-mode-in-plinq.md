---
title: Como especificar o modo de execução em PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebea62f33c5df252dd73a0708f31612cd2998728
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Como especificar o modo de execução em PLINQ
Este exemplo mostra como forçar o PLINQ a ignorar a heurística padrão e paralelizar uma consulta, independentemente da forma da consulta.  
  
> [!WARNING]
>  Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente. Para saber mais sobre agilização, confira [Noções básicas sobre agilização no PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 O PLINQ foi projetado para explorar oportunidades de paralelização. No entanto, nem todas as consultas se beneficiam da execução paralela. Por exemplo, quando uma consulta contiver um representante de usuário único que realize muito pouco trabalho, a consulta será normalmente executada mais rapidamente em sequência. Isso ocorre porque a sobrecarga envolvida na habilitação de paralelização de execução é mais cara do que o aumento de velocidade que é obtido. Portanto, o PLINQ não paraleliza automaticamente todas as consultas. Primeiro, examina a forma da consulta e os vários operadores que a compõem. Com base nessa análise, o PLINQ no modo de execução padrão pode decidir executar algumas das consultas em sequência ou todas elas. No entanto, em alguns casos, você pode saber mais sobre a consulta do que o PLINQ é capaz de determinar com base na análise. Por exemplo, você pode saber que um representante é muito caro e que a consulta se beneficiará definitivamente da paralelização. Nesses casos, você pode usar o método <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> e especificar o valor <xref:System.Linq.ParallelExecutionMode.ForceParallelism> para instruir o PLINQ a sempre executar a consulta em paralelo.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Recorte e cole este código para o [Exemplo de Dados do PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) e chame o método `Main`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
