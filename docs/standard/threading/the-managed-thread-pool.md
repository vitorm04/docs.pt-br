---
title: O pool de threads gerenciados
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
- cpp
helpviewer_keywords:
- thread pooling [.NET Framework]
- thread pools [.NET Framework]
- threading [.NET Framework], thread pool
- threading [.NET Framework], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38032fccce1a8f6f7cbcb3bbd3d3f9d008a74141
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="the-managed-thread-pool"></a>O pool de threads gerenciados
O <xref:System.Threading.ThreadPool> fornece a classe de seu aplicativo com um pool de threads de trabalho que são gerenciados pelo sistema, permitindo que você se concentrar em tarefas de aplicativo em vez de gerenciamento de threads. Se você tiver tarefas curtas que exigem processamento em segundo plano, o pool de threads gerenciados é uma maneira fácil para tirar proveito de vários threads. Por exemplo, começando com o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] você pode criar <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601> objetos, que executam tarefas assíncronas em threads de pool.  
  
> [!NOTE]
>  Começando com o [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], a taxa de transferência do pool de threads é significativamente aprimorada em três áreas principais que foram identificadas como afunilamentos em versões anteriores do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]: tarefas de enfileiramento de mensagens, despacho de threads de pool e despacho de e/s threads de conclusão. Para usar essa funcionalidade, seu aplicativo deve ter como destino o [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] ou posterior.  
  
 Para tarefas em segundo plano que interagem com a interface do usuário, o .NET Framework versão 2.0 fornece também a <xref:System.ComponentModel.BackgroundWorker> classe, que se comunicam por meio de eventos gerados no thread de interface do usuário.  
  
 O .NET Framework usa threads do pool para muitos propósitos, incluindo a conclusão de e/s assíncrona, retornos de chamada do timer, registrados aguarde as operações, chamadas de método assíncrono usando delegados, e <xref:System.Net> conexões de soquete.  
  
## <a name="when-not-to-use-thread-pool-threads"></a>Quando não usar o Thread do Pool de Threads  
 Há várias situações em que é apropriado criar e gerenciar seus próprios threads em vez de usar os threads do pool:  
  
-   Você precisa de um thread em primeiro plano.  
  
-   Você precisa de um thread para ter uma prioridade específica.  
  
-   Você tem que fazer com que o thread bloquear por longos períodos de tempo de tarefas. O pool de threads tem um número máximo de threads, para que um grande número de threads de pool de threads bloqueados pode impedir tarefas de inicialização.  
  
-   Você precisa colocar os threads em um single-threaded apartment. Todos os <xref:System.Threading.ThreadPool> threads estão no multi-threaded apartment.  
  
-   Você precisa ter uma identidade estável associada ao segmento ou dedicar um thread a uma tarefa.  
  
## <a name="thread-pool-characteristics"></a>Características do Pool de thread  
 Threads de pool são threads em segundo plano. Consulte [Threads primeiro plano e plano de fundo](../../../docs/standard/threading/foreground-and-background-threads.md). Cada thread usa o tamanho da pilha padrão, é executado com a prioridade padrão e está no multi-threaded apartment.  
  
 Há apenas um pool de threads por processo.  
  
### <a name="exceptions-in-thread-pool-threads"></a>Exceções em Threads de Pool  
 Exceções sem tratamento em threads de pool encerrar o processo. Há três exceções a essa regra:  
  
-   Um <xref:System.Threading.ThreadAbortException> é gerada em um pool de threads, porque <xref:System.Threading.Thread.Abort%2A> foi chamado.  
  
-   Um <xref:System.AppDomainUnloadedException> é gerada em um pool de threads, porque o domínio de aplicativo está sendo descarregado.  
  
-   O common language runtime ou um processo de host encerra o thread.  
  
 Para obter mais informações, consulte [exceções em Threads gerenciados](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  Nas versões do .NET Framework 1.0 e 1.1, o common language runtime silenciosamente intercepta exceções sem tratamento em threads de pool. Isso pode corromper o estado do aplicativo e, eventualmente, fazer com que aplicativos de suspensão, que podem ser muito difícil de depurar.  
  
### <a name="maximum-number-of-thread-pool-threads"></a>Número máximo de Threads de Pool  
 O número de operações que podem ser enfileiradas para o pool de threads é limitado apenas pela memória disponível; No entanto, o pool de threads limita o número de threads que podem estar ativas no processo de simultaneamente. Começando com o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o tamanho padrão do pool de threads para um processo depende de vários fatores, como o tamanho do espaço de endereço virtual. Um processo pode chamar o <xref:System.Threading.ThreadPool.GetMaxThreads%2A> método para determinar o número de threads.  
  
 Você pode controlar o número máximo de threads, usando o <xref:System.Threading.ThreadPool.GetMaxThreads%2A> e <xref:System.Threading.ThreadPool.SetMaxThreads%2A> métodos.  
  
> [!NOTE]
>  Nas versões do .NET Framework 1.0 e 1.1, o tamanho do pool de threads não pode ser definido no código gerenciado. Código que hospeda o common language runtime pode definir o tamanho usando `CorSetMaxThreads`, definido em mscoree.h.  
  
### <a name="thread-pool-minimums"></a>Mínimo de Pool de thread  
 O pool de threads fornece novos threads de trabalho ou threads de conclusão de e/s sob demanda até atingir um mínimo especificado para cada categoria. Você pode usar o <xref:System.Threading.ThreadPool.GetMinThreads%2A> método para obter esses valores mínimos.  
  
> [!NOTE]
>  Quando a demanda for baixa, o número real de threads de pool pode ficar abaixo os valores mínimos.  
  
 Quando um mínimo for atingido, o pool de threads pode criar threads adicionais ou aguarde até que algumas tarefas são concluídas. Começando com o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], o pool de threads cria e destrói threads de trabalho para otimizar a taxa de transferência, que é definida como o número de tarefas que são concluídas por unidade de tempo. Há muito poucos threads não podem fazer uso ideal dos recursos disponíveis, enquanto muitos threads podem aumentar a contenção de recursos.  
  
