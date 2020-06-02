---
title: 'Como: avaliar o desempenho da consulta PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: f240b2c275305aec5699eb42406e0689925490a8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288180"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="4a8b2-102">Como: avaliar o desempenho da consulta PLINQ</span><span class="sxs-lookup"><span data-stu-id="4a8b2-102">How to: Measure PLINQ Query Performance</span></span>

<span data-ttu-id="4a8b2-103">Este exemplo mostra como usar a <xref:System.Diagnostics.Stopwatch> classe para medir o tempo necessário para que uma consulta PLINQ seja executada.</span><span class="sxs-lookup"><span data-stu-id="4a8b2-103">This example shows how to use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a8b2-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4a8b2-104">Example</span></span>  
 <span data-ttu-id="4a8b2-105">Este exemplo usa um loop `foreach` vazio (`For Each` no Visual Basic) para medir o tempo necessário de execução da consulta.</span><span class="sxs-lookup"><span data-stu-id="4a8b2-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="4a8b2-106">No código da vida real, o loop normalmente contém etapas de processamento adicionais que se juntam ao tempo de execução total de consultas.</span><span class="sxs-lookup"><span data-stu-id="4a8b2-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="4a8b2-107">Observe que o cronômetro não é iniciado até logo antes do loop, porque é quando a execução da consulta é iniciada.</span><span class="sxs-lookup"><span data-stu-id="4a8b2-107">Notice that the stopwatch is not started until just before the loop, because that's when the query execution begins.</span></span> <span data-ttu-id="4a8b2-108">Se você precisar de uma medição mais refinada, use a propriedade `ElapsedTicks` em vez de `ElapsedMilliseconds`.</span><span class="sxs-lookup"><span data-stu-id="4a8b2-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="4a8b2-109">O tempo de execução total é uma métrica útil quando você está experimentando implementações de consulta, mas nem sempre diz a história inteira.</span><span class="sxs-lookup"><span data-stu-id="4a8b2-109">The total execution time is a useful metric when you are experimenting with query implementations, but it doesn't always tell the whole story.</span></span> <span data-ttu-id="4a8b2-110">Para obter uma visão mais profunda e mais rica da interação dos threads de consulta entre si e com outros processos em execução, use o [Visualizador de simultaneidade](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="4a8b2-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a8b2-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="4a8b2-111">See also</span></span>

- [<span data-ttu-id="4a8b2-112">LINQ paralelo (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="4a8b2-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
