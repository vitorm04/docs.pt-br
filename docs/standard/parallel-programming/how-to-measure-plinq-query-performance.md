---
title: como avaliar o desempenho de consulta PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd9e3a0ead62450e87225212f4fc6ecec6ec9489
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44211626"
---
# <a name="how-to-measure-plinq-query-performance"></a>como avaliar o desempenho de consulta PLINQ
Este exemplo mostra como usar a classe <xref:System.Diagnostics.Stopwatch> para medir o tempo de execução necessário de uma consulta PLINQ.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa um loop `foreach` vazio (`For Each` no Visual Basic) para medir o tempo necessário de execução da consulta. No código da vida real, o loop normalmente contém etapas de processamento adicionais que se juntam ao tempo de execução total de consultas. O cronômetro só é iniciado um pouco antes do loop, pois é quando começa a execução da consulta. Se você precisar de uma medição mais refinada, use a propriedade `ElapsedTicks` em vez de `ElapsedMilliseconds`.  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 O tempo total de execução é uma métrica útil quando você estiver experimentando com implantações de consulta, mas nem sempre ele aborda tudo. Para uma visão mais profunda e mais rica da interação dos threads de consulta entre si e com outros processos em execução, use a Visualização Simultânea. Para saber mais, confira [Visualização Simultânea](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Consulte também

- [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
