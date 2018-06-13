---
title: O pool de threads gerenciados
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- thread pooling [.NET Framework]
- thread pools [.NET Framework]
- threading [.NET Framework], thread pool
- threading [.NET Framework], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3894229ff5561e50d42a36f576a89ee7bf01c067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592412"
---
# <a name="the-managed-thread-pool"></a>O pool de threads gerenciados
A classe <xref:System.Threading.ThreadPool> fornece ao seu aplicativo um pool de threads de trabalho gerenciados pelo sistema, permitindo que você se concentre em tarefas de aplicativo, e não no gerenciamento de threads. Se você tiver tarefas curtas que exigem processamento em segundo plano, o pool de threads gerenciados será uma maneira fácil de aproveitar os vários threads. Por exemplo, a partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode criar objetos <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601> que executam tarefas assíncronas em threads do pool de threads.  
  
> [!NOTE]
>  A partir do [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], a taxa de transferência do pool de threads melhora consideravelmente em três áreas importantes, as quais foram identificadas como afunilamentos em versões anteriores do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]: tarefas de enfileiramento, expedição de threads do pool de threads e expedição de threads de conclusão de E/S. Para usar essa funcionalidade, seu aplicativo deve ser direcionado ao [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] ou posterior.  
  
 Para tarefas em segundo plano que interagem com a interface do usuário, o .NET Framework versão 2.0 fornece também a classe <xref:System.ComponentModel.BackgroundWorker>, que se comunicam por meio de eventos gerados no thread da interface do usuário.  
  
 O .NET Framework usa threads do pool de threads para muitos fins, incluindo a conclusão de E/S assíncrona, retornos de chamada do timer, operações de espera registradas, chamadas de método assíncrono usando delegados e conexões de soquete <xref:System.Net>.  
  
## <a name="when-not-to-use-thread-pool-threads"></a>Quando não usar o thread do pool de threads  
 Há várias situações nas quais é apropriado criar e gerenciar seus próprios threads em vez de usar os threads do pool de threads:  
  
-   Você precisa de um thread em primeiro plano.  
  
-   Você precisa que um thread tenha uma prioridade específica.  
  
-   Há tarefas que causam o bloqueio do thread por longos períodos. O pool de threads tem um número máximo de threads, portanto, a existência de muitos threads do pool de threads bloqueados pode impedir a inicialização das tarefas.  
  
-   Você precisa colocar os threads em um apartamento de thread único. Todos os threads <xref:System.Threading.ThreadPool> estão no apartamento de vários threads.  
  
-   Você precisa ter uma identidade estável associada ao thread, ou dedicar um thread a uma tarefa.  
  
## <a name="thread-pool-characteristics"></a>Características do pool de threads  
 Threads do pool de threads existem em segundo plano. Confira [Threads em primeiro plano e em segundo plano](../../../docs/standard/threading/foreground-and-background-threads.md). Cada thread usa o tamanho da pilha padrão, é executado com prioridade padrão e está no apartamento de vários threads.  
  
 Há apenas um pool de threads por processo.  
  
### <a name="exceptions-in-thread-pool-threads"></a>Exceções em threads do pool de threads  
 Exceções sem tratamento nos threads do pool de threads encerram o processo. Há três exceções a essa regra:  
  
-   Um <xref:System.Threading.ThreadAbortException> é gerado em um thread do pool de threads porque <xref:System.Threading.Thread.Abort%2A> foi chamado.  
  
-   Um <xref:System.AppDomainUnloadedException> é gerado em um thread do pool de threads porque o domínio do aplicativo está sendo descarregado.  
  
