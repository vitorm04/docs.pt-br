---
title: Parallel Programming in .NET (Programação paralela no .NET)
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
ms.openlocfilehash: ae129ef0cb2b331c1eb0220282f21fec6f6fb77d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134154"
---
# <a name="parallel-programming-in-net"></a>Parallel Programming in .NET (Programação paralela no .NET)

Muitos computadores pessoais e estações de trabalho têm vários núcleos de CPU, o que permite a execução simultânea de vários threads. Para tirar proveito do hardware, é possível paralelizar seu código para distribuir o trabalho entre vários processadores.

No passado, a paralelização exigia a manipulação em baixo nível de threads e de bloqueios. O Visual Studio e o .NET Framework aprimoram o suporte à programação paralela ao fornecer um tempo de execução, tipos de biblioteca de classes e ferramentas de diagnóstico. Esses recursos, que foram introduzidos com o .NET Framework 4, simplificam o desenvolvimento paralelo. É possível escrever código paralelo eficiente, refinado e dimensionável em uma linguagem natural sem precisar trabalhar diretamente com threads ou o pool de threads.

A ilustração a seguir oferece uma visão geral de alto nível da arquitetura de programação paralela do .NET Framework:

![Arquitetura de programação paralela .NET](./media/tpl-architecture.png)

## <a name="related-topics"></a>Tópicos relacionados

|Tecnologia|Descrição|
|----------------|-----------------|
|[TPL (Biblioteca de Paralelismo de Tarefas)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Fornece documentação para a classe <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>, a qual inclui versões paralelas de `For` e loops `ForEach`, e também para a classe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, a qual representa a forma preferencial de expressar operações assíncronas.|
|[PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|Uma implementação paralela do LINQ em Objects que melhora significativamente o desempenho em muitos cenários.|
|[Estruturas de dados para programação paralela](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|Fornece links para a documentação de classes de coleta com threads seguros, tipos de sincronização leves e tipos para inicialização lenta.|
|[Ferramentas de diagnóstico paralelo](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|Fornece links para a documentação de janelas do depurador para tarefas e pilhas paralelas, e para a [Visualização Simultânea](/visualstudio/profiling/concurrency-visualizer) do Visual Studio.|
|[Particionadores personalizados para PLINQ e TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|Descreve como os particionadores funcionam e como configurar os particionadores padrão ou criar um novo particionador.|
|[Agendadores de tarefas](xref:System.Threading.Tasks.TaskScheduler)|Descreve como os agendadores funcionam e como os agendadores padrão podem ser configurados.|
|[Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|Fornece uma visão geral das expressões lambda em C# e Visual Basic e mostra como elas são usadas em PLINQ e na Biblioteca Paralela de Tarefas.|
|[Para leitura adicional](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|Fornece links para informações adicionais e recursos de exemplo para a programação paralela no .NET.|

## <a name="see-also"></a>Consulte também

- [Visão Geral da Assincronia](../async.md)
- [Threading gerenciado](../threading/index.md)
