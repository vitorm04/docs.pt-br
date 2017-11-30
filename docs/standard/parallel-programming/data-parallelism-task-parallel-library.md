---
title: Paralelismo de dados (biblioteca de tarefas paralelas)
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
helpviewer_keywords: parallelism, data
ms.assetid: 3f05f33f-f1da-4b16-81c2-9ceff1bef449
caps.latest.revision: "25"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 13788542fa368bd5bcf1c2f277c9d83f84b35cdb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="data-parallelism-task-parallel-library"></a>Paralelismo de dados (biblioteca de tarefas paralelas)
*Paralelismo de dados* refere-se a cenários em que a mesma operação é executada simultaneamente (isto é, em paralelo) aos elementos em uma coleção de origem ou uma matriz. Operações paralelas de dados, a coleção de origem é particionada para que vários threads podem operar em diferentes segmentos simultaneamente.  
  
 O biblioteca paralela de tarefas (TPL) oferece suporte ao paralelismo de dados por meio de <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> classe. Essa classe fornece implementações de paralelas com base em método de [para](~/docs/csharp/language-reference/keywords/for.md) e [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) loops (`For` e `For Each` no Visual Basic). Gravar a lógica de loop para um <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ou <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop quanto você escreve um loop sequencial. Você não precisa criar threads ou itens de trabalho da fila. Em loops básico, você não precisa usam bloqueios. A TPL manipula todo o trabalho de baixo nível para você. Para obter informações detalhadas sobre o uso do <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, baixe o documento [padrões de programação paralela: Noções básicas e aplicação de padrões paralelos, com o .NET Framework 4](http://www.microsoft.com/download/details.aspx?id=19222). O exemplo de código a seguir mostra um simples `foreach` loop e seu equivalente paralelo.  
  
> [!NOTE]
>  Esta documentação usa expressões lambda para definir delegados na TLP. Se você não estiver familiarizado com expressões lambda no C# ou no Visual Basic, veja [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Quando um paralelo loop é executado, as partições TPL a fonte de dados para que o loop pode funcionar simultaneamente em várias partes. Nos bastidores, o Agendador de tarefas particiona a tarefa com base na carga de trabalho e recursos do sistema. Quando possível, o Agendador redistribui trabalho entre vários threads e processadores se a carga de trabalho ficar desbalanceada.  
  
> [!NOTE]
>  Você também pode fornecer sua própria particionador personalizado ou o Agendador. Para obter mais informações, consulte [Particionadores personalizados para PLINQ e TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) e [agendadores de tarefa](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65).  
  
 Tanto o <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> métodos têm várias sobrecargas que permitem que você para ou interromper a execução do loop, monitorar o estado de loop em outros threads, manter o estado de local de thread, finalizar objetos de local de thread, controla o grau de simultaneidade, e assim por diante. Os tipos de auxiliar que habilitar essa funcionalidade incluem <xref:System.Threading.Tasks.ParallelLoopState>, <xref:System.Threading.Tasks.ParallelOptions>, <xref:System.Threading.Tasks.ParallelLoopResult>, <xref:System.Threading.CancellationToken>, e <xref:System.Threading.CancellationTokenSource>.  
  
 Para obter mais informações, consulte [padrões de programação paralela](http://go.microsoft.com/fwlink/p/?LinkId=265491).  
  
 Há suporte para paralelismo de dados com a sintaxe declarativa ou semelhante a consultas, PLINQ. Para obter mais informações, consulte [PLINQ (Parallel LINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Como escrever um loop Parallel.For simples](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Descreve como escrever um <xref:System.Threading.Tasks.Parallel.For%2A> loop sobre qualquer matriz ou indexáveis <xref:System.Collections.Generic.IEnumerable%601> coleção de origem.|  
|[Como escrever um loop Parallel.ForEach simples](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|Descreve como escrever um <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop sobre qualquer <xref:System.Collections.Generic.IEnumerable%601> coleção de origem.|  
|[Como: interromper ou interromper um loop Parallel. for](http://msdn.microsoft.com/en-us/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e)|Descreve como interromper ou interromper um loop paralelo para que todos os threads serão informados sobre a ação.|  
|[Como escrever um loop Parallel.For com variáveis locais de thread](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Descreve como escrever um <xref:System.Threading.Tasks.Parallel.For%2A> loop na qual cada thread mantém uma variável privada que não é visível para qualquer outro thread e como sincronizar os resultados de todos os threads quando o loop estiver concluído.|  
|[Como escrever um loop Parallel.ForEach com variáveis locais de thread](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md)|Descreve como escrever um <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop na qual cada thread mantém uma variável privada que não é visível para qualquer outro thread e como sincronizar os resultados de todos os threads quando o loop estiver concluído.|  
|[Como cancelar um loop Parallel.For ou ForEach](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Descreve como cancelar um loop paralelo usando um<xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Como agilizar corpos de loop pequenos](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Descreve uma maneira para acelerar a execução quando um corpo do loop for muito pequeno.|  
|[TPL (Biblioteca de Paralelismo de Tarefas)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Fornece uma visão geral da biblioteca de tarefas paralelas.|  
|[Programação paralela](../../../docs/standard/parallel-programming/index.md)|Apresenta a programação paralela no .NET Framework.|  
  
## <a name="see-also"></a>Consulte também  
 [Programação paralela](../../../docs/standard/parallel-programming/index.md)
