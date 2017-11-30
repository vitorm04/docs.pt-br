---
title: "Estruturas de dados para programação paralela"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f35c5382455021f0a001604367e59204ce4ad93c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="data-structures-for-parallel-programming"></a>Estruturas de dados para programação paralela
O .NET Framework versão 4 apresenta vários novos tipos que são úteis para programação paralela, incluindo um conjunto de classes de coleção simultâneas, primitivos de sincronização leve e tipos de inicialização lenta. Você pode usar esses tipos de qualquer código de aplicativo multithread, incluindo o PLINQ e a biblioteca paralela de tarefas.  
  
## <a name="concurrent-collection-classes"></a>Classes de coleção simultâneas  
 A coleção de classes de <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace fornecem thread-safe adicionar e remover operações que sempre que possível, evite bloqueios e usará o bloqueio refinado em que os bloqueios são necessários. Ao contrário de coleções que foram introduzidas em versões do .NET Framework 1.0 e 2.0, uma classe de coleção simultâneas não requer código de usuário para fazer qualquer bloqueio ao acessar itens. As classes de coleção simultâneas podem melhorar significativamente o desempenho em tipos como <xref:System.Collections.ArrayList?displayProperty=nameWithType> e <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> (com bloqueio de implementado pelo usuário) em cenários onde vários threads adicionam e remover itens de uma coleção.  
  
 A tabela a seguir lista as novas classes de coleção simultâneas:  
  
|Tipo|Descrição|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|Fornece funcionalidades de bloqueio e delimitação para coleções thread-safe que implementam <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>. Threads de produtor bloqueiam se nenhum slot está disponível ou se a coleção está cheio. Threads de consumidor bloqueiam se a coleção está vazia. Esse tipo também oferece suporte a acesso sem bloqueio de produtores e consumidores. <xref:System.Collections.Concurrent.BlockingCollection%601>pode ser usado como uma classe base ou fazendo o armazenamento para fornecer o bloqueio e delimitadora para qualquer classe de coleção que oferece suporte a <xref:System.Collections.Generic.IEnumerable%601>.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Uma implementação de recipiente de thread-safe que fornece escalonável adicionar e operações de obtenção.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Um tipo de dicionário simultâneo e escalonável.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|Uma fila de FIFO simultânea e escalonável.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Uma pilha de UEPS simultânea e escalonável.|  
  
 Para obter mais informações, veja [Coleções thread-safe](../../../docs/standard/collections/thread-safe/index.md).  
  
## <a name="synchronization-primitives"></a>Primitivos de sincronização  
 Novos primitivos de sincronização no <xref:System.Threading?displayProperty=nameWithType> namespace habilitar simultaneidade refinada e desempenho mais rápido, evitando caros mecanismos de bloqueio encontrados no código herdado de multithreading. Alguns dos novos tipos, como <xref:System.Threading.Barrier?displayProperty=nameWithType> e <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> têm não correspondentes em versões anteriores do .NET Framework.  
  
 A tabela a seguir lista os novos tipos de sincronização:  
  
|Tipo|Descrição|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Permite que vários threads funcionar em um algoritmo em paralelo, fornecendo um ponto em que cada tarefa pode sinalizar sua chegada e então bloquear até que algumas ou todas as tarefas foram recebidos. Para saber mais, consulte [Barreira](../../../docs/standard/threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Simplifica a cenários de bifurcação e junção, fornecendo um mecanismo fácil de reunião. Para obter mais informações, consulte [CountdownEvent](../../../docs/standard/threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|Um primitivo de sincronização semelhante ao <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>. <xref:System.Threading.ManualResetEventSlim>é leve, mas só pode ser usado para comunicação entre processos. Para obter mais informações, consulte [ManualResetEvent e ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md).|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Um primitivo de sincronização que limita o número de threads que simultaneamente pode acessar um recurso ou um pool de recursos. Para obter mais informações, consulte [Semaphore e SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|Um primitivo de bloqueio de exclusão mútua que faz com que o thread que está tentando adquirir o bloqueio aguarda em um loop ou *rotação*, por um período de tempo antes de gerar seu quantum. Em cenários em que a espera para o bloqueio deve ser curto, <xref:System.Threading.SpinLock> oferece melhor desempenho que outras formas de bloqueio. Para obter mais informações, consulte [SpinLock](../../../docs/standard/threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Um tipo de pequeno e leve que irá girar por um tempo especificado e, eventualmente, coloque o thread em um estado de espera se a contagem de rotação é excedida.  Para obter mais informações, consulte [SpinWait](../../../docs/standard/threading/spinwait.md).|  
  
 Para obter mais informações, consulte:  
  
-   [Como usar SpinLock para sincronização de baixo nível](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
-   [Como: sincronizar operações simultâneas com uma barreira](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="lazy-initialization-classes"></a>Classes de inicialização lenta  
 Com a inicialização lenta, a memória de um objeto não está alocada até que seja necessário. Inicialização lenta pode melhorar o desempenho distribuindo as alocações de objeto uniformemente entre o tempo de vida de um programa. Você pode habilitar a inicialização lenta para qualquer tipo personalizado ao encapsular o tipo <xref:System.Lazy%601>.  
  
 A tabela a seguir lista os tipos de inicialização lenta:  
  
|Tipo|Descrição|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Fornece leve, thread-safe-inicialização lenta.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Fornece um valor inicializado em uma base por thread, com cada thread lentamente-invocar a função de inicialização.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Fornece métodos estáticos que não seja necessário alocar uma instância dedicada, inicialização lenta. Em vez disso, eles usam referências para garantir destinos foram inicializados conforme eles são acessados.|  
  
 Para obter mais informações, veja [Inicialização lenta](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="aggregate-exceptions"></a>Exceções de agregação  
 O <xref:System.AggregateException?displayProperty=nameWithType> tipo pode ser usado para capturar várias exceções que são geradas ao mesmo tempo em threads separados e retorná-los para o thread de junção como uma única exceção. O <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> usam tipos e PLINQ <xref:System.AggregateException> extensivamente para essa finalidade. Para obter mais informações, consulte [NIB: como: manipular exceções lançadas por tarefas](http://msdn.microsoft.com/en-us/d6c47ec8-9de9-4880-beb3-ff19ae51565d) e [como: manipular exceções em uma consulta PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Threading?displayProperty=nameWithType>  
 [Programação paralela](../../../docs/standard/parallel-programming/index.md)