-   O CLR ou um processo de host encerra o thread.  
  
 Para saber mais, veja [Exceções em threads gerenciados](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  Nas versões do .NET Framework 1.0 e 1.1, o CLR intercepta silenciosamente algumas exceções sem tratamento nos threads do pool de threads. Isso pode corromper o estado do aplicativo e, eventualmente, fazer com que aplicativos sejam suspensos, o que pode ser muito difícil de depurar.  
  
### <a name="maximum-number-of-thread-pool-threads"></a>Número máximo de threads do pool de threads  
 O número de operações que podem ser enfileiradas para o pool de threads é limitado apenas pela memória disponível; no entanto, o pool de threads limita o número de threads que podem estar ativos simultaneamente no processo. A partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o tamanho padrão do pool de threads de um processo depende de vários fatores, como o tamanho do espaço de endereço virtual. Um processo pode chamar o método <xref:System.Threading.ThreadPool.GetMaxThreads%2A> para determinar o número de threads.  
  
 Você pode controlar o número máximo de threads usando os métodos <xref:System.Threading.ThreadPool.GetMaxThreads%2A> e <xref:System.Threading.ThreadPool.SetMaxThreads%2A>.  
  
> [!NOTE]
>  Nas versões 1.0 e 1.1 do .NET Framework, o tamanho do pool de threads não pode ser definido no código gerenciado. O código que hospeda o CLR pode definir o tamanho usando `CorSetMaxThreads`, definido em mscoree.h.  
  
### <a name="thread-pool-minimums"></a>Mínimo de pool de threads  
 O pool de threads fornece novos threads de trabalho ou threads de conclusão de E/S sob demanda, até atingir um mínimo especificado para cada categoria. Você pode usar o método <xref:System.Threading.ThreadPool.GetMinThreads%2A> para obter esses valores mínimos.  
  
> [!NOTE]
>  Quando a demanda é baixa, o número real de threads do pool de threads pode ficar abaixo dos valores mínimos.  
  
 Quando o mínimo é atingido, o pool de threads pode criar threads adicionais ou aguardar a conclusão de algumas tarefas. A partir do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], o pool de threads cria e destrói threads de trabalho a fim de otimizar a taxa de transferência, que é definida como o número de tarefas concluídas por unidade de tempo. Pouquíssimos threads podem não fazer um uso ideal dos recursos disponíveis, enquanto muitos threads podem aumentar a contenção de recursos.  
  
> [!CAUTION]
>  Use o método <xref:System.Threading.ThreadPool.SetMinThreads%2A> para aumentar o número mínimo de threads ociosos. No entanto, o aumento desnecessário desses valores pode causar problemas de desempenho. Se muitas tarefas começarem ao mesmo tempo, todas elas podem parecer lentas. Na maioria dos casos, o pool de threads terá um desempenho melhor com seu próprio algoritmo de alocação de threads.  
  
## <a name="skipping-security-checks"></a>Ignorar as verificações de segurança  
 O pool de threads também fornece os métodos <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> e <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType>. Use estes métodos somente quando você tiver certeza de que a pilha do chamador é irrelevante a qualquer verificação de segurança executada durante a execução da tarefa em fila. <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> e <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> capturam a pilha do chamador, que é mesclada na pilha do thread do pool de threads quando o thread começa a executar uma tarefa. Se uma verificação de segurança for necessária, toda a pilha deverá ser verificada. Embora a verificação forneça segurança, também tem um custo de desempenho.  
  
## <a name="using-the-thread-pool"></a>Usar o pool de threads  
 A partir do [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], a maneira mais fácil de usar o pool de threads é usando a [TPL (Biblioteca de paralelismo de tarefas)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md). Por padrão, tipos de biblioteca de paralelismo como <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601> use threads do pool de threads para executar tarefas. Você também pode usar o pool de threads chamando <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> no código gerenciado (ou `CorQueueUserWorkItem` no código não gerenciado) e passando um delegado <xref:System.Threading.WaitCallback> que representa o método que executa a tarefa. Outra maneira de usar o pool de threads é enfileirando itens de trabalho relacionados a uma operação de espera usando o método <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> e passando um <xref:System.Threading.WaitHandle> que, quando sinalizado ou após tempo limite, chama o método representado pelo delegado <xref:System.Threading.WaitOrTimerCallback>. Os threads do pool de thread são usados para invocar métodos de retorno de chamada.  
  