> [!CAUTION]
>  Você pode usar o <xref:System.Threading.ThreadPool.SetMinThreads%2A> método para aumentar o número mínimo de threads ociosos. No entanto, esses valores de aumento desnecessariamente podem causar problemas de desempenho. Se iniciam muitas tarefas ao mesmo tempo, todos eles podem parecer ser lenta. Na maioria dos casos o pool de threads terão um desempenho melhor com seu próprio algoritmo para alocar threads.  
  
## <a name="skipping-security-checks"></a>Ignorar verificações de segurança  
 O pool de threads também fornece o <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> e <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> métodos. Use estes métodos somente quando você tiver certeza de que a pilha do chamador é irrelevante para qualquer verificação de segurança executada durante a execução da tarefa em fila. <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>e <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> ambos capturar a pilha do chamador, que é mesclada na pilha do thread do pool quando o thread começa a executar uma tarefa. Se é necessária uma verificação de segurança, toda a pilha deve ser verificada. Embora a verificação fornece segurança, ele também tem um custo de desempenho.  
  
## <a name="using-the-thread-pool"></a>Usando o Pool de threads  
 Começando com o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], a maneira mais fácil de usar o pool de threads é usar o [tarefa TPL (biblioteca paralela)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md). Por padrão, os tipos de biblioteca paralela como <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601> use threads do pool para executar tarefas. Você também pode usar o pool de threads chamando <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> de código gerenciado (ou `CorQueueUserWorkItem` código não gerenciado) e passando um <xref:System.Threading.WaitCallback> delegado que representa o método que executa a tarefa. É outra maneira de usar o pool de threads para a fila de itens de trabalho que estão relacionados a uma operação de espera usando o <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> método e passando um <xref:System.Threading.WaitHandle> que, quando sinalizado ou quando o tempo limite, chama o método representado pelo <xref:System.Threading.WaitOrTimerCallback> delegar. Threads de pool é usado para invocar métodos de retorno de chamada.  
  
## <a name="threadpool-examples"></a>Exemplos de ThreadPool  
 Os exemplos de código nesta seção demonstram o pool de threads, usando o <xref:System.Threading.Tasks.Task> classe, o <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> método e o <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> método.  
  
-   [Executando tarefas assíncronas com a biblioteca paralela de tarefas](#TaskParallelLibrary)  
  
-   [Executando o código de maneira assíncrona com QueueUserWorkItem](#ExecuteCodeWithQUWI)  
  
-   [Fornece dados de tarefa para QueueUserWorkItem](#TaskDataForQUWI)  
  
-   [Usando RegisterWaitForSingleObject](#RegisterWaitForSingleObject)  
  
<a name="TaskParallelLibrary"></a>   
### <a name="executing-asynchronous-tasks-with-the-task-parallel-library"></a>Executando tarefas assíncronas com a biblioteca paralela de tarefas  
 O exemplo a seguir mostra como criar e usar um <xref:System.Threading.Tasks.Task> objeto chamando o <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> método. Para obter um exemplo que usa o <xref:System.Threading.Tasks.Task%601> classe para retornar um valor de uma tarefa assíncrona, consulte [como: retornar um valor de uma tarefa](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).  
  
 [!code-csharp[System.Threading.Tasks.Task#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.task/cs/startnew.cs#01)]
 [!code-vb[System.Threading.Tasks.Task#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.task/vb/startnew.vb#01)]  
  
<a name="ExecuteCodeWithQUWI"></a>   
### <a name="executing-code-asynchronously-with-queueuserworkitem"></a>Executando o código de maneira assíncrona com QueueUserWorkItem  
 O exemplo a seguir coloca uma tarefa muito simple, representada pelo `ThreadProc` método, usando o <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> método.  
  
 [!code-cpp[Conceptual.ThreadPool#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.ThreadPool#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source1.cs#1)]
 [!code-vb[Conceptual.ThreadPool#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source1.vb#1)]  
  
<a name="TaskDataForQUWI"></a>   
### <a name="supplying-task-data-for-queueuserworkitem"></a>Fornece dados de tarefa para QueueUserWorkItem  
 O seguinte exemplo de código usa o <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> método para enfileirar uma tarefa e fornecer os dados para a tarefa.  
  
 [!code-cpp[Conceptual.ThreadPool#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.ThreadPool#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source2.cs#2)]
 [!code-vb[Conceptual.ThreadPool#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source2.vb#2)]  
  
<a name="RegisterWaitForSingleObject"></a>   
### <a name="using-registerwaitforsingleobject"></a>Usando RegisterWaitForSingleObject  
 O exemplo a seguir demonstra vários recursos de threads.  
  
-   Uma tarefa para execução pelo enfileiramento de mensagens <xref:System.Threading.ThreadPool> segmentos, com o <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> método.  
  
-   Sinalização de uma tarefa a ser executada com <xref:System.Threading.AutoResetEvent>. Consulte [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).  
  
-   Tratamento de tempos limite e sinais com um <xref:System.Threading.WaitOrTimerCallback> delegate.  
  
-   Cancelando uma tarefa em fila com <xref:System.Threading.RegisteredWaitHandle>.  
  
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
