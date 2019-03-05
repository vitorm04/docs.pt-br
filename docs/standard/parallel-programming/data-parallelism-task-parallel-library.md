---
title: Paralelismo de dados (biblioteca de tarefas paralelas)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, data
ms.assetid: 3f05f33f-f1da-4b16-81c2-9ceff1bef449
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3450908cadff453df79ab8fcf10285c25dfa50a7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976220"
---
# <a name="data-parallelism-task-parallel-library"></a>Paralelismo de dados (biblioteca de tarefas paralelas)
*Paralelismo de dados* refere-se a cenários em que a mesma operação é realizada simultaneamente (ou seja, em paralelo) em elementos em uma matriz ou coleção de origem. Nas operações paralelas de dados, a coleção de origem é particionada de modo que múltiplos threads possam operar em segmentos diferentes simultaneamente.  
  
 A biblioteca de paralelismo de tarefas (TPL) suporta paralelismo de dados por meio da classe <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>. Essa classe fornece implementações paralelas baseadas em métodos dos loops [for](~/docs/csharp/language-reference/keywords/for.md) e [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) (`For` e `For Each` no Visual Basic). Você grava a lógica do loop para um loop <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ou <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> tanto quanto você gravaria um loop sequencial. Você não precisa criar threads ou listar itens de trabalho. Nos loops básicos, você não precisa usar bloqueios. A TPL manipula todo o trabalho de nível baixo para você. Para obter informações detalhadas sobre o uso de <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, baixe o documento [Padrões da programação paralela: noções básicas e aplicação de padrões paralelos com o .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222). O exemplo de código a seguir mostra um loop `foreach` simples e seu equivalente paralelo.  
  
> [!NOTE]
>  Esta documentação usa expressões lambda para definir delegados na TLP. Se você não estiver familiarizado com expressões lambda no C# ou no Visual Basic, veja [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Quando um loop paralelo é executado, o TPL particiona a fonte de dados para que o loop possa operar em várias partes simultaneamente. Nos bastidores, o Agendador de Tarefas particiona a tarefa com base na carga de trabalho e recursos do sistema. Quando possível, o agendador redistribui o trabalho entre vários threads e processadores se a carga de trabalho ficar desequilibrada.  
  
> [!NOTE]
>  Você também pode fornecer seu próprio particionador ou agendador personalizado. Para obter mais informações, confira [Particionadores personalizados para PLINQ e TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) e [Agendadores de tarefas](xref:System.Threading.Tasks.TaskScheduler).  
  
 Ambos os métodos <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> têm várias sobrecargas que permitem parar ou interromper a execução do loop, monitorar o estado do loop em outros threads, manter o estado local do thread, finalizar os objetos locais do thread, controlar o grau de simultaneidade, e assim por diante. Os tipos auxiliares que permitem essa funcionalidade incluem <xref:System.Threading.Tasks.ParallelLoopState>, <xref:System.Threading.Tasks.ParallelOptions>, <xref:System.Threading.Tasks.ParallelLoopResult>, <xref:System.Threading.CancellationToken>, e <xref:System.Threading.CancellationTokenSource>.  
  
 Para obter mais informações, confira [Padrões da programação paralela: noções básicas e aplicação de padrões paralelos com o .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222).  
  
 O paralelismo de dados com a sintaxe declarativa ou similar a uma consulta é suportado pelo PLINQ. Para obter mais informações, consulte [PLINQ (Parallel LINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Como: escrever um loop Parallel.For simples](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Descreve como gravar um loop <xref:System.Threading.Tasks.Parallel.For%2A> sobre qualquer matriz ou coleção de origem <xref:System.Collections.Generic.IEnumerable%601> indexável.|  
|[Como: escrever um loop Parallel.ForEach simples](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|Descreve como gravar um loop <xref:System.Threading.Tasks.Parallel.ForEach%2A> sobre qualquer coleção de origem <xref:System.Collections.Generic.IEnumerable%601>.|  
|[Como: Parar ou interromper um loop Parallel.For](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100))|Descreve como parar ou interromper um loop paralelo para que todos os threads sejam informados da ação.|  
|[Como: Gravar um loop Parallel.For com variáveis locais de thread](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Descreve como gravar um loop <xref:System.Threading.Tasks.Parallel.For%2A> em que cada thread mantém uma variável privada que não está visível para outros threads, e como sincronizar os resultados de todos os threads quando o loop for concluído.|  
|[Como: escrever um loop Parallel.ForEach com variáveis locais de partição](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|Descreve como gravar um loop <xref:System.Threading.Tasks.Parallel.ForEach%2A> em que cada thread mantém uma variável privada que não está visível para outros threads, e como sincronizar os resultados de todos os threads quando o loop for concluído.|  
|[Como: cancelar um loop Parallel.For ou ForEach](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Descreve como cancelar um loop paralelo usando um <xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Como: acelerar corpos de loop pequenos](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Descreve uma maneira de acelerar a execução quando um corpo de loop é muito pequeno.|  
|[TPL (Biblioteca de Paralelismo de Tarefas)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Fornece uma visão geral da biblioteca de paralelismo de tarefas.|  
|[Programação paralela](../../../docs/standard/parallel-programming/index.md)|Apresenta a Programação paralela no .NET Framework.|  
  
## <a name="see-also"></a>Consulte também

- [Programação paralela](../../../docs/standard/parallel-programming/index.md)