## <a name="threadpool-examples"></a>Exemplos de ThreadPool  
 Os exemplos de código nesta seção demonstram o pool de threads usando a classe <xref:System.Threading.Tasks.Task>, o método <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> e o método <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType>.  
  
-   [Executar tarefas assíncronas com a Biblioteca de paralelismo de tarefas](#TaskParallelLibrary)  
  
-   [Executar o código de maneira assíncrona com QueueUserWorkItem](#ExecuteCodeWithQUWI)  
  
-   [Fornecer dados de tarefa para QueueUserWorkItem](#TaskDataForQUWI)  
  
-   [Usar RegisterWaitForSingleObject](#RegisterWaitForSingleObject)  
  
<a name="TaskParallelLibrary"></a>   
### <a name="executing-asynchronous-tasks-with-the-task-parallel-library"></a>Executar tarefas assíncronas com a Biblioteca de paralelismo de tarefas  
 O exemplo a seguir mostra como criar e usar um objeto <xref:System.Threading.Tasks.Task> chamando o método <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>. Para obter um exemplo que usa a classe <xref:System.Threading.Tasks.Task%601> para retornar um valor de uma tarefa assíncrona, consulte [Como retornar um valor de uma tarefa](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).  
  
 [!code-csharp[System.Threading.Tasks.Task#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.task/cs/startnew.cs#01)]
 [!code-vb[System.Threading.Tasks.Task#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.task/vb/startnew.vb#01)]  
  
<a name="ExecuteCodeWithQUWI"></a>   
### <a name="executing-code-asynchronously-with-queueuserworkitem"></a>Executar o código de maneira assíncrona com QueueUserWorkItem  
 O exemplo a seguir enfileira uma tarefa muito simples, representada pelo método `ThreadProc`, usando o método <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>.  
  
 [!code-cpp[Conceptual.ThreadPool#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.ThreadPool#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source1.cs#1)]
 [!code-vb[Conceptual.ThreadPool#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source1.vb#1)]  
  
<a name="TaskDataForQUWI"></a>   
### <a name="supplying-task-data-for-queueuserworkitem"></a>Fornecer dados de tarefa para QueueUserWorkItem  
 O exemplo de código a seguir usa o método <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> para enfileirar uma tarefa e fornecer os dados para a tarefa.  
  
 [!code-cpp[Conceptual.ThreadPool#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.ThreadPool#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source2.cs#2)]
 [!code-vb[Conceptual.ThreadPool#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source2.vb#2)]  
  
<a name="RegisterWaitForSingleObject"></a>   
### <a name="using-registerwaitforsingleobject"></a>Usar RegisterWaitForSingleObject  
 O exemplo a seguir demonstra vários recursos de threading.  
  
-   Enfileiramento de uma tarefa para execução pelos threads <xref:System.Threading.ThreadPool>, com o método <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A>.  
  
-   Sinalização de uma tarefa a ser executada, com <xref:System.Threading.AutoResetEvent>. Confira [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).  
  
-   Tratamento de tempos limite e sinalizações com um delegado <xref:System.Threading.WaitOrTimerCallback>.  
  
-   Cancelamento de uma tarefa em fila com <xref:System.Threading.RegisteredWaitHandle>.  
  
 [!code-cpp[Conceptual.ThreadPool#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.ThreadPool#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source3.cs#3)]
 [!code-vb[Conceptual.ThreadPool#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.Tasks.Task>  
 <xref:System.Threading.Tasks.Task%601>  
 [TPL (Biblioteca de Paralelismo de Tarefas)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [TPL (Biblioteca de Paralelismo de Tarefas)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Como retornar um valor de uma tarefa](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Threads e threading](../../../docs/standard/threading/threads-and-threading.md)  
 [E/S de arquivo assíncrona](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [Temporizadores](../../../docs/standard/threading/timers.md)
