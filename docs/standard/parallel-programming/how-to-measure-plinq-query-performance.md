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
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45618753"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="15139-102">como avaliar o desempenho de consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="15139-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="15139-103">Este exemplo mostra como usar a classe <xref:System.Diagnostics.Stopwatch> para medir o tempo de execução necessário de uma consulta PLINQ.</span><span class="sxs-lookup"><span data-stu-id="15139-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15139-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15139-104">Example</span></span>  
 <span data-ttu-id="15139-105">Este exemplo usa um loop `foreach` vazio (`For Each` no Visual Basic) para medir o tempo necessário de execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="15139-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="15139-106">No código da vida real, o loop normalmente contém etapas de processamento adicionais que se juntam ao tempo de execução total de consultas.</span><span class="sxs-lookup"><span data-stu-id="15139-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="15139-107">O cronômetro só é iniciado um pouco antes do loop, pois é quando começa a execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="15139-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="15139-108">Se você precisar de uma medição mais refinada, use a propriedade `ElapsedTicks` em vez de `ElapsedMilliseconds`.</span><span class="sxs-lookup"><span data-stu-id="15139-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="15139-109">O tempo total de execução é uma métrica útil quando você estiver experimentando com implantações de consulta, mas nem sempre ele aborda tudo.</span><span class="sxs-lookup"><span data-stu-id="15139-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="15139-110">Para uma visão mais profunda e mais rica da interação dos threads de consulta entre si e com outros processos em execução, use a Visualização Simultânea.</span><span class="sxs-lookup"><span data-stu-id="15139-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="15139-111">Para saber mais, confira [Visualização Simultânea](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="15139-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15139-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15139-112">See also</span></span>

- [<span data-ttu-id="15139-113">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="15139-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
