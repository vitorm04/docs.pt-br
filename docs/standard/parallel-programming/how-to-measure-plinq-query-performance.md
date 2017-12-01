---
title: como avaliar o desempenho de consulta PLINQ
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
helpviewer_keywords: PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03432e70454cb6203e55e340111a6cb7efe62dc4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-measure-plinq-query-performance"></a>como avaliar o desempenho de consulta PLINQ
Este exemplo mostra como usar o <xref:System.Diagnostics.Stopwatch> classe para medir o tempo necessário para uma consulta PLINQ executar.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa um vazio `foreach` loop (`For Each` no Visual Basic) para medir o tempo necessário para executar a consulta. No código do mundo real, o loop normalmente contém etapas de processamento adicionais que adicionar o tempo de execução total de consultas. Observe que o cronômetro não é iniciado até que antes do loop, pois esse é começa a execução da consulta. Se você precisar de mais de medição refinada, você pode usar o `ElapsedTicks` propriedade em vez de `ElapsedMilliseconds`.  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 Tempo total de execução é uma métrica útil quando você estiver experimentando com implementações de consulta, mas ele não aborda toda a história sempre. Para obter uma visão mais profunda e mais rica da interação entre os threads de consulta entre si e com outros processos em execução, use o Visualizador de simultaneidade. Para obter mais informações, consulte [Visualizador de simultaneidade](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Consulte também  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
