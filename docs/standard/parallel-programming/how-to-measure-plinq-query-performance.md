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
ms.openlocfilehash: 37bd3bc464f719876b2fe13ee1a11ebca4339988
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635825"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="67c24-102">como avaliar o desempenho de consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="67c24-102">How to: Measure PLINQ Query Performance</span></span>

<span data-ttu-id="67c24-103">Este exemplo mostra como <xref:System.Diagnostics.Stopwatch> usar a classe para medir o tempo necessário para uma consulta PLINQ ser executada.</span><span class="sxs-lookup"><span data-stu-id="67c24-103">This example shows how to use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67c24-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="67c24-104">Example</span></span>  
 <span data-ttu-id="67c24-105">Este exemplo usa um loop `foreach` vazio (`For Each` no Visual Basic) para medir o tempo necessário de execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="67c24-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="67c24-106">No código da vida real, o loop normalmente contém etapas de processamento adicionais que se juntam ao tempo de execução total de consultas.</span><span class="sxs-lookup"><span data-stu-id="67c24-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="67c24-107">Observe que o cronômetro não é iniciado até pouco antes do loop, porque é quando a execução da consulta começa.</span><span class="sxs-lookup"><span data-stu-id="67c24-107">Notice that the stopwatch is not started until just before the loop, because that's when the query execution begins.</span></span> <span data-ttu-id="67c24-108">Se você precisar de uma medição mais refinada, use a propriedade `ElapsedTicks` em vez de `ElapsedMilliseconds`.</span><span class="sxs-lookup"><span data-stu-id="67c24-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="67c24-109">O tempo total de execução é uma métrica útil quando você está experimentando implementações de consulta, mas nem sempre conta toda a história.</span><span class="sxs-lookup"><span data-stu-id="67c24-109">The total execution time is a useful metric when you are experimenting with query implementations, but it doesn't always tell the whole story.</span></span> <span data-ttu-id="67c24-110">Para ter uma visão mais profunda e rica da interação dos segmentos de consulta uns com os outros e com outros processos em execução, use o [Visualizador de Moedas .](/visualstudio/profiling/concurrency-visualizer)</span><span class="sxs-lookup"><span data-stu-id="67c24-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67c24-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="67c24-111">See also</span></span>

- [<span data-ttu-id="67c24-112">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="67c24-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
