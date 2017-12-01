---
title: "Noções básicas de threading gerenciado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62c207f6074e33813887c6903f5285ee72d14e85
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="managed-threading-basics"></a>Noções básicas de threading gerenciado
Os cinco primeiros tópicos desta seção são projetados para ajudá-lo a determinar quando usar threading gerenciado e explicar alguns recursos básicos. Para obter informações sobre classes que fornecem recursos adicionais, consulte [recursos e objetos de Threading](../../../docs/standard/threading/threading-objects-and-features.md) e [visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 O restante da capa desta seção abordam os tópicos avançados tópicos, incluindo a interação de threading gerenciado com o sistema operacional Windows.  
  
> [!NOTE]
>  No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], a biblioteca de tarefas paralelas e em PLINQ fornecem APIs para o paralelismo de tarefa e dados em programas multithread. Para obter mais informações, consulte [Programação paralela](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Threads e threading](../../../docs/standard/threading/threads-and-threading.md)  
 Discute as vantagens e desvantagens de vários threads e descreve os cenários em que você pode criar threads ou use threads de pool.  
  
 [Exceções em threads gerenciados](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 Descreve o comportamento de exceções sem tratamento em threads para diferentes versões do .NET Framework, em particular as situações em que eles resultam no encerramento do aplicativo.  
  
 [Sincronizando dados para multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 Descreve estratégias para sincronizar dados em classes que serão usados com vários threads.  
  
 [Estados de thread gerenciado](../../../docs/standard/threading/managed-thread-states.md)  
 Descreve os estados de thread básico e explica como detectar se um thread está em execução.  
  
 [Threads em primeiro plano e em segundo plano](../../../docs/standard/threading/foreground-and-background-threads.md)  
 Explica as diferenças entre os threads de primeiro plano e plano de fundo.  
  
 [Threading gerenciado e não gerenciado no Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 Discute o relacionamento entre threading gerenciado e lista equivalentes gerenciados para threading de APIs do Windows e discute a interação de apartments COM e threads gerenciados.  
  
 [Thread.Suspend, coleta de lixo e pontos seguros](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 Descreve o thread suspensão e coleta de lixo.  
  
 [Armazenamento local de thread: campos estáticos relativos a thread e slots de dados](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 Descreve os mecanismos de armazenamento relativos a thread.  
  
 [Cancelamento em threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 Descreve como assíncronas ou demoradas operações síncronas podem ser canceladas usando um token de cancelamento.  
  
## <a name="reference"></a>Referência  
 <xref:System.Threading.Thread>  
 Fornece documentação de referência para o **Thread** classe que representa um segmento gerenciado, se ele veio com código não gerenciado ou foi criado em um aplicativo gerenciado.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Fornece uma maneira segura de implementar multithread juntamente com objetos de interface do usuário.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Visão geral dos primitivos de sincronização](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Descreve as classes gerenciadas usadas para sincronizar as atividades de vários threads.  
  
 [Práticas recomendadas de threading gerenciado](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Descreve problemas comuns com multithread e estratégias para evitar problemas.  
  
 [Programação paralela](../../../docs/standard/parallel-programming/index.md)  
 Descreve a biblioteca paralela de tarefas e PLINQ, que simplifica muito o trabalho de criação de aplicativos do .NET Framework multithread e assíncronos.
